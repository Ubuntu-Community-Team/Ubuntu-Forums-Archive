---
title: "open a port in my ubuntu 7.1"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by Mo9a7i on 2007-11-19
Hello every one ,,
I just finished installing and fixing my ubuntu to the way i need
as i started to love linux ,, i actually removed all the windows files through my ubuntu file browser :p
:popcorn:
will never go back to that thing,,

any way ,, 
everything that i needed from my Windows, i found something better for it here in linux
:guitar:

there's still one more problem 
i tried searching here and in google about it and couldn't figure it out

my problem simply and directly is

[B][COLOR=Black]i want to open a port in my system (1523) to use for Netcat back[/COLOR] connection ,,

[/B] the port used to work perfectly on windows ,, by opening that port in the firewall thing ,, or disabling the whole firewall 


i had a hard time trying to do this with my iptables ,, i ended up removing iptables ,, but the problem still exists

i tried to connect to my pc through this site
[http://canyouseeme.org/](http://canyouseeme.org/)

but it never succeeded,


how many firewalls are there on ubuntu ?? is there anything other than iptables ?
or my understanding to the firewall concept on ubuntu is completely wrong ???


[COLOR=Black][B] i'd love to get my help as simple as possible
and plz don't refer me to another thread here in the forum or in any other site ,
i'm begging you:lolflag:

thanx in advance
[/B][/COLOR]

---

### Post by Mo9a7i on 2007-11-23
Thank you very much for reading

---

### Post by Blutack on 2007-11-23
Ubuntu will ignore forwards to ports by default.  However, if you have installed a program that listens on a port there is no reason that program will not work.  It's like a catflap that won't open from the outside.  Well, ok, not really like a catflap.  But if a program holds the catflap open then data can come in.  That is what things like Apache and SSH do.  
Do you use a router to connect to the internet?

---

### Post by Blutack on 2007-11-23
Oh, and rather than deleting all your windows files have you considered using Gparted on an Ubuntu live cd to delete the windows partition and grow your linux partition to fill the extra space...

---

### Post by Mo9a7i on 2007-11-24
Thanx for your reply bultack
i'll sure use Gparted from the CD as soon as i need the space

about the open port
yes i use NetGear DG834N router and i opened a port in it forwarded it to my IP address

Netcat is integrated in linux as i know ,, you can use it through the terminal by (nc) command

i tried listening to  a port 
but tried to reach my computer from that website i posted in the begining but the site says it can't see me
i don't know why that is happening actually

thanx again

---

