---
title: "Need help with ndiswrapper and Dell Wireless 1450 USB2.0"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by hansi001 on 2006-08-11
Hi. I just installed Ubuntu Dapper Drake 6.06, and i LOVE it!!! The only thing is my wireless. I know i can just drag a ethernet cable over my livingroom, but i really want my wifi to work. Now I have been searching all over the web for a solution and I have found lots of grate articles about this, but i just can't get it to work ](*,) 

I have a Dell Wireless 1450 USB2.0 card. What do i do to install the windows driver with ndiswrapper? I think i have the CD with the windows drivers on here somewhere. 
Is there anyone on this forum that has made this on ubuntu with similar cards?
EDIT: This is my first time on Linux (except for my linux server that i worked with a few months ago running debian, so i know a little linux. I have also had a Mandriva installation once, but i didn't really like it)

Thanks for all answers :-D

---

### Post by hansi001 on 2006-08-11
Ok i have now installed ndiswrapper and it seems like evrything whent the way it should. 
This is what I get when I write ndiswrapper -l```
hansi@hansi-desktop:~$ ndiswrapper -l
Installed ndis drivers:
dellnic         driver present, hardware present

```
Evrything seems good so far.

I get no errors when writing modprobe ndiswrapper :D 

Now comes the weird part that i don
t understand.. When i type iwconfig i get this:```
hansi@hansi-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:"ThangstadLAN"
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth0      no wireless extensions.
```

anything i have missed?
does this mean my wireless is working???

---

### Post by az on 2006-08-11
Boot without the ndiswrapper module loaded, run

tail -f /var/log/messages

in a terminal.  In another terminal, load the ndiswrapper module and post the output of the tail here.

---

### Post by hansi001 on 2006-08-11
How do i loade the ndiswrapper module? modprobe ndiswrapper? sorry, i'm a little new to all this

---

