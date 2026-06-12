---
title: "how to execute run.sh script"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by tricia56 on 2009-04-01
I have downloaded a program and to start on Ubuntu the documentation says "execute run.sh script".  I have searched but all the instructions that I have read, for how to do this, are going over my head.  Can someone tell me how to this?  And, now I am confused.

(64 bit 9.04)

---

### Post by logic++ on 2009-04-01
> **tricia56 said:**
> I have downloaded a program and to start on Ubuntu the documentation says "execute run.sh script".  I have searched but all the instructions that I have read, for how to do this, are going over my head.  Can someone tell me how to this?  And, now I am confused.

(64 bit 9.04)

Open a terminal and locate the directory where the run.sh scripts is. For example let's say it is in your home folder:
```
cd /home/yourusername
```
```
sh run.sh
```
and you are done.

---

### Post by aeiah on 2009-04-01
navigate to it in a terminal and type:
```

sh run.sh

```

as a tip for navigating in the terminal if you've never done it before, use the command cd to change directory. your terminal starts in your home directory. if your folder is called program_folder and its on your desktop you'd do

```

cd Desktop/program_folder

```

pressing tab will autocomplete names of directories for you.

---

### Post by steeleyuk on 2009-04-01
You'll probably need to change the file so you can execute it. This is called setting the execute bit.

Two ways to do that.

1) Right click the file and select the Permissions tab, then choose Allow executing file as program
2) Using the terminal, navigate to the directory where the file is. Enter this command: chmod +x nameoffile.sh

---

### Post by aeiah on 2009-04-01
im such a slowpoke :'(

---

### Post by ibuclaw on 2009-04-01
Or make the script executable
```
chmod +x run.sh
```
then execute it with using **./**
```
./run.sh
```

Regards
Iain

---

### Post by logic++ on 2009-04-01
Let's be optimistic. Since you are told to execute a "run.sh" script then it most probably is already executable. So, initially try the first suggestions: ```
sh run.sh
``` and if that doesn't work, post the error you get. You will need though to be in the directory that the script is into.

---

### Post by tricia56 on 2009-04-01
Sorry, to be pain, but how do I find the directory that this run.sh script is in, some of the programme loaded in my home directory but there is not that script in those files.  Sorry to be lame but I am not sure how to locate this file now.  

btw thanks for the help so far

tricia

---

### Post by Volt9000 on 2009-04-01
Assuming the file is in your home directory, type:

```

find ~ -name run.sh

```

This will search for the file starting in your home directory (~) and traversing all subdirectories.
If not found, then you'll have to search the entire system...

```

sudo find / -name run.sh

```

Of course this will take a while.
Notice the "sudo" in front-- this means to execute the following as a superuser. This will search the system directories you normally don't have access to as a "regular" user.

---

### Post by egalvan on 2009-04-01
I put my scripts in ~/bin,

type the file name and it runs...

Read that bit of info somewhere on this forum.

---

### Post by tricia56 on 2009-04-01
Okay, I put in sudo find / -name run.sh and I got oodles of this


find: `/var/spool/cron/crontabs': Permission denied
find: `/var/spool/cron/atjobs': Permission denied
find: `/var/spool/cups': Permission denied
find: `/var/cache/system-tools-backends': Permission denied
find: `/var/cache/ldconfig': Permission denied
find: `/tmp/kPynLeuu3I': Permission denied


Doesn't seem that helpful?  ?

Or is name meant to be NAME of something like the programme??  

Then I did 

sudo find / -name run.sh and that just returns me to my prompt.

What I am trying to find is how to run ifreebudget in case that helps, it ran immediately afterdownloading etc in gui but now I cant get it to run doing execute run.sh script which is how it says to do it.  The folder in my home directory is called fmdata, I have looked all through that and can't find this script thingy.



thanks

---

### Post by tricia56 on 2009-04-01
oops sorry double post

---

### Post by egalvan on 2009-04-01
Are you sure you downloaded the Ubuntu version?

the Ubuntu version is a .deb that automatically runs...

the generic Linux seems to need scripts and stuff.

check it again...

---

### Post by egalvan on 2009-04-01
Anybody familiar with ifreebudget?

It asks for admin rights, and I'm loathe to do this with un-known (to me) software.

Anybody?

---

### Post by tricia56 on 2009-04-01
Yeah I checked that I downloaded
ifreebudget_2.0.3.1~getdeb1-i386.deb

I am bewitched and bewildered now


ubuntu 9.04 64 bit

---

### Post by Volt9000 on 2009-04-01
> **tricia56 said:**
> Okay, I put in sudo find / -name run.sh and I got oodles of this


find: `/var/spool/cron/crontabs': Permission denied
find: `/var/spool/cron/atjobs': Permission denied
find: `/var/spool/cups': Permission denied
find: `/var/cache/system-tools-backends': Permission denied
find: `/var/cache/ldconfig': Permission denied
find: `/tmp/kPynLeuu3I': Permission denied


Doesn't seem that helpful?  ?

Or is name meant to be NAME of something like the programme??  

Then I did 

sudo find / -name run.sh and that just returns me to my prompt.

What I am trying to find is how to run ifreebudget in case that helps, it ran immediately afterdownloading etc in gui but now I cant get it to run doing execute run.sh script which is how it says to do it.  The folder in my home directory is called fmdata, I have looked all through that and can't find this script thingy.



thanks


Hmm interesting... are you sure you typed the command correctly?
If you typed that line beginning with "sudo" then you should be asked for your password. If you typed in your password correctly you shouldn't get any errors about accessing directories.

Copy and paste this line EXACLY into terminal:

sudo find / -name run.sh

When you press Enter you should get a prompt for YOUR password. Enter your password and the find command will run.

---

### Post by tricia56 on 2009-04-01
Okay you are right, when I put it in correctly, carefully pasting from Volt I was asked for my password and then returned to my prompt.  (Do not pass go)  

I am sure I have downloaded the right file, perhaps I should just start again.

---

### Post by llamabr on 2009-04-01
From where did you download this file?  Where did you tell it to save?

---

### Post by tricia56 on 2009-04-01
okay I have found the run.sh scrip it is in /usr/share/ifreebudget

but then I have done the following

muriel@manuka-laptop:/usr/share/ifreebudget$ sh run.sh
run.sh: 42: /bin/java: not found

so this is a bit trickier with 64 bit, isn't that right?  I have found the how to about java and I guess I need to follow that now.

thanks for the help, nearly, nearly there.

tricia

---

