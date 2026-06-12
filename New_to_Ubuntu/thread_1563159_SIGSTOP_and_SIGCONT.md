---
title: "SIGSTOP and SIGCONT"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by -A- on 2010-08-28
Where exactly does the SIGSONT start the execution of a stopped program from? Im assuming from where it left off in the code, but its not doing that for me.
My basic aim is to create a number of child processes and not let any of them start their execution till all of them are created. So after creating I issue a kill(getpid(),19) from inside the child process.
Hopwever when I issue SigCONT to the child from the parent it doesnt continue. Why is this?

Heres my code:

```
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/types.h>

typedef struct
{
        char stID[12];
        char stName[50];
        int T,t1,t2,t3;
        pid_t cpid;
}stData;

int main()
{
        stData dataArray[50];
        int i,elem;
        FILE *inpFile;

        inpFile=fopen("testfile.txt","r");

        fscanf(inpFile,"%d", &elem);

        for(i=0;i<elem;i++)
        {
                fscanf(inpFile, "%s %s %d %d %d %d", dataArray[i].stID,
                dataArray[i].stName, &dataArray[i].T, &dataArray[i].t1,
                &dataArray[i].t2, &dataArray[i].t3);
        }

        fclose(inpFile);

        for(i=0;i<elem;i++)
        {
                printf("\n%s %s %d %d %d %d \n", dataArray[i].stID,
                dataArray[i].stName, dataArray[i].T, dataArray[i].t1,
                dataArray[i].t2, dataArray[i].t3);
        }

        for(i=0;i<elem;i++)
        {
                dataArray[i].cpid=fork();
                printf("%d ", dataArray[i].cpid);
                if(dataArray[i].cpid==0)
                {
                        kill(getpid(),19);
                        printf("Kids respond.\n");

                        printf("Child process with pid %d ", getpid());
                        printf("Kids responding.\n");
                        exit(EXIT_SUCCESS);

                }
        }
        printf("\n Parent process after making the kids.\n");


        for(i=0;i<elem;i++)
        {
                printf("%d ",dataArray[i].cpid);
                    kill(dataArray[i].cpid,18);
        }

        return 0;
}


        


```

---

### Post by -A- on 2010-08-29
Umm...so it doesn't exactly not work. It randomly finishes till some point in the program execution.

:(

Any clues?

Full code:

```
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/types.h>
#include<signal.h>
#include<sys/wait.h>

typedef struct 
{
    char stID[12];
    char stName[50];
    int T,t1,t2,t3;
    pid_t cpid;
}stData;

int main()
{
    stData dataArray[50];
    int i,elem;
    FILE *inpFile;
    pid_t pid1,pid2,pid3,mainpid; 
    
    mainpid=getpid();
    inpFile=fopen("testfile.txt","r");
    
    fscanf(inpFile,"%d", &elem);
    
    for(i=0;i<elem;i++)
    {
        fscanf(inpFile, "%s\t%s\t%d\t%d\t%d\t%d", dataArray[i].stID,
        dataArray[i].stName, &dataArray[i].T, &dataArray[i].t1,
        &dataArray[i].t2, &dataArray[i].t3);
    }

    fclose(inpFile);

    for(i=0;i<elem;i++)
    {
        printf("\n%s %s %d %d %d %d \n", dataArray[i].stID,
                dataArray[i].stName, dataArray[i].T, dataArray[i].t1, 
                dataArray[i].t2, dataArray[i].t3);
    }
    
    
    for(i=0;i<elem;i++)
    {
        dataArray[i].cpid=fork();
        printf("%d ", dataArray[i].cpid);
        if(dataArray[i].cpid==0)
        {
            kill(getpid(),19);

            if(dataArray[i].T<dataArray[i].t1)
            {    
                pid1=fork();
                if(pid1==0)
                {
                    printf(" %s %s does not have time for the course.\n",
                    dataArray[i].stID, dataArray[i].stName
                    );
                    exit(0);
                }
                else if(pid1>0)
                {
                    waitpid(pid1,NULL,WCONTINUED);
                    exit(0);
                }
                else{ printf("Fork Failed.\n");}
            }
            else if(dataArray[i].T>=dataArray[i].t1)
            {
                pid1=fork();
                if(pid1==0)
                {
                    printf("First question done.\n");
                    if(dataArray[i].T<dataArray[i].t1+dataArray[i].t2)
                    {
                        printf("%s %s can only do the first question.\n", dataArray[i].stID, dataArray[i].stName);
                        exit(0);
                    }
                    else
                    {
                        pid2=fork();
                        if(pid2==0)
                        {
                            printf("Second question done.\n");
                            if(dataArray[i].T<dataArray[i].t1+dataArray[i].t2+dataArray[i].t3)
                            {
                                printf("%s %s can only do the first two questions.\n", dataArray[i].stID, dataArray[i].stName);
                                exit(0);
                            }
                            else
                            {
                                pid3=fork();
                                if(pid3==0)
                                {
                                    printf("%s %s can do all assignment questions.\n");
                                    exit(0);
                                }
                                else if(pid3>0)
                                {
                                    waitpid(pid3,NULL,WCONTINUED);
                                    exit(0);
                                }
                                else{printf("Fork failed.\n");}
                            }
                        }
                        else if(pid2>0)
                        {
                            waitpid(pid2,NULL,WCONTINUED);
                            exit(0);
                        }
                        else{printf("Fork failed.\n");}
                    }
                }

                else if(pid1>0)
                {
                    waitpid(pid1,NULL,WCONTINUED);
                    exit(0);
                }            
                else {printf("Fork Failed.\n");}
            }
//            printf("Kids respond.\n");
//            
//            printf("Child process with pid %d ", getpid());
//            printf("Kids responding.\n");
//            exit(EXIT_SUCCESS);
            
        }
    }
    printf("\n Parent process after making the kids.\n");

    if(getpid()==mainpid)
    {
    for(i=0;i<elem;i++)
    {
        printf("%d ",dataArray[i].cpid);
        kill(dataArray[i].cpid,18);
        waitpid(dataArray[i].cpid, NULL, WCONTINUED);
    }
    }

    for(i=0;i<elem;i++)
    {
        waitpid(dataArray[i].cpid,NULL,0);
    }
    return (0);
}
```

---

### Post by ThunddeR on 2010-08-29
?

---

