---
title: "bash"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-19
I can't seem to work out how to get a simple bash scrip to execute commands (like acpi -V fro example) using cron...not the cron bit the actual script...anyone got a template or a link, been trying to find something for ages, and my attempts don't work :-)

---

### Post by Sealbhach on 2010-10-19
Did you make it executable?

```
chmod a+x script.sh
```

Also, make sure
    
#!/bin/bash     

is your first line. There are lots of bash scripting guides:

[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#toc2](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html#toc2)

.

---

### Post by hekastos on 2010-10-19
I'm not 100% sure I understand you correctly,
do you mean something like:
```
#! /bin/bash
#
#

STATUS=$(acpi | cut -f 2 -d "," | tr -d " %")

if [ $STATUS -lt 5 ] ;

then echo -e "$STATUS"
```

---

### Post by A_M_S on 2010-10-19
Your script runs in the CLI?

When i upgraded do Lucid some scripts continued to run in the CLI but stop working in the cron.

---

### Post by CharlesA on 2010-10-19
Make sure you use the full path to the program you want to run. I've made the mistake of not doing that and having the script fail to run the program because of it.

---

### Post by Hippytaff on 2010-10-20
THanks everyone, maybe I'm just getting confused but I though it would be possible to do say
 
```

#!/bin/bash
#check for updates
 
echo 'sudo apt-get update'

```
 
then get cron to run it once a day. I know update manager does all this, but this is just an example :-)
 
I'll need to do some more reading on bash :-) got my head around pythom basics, but can't seem to understand how the shell knows when to execute a command in a bash script. and not just print it.

---

### Post by mastablasta on 2010-10-20
doesn't echo just "print" the stuff on screen?
would that just put print "sudo apt-get update" in terminal?

---

### Post by SuaSwe on 2010-10-20
Yes, that wouldn't execute the command, just send it to terminal:

```

suave@lxhome:~$ chmod +x tmp
suave@lxhome:~$ ./tmp 
sudo apt-get update
suave@lxhome:~$ 

```

If you want it to execute the command, get rid of the 'echo' and quotes. :)

---

### Post by Hippytaff on 2010-10-20
> **SuaSwe said:**
> Yes, that wouldn't execute the command, just send it to terminal:
 
```

suave@lxhome:~$ chmod +x tmp
suave@lxhome:~$ ./tmp 
sudo apt-get update
suave@lxhome:~$ 

```
 
If you want it to execute the command, get rid of the 'echo' and quotes. :)
 
excellent...so
 
```

#!/bin/bash
#check for updates
sudo apt-get update

```
 
cmod to make executable and
./update.sh
should run the command. Will check it out when I get home...thanks!

---

### Post by Diametric on 2010-10-20
Yes, but this would only run the script (typing ./update.sh) when in the terminal, it has yet to be added to crontab so that it is run at the interval the OP decides.

---

### Post by Hippytaff on 2010-10-20
> **Diametric said:**
> Yes, but this would only run the script (typing ./update.sh) when in the terminal, it has yet to be added to crontab so that it is run at the interval the OP decides.
 
I wanted to get this bit sorted first...no doubt I'll be asking about cron after work - got some stuff on it in and oldish linux format though :-)

---

### Post by Diametric on 2010-10-20
Cool, just wanted ot make sure.  One of the best palces to start is the man page.  When in a shell simply type "man cron" without the quotes.  The man pages in bash are very helpful.
 
Good luck!

---

### Post by Hippytaff on 2010-10-20
> **Diametric said:**
> Cool, just wanted ot make sure. One of the best palces to start is the man page. When in a shell simply type "man cron" without the quotes. The man pages in bash are very helpful.
 
Good luck!
 
Cool, I'm familiar with the man pages, but I sometimes overthink stuff :-) so I might need to post scripts for sanity testing quite a lot :-) maybe here isn't the right place for that though? but people have been tremendously helpful so far :-)

---

### Post by JKyleOKC on 2010-10-20
For the script to run in cron, you'll have to leave out the "sudo" since cron normally runs as the super-user already. If you definitely want to force cron to run it as your limited user, then the sudo would be necessary, but you would also have to edit the /etc/sudoers file to allow running the script without asking for a password. This would be going the long way around!

Just for curiosity, why do this just to check for updates? You can configure the update manager to do it automatically, with no need for a script. Or is this simply an example to keep things simple while you become familiar with scripting and using cron?

---

### Post by CharlesA on 2010-10-20
Maybe just to learn?

I've connected to my server every so often to do an apt-get update && apt-get upgrade whenever I feel like it.

---

### Post by Hippytaff on 2010-10-20
Yes...just to learn, I've got an alias in .bashrc for update upgrade - upgd, but I find it easier to learn when I'm familiar with the commands/functions...upgrade etc - that probably makes no sense, but I know what I mean :-)

---

