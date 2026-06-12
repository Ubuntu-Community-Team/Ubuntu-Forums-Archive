---
title: "Hostname is localhost.localdomain"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Andrik.if on 2009-08-21
[offtopic]
1st: Sorry my poor English
2nd: Sorry that I'm writing in wrong place, i've just registered here
[/oftopic]

 I'm having a problem: My hostname was **KOMP** (I set it when intalled Ubuntu). But since last week there's something wrong... *tty1* writes "**localhost.localdomain** login:"; *gnome-terminal* and *xterm* writes "andrik@**localhost**:". But, in same time, tty2, 3, 4, 5 and 6 writes "**KOMP** login". I can't understand what's going on with my 9.04 Jaunty system. I want to take back old hostname. Help me please!

P.S. By the way: Avahi can't start because my domain is .local - can I change it? Or another solution to start Avahi?

P.P.S. Another trouble:

```

andrik@localhost:~$ shutdown -h now
shutdown: Need to be root
andrik@localhost:~$ halt
halt: Need to be root
andrik@localhost:~$ reboot
reboot: Need to be root

```

I can just "Log Out...", "Lock screen" and "Guest session".

P.P.P.S. About week or two ago ewerything were fine.

---

### Post by xPr0star on 2009-08-21
Well you need to use sudo to get root access man. so it would look like this

```
sudo shutdown h now
```

To change your host name open a terminal and type 

```
sudo gedit /etc/hostname
``` and also change it in /etc/hosts

```
sudo gedit /etc/hosts
```

---

### Post by Andrik.if on 2009-08-21
1. I KNOW WHAT IS SUDO AND HOW CAN I USE IT WITH SHUTDOWN

I'm asking about no-sudo/gksudo/gksu shutdowning. A week ago everything were fine.

2. About hostname... I'll reboot and see the result of changing /etc/hosts (i changed /etc/hostname yesterday but it haven't worked for me).

3. What about Avahi and domain?

---

### Post by Penguin Guy on 2009-08-21
On a new Ubuntu system you need to use sudo to shutdown, nothing has suddenly gone wrong with yours. However there is a way that you can change this:
Type [COLOR="Green"]visudo[/COLOR] into a terminal. Now press [COLOR="Green"]i[/COLOR] and scroll to the bottom of that file. Add this after the last line: [COLOR="Green"]ALL     ALL=NOPASSWD: /sbin/shutdown[/COLOR]

---

### Post by Andrik.if on 2009-08-22
> **xPr0star said:**
> To change your host name open a terminal and type 

```
sudo gedit /etc/hostname
``` and also change it in /etc/hosts

```
sudo gedit /etc/hosts
```

1. I knew it! But I forgot it :) That didn't change hostname. Hostname is still "localhost" (in *tty1, xterm and gnome-terminal*), but *tty2, 3, 4, 5 and 6* writing "Ubuntu 9.04 KOMP *tty[number]*"

2. Abot *visudo*... I can shut down using *sudo* without password. But question was "Can I shut down without using *sudo*?". When I installed my jaunty everything were fine (hostname & shutdown), but about 2 weeks ago many features in system have broken. I can just "Log Out...", "Lock screen", "Guest session" and "Hibernate". Hibernation isn't working at all.

3. And what about Avahi? (Avahi isn't working since I installed Ubuntu)

P.S. I'm not telling you the reason of this madness because it can take a lot of words - my fingers will hurt :)

---

### Post by Iowan on 2009-08-22
FYI: [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") should be used with **gedit**.

---

### Post by K.Y.A on 2009-08-22
> **Andrik.if said:**
> 1. I knew it! But I forgot it :) That didn't change hostname. Hostname is still "localhost" (in *tty1, xterm and gnome-terminal*), but *tty2, 3, 4, 5 and 6* writing "Ubuntu 9.04 KOMP *tty[number]*"

2. Abot *visudo*... I can shut down using *sudo* without password. But question was "Can I shut down without using *sudo*?". When I installed my jaunty everything were fine (hostname & shutdown), but about 2 weeks ago many features in system have broken. I can just "Log Out...", "Lock screen", "Guest session" and "Hibernate". Hibernation isn't working at all.

3. And what about Avahi? (Avahi isn't working since I installed Ubuntu)

P.S. I'm not telling you the reason of this madness because it can take a lot of words - my fingers will hurt :)

**I use aliases. Try this:**
```

alias "byeubuntu"="sudo halt"
```
Now, run "byeubuntu" to shutdown. Personally, I have it set so if I type "die" it shuts down. 
Here's my ~/.bash_aliases file.

```

alias die="sudo halt"
alias server="ssh -X root@192.168.1.125"
alias server2="sudo mount 192.168.1.125:/home/guest ~/MAXTOR"
alias server3="sudo mount 192.168.1.125:/media/cache ~/NAS"
alias backup="cp -R  -v /home/winrid/MAXTOR /home/winrid/backup"
alias reload="/bin/bash"
alias fire="echo Out of bullets God damn it!"
alias cockgun="echo *Cocks shotgun, fires at desktop*"
alias boom="echo "starting_music,_my_lord"  audacious -p /home/winrid/Music/*.mp3"
alias servercd="sudo mount 192.168.1.125:/mnt/cdrom ~/ATAPI"
alias "Fire_Missile"="echo Ignition\ sequence armed\ -Fireing\ Missile\ at"
alias "stop"="/home/winrid/Documents/C/stop"
```

---

