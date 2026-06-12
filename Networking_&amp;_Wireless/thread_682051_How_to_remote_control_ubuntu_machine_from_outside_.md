---
title: "How to remote control ubuntu machine from outside the internal network like logmein"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by philidox on 2008-01-29
I am will versed in logmein's remote control feature but unforunately they only work for windows. Iis there any way to remote control any other ubuntu machine from outside the network like logmein or gotomypc. I need to know how to do it from the internet and not just the intranet.  Please help I need this bad!!!

---

### Post by diaa on 2008-01-29
I haven't tried logmein or gotomypc, but I know what you mean:

There are several options:
1- VNC, you have to be logged in on the target computer, no one else will be able to use the target computer while you're using it(because you'll control its mouse and keyboard).
2- SSH, provides remote command-line access, you don't need to be logged in on the target computer, others can use the computer freely.
3- FreeNX, like VNC but more sophisticated and faster in operation, no need to be logged in on the target computer, others can use the computer freely.

FreeNX is quite good but its setup is somehow complex, I recommend VNC for its simplicity.

[Setup VNC on Ubuntu]("http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php") | [Setup FreeNX on Ubuntu]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx")

---

### Post by freddyp on 2008-01-29
I have one Windows box on my home network that I use LogMeIn to reach and then from there I use TightVNC to go to any of the Ubuntu boxes inside the home network.  Not elegant, but it works well for me.  There have been a growing list of people on the LogMeIn forum asking them to build a Linux version!!

---

### Post by philidox on 2008-01-29
> **freddyp said:**
> I have one Windows box on my home network that I use LogMeIn to reach and then from there I use TightVNC to go to any of the Ubuntu boxes inside the home network.  Not elegant, but it works well for me.  There have been a growing list of people on the LogMeIn forum asking them to build a Linux version!!

Thats genius I never thought of that, I cant believe I did not think of this myself, I do have a windows xp virtual machine running inside my ubuntu physical machine.  Cool thing is that logmein works flawlessly on virtual windows machines.  So maybe I can install VNC on my logmein controlled virtual machine to control my ubuntu host os machine.  I'll report success or failure.

---

### Post by Herman on 2008-01-29
I have just recently been improving a web page about SSH networking between Linux (Ubuntu) boxes and it starts off very simple and gets a little bit more technical as you work down the page. The entire page is intended to be usable by new users, I hope there's nothing there that's too hard to understand.

Down around the bottom of the page I explain how I ssh into my network from the internet. Of course it will be different for everyone depending on what hardware you have, but you should be able to do something similar to what I do and you shouldn't need any Wijndows software at all.
If you feel like doing it that way (through your Windows 'Logmein') then fine, but there is no reason why a Ubuntu user needs to rely on Windows based software for any reason, especially when it comes to networking. 

Here's the link, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm"),  it's mainly only for beginners level users. If you're after something more technical you should be able to find some more advanced SSH websites and bloggs somewhere whenever you want.

Regards, Herman :)

---

### Post by philidox on 2008-01-29
> **Herman said:**
> I have just recently been improving a web page about SSH networking between Linux (Ubuntu) boxes and it starts off very simple and gets a little bit more technical as you work down the page. The entire page is intended to be usable by new users, I hope there's nothing there that's too hard to understand.

Down around the bottom of the page I explain how I ssh into my network from the internet. Of course it will be different for everyone depending on what hardware you have, but you should be able to do something similar to what I do and you shouldn't need any Wijndows software at all.
If you feel like doing it that way (through your Windows 'Logmein') then fine, but there is no reason why a Ubuntu user needs to rely on Windows based software for any reason, especially when it comes to networking. 

Here's the link, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm"),  it's mainly only for beginners level users. If you're after something more technical you should be able to find some more advanced SSH websites and bloggs somewhere whenever you want.

Regards, Herman :)

Thank you so much and I completely agree with you not having to rely on "The Man" to get stuff done I'll follow your link and diaa's. I know I'll be able to get it done just need a means to an end once again thx for the quick and simple response, you guys are the best, viva la ubuntu.  By the way the logmein idea did not work cause it just showed redundant pictures like having a mirror facing a mirror

---

### Post by loell on 2008-01-29
I think hamachi is part logmein? I haven't really tried this kind of setup yet.

hope, this is useful.

[Hamachi: Install on Linux]("http://logmeinwiki.com/wiki/Hamachi:Install_on_Linux")



[http://ubuntuforums.org/showpost.php?p=763014&postcount=1]("http://ubuntuforums.org/showpost.php?p=763014&postcount=1")

---

### Post by ridgeland on 2008-01-30
Herman,
Thanks for the ssh page.  I've been trying to get ssh over the internet for a while now.  Linux to Linux.  I have ssh over my LAN (192.168.123.123) also VNC over SSH on my LAN to two other computers.  No problems.
I still don't see how to do this over the internet.  Just a simple
ssh ridgeland@192.168.123.123 
works fine.  I enter the password and have a prompt.
My IP changes when I restart the modem which is fine.  Now I see 216.123.123.123
I have configured my router to forward port 5900 to one specific PC on the LAN.  With CanYouSeeMe.org I get verification that port 5900 can be seen, other ports cannot (like 22 for instance).
What is the correct ssh command to connect via the internet?  I tried some ssh -R but have not suceeded.  I read elsewhere that 5900 was good for ssh.
Thanks,
ridgeland

---

### Post by ridgeland on 2008-01-31
I did it!
My successful command was
ssh -l ridgeland 216.123.123.123
Don't know if it mattered but I opened ports 22, 5800-5801, 5900-5901

With port 5801 open I can login to the system using Firefox.
[http://216.123.123.123:5801](http://216.123.123.123:5801)
This pops up the usual login screen.  It also sends your user name and password across the web WITHOUT encryption!  It could be viewed and used by others!  I played with it some then turned off ports 5800-5801 on the router's firewall.
I'm still learning about the other two ports.  Which did ssh use?

---

### Post by Herman on 2008-01-31
Hello Ridgeland,
Try using the VNC command with the -via option. [VNC Over SSH: Securing the Remote Desktop]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/")
That should connect through port 22 and you can leave port 5900 unforwarded or even closed.

Regards, Herman :)

---

### Post by ridgeland on 2008-01-31
Hi Herman,
I've been playing with remote access today.
I can use
vncviewer -via davidssh@216.123.123.123 localhost:1
to access a new logon screen when the host (192.123.123.123) has SuSE up.
I can use
vncviewer -via davidssh@216.123.123.123 localhost:0
to take control of the current user's screen in Ubuntu.
My puzzle is - each Linux only allows me one choice, not both.  That is I cannot get SuSE to let me control :0 (the current user's screen) and I cannot get Ubuntu to let me create a new X session :1
Any clue what to tweak where?
Maybe that should be a new thread.  Sorry Philidox.
p.s. you're right only port 22 is open on the router now and vncviewer -via is still connecting.

---

### Post by kernelCompile on 2008-01-31
> **ridgeland said:**
> I did it!
My successful command was
ssh -l ridgeland 216.123.123.123
Don't know if it mattered but I opened ports 22, 5800-5801, 5900-5901

With port 5801 open I can login to the system using Firefox.
[http://216.123.123.123:5801](http://216.123.123.123:5801)
This pops up the usual login screen.  It also sends your user name and password across the web WITHOUT encryption!  It could be viewed and used by others!  I played with it some then turned off ports 5800-5801 on the router's firewall.
I'm still learning about the other two ports.  Which did ssh use?

SSH uses 22 by default. If you are using VNC over the internet, you should run your VNC with the -localhost option and tunnel 5900 or 5901 through SSH. This will encrypt your traffic. VNC uses port 5900 + display number. 5800 + display number is used for web access to the VNC server. This also should be sent through an SSH tunnel if you are communicating over the internet.

---

### Post by Herman on 2008-02-01
> SSH uses 22 by default. If you are using VNC over the internet, you should run your VNC with the -localhost option and tunnel 5900 or 5901 through SSH. This will encrypt your traffic. VNC uses port 5900 + display number. 5800 + display number is used for web access to the VNC server. This also should be sent through an SSH tunnel if you are communicating over the internet.Hello kernelCompile,
I was under the impression that the vcnviewer command with the -via option does make an encrypted TCP tunnel to the gateway machine before connection and connects to the host through that tunnel, and by default invokes SSH  local port  forwarding. That sounds pretty good to me, and seems to do the job really well.
```
man vncviewer
```Now I'm wondering if I'm interpreting the vncmanual page wrongly or if there is some evidence to suggest the option is faulty. I'm always open to corrections and new information.

Regards, Herman :)

---

### Post by ridgeland on 2008-02-01
I see the man page as saying 
vncviewer -via
uses ssh and is secure.  Two ways to do the same thing I guess.

I'm still working on my puzzles.
In SuSE
vncserver :2 -geometry 1024×768 -depth 16 -localhost
lets me add another port (here 5902) so I can
vncviewer -via davidssh@192.123.123.123 localhost:2
but unlike :1 it gives me a window with a terminal window CLI, no real GUI, so SSH is better than this :2.
But in Ubuntu
vncserver :1 -geometry 1024×768 -depth 16 -localhost
is met with a fatal error of could not open default font 'fixed'
I couldn't get past this before I remember.
So far my most helpful link has been
[http://www.realvnc.com/](http://www.realvnc.com/)
Still searching........

---

