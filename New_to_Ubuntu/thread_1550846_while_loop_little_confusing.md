---
title: "while loop little confusing"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by navaneethan on 2010-08-11
int main()
{
   int a=5;
   while(a==5);
     printf("a is not five");
}

int main()
{
   int a=5;
   while(a!=5){
     printf("a is not five");break;}

}

what is the difference between both while loops?

while(condition)
{
}

and 

while(condition);
xxxxxxxx;
xxxxxxx;

getting little confuse

---

### Post by hudsonl on 2010-08-11
> **navaneethan said:**
> int main()
{
   int a=5;
   while(a==5);
     printf("a is not five");
}

int main()
{
   int a=5;
   while(a!=5){
     printf("a is not five");break;}

}

what is the difference between both while loops?

while(condition)
{
}

and 

while(condition);
xxxxxxxx;
xxxxxxx;

getting little confuse

The first one is an infinite loop ... never terminates ... it also never prints anything, because the while statement does not have a begin "{" and end "}" of block.  The squiggly brackets for the while will execute everything in the block as long as the while condition is true.

It's an infinite loop because you initialize a=5 in your declaration ... so the while statement is ALWAYS true because the value of "a" never changes ... and there is no block to change the value of "a" ... for example: **a++;**


The second while statement** would be** an infinite loop ... except for two reasons:
1. The "break" forces it out of the while statement.  Thus it never changes the value of "a" and there is a begin "{" and end "}" of block .... but again a never changes and the "break" is the only thing that saves it.
2. It **never executes** the while loop because "a" is initialized to 5 and while will ONLY execute when NOT equal to 5 ... so never executes.

int main()
{
   int a=1;
   while(a!=5){
        printf("a is not five\n");
   a++;
  }

}

---

