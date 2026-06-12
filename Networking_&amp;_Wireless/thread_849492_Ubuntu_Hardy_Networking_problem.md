---
title: "Ubuntu Hardy Networking problem"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by nickdiacre on 2008-07-04
Hi there,

I am abit confused regarding samba and networking in Ubuntu. I have been using it for about a year and am really enjoying it... 

Recently I have put my hand to networking via wifi, and I have a problem which no amount of searching  can solve...

I have 3 laptops...

1) Targa Ubuntu Hardy + printer
2) Lifebook Ubuntu Hardy
3) Acer WinXP

a) Targa and Acer can both be seen on the network, and share fine.

b) Lifebook can see the others, and access files fine.

c) Targa and Acer cannot see Lifebook at all.

d) When I try to share a folder on Lifebook I get "net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Access denied." error.

e) All three can print fine to the printer.

Usually I manage to solve my problems thru forums and google, but this has me stumped...

Any ideas would be very much appreciated!

Thank you for all your contributions in the past... Linux was for years an unsurmountable hurdle, but thanks to the Ubuntu community I have finally got to try it out, and damn is it good.

Regards
to all


Nick

---

### Post by terencelhl on 2008-07-04
Hi Nick,

Kindly provide more information such as

1) IP addresses for each computer
2) user names created on each computer
3) Firewall/router/ADSL used

Thank you.

Terence Loo

---

### Post by nickdiacre on 2008-07-04
OK...

Targa(ubuntu)= dogboy-targa on 192.168.0.110
Lifebook(ubuntu)= dogboy-lifebook on 192.168.0.101
Acer(winxp)= ANNA on 192.168.0.102

This is using a D-link DIR-301 wireless router.

The Acer winxp box user is 'annabee' (admin)
Both ubuntu boxes user is 'dogboy'...

Thankyou for the quick response...

Regards

Nick

---

### Post by nickdiacre on 2008-07-06
Sorry... just to add to this...

if i type smb://dogboy-targa/

i can get to the machine, I just don't see it in my shares...

Thanks

Nick

---

### Post by pietjanjaap on 2009-06-20
Try to use the samba (and not share on the map itself).
Go to system-administration-samba, here share the map you want, put users in it, and fill in server info.

---

### Post by Iowan on 2009-06-22
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To (maybe you've already seen it). This part might be helpful for Lifebook:> Problem 2 - part 2
It may also help to add netbios name = computer-name just below "workgroup = WORKGROUP".

Your "computer-name" can be anything, but common convention is to use the name you gave it when you installed Ubuntu (everything after the "@" symbol on the CLI prompt).


---

