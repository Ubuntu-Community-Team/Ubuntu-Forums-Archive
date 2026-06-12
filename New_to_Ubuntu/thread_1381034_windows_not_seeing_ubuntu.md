---
title: "windows not seeing ubuntu"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by aprillia99 on 2010-01-14
ok i have a ubuntu machine, and 2 vista machines. the ubuntu is a basic server. so my problem is vista machine A can see the ubuntu machine through the internet wirelessly, but vista Machine B cannot. if i hook up machine B directly to the LAN with a cat5 it can see the ubuntu machine but not wirelessly.

is that a ubuntu problem or a windows problem and if anyone has any suggestion let me know ty.

EDIT 

also vista machine A and B can see eachother

---

### Post by warfacegod on 2010-01-14
If machine A can see it but not machine B that would almost certainly be Windows on machine B's fault not Ubuntu's.

---

### Post by aprillia99 on 2010-01-14
Thats what i thought to but i was just checking ty tho

---

### Post by warfacegod on 2010-01-14
It is possible (unlikely) that your Ubuntu machine is masking itself to machine B and not A. Again, unlikely.

---

### Post by donaldhall on 2010-01-14
well the thing in windows is your using vista. Windows completely redesigned the networking scheme so thats why it wont see the machine. same thing happens if you have XP and Vista machines, the xp will talk to vista, vista will not talk to xp. Pretty lame if you ask me.

EDIT: Also have you tried to see if your Ubutu machine can see both Vistas' wirelessly

---

### Post by DestructionsRightHand on 2010-01-14
Can your windows box read Ext.*

---

### Post by fromthehill on 2010-01-14
define "seeing"
if you're talking about windows/samba shares try typing \\<ip-adress> in a windows explorer window bar

---

### Post by Morbius1 on 2010-01-14
So VistaB can see linux when wired to the router but cannot when wireless?

Do you have the same firewall and anti-virus on VistaA and VistaB? What you could try is this:

On VistaB when wireless:

Open **Command Prompt** ( not "Run" but Command prompt )
Type **net view**

It should output to the Windows terminal all the machines on your network from Vista perspective. If we're lucky it will post some kind of error message about your linux box.

---

### Post by DestructionsRightHand on 2010-01-14
What are the wireless settings?  Do you isolate the wireless or the wired lan?  What are the firewall settings?  on network connections right click the connection and verify the ipsettings and "File and Print Sharing for Microsoft Netowrks?" is enabled

---

### Post by steve-shinn on 2010-01-14
> **donaldhall said:**
> well the thing in windows is your using vista. Windows completely redesigned the networking scheme so thats why it wont see the machine. same thing happens if you have XP and Vista machines, the xp will talk to vista, vista will not talk to xp. Pretty lame if you ask me.


Sorry but that's just not true. I have 3 pc's 1 running ubuntu 9.04 one running vista and one running xp, and each one see's every other pc and shares files !

---

### Post by steve-shinn on 2010-01-14
Have you tried pinging the pc's from machine b when connected wirelessly ?

---

