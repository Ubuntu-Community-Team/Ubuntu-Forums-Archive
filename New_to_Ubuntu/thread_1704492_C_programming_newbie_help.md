---
title: "C programming newbie help"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by vuduz on 2011-03-10
bout an hour ago i decided i needed to learn programming, started on c cause a friend recommended it, something to do about learning structure.

right now im stuck on a basic addition exercise:

Code:


/* addition exercise */

#include <stdio.h>

main()
{
    int integer1, integer2, sum;     

    printf("Enter first integer\n");   
    scanf("%d", integer1);             
    printf("Enter second integer\n"); 
    scanf("%d", integer2);             
    sum = integer1 + integer2;        
    printf("Sum is %d\n", sum);       

    return 0;                            
}


After inputing both integers program crashes and i get one of these messages:

Process terminated with status 255 (0 minutes, 26 seconds

or

Process terminated with status -1073741819 (0 minutes, 5 seconds

---

### Post by pikabuntu on 2011-03-10
You want this instead:

```

#include <stdio.h>

int main(){
      int integer1;
      int integer2;
      int sum;

      printf("Enter first integer\n");
      scanf("%d", &integer1);
      printf("Enter second integer\n");
      scanf("%d", &integer2);
      sum = integer1 + integer2;
      printf("Sum is %d\n", sum);

      return 0;
}

```

scanf() is expecting to receive a pointer to a memory location.  In &integer1, the prefix & tells scanf() to use the memory location of integer1 rather than the value of integer1.  The reason that it does this is because when you pass a value to a function, you cannot change it.  However, if the value we are passing to the function is the location of a variable, we can just change what lives there.

---

