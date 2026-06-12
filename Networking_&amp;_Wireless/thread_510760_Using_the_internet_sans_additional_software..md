---
title: "Using the internet sans additional software."
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by Zeppelin! on 2007-07-26
I read:
[The advice for connecting to the internet, sans additional software]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6")

This is perfect for me, but I need to know how to get the information I'm going to need: your device name, ISP phone number, username and password

Can I get some help?

---

### Post by Zeppelin! on 2007-07-27
Okay, my problem is this, the number AOL supplies, doesn't seem to work with Networking app. I think this is because of how AOL does this connection.

I got this from a chat with tech support:

AOLTechFRM Pleased to meet you. 
Zeppelin! Hello, nice to meet you too. 
Zeppelin! Shall I begin? 
AOLTechFRM I am not able to determine exactly what type of assistance you need. If you could restate your question or provide more information, I'll be more than happy to assist you. 
Zeppelin! Ah, it was hard to describe. My problem is that I do not have any use for the AOL program, in fact, it doesn't even work where I need it. So, I wanted to use the number my computer uses to access the AOL service, to use an interface that does work where I need to be able to connect to the internet. 
AOLTechFRM Thanks for confirming the issue. 
Zeppelin! However, when I actually went to check my access numbers, none of them seem to work, and indeed, the number that appears when I am dialing in to AOL does not match any of those on the list. 
AOLTechFRM I appreciate the opportunity to handle this for you. I am going to do my best to make sure you receive all the help you need. 
AOLTechFRM How are you connecting? Do you have a dial-up connection or broadband connection like DSL, cable, or satellite? 
Zeppelin! Dial-up, cute little white modem port and everything. 
AOLTechFRM Thanks for confirming. 
AOLTechFRM The AOL software uses only the access number currently setup when connecting to the service. 
Zeppelin! So, (default access number AOL provides) should work? 
AOLTechFRM Sorry but I cannot guarantee that will work on the program that you are trying to use. That is the only available information we can provide regarding the access number. 
AOLTechFRM The AOL software only uses those number to make the connection. 
Zeppelin! Fair enough. Which makes life a little more difficult than it has to be. 
AOLTechFRM I suggest you to contact the manufacturer of the software that you are trying to connect to the internet, for further assistance. 
Zeppelin! Mmm, have a nice day. I've got plenty to think about. 
AOLTechFRM I suggest you to check the web site where you purchased the program to see if they you can fine there contact person. 
System The session has ended! 


All I gathered from this is that the number I was using is the first of a series of numbers necessary, which it is possible that the networking app doesn't pick up upon.

Then again, I'm not even sure I got Network to *try* to connect.

Can someone tell me how to actually connect? (I haven't installed Ubuntu yet, I'm using LiveCD. I'm making sure I can connect to the internet before I install it)

---

### Post by audax321 on 2007-07-27
The weird thing with AOL is that it uses some proprietary weird way of connecting to the internet. So you can't really connect using plain old dial-up networking. Its designed so you have to connect through the AOL software. However, there are other solutions. 

For Windows there is a program called PPPShar, but this is more or less intended to share a dial-up connection to AOL over a network. This could be a solution if you have a Windows box available to act as a server the Linux comupter can connect to. I'm not sure but it seems you will have to log in to AOL using their software on the Windows box for it to work. It's just internet connection sharing designed to work with AOL dial-up.

In Linux, the only thing I've come across is a program called Penggy. Its aim is to allow you to dial into AOL in Linux.

PPPShar: [http://www.pppindia.com/intl/pppshar/](http://www.pppindia.com/intl/pppshar/)

Penggy: [http://savannah.nongnu.org/projects/pengfork/](http://savannah.nongnu.org/projects/pengfork/)

This is some website I came across for Peng, which was the program Penggy forked from:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

This is where my help stops unfortunately. I haven't used PPPShar since the late 90s  and never had a chance to use Penggy because I switched to broadband before I got into Linux.

I'd try Penggy first because its in one of the repositories and is a much simpler solution.

Hope this helps you out.

---

### Post by Bartender on 2007-07-27
First thing to do is drop AOL.  Go with someone who doesn't use proprietary software.  Copper.net, 550access, totalspeed, Fry's, ISP.com are just a few U.S. ISP's that work with Linux.

---

### Post by Zeppelin! on 2007-07-27
Believe you me, I have every intention of going sans AOL in addition to sans additional software. But first, I need to get things working.

I'm checking out those ISP companies.

---

### Post by Zeppelin! on 2007-07-27
I keep finding the same problem with these ISPs over and over.

I need *UNLIMITED* access, not 300 hours. I need to be able to get on the computer, when I want, for however long I want, at a good price.

:s Any help?

---

### Post by Zeppelin! on 2007-07-27
NetZero any good?

-Scratch NetZero-

Netscape any good?

---

