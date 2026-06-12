---
title: "Install Ubuntu Server on a computer with no monitor, mouse, or keyboard?"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-03
Hi!  Is it possible to install Ubuntu Server Edition on a computer with no monitor, mouse, or keyboard?  It does have a CD drive and a bootable network card.  I looked at the "Install over SSH entry on the Ubuntu wiki, but it requires keyboard input.  Is there any way I can accomplish this?

Thanks in advance!

---

### Post by halitech on 2009-04-03
do you have the link to installing over SSH? I'm not sure but from what I can remember you need to start it at the server and then continue over SSH (but I could be wrong)

---

### Post by pi.boy.travis on 2009-04-03
[https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole)

[https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH)

There they are.

Thanks for your reply!

---

### Post by pi.boy.travis on 2009-04-03
[https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole)

[https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH)

There they are.

Thanks for your reply!

EDIT: double post. . .

---

### Post by halitech on 2009-04-03
ummm yeah, way over my head. personally I'd recommend hooking up a monitor, keyboard and mouse and do the install, then shut it down and move it to where you want it minus the extras and power it up but thats me.

---

### Post by pi.boy.travis on 2009-04-03
There must be some way to do it. . .

What if one was in a large datacenter, and you wanted a rack without a human interface on it?

---

### Post by halitech on 2009-04-03
then one would probably follow those instructions but I don't follow them very well and the hardware is different then a home PC that you want to turn into a home server.

---

### Post by balloooza on 2009-04-03
I have just installed a server, it is the third I have done (I use Ebox ebox-platform. [http://ebox-platform.com/](http://ebox-platform.com/) web interface, screenshots: [http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79](http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79) )

And I did the install with a keyboard and a monitor, and now it runs without one, tucked away in a quiet corner, so it dose not disturb me with noise. This is common to have a server put away, without a monitor or keyboard (it is called a headless server) and the ebox web interface is a good way to control it.

What you are asking is difficult, because you will need to install the system with a keyboard and mouse, that is if it was a standered computer. There is one option, but it is not worth the time spent taking the monitor and keyboard that you are using now, and starting up the server with a fresh ubuntu server disk.

BTW, I just use this ebox (ubuntu 8.04 server, with some extera packages intstalled) at home, and it works great as a dns dhcp gayeway, and it runs a webserver, and a file server, all at once (in server world, that is not neccecarily good) The ebox administration is good, because it automagicly sets all the settings, ports to open, to make the system work.

---

### Post by pi.boy.travis on 2009-04-03
> **balloooza said:**
> I have just installed a server, it is the third I have done (I use Ebox ebox-platform. [http://ebox-platform.com/](http://ebox-platform.com/) web interface, screenshots: [http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79](http://www.getdropbox.com/gallery/644494/1/ebox?h=b9fc79) )

And I did the install with a keyboard and a monitor, and now it runs without one, tucked away in a quiet corner, so it dose not disturb me with noise. This is common to have a server put away, without a monitor or keyboard (it is called a headless server) and the ebox web interface is a good way to control it.

What you are asking is difficult, because you will need to install the system with a keyboard and mouse, that is if it was a standered computer. There is one option, but it is not worth the time spent taking the monitor and keyboard that you are using now, and starting up the server with a fresh ubuntu server disk.

BTW, I just use this ebox (ubuntu 8.04 server, with some extera packages intstalled) at home, and it works great as a dns dhcp gayeway, and it runs a webserver, and a file server, all at once (in server world, that is not neccecarily good) The ebox administration is good, because it automagicly sets all the settings, ports to open, to make the system work.


I usually just use SSH.  I'm a command line junky.  I thought I could just fire up SSH from the debian installer, but it asks too many questions first. . . .

---

### Post by CyberMando on 2009-04-03
Try 
aptitude show fai-client

---

### Post by pi.boy.travis on 2009-04-03
Sounds like just what I need!  Is there a website of a man page?

---

### Post by CyberMando on 2009-04-04
aptitude show fai-client
shows
Homepage: [http://www.informatik.uni-koeln.de/fai](http://www.informatik.uni-koeln.de/fai)

---

### Post by Net_Resident on 2009-04-04
> **CyberMando said:**
> aptitude show fai-client
shows
Homepage: [http://www.informatik.uni-koeln.de/fai](http://www.informatik.uni-koeln.de/fai)Very cool, not that I have a burning need for it but it is very cool for people that can make productive use of such a tool. :)

---

### Post by hyper_ch on 2009-04-05
I think in datacenter upon installation they just load a live system through PEX which then installs automagically a created basic image and then a few things are being changed like network settings and initial passwords.

---

