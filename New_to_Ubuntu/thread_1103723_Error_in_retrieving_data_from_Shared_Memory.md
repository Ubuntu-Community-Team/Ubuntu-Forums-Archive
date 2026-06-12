---
title: "Error in retrieving data from Shared Memory"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by coolyogs on 2009-03-23
Hi friends,

 I am beginner of UNIX shell programming,I wish to store integer data in the shared memory and i wish to retrive ths same which i have inserted.I wrote the following code but it is not working can you help me out


//Sender.c (acts as a Server)

#include <unistd.h>
#include <sys/shm.h>
#include <sys/ipc.h>

int main()
{
 int shmid,*res,*a;
 key_t key = 0x98;
 if((shmid = shmget(key,90,IPC_CREAT | 0666)) < 0)
 {
  perror("Error in Creation!");
  exit(1);
 }
 printf("shmid-->%d",shmid);
 if(( res = shmat(shmid,NULL,0))==(int *) -1)
 {
  perror("Error in Attachment!");
  exit(1);
 }
 a = res;
 printf("Enter the number:");
 scanf("%d",&a);
 exit(0);
}

//receiver.c (acts as a client)

#include <unistd.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main()
{
 int shmid;
 int *res,*R;
 key_t key = 0x98;
 if((shmid = shmget(key,0,0666)) < 0)
 {
  perror("Error in accessing Shared memory!");
  exit(1);
 }
 printf("shmid--->%d\n",shmid);
 if((res = shmat(shmid,NULL,0))==(int *)-1)
 {
  perror("Error in Attaching!");
  exit(1);
 }
 R = res;
 printf("Data in the shared memory is:%d\n",*R);
 exit(0);
}

Thanks in advance.

---

### Post by Xiong Chiamiov on 2009-03-23
This isn't shell programming, but C.  C is compiled into an executable, whereas shell scripting is interpreted, usually by bash.

It'll be a lot easier to read your code if you enclose it in [noparse]```

```[/noparse] tags.

You should move this to the Programming forum; you're much more likely to get help there.

---

