---
title: "Attempting to setup web server"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by detour21 on 2010-03-11
I installed Ubuntu 3 weeks ago and then realized I needed the web server edition, installed that on a partitioned Windows XP computer. I then installed web server and it took over the windows partition (I think). I was following the instructions from a nettuts web site (How to Setup a Dedicated Web Server for Free) by Alex Williamson. It went along just fine until I got to changing the Apache2 conf file to change the "Server Tokens Full" to "Server Tokens Prod", I could not find "Server Tokens Full" listed in the conf file and yes I looked like 15 times, the instructions even had a photo of where the line should be and it was not there and have been basically stuck there. When I turn on the machine now I get through login and then have randy@web-server:~$ prompt. I don't have a clue where to go from here. I have run across what I think is a GUI named webmin, should I install that to help get past the learning curve of all the sudo commands? I also think maybe it is time to format the hard drive and start over but, have run into trouble doing that have tried fdisk /dev/sda2 and get bad command. Am obviously totally a beginner in Linux land, any suggestions would be welcome.

---

### Post by Mighty_Joe on 2010-03-11
> **detour21 said:**
> I installed Ubuntu 3 weeks ago and then realized I needed the web server edition, 

You can install Apache on the standard desktop Ubuntu. If you are just installing it to fool around with, a dedicated server is overkill. Something tells me you'll also be more comfortable with a gui to fall back on.

> **detour21 said:**
> 
It went along just fine until I got to changing the Apache2 conf file to change the "Server Tokens Full" to "Server Tokens Prod",

Note that this step only helps to secure your server.  It should not be a blocker to toying around with it.  I doubt you'll want to put this server out for everyone to see (and hax) until you get a little more experience.

---

### Post by detour21 on 2010-03-11
So I really should start over and just install Ubuntu and then 
Apache. Now can I just load Ubuntu over the web server version?

---

### Post by Mighty_Joe on 2010-03-11
> **detour21 said:**
> So I really should start over and just install Ubuntu and then 
Apache. Now can I just load Ubuntu over the web server version?

You could do that or install the "ubuntu-desktop" package on your "server".  Practice makes perfect ;)

---

### Post by sandyd on 2010-03-11
> **detour21 said:**
> I installed Ubuntu 3 weeks ago and then realized I needed the web server edition, installed that on a partitioned Windows XP computer. I then installed web server and it took over the windows partition (I think). I was following the instructions from a nettuts web site (How to Setup a Dedicated Web Server for Free) by Alex Williamson. It went along just fine until I got to changing the Apache2 conf file to change the "Server Tokens Full" to "Server Tokens Prod", I could not find "Server Tokens Full" listed in the conf file and yes I looked like 15 times, the instructions even had a photo of where the line should be and it was not there and have been basically stuck there. When I turn on the machine now I get through login and then have randy@web-server:~$ prompt. I don't have a clue where to go from here. I have run across what I think is a GUI named webmin, should I install that to help get past the learning curve of all the sudo commands? I also think maybe it is time to format the hard drive and start over but, have run into trouble doing that have tried fdisk /dev/sda2 and get bad command. Am obviously totally a beginner in Linux land, any suggestions would be welcome.
1. Please try not to put everything in one block of text

2. You will have to add "Server Tokens Prod" to the apache conf manually.

3. dont use webmin., you dont want random people administrating your server do you?

4. You need to format the hard drive from the livecd.

---

### Post by detour21 on 2010-03-17
I have now installed the desktop but, still boot to randy@web-server:~$
How do I change boot to desktop?

---

### Post by MooFx on 2010-03-17
Use the command: 
 
sudo startx or xstart or something

---

### Post by 3rdalbum on 2010-03-17
```
sudo gdm
```

(possibly 'sudo service gdm start' depending on what version of Ubuntu you are using).

---

### Post by detour21 on 2010-03-17
Tried sudo startx
Tried sudo xstart
Tried sudo gdm
Tried sudo service gdm start
got either command not found or unrecognized service

---

### Post by detour21 on 2010-03-17
Decided to reinstall Desktop from boot disk
Booted from disk
Selected language
Selected install Ubuntu
Screen is blank as and has been for about an hour
Tested CD prior to install and it checked out ok
Should I download a fresh ISO?
Burn new boot disk?

---

### Post by Paqman on 2010-03-17
If you just want to get up and running you can get a ready-made and preconfigured Ubuntu 8.04 server from [Turnkey Linux]("http://www.turnkeylinux.org/"). Just make sure you change the logon/password after installing.

Don't listen to people telling you not use Webmin, it's a perfectly legit way to interact with a server, especially if you aren't gripped up on using the CLI.

---

### Post by Mighty_Joe on 2010-03-18
> **detour21 said:**
> 
Screen is blank as and has been for about an hour


Strange.  Did you try the "try ubuntu" option on the CD?  
You may have a problem that only crops up with the GUI version.  For example, I have a "home server" that has a [VIA c3 motherboard]("http://ubuntuforums.org/showthread.php?t=1244304&highlight=nas").  The video drivers are notorious for hanging up but since I'm not running X, no problems.
There are other things that can cause problems, ACPI, for instance.  I have a laptop that wouldn't boot unless you had a CPU fan setting in the BIOS just right.
Your best bet may be to search the forum for your computer model and video card and see if anyone else is having problems.  There may be a workaround.

---

