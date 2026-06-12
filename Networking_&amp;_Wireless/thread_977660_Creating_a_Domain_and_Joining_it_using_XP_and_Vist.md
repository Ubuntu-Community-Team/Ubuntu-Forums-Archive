---
title: "Creating a Domain and Joining it using XP and Vista"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by -tom-64 on 2008-11-10
Hi,

Well I dont have ANY experience in ubuntu server or all of the server stuff but have been reading around about using SAMBA or something like that.

Currently I have a XP Pro machine with a shared hard drive and have one XP Pro and one Vista machine, with 4 accounts on each, with each accounts' my documents folder located on the XP Pro 'server'

But I'm looking for something better! I have heard about using 'Windows Home Server' but that costs and I like to use the open source option if I can!

I have fiddled with ubuntu desktop before but never ventured into using ubuntu server.

I have a Netgear DG834GT with the Vista machine and the XP Pro 'server' hard wired and the other XP Pro machine is wireless.

I also have one spare PC which I can hard wire to the router as well, but I would like to eventually swap over onto using ubuntu server on the computer that currently runs as the 'server'

Are you keeping up? 

So the question is, HOW do I create a domain on the spare PC (Using ubuntu?) and then be able to connect to that using a logon on the vista and XP Pro machines and access files and one printer (Connected to the wireless XP Pro) on either of the two machines?

Thanks in advance for the help,

Tom

---

### Post by gpsmikey on 2008-11-10
Check out the book "Samba 3 by Example" - there is a free pdf version of it here:
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
(or you can buy the book from Amazon etc).  Lots of examples in there of different configurations and he explains why he does what he does for the various configurations.  I have found it very helpful in trying to get Samba to do what I wanted.  There are a number of steps you have to do (I haven't done it yet, but it is on my todo list !! ) :)

mikey

---

### Post by bab1 on 2008-11-10
It's worth noting that the example installation is on Redhat with rpm packages.  The install sections should be skipped.  The implementation examples are correct for Ubuntu (Debian).

---

### Post by -tom-64 on 2008-11-10
yes I realised that :)

They look very useful thank you.

Tom

---

### Post by -tom-64 on 2008-11-10
ok so I have been following that guide and another one at [here]("http://ubuntuforums.org/showthread.php?t=640760")

when editing the file at etc/network/interfaces i cant seem to edit the file as it says permission denied when trying to save it. I am using NANO to edit it by the way

Tom

---

### Post by gpsmikey on 2008-11-10
you need to use sudo to give yourself root rights for editing most of those config files since they are typically owned by root and set so only root has write privs.

mikey

---

### Post by -tom-64 on 2008-11-10
googled it and found out that you cant edit while connected to a network so shutdown, disconnected cable, booted, changed, saved, shutdown, connected cable, booted...

Then when it was booting i got two items which 'failed'

The first was the network interfaces (will get the exact text later)

and the second was the firewall which it said was not enabled anyway?!?

Tried loggin onto the server via the static IP but says server is taking too long to respond.

SO what now?

Tom

---

### Post by gpsmikey on 2008-11-10
eh ??  As a test, I just went in on my server in a window and did
"sudo vi /etc/network/interfaces" -- added a comment in it and wrote it back out again with no problem.  Checked the file and my comment is just where I put it.  This is on a machine that is a server in my LAN here at home (in fact, I did the edit via a window using PuTTy from my XP machine so it HAD to be running the network or PuTTy would not have worked).

mikey

---

