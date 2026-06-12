---
title: "plain old telephone in ubuntu?"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by juanitobanana on 2008-06-26
Hello, I have been reading many many posts and searched for a solution for this but it simply isn't clear..

to avoid confusion, this thread doesn't concern internet connection in ANY way. I just want to call through a british normal telephone line so I can make and receive calls.

(again no VOIP in this thread)

I would like to put my telephone line to a voice modem and be able to use my computer with microphone and speakers as a phone. Of course I would love then to use some great applicatioin that would make calls log them etcetera. what is the Hardware/ software available for this? I've seen the ISDNHowto page in [https://help.ubuntu.com/community/IsdnHowto](https://help.ubuntu.com/community/IsdnHowto) but I'm not sure that this "ISDN" would also allow a phone call to POTS (I'm new to this terminology, anyway). 

I also checked for this [http://forums.bit-tech.net/showthread.php?t=111225](http://forums.bit-tech.net/showthread.php?t=111225)

every post I see on the subject is a dead end, some don't even get answers..

This is my first post anyway, please be gentle ;-)

---

### Post by cmay on 2008-06-26
hi .
try go to the local music store
or find a place where you can buy a signal splitter that is designed for this purpose.
 so once the phone line gives an audio output you can record or amplifie trough external media.
 you can use the computer or stereo system if you choose.
some companies use this to record the calls they recieve from customers.
if any other fails then ask a phone company what they do.

hope maybe that can help.

---

### Post by juanitobanana on 2008-06-26
but this signal splitter could be controlled by the computer? isn't there any specialized hardware to make simple phone calls? (I guess that's what voice modems do but everyone is talking about Pc answering machines or automatic dialing and nobody says plainly "making voice telephone calls" or any equivalent through your pc microphone..)

I'm pretty surprised this doesn't already exists in a mass scale since it would be very simple hardware and could replace the thousands hyper advanced telephones I see everyday on a trading floor, by simply using some well done software and a good voice modem (again I am still not sure voice modems are for this..)

---

### Post by juanitabanana on 2008-06-26
OK.. after 2 days of active searching (even during work) I guess one of the (alive) applications I'm looking for would be ANT is not a phone. on [http://www.nongnu.org/ant-phone/](http://www.nongnu.org/ant-phone/)

I'm posting this because it looks like a promising application and it isn't well publicized on the internet since I didn't find it before..

---

### Post by lisati on 2008-06-26
I've seen Windows software that can make a PC behave like a super-intelligent call centre/answering machine without the need for special hardware other than the normal modem and the speakers a PC already has and a microphone, so I'm pretty sure it can be done with Linux too,.

---

### Post by sTpny on 2008-07-22
Hey bud, you need to look in your synaptic package manager... ant-phone is already there, and there is vbox3... 

voice response system for isdn4linux
vbox3 can answer phone calls on ISDN lines, and also initiate phone
calls itself.  In a simple configuration it can act as a answering
machine, playing and recording messages, recorded messages are
forwarded through email.  With the help of the raccess4vbox3 package
it's possible to create a complete voice response system, with DTMF
touch-tone support, navigating through menus, and even remote
controlling your Debian system.

See [http://smarden.org/pape/vbox3/](http://smarden.org/pape/vbox3/) for details. 

... 

and then there is mgetty....


The program 'mgetty' allows you to use a modem for handling external
logins, receiving faxes and using the modem as a answering machine without
interfering with outgoing calls.

This package includes basic modem data capabilities. Install mgetty-fax to
get the additional functionality for fax. Install mgetty-voice to get the
functionality to operate voice modems.

... and isdnvbox

ISDN answering machine, client and server
Let your debian system be your answering machine! Messages can be accessed
remotely, automatically emailed, etc.


...  That all comes from synaptic... learn to use it well.. it is your friend.

---

### Post by dmizer on 2008-07-22
frankly ... unless you're configuring your computer as a PBX server (as with a call center), there's really not much call for this.  mostly because duplexing with a computer mic and speakers makes for terrible call quality.

i think [decibel](http://www.nlnet.nl/project/decibel/description.html) seems to be what you're looking for.  it is in the repositories.

---

