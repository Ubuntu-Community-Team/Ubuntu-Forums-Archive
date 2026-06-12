---
title: "Conditional variables-Posix threads"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by bois on 2009-05-03
Hello,

consider a bunch of threads which want to execute a while
 loop in parallel but after each iteration of while loop,
 we need a synchornization.That is, we have a global 
 count varibale which is equal to zero at beginig of each iteration and at the end of each iterartion this variable should be equal to numberof threads before satrting the next iteration of while loop(this helps us to be sure that all threads has already finished the iteration).
so I decided that at the end of while loop all threads will incrementthe counter value and then one of threads(for example thread 0)checks if the value of counter is equal to number of threads.As soon as the counter value becomes equal to numberOfthreads it signals this change to the other threads which are waiting for this condition ,so they can start the next while loop iterartion.
 
My question is how should I reset the value of counter variable
to zero?that should be done once(in one of threads) and just before the next iterartion of while loop,I am also wondering 
if the code below is logicaly correct.

[code]
while(k<n){

if(thread->id==0){	
			
for(;;)//infinite for loop
{
     pthread_mutex_lock(&condition_mutex );
       if( count==NUMBEROFTHREADS )
       pthread_cond_broadcast(&condition_cond);
     pthread_mutex_unlock( &condition_mutex );
     break;
}

else{

pthread_mutex_lock( &condition_mutex );
while( count <NUMBEROFTHREADS )
{
    pthread_cond_wait( &condition_cond, &condition_mutex );
 }
			
pthread_mutex_unlock( &condition_mutex );

}
			
k++;			
			

		}
		
		k=k+1;
	}
			
[\code]			
        		
			
		}
		else
		{
			for(; ;)
			{	pthread_mutex_lock( &condition_mutex );
				while( count <2 )
      				{
         				pthread_cond_wait( &condition_cond, &condition_mutex );
      				}
			
		 		pthread_mutex_unlock( &condition_mutex );
				break;
			}
			
			
			

		}
		
		k=k+1;
	}


Thanks,
regards

---

