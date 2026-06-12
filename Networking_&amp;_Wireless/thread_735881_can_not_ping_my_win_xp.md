---
title: "can not ping my win xp"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by imax36581 on 2008-03-26
hi
im have a workgroup with two computer win xp and ubuntu gutsy
but i cant ping my ubuntu from win and vice versa.
what should i do to that computers see each other.
10x

---

### Post by anantshri on 2008-03-26
please check the following things before handedly.

1) ip addresses : they should not have same address rather should have addresses in same range.

2) check physical connection.

as both side pinging is not working also check your switch.

Tell us the result so that we can help you furthur.

---

### Post by peitschie on 2008-03-26
Also some other questions to answer:
[LIST]
[*]Do the windows XP computers have firewalls? (This INCLUDES the default windows firewall which will block pinging)
[*]Are you trying to ping the Windows computers by name or by ip address (e.g., 192.168.0...)?
[/LIST]

---

### Post by imax36581 on 2008-03-26
im sure that my ip's in the same subnet
im using mask 255.255.255.0
im sure my physical connection work perfectly..because one of the pc's have both ubuntu and xp...and when i work with xp its works the problem is when im using ubuntu it isnt work
ping is ping ....(just  icmp protocol) ... it must work but.....
i have two network adapter on of them for internet connection(eth0) and another(eth1) connect to my laptop(win xp).

---

### Post by imax36581 on 2008-03-26
> **peitschie said:**
> Also some other questions to answer:
[LIST]
[*]Do the windows XP computers have firewalls? (This INCLUDES the default windows firewall which will block pinging)
[*]Are you trying to ping the Windows computers by name or by ip address (e.g., 192.168.0...)?
[/LIST]

no ...my firewall donot block icmp protocol.
i donot have any wins or dns so im using ip address to ping.

---

### Post by peitschie on 2008-03-26
> no ...my firewall donot block icmp protocol.
Can your XP computers ping each other...?

---

### Post by imax36581 on 2008-03-26
> **peitschie said:**
> Can your XP computers ping each other...?
yes
all of the things between two windows is true .the problem is when i use ubuntu.
thanks
im wait for your anwsers.....

---

### Post by imax36581 on 2008-03-26
:-s:-k
really i dont know what was the matter?
just by resetting my configuration my problem fix and all things work perfectly!!
if i work with windows this event is usual but in ubuntu ....i think we use that method(for example : uncheck the check box and check it again) just in windows.but know see it in ubuntu...
thanks fo all of the answers

---

### Post by peitschie on 2008-03-26
Hmm... that is mysterious!  Just out of interested, had you restarted the Ubuntu box while trying the pinging?  It occasionally has issues if it gets its eyes crossed while trying to set up the network.

Oh, and regarding pinging by computer name, you don't actually need a dns server.  Windows uses something called "Samba" which allows you to use the computer-listed name (this will need to be unblocked through the firewalls though).  Linux can also link into this with a little bit of configuring, but if you indicate an interest I'm pretty sure I can dig up relevant posts for you.

Glad its all working for you now :)

---

### Post by imax36581 on 2008-03-27
> **peitschie said:**
> Hmm... that is mysterious!  Just out of interested, had you restarted the Ubuntu box while trying the pinging?  It occasionally has issues if it gets its eyes crossed while trying to set up the network.

Oh, and regarding pinging by computer name, you don't actually need a dns server.  Windows uses something called "Samba" which allows you to use the computer-listed name (this will need to be unblocked through the firewalls though).  Linux can also link into this with a little bit of configuring, but if you indicate an interest I'm pretty sure I can dig up relevant posts for you.

Glad its all working for you now :)


im reset my pc after resetting the ip address and after it its work....!?
i dont thinks that we have to  restart our pc after reseting confiquration.....erally we dont need restarting in this situation but.....

---

### Post by anantshri on 2008-03-27
> **peitschie said:**
> Hmm... that is mysterious!  Just out of interested, had you restarted the Ubuntu box while trying the pinging?  It occasionally has issues if it gets its eyes crossed while trying to set up the network.

Oh, and regarding pinging by computer name, you don't actually need a dns server.  Windows uses something called "Samba" which allows you to use the computer-listed name (this will need to be unblocked through the firewalls though).  Linux can also link into this with a little bit of configuring, but if you indicate an interest I'm pretty sure I can dig up relevant posts for you.

Glad its all working for you now :)


good to hear that your problem is solved.


and hey buddy,
SAMBA is a linux software made to act as a medium to let the linux machine access windows server.

i am not sure about ubuntu but samba comes preconfigured and ready to use with debian.

---

### Post by Eiríkr on 2008-03-27
Samba isn't installed by default in Ubuntu, but it's very easy to install as it's there in the repositories.  

Incidentally, while "Samba" is indeed the name of the Linux package for Windows sharing, the name comes from the acronym "SMB", which stands for "**_S_**erver **_M_**essage **_B_**lock", a network protocol for networked file systems first developed some time before 1990 at IBM.  Microsoft picked it up for Windows sharing in 1990, and has stuck with it since (though it has been greatly expanded and the name was changed to CIFS, for "**_C_**ommon **_I_**nternet **_F_**ile **_S_**ystem").  Have a look at [the Wikipedia article]("http://en.wikipedia.org/wiki/Server_Message_Block") if you're at all interested in the history and other details.  

Cheers,

Eiríkr

---

### Post by peitschie on 2008-03-27
I stand very corrected on the samba issue.  It needs to be noted though that just installing samba would not provide the ability to ping other computers by their windows network name. Thanks all for the clarification though :D

---

### Post by kazak_vmik on 2008-03-28
**Delete your Windows XP and install Ubuntu 7.10 :)**

---

