# linked-list
#include <stdio.h>
#include <stdlib.h>

struct node
{
int data;
struct node* next;
};

typedef struct node node;

node* createNod(int value)
{
  node* new=(node*)malloc(sizeof(node));
  new->data=value;
  new->next=NULL;
  return new;
}

node* createLL()
{
  int sizell = 0;
  printf("Enter size: ");
  scanf("%d", &sizell); 
  
  int tempvalue = 0;
  printf("Enter value[1]: ");
  scanf("%d", &tempvalue);   
  
  node* head = createNod(tempvalue);
  node* ptr=head;    
  
  for(int i =1 ; i <sizell ; i++)  
  {
    printf("Enter value[%d]: ", i+1);  
    scanf("%d", &tempvalue);            
    ptr->next= createNod(tempvalue);    
    ptr=ptr->next;                      
  }
 return head;
}

void* displayLL(node* head)
{
  node* iterator=head;
  while(iterator)
  {
  if(iterator->next)
  {
    printf("%d-->",iterator->data);
  }
  else
  {
    printf("%d->NULL", iterator->data);
  }
  iterator= iterator->next;
 }
}

void deleteNod(node** head)
{
 int position;
 printf("\n Enter NODE: ");
 scanf("%d", &position);
 node* current=*head;
 node* previous=*head;
 if(*head==NULL)
 {
   printf("the node is empty");
 }
  else if(position==1)
 {
   *head=current->next;
   free(current);
   current=NULL;
 }
  else
  {
    while(position!=1)
    {
      previous=current;
      current=current->next;
      position--;
    }  
    previous->next=current->next;
    free(current);
    current=NULL;
  }
}
  

int main(void)
{
  
  node* llhead = createLL();
  displayLL(llhead);
  deleteNod(&llhead);
  displayLL(llhead); 
 return 0;
}
