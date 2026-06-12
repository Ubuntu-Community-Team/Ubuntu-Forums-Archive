---
title: "cannot get my netgear WN511B-PCMCIA device to work"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by t0bias on 2006-10-12
hi

i cannot get my netgear WN511B-PCMCIA-device to work,
[see here]("http://www.netgear.com/Products/Adapters/RangeMaxNextWirelessAdapters/WN511B.aspx").
the system 6.06.1 doesn't show me the card in the network manager.
what to do?

thanks,

toby

---

### Post by lazcool on 2006-10-26
Same here.

Does anyone know if a driver is imminent (no mention of it, or even 802.11n in the lkml!), or should I ebay it?

---

### Post by jalexstark on 2006-11-08
I wouldn't eBay it.  For my part, I am hoping that a new laptop that I am helping someone with at the end of the month will work with, say, ndiswrapper:
[http://ndiswrapper.sourceforge.net/support.html]("http://ndiswrapper.sourceforge.net/support.html")

---

### Post by lounge lizard on 2007-12-15
Hi there, I'm fairly new to ubuntu (installed yesterday and used linux for the first time), I had the same problem with the wn511b pcmicia card. After reading a number of the issues on this forum about this card I downloaded the NDIS wrapper but could not get it to load. However I did find the same software in the applications add/remove section and run the wrapper from there, I managed to get hols of the WN511b.inf file from an older laptop that I used the netgear card on and copied the inf file from the netgear driver fold in program files to mt docs in ubuntu. Run the wrapper pointer the browse at the inf file and BINGO as was well. BRILL and easy.

Hope this helps, it was easy, even for a ubuntu/linux virgin like me.

Lounge Lizard

:popcorn:

---

### Post by stump1k on 2008-03-09
If you have integrated wireless, make sure you disable that in device manager before installing this adapter.  Download the newest drivers from Netgears website and run them, and do exactly as it says.  It took me 3 hours lastnight to figure out why mine would install right.

---

### Post by uberlube on 2008-03-09
I just found the driver on netgears support page:
[ftp://downloads.netgear.com/files/wn511b_setup_6_0.exe](ftp://downloads.netgear.com/files/wn511b_setup_6_0.exe)

You could use the HOWTO in my sig to install this. Just modify the guide a bit.
```

mkdir /root/wireless_driver
cd /root/wireless_driver/
Then put your .exe in here
unzip -a (the .exe file name)
Then find the .inf file and
ndiswrapper -i (.inf file name)
modprobe ndiswrapper
reboot


```

this should work

---

### Post by odysseusjak on 2008-04-16
Okay.  I got this working...sorta.  Whenever I reboot the system, wifi doesn't work automatically.  I have to launch terminal and do a modprobe ndiswrapper then it works.  How do I have it load the card each time?

Thanks.

---

### Post by bmachia on 2008-04-17
I, like a few of you folks, have the same problem.  

I just got a Netgear wn511b and had to dnload the drivers (Version 6.0) from Netgear support website.  

I did an ndiswrapper -i wn511b.inf

This did install into ndiswrapper, (confirmed with an ndiswrapper -l) but the card just flashes after a 'modprobe ndiswrapper' & Reboot.  I'm wondering if I have the wrong inf & sys files.

Can any one point me in the right direction for inf & sys files that work with this card on their system?
Also;
How successful have folks been using Draft N speeds with this card?  Or should I just expect 802.11g performance?

FYI, I'm running Gusty, 32 bit

Thx
Bill

---

### Post by odysseusjak on 2008-04-18
Attached are the drivers I use.  According to the Active Connection Information window, I am connected at 130Mbs.

---

### Post by mazor on 2008-06-29
I too am having problems getting my WN511B CPMCIA card working in Ubuntu 7.04. 

After sudo modprobe ndiswrapper, I get bright blue fashing light on the Wireless card, and a new adapter appears, but I am unable to scan or connect manually to any wireless networks.

---

### Post by mazor on 2008-06-30
Update, I managed to get the scanning going.

You must use "sudo iwlist scan"

Failing to do so, the scanning using ndiswrapper does not work, and hence no visible networks will appear in Network-admin.


Still having problems connecting though to visible access points. By some luck I managed to get it to go once, and the flashing blue light became a solid blue light, but have not got a successful connection since then.

MAzor

---

