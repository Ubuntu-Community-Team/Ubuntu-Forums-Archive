---
title: "Network Manager"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by i386DX on 2007-01-08
I used [this](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61) howto to install the RT61-driver, which worked (i think...)
then I followed [this](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) tutorial to install networkmanager/WPA.

Now I think that networkmanager doesn't recognize my wireless networkcard. When I click on the network manager icon I don't get I screen like this:

[img]http://www.debianadmin.com/images/wpa/2.png[/img]

I only see 'wired network'
there are no wireless networks found (that's ok at this moment, because there are no wireless networks at this place) but I think I should see Connect to other wireless network and Create new in the menu or does networkmanager work like that?

ifconfig gives:
```

ra0       RT61 Wireless  ESSID:""
           Mode: Auto  Frequency:2.412 Ghz    Bit Rate=54Mb/s
           RTS thr:off    Fragment thr:off
           Link Quality=0/100    Signal level:-121 dBm     Noise Level:-111 dBm
           Rx invalid nwid:0   Rx invalid crypt:0     Rx invalid frag:0
           Tx excessive retries:0    Invalid misc:0     Missed beacon:0

```

iwlist ra0 list
```

ra0      No scan results

```

I'm not sure if there's anything wrong (i don't have a wireless connection at this place), but I want to be sure that it works when I enter a network. Everything looks normal, but I think I should see Connect to other wireless network and Create new Wireless Network in the networkmanager menu even there's no wireless network available?

---

### Post by teaker1s on 2007-01-08
gnome panel click
system 
administration
networking

your interfaces must be unconfigured to allow
[COLOR="Red"]
network-manager-gnome[/COLOR] manage them

---

### Post by i386DX on 2007-01-09
I already did that...

---

### Post by darkmediator on 2007-01-09
@i386DX : 
1. Open "/etc/network/interfaces" and comment the "wireless" interface from it like eth1 if that corresponds to ur system!
2. Do "sudo /etc/init.d/dbus restart"
or reboot!
3. It shud work now!

---

### Post by i386DX on 2007-01-09
Also this is already done (see second howto)...

---

### Post by @trophy on 2007-01-09
I have my own thread about this problem... unconfiguring the card and commenting/deleting it out of /etc/network/interfaces has no effect.  Is there anything else I could try?

---

### Post by i386DX on 2007-01-09
Do you have the same driver of me? (rt61) or another one?
My card is a D-link DWL-G630 ver E1 (pcmcia)

---

### Post by @trophy on 2007-01-09
No, mine's a 2WIRE branded Orinoco Gold (Hermes I chipset) and I've patched the native drivers to include support for monitor mode.

Let me know if you find anything else I should try...

---

### Post by @trophy on 2007-01-09
Bumped in the hope that someone else might be able to help us.

---

### Post by gloscherrybomb on 2007-01-09
I also have this problem, with a INPROMM 2220 wireless card.

To get the net to work I have to use admin-networking, disable the device and then enable it again. It doesnt work from system start up. Also I can't use network manager even after following all of the above steps as it just shows a grey box saying wired connection. no options at all regarding wireless, Im guessing it doesnt recognise my card. please help!

---

### Post by darkmediator on 2007-01-10
> **i386DX said:**
> Also this is already done (see second howto)...
Then its most probably a driver problem!

---

### Post by RainGeek on 2007-01-12
I seem to be having a similar problem - I only see "Wired network connection".

I have a Broadcom BCM4310 chipset and had to use ndiswrapper. I have a thread going about my problems there - my hardware appears to be working but I can't get network manager (or network tools, for that matter) to use it. I thought this was a configuration problem until someone pointed out I might have a network manager problem and to scan for that, which is how I found your post.

My other thread:
[http://www.ubuntuforums.org/showthread.php?p=1985447#post1985447](http://www.ubuntuforums.org/showthread.php?p=1985447#post1985447)

On different from what has been posted thus far, my ifconfig doesn't even show an entry for ra0 or anything else. Only eth1 (ethernet port) and lo.

-RG

---

### Post by i386DX on 2007-01-15
> **RainGeek said:**
> 

On different from what has been posted thus far, my ifconfig doesn't even show an entry for ra0 or anything else. Only eth1 (ethernet port) and lo.

-RG

I have exactly the same problem.
When I add the ra0 interface to my /etc/network/intefaces-file I get output the right output on iwconfig etc (but not found by networkmanager).
When you remove those lines (because it has to be done for networkmanager) nothing works anymore...

---

### Post by Helgeland on 2007-01-18
I also have this problem. Using the RT61 driver,  my only options in the networkmanager applet are  
wired network (nVidia corporation ck804 ethernet controller)
wired network (RaLink RT2561/RT61 802.11g PCI)
no wireless, no add wireless, nothing but those two options...

---

### Post by gloscherrybomb on 2007-01-18
try: iwconfig wlan0 essid 111111111111


(replace numbers with your essid)

suddenly network manager noticed wireless when I did this (as long as all the other variables are right)

---

### Post by jerrynewt on 2007-01-19
To unconfigure the interfaces do you just delete the information that has been entered or is ther some other way I have to do it.?

---

### Post by dr_d12 on 2007-01-26
> **jerrynewt said:**
> To unconfigure the interfaces do you just delete the information that has been entered or is ther some other way I have to do it.?

I think you want to comment them out by placing a # before all the lines that don't contain " lo "

sudo gedit /etc/network/interfaces

---

