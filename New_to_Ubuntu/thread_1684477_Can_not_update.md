---
title: "Can not update"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-02-09
Every time I try to update I get this message
[IMG]http://i229.photobucket.com/albums/ee246/robert1305/Screenshot-2.png[/IMG]

I don't have anything running as far as I can see.

---

### Post by anglican on 2011-02-09
> **Robert1305 said:**
> 

I don't have anything running as far as I can see.To be absolutely sure try:
```
ps -e | grep -i -e apt -e dpkg -e update-manager
```

H

---

### Post by Robert1305 on 2011-02-09
Its all double dutch to me

[COLOR="Blue"]
ERROR: Garbage option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
robert@robert-desktop:~$ 
[/COLOR]

---

### Post by anglican on 2011-02-09
> **Robert1305 said:**
> Its all double dutch to me

[COLOR=Blue]
ERROR: Garbage option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
robert@robert-desktop:~$ 
[/COLOR]That's what you'll get if you type in the left hand side incorrectly (the ps -e bit). Use copy and paste to get it right.

H

---

### Post by Robert1305 on 2011-02-11
I have not been able to solve the problem, but, I have found a way round it, when I first switch my PC on I go directly into the update manager and it works perfectly, start using my PC as normal then the problem occurs.

---

### Post by philinux on 2011-02-11
> **Robert1305 said:**
> I have not been able to solve the problem, but, I have found a way round it, when I first switch my PC on I go directly into the update manager and it works perfectly, start using my PC as normal then the problem occurs.

Open a terminal and use Copy and paste the command in post #2.

---

### Post by Robert1305 on 2011-02-11
I have done exactly as you said, and it returns [COLOR="Blue"]command not found[/COLOR]

---

### Post by Bölvaður on 2011-02-11
it's very hard to write down commands like this and Im very confused why even a moderator did not explain the easiest way to copy and paste into the terminal because there are different and not so obvious key shortcuts to do it (ctrl+c does not work!)

You will need to copy the entire command, you can try it out with just the first part to begin with

ps -e

and then go to the terminal window and hold down ctrl+shift+v
Or what I almost always do:
Highlight the command with your mouse, and then use the middle mouse button (pushing down scroll wheel of your mouse) to paste the command.

the command works and was tested. But man I would hate to have to write this down without knowing the syntax and what the commands do.
If you write this down make sure you have every letter right and the most important is remembering about white spaces.
You should begin with something small like "ps -e" and then use up arrow key and add to the command the other things.

---

### Post by philinux on 2011-02-11
To paste into a terminal "right mouse click" and choose paste is pretty easy and straight forward. Or other methods as in above post.

OP.You must not be selecting the command and copying it correctly as it works fine here.

```
ps -e | grep -i -e apt -e dpkg -e update-manager

It returns this for me:-
 2028 pts/1    00:00:01 aptitude
 2044 ?        00:00:00 apt

```

---

### Post by Robert1305 on 2011-02-11
Doesnt happen for me

---

### Post by Robert1305 on 2011-02-12
robert@robert-desktop:~$ ps -e | grep -i -e apt -e dpkg -e update-manager
 1948 ?        00:00:00 apt
 2206 ?        01:00:46 apt-get
robert@robert-desktop:~$ 

Finally worked, this is the result, still dont know what it means:confused:

---

### Post by philinux on 2011-02-12
Robert,

I just rebooted and as expected that command for me shows nothing.

Since you get a response it means you have apt already running.

Have you by any chance selected this. If so make sure it's unchecked.

System>prefs>startup apps.

---

### Post by Robert1305 on 2011-02-12
No, its not checked

---

### Post by anglican on 2011-02-12
> **Robert1305 said:**
> robert@robert-desktop:~$ ps -e | grep -i -e apt -e dpkg -e update-manager
 1948 ?        00:00:00 apt
 2206 ?        01:00:46 apt-get
robert@robert-desktop:~$ 

Finally worked, this is the result, still dont know what it means:confused:It means that you have got another package manager running - apt-get - you can only have one package manager running at a time. apt-get is run on the command line so there must be a terminal open somewhere that it was run in - possibly awaiting some input. Can you find that open terminal (there should be a taskbar entry called "Terminal" for it wherever you have the task list (it is probably at either the top or bottom of the screen). Open any currently running terminals to try and find it. If you absolutely cannot then you could kill the process with:
```
sudo kill -9 2206
```(2206 comes from the output of the command above). Killing a process is a last resort which can leave the system in an unstable state - processes prefer to close normally.

H

---

### Post by Bölvaður on 2011-02-14
> **anglican said:**
>  Open any currently running terminals to try and find it. If you absolutely cannot then you could kill the process with:
```
sudo kill -9 2206
```
it is much easier to kill it like this

```
killall apt-get
```apt is also running there but I think it will die when you kill apt-get.. but just in case you can also do this
```
sudo killall apt-get apt -9
```
this command should kill everything xD it's an overkill but it's just to be 100% sure :D

---

