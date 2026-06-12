---
title: "hamachi install issues 7.10 - package soon?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by morpher99 on 2007-10-21
I'm a new Linux user, although one not new to the idea and usage of command-lines. 

I've been trying to install hamachi on Ubunto 7.10 for a while now, reading and following both the readme as well as various installation threads around. I haven't been successful, as once I get to to "-init" command, no prompts let me know what's happening. Does anyone know if synaptic is going to have a package any time soon tested for 7.10, or how I can contact them directly and find out?

Thank you very much,
- Josh

---

### Post by captaink on 2007-10-22
I have the same problem too! In feisty it worked very good. But after the upgrade to gutsy, it doesn't work anymore. As if it is a dummy program that executes the CPU command "nop", like Z-80 assembly :-p.
Have you upgraded from feisty too? What is your architecture? Mine is x86_64, but in feisty  x64 it worked well...

---

### Post by zeronothing on 2007-10-22
hey guys,

to get hamachi to work in gutsy all you have to do is follow the instuction to install hamachi (which I believe is only "make install"). then open up synaptic and install upx-ucl-beta. after that is installed open up terminal and type

1.) cd /usr/bin

2.) sudo upx-ucl-beta -d hamachi

3.) sudo /sbin/tuncfg

4.)hamachi-init

5.)hamachi

hopefully you will be back in business. if you have anymore problems don't hesitate to ask....

---

### Post by zeronothing on 2007-10-22
hey guys,

I just wanted to mention that their is also a gui for hamachi that is pretty nice to have. go to [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/) and down towards the bottom is the newest beta version that works well if you have compiz enabled. once you have it downloaded all you have to do is extract it and then just run it. Just thought i would mention it. if you have any questions don't hesitate to ask....

---

### Post by morpher99 on 2007-10-22
First off, thank you very much for your help, I really appreciate it.

Following your directions, I was able to get online with Hamachi, such that my other computer was able to see me in the hamachi window. However, whenever I actually try to connect to the computer via hamachi's tunnel, I'm unsuccessful, whether I use the hostname or IP address.

Any ideas?

Thanks,
- Josh

---

### Post by zeronothing on 2007-10-22
so you can login, and to my knowledge it sounds like you can join a network and go-online. the problem you are having is trying to connect to it to see a share folder on the other pc. if that is so trying doing this. if you run the command "hamachi list" in terminal it will show you the clients address that you want to connect to. then what you need to do is go to places-> network-> click on the paper with pencil icon which is up near the top left hand corner to bring up the address bar. type in the address in this format "smb://enter_ip_address" then hit enter. if you have samba server install and configured correctly it should connect to the samba share on the pc your trying to connect too. I hope this is what your trying to do. also if you want to make this how-to easier download "ghamachi" its the gui interface for hamachi. allow you to right click on a pc connected to the network and browser their files, right from a nice little gui list. hope this can help you..

---

### Post by toddward on 2007-10-22
Whew, thanks for the help.  I really needed to get this installed too!

---

### Post by Scubaduud on 2007-10-25
I tried the sudo upx-ucl-beta -d hamachi fix but it just says "upx-ucl-beta: hamachi: NotPackedException: not packed by upx".  Any ideas?

---

### Post by toddward on 2007-10-27
Hmm, not sure.  I'm doing this on another system...installing hamachi that is.  I'll keep note if I have any issues and let you know.

You might want to try to reinstall the deb package?

---

### Post by kuzotare on 2007-10-28
hi everyone

I have followed the instructions above and I managed to successfully install hamachi on Ubuntu 7.10.  on  Ubuntu 7.04 had followed a how-to which created a script for the automatic start as a service for hamachi. I would like to do the same now on gutsy. How can I do? Thanks to all

---

### Post by toddward on 2007-10-28
To do this, I know of two methods.  In either method, you're going to need the below script--tailored to your specific needs of course.  However, in either method you're going to have to make a call to a script (hashed out below).

The first option is to create a session which starts up upon login (and executes a script or application).  There is a guide here  [https://help.ubuntu.com/community/AddingProgramToSessionStartup]("https://help.ubuntu.com/community/AddingProgramToSessionStartup").  This is all GUI based...which should make it easy.

The second option is to have a call to your hamachi script from your /etc/rc.* section.  In here each script starts a different run-level in the system.  You'll most likely want to put the call to your script  into **rc.local**.  *I'm fairly sure this is the location that you need to put the script call.*

Here's the script that I've used for my *nix systems:
```

#!/bin/bash
tuncfg
sleep 2
hamachi start 
sleep 2
hamachi login
sleep 5
# hamachi join <<Your Network>> <<Your Password>>
# sleep 5
hamachi go-online <<Your Network>>

```

Ensure that the script can be executed.
```

chmod 755 <<your script name>>

```

This script assumes that you're already a member of the network, however, if you aren't, uncomment the join command and corresponding sleep.  The script also assumes that you've changed the permissions on your tuncfg executable.  To do this you'll need to (in order for this script to work) to alter the permissions on your *tuncfg* executable file.
```

chmod 755 /sbin/tuncfg

```

The *sleep* commands are in there to ensure that your commands don't run into each other.  You may need to adjust those times (in seconds) if commands are conflicting.

This is fairly easy to implement, please let me know if you have more questions and I'll be sure to help as much as I can.

---

### Post by kuzotare on 2007-10-28
Hi and thanks for your replay
sorry for my bad english 

I hope to be as clear as possible. I read your instructions but I would not commit any error. Carry-over here the script that 7.04 used to travel on Ubuntu for startup automatic hamachi ```
 1.D.2) Hamachi Startup Script

Open gedit and save the following as /etc/init.d/hamachi
Code:

#!/bin/sh

hamachi_start() {
  echo "Starting hamachi..."
  /sbin/tuncfg
  /usr/bin/hamachi -c /etc/hamachi start
  /bin/chmod 760 /var/run/tuncfg.sock
  /bin/chgrp hamachi /var/run/tuncfg.sock
}

hamachi_stop() {
  echo "Stopping hamachi..."
  killall tuncfg
  /usr/bin/hamachi -c /etc/hamachi stop
}

hamachi_restart() {
  hamachi_stop
  sleep 1
  hamachi_start
}

case "$1" in
'start')
  hamachi_start
  ;;
'stop')
  hamachi_stop
  ;;
'restart')
  hamachi_restart
  ;;
*)
  hamachi_start
esac

Lastly, you need to make the script executable and add it to startup:
Code:

sudo chmod +x /etc/init.d/hamachi
sudo update-rc.d hamachi defaults


```,
 I want to see if the file that I create I must save it in the same position and using the same chmod. Many thanks for the aid

---

### Post by kuzotare on 2007-10-29
I have tested following your instructions and placing the script in rc.local. I have also tested by placing the script in /etc/init. d/hamachi...... but nothing no start at start of the system

---

### Post by Stereotypical Rage on 2007-11-01
> **Scubaduud said:**
> I tried the sudo upx-ucl-beta -d hamachi fix but it just says "upx-ucl-beta: hamachi: NotPackedException: not packed by upx".  Any ideas?
[http://ubuntuforums.org/showthread.php?t=553774](http://ubuntuforums.org/showthread.php?t=553774) <---Try this thread. It worked wonders for me. I had to go into the /usr/bin dir.... Then run upx -d hamachi and it worked. =)

---

### Post by SoulRaver on 2007-11-25
This is really starting to agrevate me.

I got it to work once using the upx. But it did not survive a reboot.
```

user@box:~$ hamachi start
25 13:46:04.040 [   0] [ 5960] tap: connect() failed 2 (No such file or directory)
user@box:~$

```

the /.hamachi folder is still there in /home/user as well as the respective folders in /usr/bin

Could anyone plz explain this to me?

---

### Post by megajeff on 2007-11-27
I haven't set Hamachi up to start at boot automatically yet, but I did get it to run on 7.10 Gutsy without using upx. I wrote up the method [here]("http://forums.hamachi.cc/viewtopic.php?p=59409#59409").

---

### Post by seanreynoldscs on 2007-11-30
Run: sudo tuncfg 

after you restart.

---

