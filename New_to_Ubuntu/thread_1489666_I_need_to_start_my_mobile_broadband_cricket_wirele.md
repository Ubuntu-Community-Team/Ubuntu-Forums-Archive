---
title: "I need to start my mobile broadband cricket wireless modem through terminal"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by jakeeee on 2010-05-21
Anyone know how?

---

### Post by Chesamo on 2010-05-21
Why?

---

### Post by jakeeee on 2010-05-21
Long story short.
I messed my desktop up and need internet

---

### Post by Chesamo on 2010-05-21
You mean "set up" or "install".

[http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-cricket-wireless-a600-broadband-modem-in-ubuntu.html)

---

### Post by -humanaut- on 2010-05-21
If you can get a wired connection try sudo apt-get install wicd 

that will replace gnome-network-manager but don't worry its garbage wicd should set it up properly.

---

### Post by iponeverything on 2010-05-21
good news is can be done

bad news is that you need download usb_modeswitch and wvdial do it.

;)


```
sudo -i 
usb_modeswitch
/usr/bin/wvdial&
disown %1
exit
```

my /etc/wvdial.conf looks like this
google around for correct configuration for your provider
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATZ
Init3 = AT+CPBS="SM"
Init4 = AT+CPMS="SM","SM",""
Init5 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init6 = AT+CGDCONT=1,"IP","Telstra.Internet"
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 921600
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
 Phone = *99#
 Password = Telstra
 Username = Telstra
```

---

### Post by jakeeee on 2010-05-21
Can I do it without downloading anything..
I put that tar.gz on my flash drive but I dont think ubuntu is recignizing it.
I cant boot into gnome.
Im just at the terminal. You guys know what I mean right?

---

### Post by Chesamo on 2010-05-21
sudo mkdir /media/usb0 && sudo mount /dev/usb0 /media/usb0

---

### Post by jakeeee on 2010-05-21
Special device does not exist? :/

---

### Post by jakeeee on 2010-05-21
Error:

mount: special device /dev/usb0 does not exist..

---

### Post by -humanaut- on 2010-05-21
What happened to Gnome?

---

### Post by jakeeee on 2010-05-21
Idk..
I stopped a dist upgrade.
ANd shutdown
And now I have this.
So I'm trying to get internet so I can run sudo apt-get -f upgrade hopinf thatll fix things..

---

### Post by iponeverything on 2010-05-21
I would just tar up /home save it to flash drive and do and a fresh install on partition - then restore /home --

 It will probably save you lot of time and things might very well work better in the end.

Be careful though.. way to many people seem to nuke their windows partitions accidentally for some reason. I saw two yesterday and 1 today.

---

### Post by jakeeee on 2010-05-21
I was thinking about that.
But I have nothing to install off of.
No cd's. :|
My comp is to old to boot from usb too

---

### Post by iponeverything on 2010-05-21
you are in a pickle ;) 

I take it have a cdrom drive, just no CD? 

Call up someone, get them download the ISO and burn the CD for you.

---

### Post by elliotn on 2010-05-21
copy the tar file to desktop and extract it by double clicking on it then in terminal cd to the extracted folder.

The read me or install file would help

---

### Post by elliotn on 2010-05-21
> **elliotn said:**
> copy the tar file to desktop and extract it by double clicking on it then in terminal cd to the extracted folder.

The read me or install file would help

oops got lost

---

### Post by jakeeee on 2010-05-21
Alright.
I guess I'm just gonna wait till I get a cd.
I don't think theres anything I can do :/

---

