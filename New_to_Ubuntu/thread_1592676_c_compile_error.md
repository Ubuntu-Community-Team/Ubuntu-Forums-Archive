---
title: "c compile error"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by newport_j on 2010-10-10
[code]

void depart(void)   /* Event function for departure of a job from a particular
                          station.  */

    {
         int station, job_type_queue, task_queue;

         /* Determine the station from which the job is departing. */
    
        job_type  = transfer[3];
        task      = transfer[4];
        station   = route[job_type][task];

        /* Check to see whether the queue for this station is empty */

        if (list_size[station] == 0)  {

           /* The queue for this station is empty, so make a machine in this
              station idle.  */

        --num_machines_busy[station];
        timest((float) num_machines_busy[station], station);
 }

     else  {
         
         /* The queue is nonempty, so start serivce o0n first job in queue. */
     
        list_remove(FIRST, station);
 
        /* Tally this same delay for this job type */

        sampst(sim_time - transfer[1], station);

        /* Tally this same delay for this job type. */

        job_type_queue = transfer[2];
        task_queue     = transfer[3];
        sampst(sim_time - transfer[1], num_stations + job_type_queue);

        /* Schedule end of service for this job at this station. Note defining  
           attributes beyond the first two for the event record before invoking
           event_schedule. */
      
       transfer[3] = job_type_queue;
       transfer[4] = task_queue; 
        
       event_schedule(sim_time + erlang(2, mean_service[job_type_queue][task_queue],STREAM_SERVICE),EVENT_DEPARTURE);

       /* If the current departing job has one or more tasks yet to be done, send the job to the next stations on its route. */


       if  (task < num_tasks[job_type])  {
           ++task;
           arrive(2);
      }
  }
  

    void report(void)  /* Report Generator function. */
    { 
        int   i;
        float overall_avg_job_tot_delay, avg_job_tot_delay, sum_probs;

        /*  Compute the average total delay in queue for each job type and the 
            overall average job total delay. */

        fprintf(outfile, "\n\n\n\nJob type    Average total delay in queue");
        overall_avg_job_tot_delay = 0.0;
        sum_probs                 = 0.0;
        for (i = 1; i <= num_job_types; ++i)  {
            avg_job_tot_delay = sampst(0.0, -(num_stations + i))  * num_tasks[i];
            fprintf(outfile, "\n\n%4d%27.3f", i, avg_job_tot_delay);
            overall_avg_job_tot_delay += (prob_distrib_job_type[i] - sum_probs)
                                         * avg_job_tot_delay;
            sum_probs = prob_distrib_job_type[i];
         } 
         fprintf(outfile, "\n\nOverall average job total delay = %10.3f\n",
                 overall_avg_job_tot_delay);

         /* Compute the average number in queue, the average utilization, and the average delay in queue for each station. */

         fprintf(outfile,"\n\n\n Work    Average Number     Average       Average delay");
         fprintf(outfile,"\nstation       in queue         Utilization      in queue");
         for (j = 1; j <= num_stations; ++j)
             fprintf(outfile, "\n\n%4d%17.3f%17.3f%17.3f",  j,  filest(j),
                     timest(0.0, -j) / num_machines[j], sampst(0.0, -j));

    } 

[/code|



The code above when compiled gives the following output.




james@jyunkernetwork:~/Desktop/jobshop$ gcc jobshop.c simlib.c -o jobshop
jobshop.c: In function ‘depart’:
jobshop.c:296: error: expected declaration or statement at end of input

I am unsure where the error is. The line 296 is the last one in the shown code, The one with the }.


Where is the Programming Talk section. I will post there in the future.


Newport_j

---

### Post by Vaphell on 2010-10-10
could you fix the closing code tag


ubuntu forums -> development & programming (down the page) -> programming talk

---

### Post by talonmies on 2010-10-11
Let's try again, shall we:

```
void depart(void) /* Event function for departure of a job from a particular station. */ 
{
    int station, job_type_queue, task_queue;

    /* Determine the station from which the job is departing. */

    job_type = transfer[3];
    task = transfer[4];
    station = route[job_type][task];

    /* Check to see whether the queue for this station is empty */
    if (list_size[station] == 0) {
        /* The queue for this station is empty, so make a machine in this station idle. */
        --num_machines_busy[station];
        timest((float) num_machines_busy[station], station);
    } else {

        /* The queue is nonempty, so start serivce o0n first job in queue. */

        list_remove(FIRST, station);

        /* Tally this same delay for this job type */

        sampst(sim_time - transfer[1], station);

        /* Tally this same delay for this job type. */

        job_type_queue = transfer[2];
        task_queue = transfer[3];
        sampst(sim_time - transfer[1], num_stations + job_type_queue);

        /* Schedule end of service for this job at this station. Note defining
        attributes beyond the first two for the event record before invoking
        event_schedule. */

        transfer[3] = job_type_queue;
        transfer[4] = task_queue;

        event_schedule(sim_time + erlang(2, mean_service[job_type_queue][task_queue],STREAM_SERVICE),EVENT_DEPARTURE);

        /* If the current departing job has one or more tasks yet to be done, send the job to the next stations on its route. */
        if (task < num_tasks[job_type]) {
            ++task;
            arrive(2);
        }
    }


void report(void) /* Report Generator function. */
{
    int i;
    float overall_avg_job_tot_delay, avg_job_tot_delay, sum_probs;

    /* Compute the average total delay in queue for each job type and the
    overall average job total delay. */

    fprintf(outfile, "\n\n\n\nJob type Average total delay in queue");
    overall_avg_job_tot_delay = 0.0;
    sum_probs = 0.0;
    for (i = 1; i <= num_job_types; ++i) {
        avg_job_tot_delay = sampst(0.0, -(num_stations + i)) * num_tasks[i];
        fprintf(outfile, "\n\n%4d%27.3f", i, avg_job_tot_delay);
        overall_avg_job_tot_delay += (prob_distrib_job_type[i] - sum_probs)
        * avg_job_tot_delay;
        sum_probs = prob_distrib_job_type[i];
    }
    fprintf(outfile, "\n\nOverall average job total delay = %10.3f\n",
    overall_avg_job_tot_delay);

    /* Compute the average number in queue, the average utilization, and the average delay in queue for each station. */
    fprintf(outfile,"\n\n\n Work Average Number Average Average delay");
    fprintf(outfile,"\nstation in queue Utilization in queue");
    for (j = 1; j <= num_stations; ++j)
        fprintf(outfile, "\n\n%4d%17.3f%17.3f%17.3f", j, filest(j),
            timest(0.0, -j) / num_machines[j], sampst(0.0, -j));

} 

```

And when we do, it is pretty obvious that depart() has unbalanced braces. When you take the time to format code in a sensible fashion, these sorts of "day 0" errors become rather obvious......

---

