---
title: "Huawei E169"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Mbengi Bongi on 2008-08-20
Hi Guys

I am trying to get my Huawei E169 (K3520) USB modem to work in Hardy.

Currently my only internet connection is through the Mac using the modem.

I'm trying to configure my **wvdial.conf** and am unsure what settings I need, my network is Vodafone UK.


can anyone help?

---

### Post by Fingers &amp; Thumbs on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)

The above link should be usefull.

---

### Post by siouzi on 2008-08-20
Same problem here. What I've found out so far that the modem doesn't even reply to wvdial if theres only one /dev/ttyUSB* device. Only once after I plugged it in there were /dev/ttyUSB0, /dev/ttyUSB1, ... like four of them. Then I got something more out of wvdial... ending with NO CARRIER repeating over and over again... *sigh*

---

### Post by siouzi on 2008-08-21
Sweet, I got my modem to work! The problem is not completely resolved though. Anyway, here's some observations.

- The dual usb memory stick / modem function seems to cause problems in Hardy. On one Hardy machine E169 was consistently recognized as a memory stick (usb mass storage), but on another machine, most of the time kind of "in between" because neither function would work. I have yet to solve this problem but some usb_modeswitch thing is required I think...

However, IF the modem is recognized but you get only one /dev/ttyUSB* device, this does help:
```

> sudo modprobe -r uhci_hcd
> sudo modprobe uhci_hcd

# now you have four /dev/ttyUSB* devices, which is the correct number
> ls /dev/ttyUSB*
/dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2 /dev/ttyUSB3

```
(source: [http://ph.ubuntuforums.com/showpost.php?p=3902243&postcount=98](http://ph.ubuntuforums.com/showpost.php?p=3902243&postcount=98))

- One time I did get four devices without the modprobe, but the modem just ended up saying "Bad init string." - and that same init string works now... go figure.

- As for how to connect, wvdial seems to be #1 choice. There is a LOT of variations on how to configure the **/etc/wvdial.conf** file and one line (Init3 below) depends on your mobile operator, so you either have to search for the correct format or try without it. Here's what worked for me (modify or remove Init3 line!):
```

[Dialer Defaults]
Phone = *99***1#
Username = *
Password = *
NewPPPD = yes
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Init = ATZ
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","ACCESS POINT NAME HERE, try: internet"

```

When you see a blue light (color depends on network speed, but some indication that the modem is connected), to connect just do: sudo wvdial

**Obviously this is a makeshift solution**, but at least you'll know if the modem works or not... =)


- Note that if the modem has a default pincode (like 0000), you might want to remove it using a mobile phone first because a pincode WILL STOP you from connecting! I did saw a wvdial configuration with a pincode but I have yet to try it, so using one should be OK...

- If you've tried gnome-ppp already, it's configuration file might mess things up... remove ~/.wvdial.conf.

---

### Post by Mbengi Bongi on 2008-08-21
Have tried all your suggestions, and am no longer getting error messages relating to the ttyUSB0 etc, but I think I'm getting what you got Siouzi i.e. **No carrier detected** repeating!

Any ideas?

---

### Post by Mbengi Bongi on 2008-08-21
Have just managed to get connected, forgot to have the dongle in at boot time!

Thanks for all your help guys

---

### Post by adm1968 on 2008-10-03
Did you see this? [http://blog.surgeons.org.uk/2008/02/three-cheers-for-vodafone.html]("http://blog.surgeons.org.uk/2008/02/three-cheers-for-vodafone.html")

---

### Post by Redptc on 2008-10-03
> **adm1968 said:**
> Did you see this? [http://blog.surgeons.org.uk/2008/02/three-cheers-for-vodafone.html]("http://blog.surgeons.org.uk/2008/02/three-cheers-for-vodafone.html")

Thanks for this link!

---

### Post by adm1968 on 2008-10-19
You are welcome!
;)

---

