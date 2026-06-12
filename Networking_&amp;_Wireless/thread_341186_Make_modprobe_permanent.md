---
title: "Make modprobe permanent"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by dblbogey on 2007-01-18
I'm running Dapper on an old computer with an (I think) ISA NIC. A few months ago a fellow forum resident helped me get my computer to see the card with the following:

sudo modprobe 3c509

[login]

sudo config -a

That worked great. Then he said to make this a permanent fix, enter the following:

sudo dhclient

sudo config -a

That also worked until I did a reinstall (another story!) Now the fix works only for each time I start Ubuntu and manually reenter the above commands, but it won't survive a reboot. I have to go to the terminal and reenter the commands every time I restart my computer. Can anyone tell me why this isn't working and, more importantly, how can I make this a permanent fix?

---

### Post by corax on 2007-01-18
Hi,
If you add the module name to the /etc/modules file the system will load it automatically at boot time.

bye :-)

---

### Post by dblbogey on 2007-01-18
Thanks, Corax, for your effort to help, but I have problems still. Also, my apologies to you (and any others looking on) for not disclosing before, but I am a newbie, so please bear with me, while I learn all this.

1. My 'etc' directory doesn't have a subdirectory 'modules'; it does have subs called 'modprobe' and 'modutils' .
2. I don't know the "module name".
3. If I did know the name, I don't know how to enter it into a file.

---

### Post by spd106 on 2007-01-18
To edit this file you need root privileges, the simplest way to do this is to enter this command at a terminal **gksudo gedit /etc/modules**. You will have to enter your password. 

Once you've added 3c509 to the end, just save and close. 


If you are on kde, you will need a different command, I think it's something like **kdesu kate /etc/modules**.

---

### Post by dblbogey on 2007-01-20
Hooray, it worked. Bravo, spd106, and thanks also to Corax for your effort.

---

### Post by tiver on 2007-05-17
Hello!

I followed these steps but when booting again it takes 2 minutes to do so (!) and finally it brings up an error (attachment). 

It says (partially translated):


While starting of the GNOME configuring services an error occurred:

Maybe certain things like themes, sounds or background services do not function correctly. 

The last error message was:

Did not receive a reply. Possibly causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

On the next logon GNOME will go on trying to start the configuration service.



If I leave the line 3c509 in /etc/modules it does not connect to the network on startup but it loads fast. When I include the line it connects on startup but it lasts very long and it brings this error. 

What can this be?

I hope you can help me.

---

### Post by mbradlcu on 2007-05-17
ok, I"m going to take heat for this but here's a not recommended fix. Create a script like
#!/bin/bash
echo {your_password_here} | sudo -S modprobe 3c509 
#eof

make it executable,, chmod 700 {script_name}
then use the gnome session "thinggy" to run the script at gnome startup..

for security reasons this is a bad idea but,,,
have fun

> **tiver said:**
> Hello!

I followed these steps but when booting again it takes 2 minutes to do so (!) and finally it brings up an error (attachment). 

It says (partially translated):


While starting of the GNOME configuring services an error occurred:

Maybe certain things like themes, sounds or background services do not function correctly. 

The last error message was:

Did not receive a reply. Possibly causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

On the next logon GNOME will go on trying to start the configuration service.



If I leave the line 3c509 in /etc/modules it does not connect to the network on startup but it loads fast. When I include the line it connects on startup but it lasts very long and it brings this error. 

What can this be?

I hope you can help me.

---

### Post by tiver on 2007-05-18
I remember, before I installed Ubuntu on the same harddisc again, it worked. I don't know why. I also had the option in Administration - Users to chose between User, Admin [and one more] on the first register card of a single user. I don't know why this is gone. Maybe it has something to do with it?

I'm a bit unexperienced in scripting ...... could you put this into a script, attach it and I just put my password in there? Would be great. 
And with "thingy" you mean possibly terminal - sudo nano /etc/modules and add it there?

Thanks for your help in advance!

---

### Post by mbradlcu on 2007-05-19
ok, I've never attached anything but here goes. You may still need to make it executable but if you're uncomfortable using the command like just do it with nautilus. I needed to add .txt to the file, so you may also want to rename it.
O and also, you don't need to mess with the modules file just put the attached file anywere, and point to it with the gnome-session - Startup Programs, using the add button... for good measure check out the contents of the file,, it's plane text,, just to make sure it doesn't say something like 'rm -rvf ~/' ; )

---

### Post by tiver on 2007-05-20
I thank you a bunch for your effort, still, I am too dumb to get it working. I ended up with searching around for another network card and finally found one which fitted so that I "only" need to click the network button on the desktop on the top right corner. I became sick of sudo and nano and so on ...... That is probably the biggest obstacle Linux has to face in order to gain more folks using it because this is simply crazy. The next big thing will be to get RealPlayer (available on the real.com site in version 8 as bin-file) or Thunderbird 2 (which is not yet available through Synaptics) working .... installation routines would help!
But that's not your business, I thank you once again that you took the time to help me. I will save this web page and come back to it once the card now plugged in won't work any more ;)

---

