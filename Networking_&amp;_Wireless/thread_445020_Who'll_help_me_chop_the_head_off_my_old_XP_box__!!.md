---
title: "Who'll help me chop the head off my old XP box ? !!"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by rubix64 on 2007-05-15
Heres the deal:

I am  a new linux convert and Im never going back. Aty the moment though what I am trying to do is to run my old Dell 4600 Inspirion (xp) as a headless box from my Ubuntu Box....

any ideas Ubuntu ninjas?


Thanks in advance all...Cheers

R

---

### Post by rubix64 on 2007-05-15
Oh yeah ..... if possible could the solution NOT involve a wireless router. I have major security issues here for some reason and my firewall is logging tens of thousands of attacks a month (even w/ my wireless gone) and when I had wireless someone was doing some major DoS attacks & I couldnt stop them...so maybe a solution involving a NAT router...i dunno  Im out of my league here..help!

R

---

### Post by rubix64 on 2007-05-17
O.K.  not all at once you guys ! :)

maybe I should have clarified a little bit...

I know that I need a NAT router to accomplish what I want to do but the specifics are where I get a little sketchy.

Im envisioning something like this:

                                                      ---------------->Linux box acting as an FTP server
                                                      |
ADSL --------->NAT router #1 ---- |
                                                      -------------NAT router #2 -------------> Secure Main Linux Box


Am I way off...retarded....crazy....any and all help appreciated especially NAT router make/model suggestions as well as their configuration with firestarter OR  is there a better way to do this?

Thanks again

Rube

---

### Post by commbot on 2007-05-20
um, what exactly is it you are trying to do?

you have a firewall, you have a connection. when you say a headless xp box do you mean you want to run xp on it without a kvm? if that's the case, I don't think its possible as i believe xp looks for a keyboard and mouse when booting and won't start without them. and while you can certainly run it without a monitor,  what on earth for?

if you want to run a linux box with an ftp server inside your network then thats easy

---

