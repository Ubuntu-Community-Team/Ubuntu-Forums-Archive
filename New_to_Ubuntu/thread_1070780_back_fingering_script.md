---
title: "back fingering script"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-15
Hi friends,
I use an account in my department server. It allows us to 'finger' users.

'finger' will show the last login time, from where you did the login, did you get a new mail and when is the last time you read your mail. 

Now I want to know if there is anyway I can track who is doing fingering to my account and log it in file. 

Thanks for your help

---

### Post by indeterminate on 2009-02-15
Well, an administrator could probably set up a log of all finger requests that the server receives, but it would be inconvenient to split up that log by user and send each user a log of requests about them.

I'm almost certain that unprivileged users have no way of finding out who's been fingering them.

---

### Post by lswb on 2009-02-15
If you have admin priveledges yourself you can write a wrapper script for finger that writes to a log file before actually calling the finger command.

---

### Post by ibuclaw on 2009-02-15
there are two applications that read the logfiles on a local machine.

```
lastlog
```
displays the last time you logged in. Though you can specify just your own user account like so:
```
lastlog -u **username**
```
or you can display all successful logins
```
lastlog -a
```

The other application being
```
faillog
```
displays all instances of the times that you have failed to authenticate yourself on the machine.
The same switches shown above work for faillog too.


Similarly, the command **last** or **lastb** do similar things too.

Regards
Iain

---

### Post by cosine352 on 2009-02-15
ok I was thinking if is it possible to log the update time for the .plan file. actually everytime some one do the finger on the user the .plan file is being updated. So is there any way to log the update time for the .plan file ? 

In this way I will only know when but not who.

I do not have administration privileges

---

### Post by cosine352 on 2009-02-15
> **tinivole said:**
> there are two applications that read the logfiles on a local machine.

```
lastlog
```
displays the last time you logged in. Though you can specify just your own user account like so:
```
lastlog -u **username**
```
or you can display all successful logins
```
lastlog -a
```

The other application being
```
faillog
```
displays all instances of the times that you have failed to authenticate yourself on the machine.
The same switches shown above work for faillog too.


Similarly, the command **last** or **lastb** do similar things too.

Regards
Iain

Nice information. the 'last' command is good to know about when and where did you login but not the time when someone finger your account though.

---

### Post by cosine352 on 2009-02-15
guys I have made a script that will log the update time of file '.plan' in my department server. Everytime someone 'finger' the update time of '.plan' file changes and this script will log that event. 

It is not a very good way to do it (any improvement is greatly appreciated)

Here is the script
> while true
# this script will log the update time of file '.plan' to a file 'plan_data'
do
   ls -lu .plan > d1
   diff d1 d2 >> plan_data
   cat d1 > d2
   sleep 10
done 
 

what it will do is 
> ls -lu .plan > d1

get the update time of .plan and write it to file 'd1'. Now there is an empty file 'd2' I have created before
> diff d1 d2 >> plan_data

this will write the difference (update time) to file 'plan_data' and new information will be appended (>>). 
> cat d1 > d2

this will write the content of file 'd1' to 'd2'. So now you have same content so no 'diff' in 'd1' and 'd2' and nothing will be written to 'plan_data'. 

If '.plan' get updated, the content of 'd1' will change and the 'diff' will be appeneded to 'plan_data'

[COLOR="Red"]Drabacks[/COLOR]

you need to start with d1, d2 as empty files. So before run the script each time you need to 

> rm d1 d2
touch d1 d2

Also the out put will be like this

> 1d0
< -rw-r--r-- 1 user user 0 2009-02-15 22:21 .plan
1c1
< -rw-r--r-- 1 user user 0 2009-02-15 22:22 .plan
---
> -rw-r--r-- 1 user user 0 2009-02-15 22:21 .plan


next time '.plan' is updated it will create two lines 
> 
1c1
< -rw-r--r-- 1 user user 0 2009-02-15 22:22 .plan
---
> -rw-r--r-- 1 user user 0 2009-02-15 22:21 .plan

as the 
> diff d1 d2 

is 'just previous update time' (file d2) and the 'most recent update time' (d1)

---

### Post by cosine352 on 2009-02-18
This is the most updated script. This will record the update time of the file '.plan'. In this way I will know when somebody has fingerd in my department server. This will not tell you who just when. 

> #!/bin/sh
while true
do
  ls -lu .plan > d1
  diff d1 d2 | awk NR==2 >> dp
  cat d1 > d2
  sleep 10s
done

---

### Post by cosine352 on 2009-03-05
This is the script I am using now to check who did fingering to my account in my department server. 
This will save the time and username if some user uses the command 'finger' (the first line and save it to file 'df') and also will record what time your account got fingered (saved to file 'df'). By matching the two time (in file 'df' and 'dp') you can know who did the fingering.


> #!/bin/sh
while true

do
  ps -A -o stime,user,comm | perl -e '($_ = join "",<>) =~ s/(\t)/     /g; print;' | grep finger >> df
  ls -lu .plan | grep -v -f dp >> dp
  perl -e 'select(undef,undef,undef,.1)'
done

---

