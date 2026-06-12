---
title: "Where it's at"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Langstracht on 2010-04-13
I think I must be missing something real simple, and real basic, but my problem is, if you will, "converting" terminal commands so as to have them run later with "at".

I think maybe the problem is that at is running in a different directory than the one terminal is using.  However, anything that would tell me where (ls, pwd) don't run in at either.

Can anyone straighten me out here?  Please and thank you.

---

### Post by Doctor Mike on 2010-04-13
> **Langstracht said:**
> I think I must be missing something real simple, and real basic, but my problem is, if you will, "converting" terminal commands so as to have them run later with "at".

I think maybe the problem is that at is running in a different directory than the one terminal is using.  However, anything that would tell me where (ls, pwd) don't run in at either.

Can anyone straighten me out here?  Please and thank you.
**NAME**

  at, batch, atq, atrm - queue, examine or delete jobs for later execution   **SYNOPSIS**

  **at**  [**-V**]  [**-q**  *queue*]  [**-f**  *file*]  [**-mldbv**]  **TIME**  
 **at -c**  *job*  [*job...*]  
 **atq**  [**-V**]  [**-q**  *queue*]  
 **atrm**  [**-V**]  *job*  [*job...*]  
 **batch**  [**-V**]  [**-q**  *queue*]  [**-f**  *file*]  [**-mv**]  [**TIME**]    **DESCRIPTION**

  **at**  and **batch**  read commands from standard input or a specified file which are to be executed at a later time, using the shell set by the user's environment variable **SHELL,**  the user's login shell, or ultimately **/bin/sh**.  **at**   executes commands at a specified time. **atq**   lists the user's pending jobs, unless the user is the superuser; in that case, everybody's jobs are listed.  The format of the output lines (one for each job) is: Job number, date, hour, job class. **atrm**   deletes jobs, identified by their job number. **batch**   executes commands when system load levels permit; in other words, when the load average drops below 0.8, or the value specified in the invocation of **atrun**.     **At**  allows fairly complex time specifications, extending the POSIX.2 standard.  It accepts times of the form  **HH:MM**  to run a job at a specific time of day. (If that time is already past, the next day is assumed.) You may also specify **midnight,**  **noon,**  or **teatime**  (4pm) and you can have a time-of-day suffixed with **AM**  or **PM**  for running in the morning or the evening. You can also say what day the job will be run, by giving a date in the form **month-name**  **day**  with an optional **year,**  or giving a date of the form **MMDDYY**  or **MM/DD/YY**  or **DD.MM.YY.**  The specification of a date *must*  follow the specification of the time of day. You can also give times like **now**  **+**  *count*  *time-units,*  where the time-units can be **minutes,**  **hours,**  **days,**  or **weeks**  and you can tell **at**  to run the job today by suffixing the time with **today**  and to run the job tomorrow by suffixing the time with **tomorrow.**  
  For example, to run a job at 4pm three days from now, you would do **at 4pm + 3 days,**  to run a job at 10:00am on July 31, you would do **at 10am Jul 31**  and to run a job at 1am tomorrow, you would do **at 1am tomorrow.**  
  */usr/share/doc/at-3.1.8/timespec*  contains the exact definition of the time specification. 
  For both **at** and **batch**,  commands are read from standard input or the file specified with the **-f**  option and executed. The working directory, the environment (except for the variables **TERM**,  **DISPLAY**  and **_**)  and the umask are retained from the time of invocation. An **at **-  or **batch -**  command invoked from a  **[su]("http://linux.about.com/library/cmd/blcmdl1_su.htm")(1)**  shell will retain the current userid. The user will be mailed standard error and standard output from his commands, if any. Mail will be sent using the command **/usr/sbin/sendmail**.  If **at**  is executed from a  **[su]("http://linux.about.com/library/cmd/blcmdl1_su.htm")(1)**  shell, the owner of the login shell will receive the mail. 
  The superuser may use these commands in any case. For other users, permission to use at is determined by the files */etc/at.allow*  and */etc/at.deny*.  
  If the file */etc/at.allow*  exists, only usernames mentioned in it are allowed to use **at**.  
  If */etc/at.allow*  does not exist, */etc/at.deny*  is checked, every username not mentioned in it is then allowed to use **at**.  
  If neither exists, only the superuser is allowed use of at. 
  An empty  */etc/at.deny*  means that every user is allowed use these commands, this is the default configuration.

---

### Post by Langstracht on 2010-04-13
Thanks for the immediate response.

As it is I have already read the manual page a number of times ... and was/am no further ahead.

A simple "use blah/blah/filename" instead of the terminal command (just) "filename" would be much appreciated.

Thank you.

---

