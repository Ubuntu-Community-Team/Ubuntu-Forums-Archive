---
title: "[HELP] Remote control Win XP &lt;-&gt; Ubuntu"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Mustek on 2007-04-30
Hey, I'm currently setting up a gameserver on Linux,
As the server stands most of the time on an other location it's impossible
to get access to the server. My computer I use to work on is a Windows XP
Home edition. Is it possible to connect and controll the server with Windows XP
without having any costs?

Thanks in advance.

P.S. Sorry if this is the wrong section.

---

### Post by kvonb on 2007-04-30
For the Windows computer, download and install "vnc".  I believe you can get it from [www.realvnc.com]("http://www.realvnc.com").

On the Ubuntu computer it is already installed, go into the menu under system->preferences and enable remote desktop.

Then from your win computer, run vnc and connect to your Ubuntu computers IP address.

---

### Post by Mustek on 2007-04-30
Thank you for your fast reaction!
I'll go try it out.

---

### Post by peterLinux on 2007-04-30
Take a peek at nomachine too.

[www.nomachine.com](www.nomachine.com)
and there is an 'open' version called freeNX.

Peter

---

### Post by Mustek on 2007-04-30
Now, I'm also planning to make it a gameserver for Lan-party's etc...
Not a web server, should I use the server edition or does the normal edition it's job?

---

### Post by cerdiogenes on 2007-04-30
If you don't need graphical interface you can connect in it throw ssh from other Linux machine or with the putty application for Windows.

Best regards,
Carlosl

---

### Post by kvonb on 2007-04-30
Stick with the normal edition, there is no need for the server edition unless you have a really low end computer or are planning to run a major web server.

The server edition does not have a GUI.

---

### Post by Threbus5 on 2007-04-30
Hi,

I have been using NX client for Windows (free from NoMachine) for quite a while concurrently with the Linux remote desktop to allow windows machines acess to games and apps on a Linux machine. They each configured easily and work well.

Best wishes for success on your plans.

Your bidirectional arrow indicates a desire to enable Windows to also accept remote desktop control from the Linux.
the procedure by jbaloul at [http://ubuntuforums.org/showthread.php?t=224212&highlight=rdesktop](http://ubuntuforums.org/showthread.php?t=224212&highlight=rdesktop) worked perfectly on the first attempt between Dapper Ubuntu and Windows XP Pro. It might work for XP Home.

Take care

---

### Post by frafu on 2007-05-01
Hello, 

I am moving this thread to the Networking &Wireless forum, where it is more appropriate. 

Have a nice day.

---

### Post by Kourosism on 2007-11-20
Is it possible to do this is reverse? I mean, I want to control XP from my Ubuntu laptop...

---

### Post by xxLONESTARxx on 2008-01-20
Yes it is possible to do the reverse. I remote into my work PC (WinXP) from my home PC (Ubuntu). I set up my VPN connection through the Network Manager and use the Terminal Server Client to remote into work PC.

---

