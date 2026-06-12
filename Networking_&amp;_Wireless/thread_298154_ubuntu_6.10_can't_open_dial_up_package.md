---
title: "ubuntu 6.10 can't open dial up package"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2006-11-12
I am trying to install a package for my dial up modem cnxtinstaller.run.  when I enter sh cnxtinstaller.run I get back a message like this:  verifying archive integrity ---all good.
uncompressing linus drivers for conxant modem chip set installer verion 0.9.8 please run this installer as root you cam probably do it with the 'sudo sh cnxtinstaller.run' command

When I use sudo shcnxtinstall.run command I get:  uncompressing linux drivers for conexant modem chip set installer verion 0.9.8 eval: 1: ./setup permission denied. 

does anyone know why I can't install this program or am I just doing something wrong. :confused:

---

### Post by towsonu2003 on 2006-11-13
looks like you're trying to install a conexant driver. did you check [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) to see if it has better instructions? 

PS. I don't know why it gives "permission denied" with sudo...

---

### Post by ronbrooks on 2006-11-13
I am having the same trouble as you are with the same message. I hope we can find out why it is not working.  I have sent three e mail to Linuxant and as of yet no reply.

---

### Post by ronbrooks on 2006-11-14
I got a answer back from Linuxant on the package for conexant chipset with Ubuntu 6.10 and I am e mailing them again because with what they sent me is not working either. I will keep posting until I get it working. If anyone else has an answer please post it here.

---

### Post by ronbrooks on 2006-11-16
OK I got the diver installed but now I can't set it up because it is not showing up in the list of modem to install when I try to set it up.  I can see the file ttyshsf0 but it is not one of the choices on the drop down menu.  Does anyone know why this would be.

---

### Post by m24f75 on 2006-11-17
[FONT="Tahoma"]Hi to all,
I have the same problem :confused: and the same message :evil: "uncompressing linux drivers for conexant modem chip set installer verion 0.9.8 eval: 1: ./setup permission denied" 

Ronbrooks could you indicate me how has Linuxant support fixed the first problem?

Thanks![/FONT]

---

### Post by ronbrooks on 2006-11-19
No I have not fixed the problem as of yet It is like firefox is not seeing the modem at all.  I have checked to see if the modem was in the drive manager and it is. I have had some e mail help with linuxant but as of yet we have not been able to get it going. I am still working on it and hope to get it going some time before the first of the year.

---

