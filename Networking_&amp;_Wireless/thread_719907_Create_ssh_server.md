---
title: "Create ssh server"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by ASPCartman on 2008-03-09
I want to create ssh server but i don't know how. I can't find any topics about it. 
So i installed openssh client and server from repository. When i try to run sshd i got:
```
aspcartman@PC:/usr/bin$ sshd 
sshd re-exec requires execution with an absolute path
```
Can someone give me a link to a tutorial or just say what i need to do and how to use all it?

---

### Post by koenn on 2008-03-09
apparently, you need a full (absolute) path
try starting it with ```
 /usre/bin/sshd 
```
or else ```
/etc/init.d/sshd start
``` or ```
/etc/init.d/openssh-server start 
```


---
edit : but then again, it may already have started - that is usually what it does as the last step in the installation process. It also starts automatically when you boot
---

you use it by connecting to it from another machine, with
```
ssh unsername@remote_host_name_or_ip_address
```
username should be a user on the remote host. 
it returns a shell on the remote machine, to be used as any other shell.

---

### Post by Eiríkr on 2008-03-09
If you've installed openssh-server, you shouldn't need to run the sshd executable directly.  You're better off invoking the service script:
```
sudo /etc/init.d/ssh start|stop|reload|force-reload|restart|try-restart
```
(Pick just one of the options listed.)  This service script should be invoked during boot.  You can check if sshd is running like this:
```
user@ubuntu:~$ ps aux | grep ssh
root      4581  0.0  0.1   5284  1000 ?        Ss   Mar04   0:00 /usr/sbin/sshd
user      5147  0.0  0.0   4432   584 ?        Ss   Mar04   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
root      8292  0.0  0.2   8044  2408 ?        Ss   15:40   0:00 sshd: user [priv]
user      8294  0.0  0.1   8044  1552 ?        S    15:40   0:00 sshd: user@pts/1
user      8332  0.0  0.0   2976   752 pts/1    R+   15:42   0:00 grep ssh
user@ubuntu:~$
```
[font=courier]ps aux[/font] lists running processes.  This list is then piped via the | to the [font=courier]grep[/font] command, which weeds out all entries including the string "ssh".  The output here shows that I've got the sshd daemon process running, as well as ssh-agent.  If sshd were not running, I'd try [font=courier]sudo /etc/init.d/ssh start[/font].

HTH,

Eiríkr

---

### Post by ASPCartman on 2008-03-09
Thank u guys it worked and servies started. Now other question - how to make a client on a windows machine and will client be able to login to a server with username that is already loged in? I have a friend with winxp and i want me to be able to connect to his pc with a shell and he to mine (at least he to mine)

---

### Post by koenn on 2008-03-09
your friend to connect to your computer is easy. 
He needs an ssh client for Windows, eg putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
all he needs to do is download the .exe and run it

the same user account can be logged in several times, in separate sessions. 
If you're planning to let your friend use your account, remember that this means he probably can sudo - your handing over your entire system. bad idea. 


for you to connect to his computer, he'll need to install an ssh server for windows. I don't know if that exists. 

Also : are you allowing him to connect over the internet
1- be careful - use strong passwords at least
2- if your behind a NAT router, you need to configure the router to do "portforwarding" so that port 22 is accessible from the internet and redirected to your computer

---

### Post by ASPCartman on 2008-03-09
Thanks! =) ammm and yeah - what about authentification? How to set password or a key what ever?

---

### Post by hackertarget on 2008-03-10
> Thanks! =) ammm and yeah - what about authentification? How to set password or a key what ever?

From a terminal you can create a seperate account for your friend.

sudo useradd friendsaccountname
sudo passwd friendsaccountname

In this case you would not need to worry about keys as you are using password for authentiFIcation.

---

### Post by ASPCartman on 2008-03-11
A cuestion again. I work with my pc using my pda. 
Everything is fine (maybe little bit laggy but it's pda's bug i think) but i have a problem. For example i want to play music. I write ximp3 ./Music/00* (for example) and ximp3 starts playing. In terminal on pda i got info of song and etc. But how to continue work? I need to wait until song is over or ctrl+c it =( I cant open new instance of terminal cos it's pda. Please help! Or name other good console player

---

