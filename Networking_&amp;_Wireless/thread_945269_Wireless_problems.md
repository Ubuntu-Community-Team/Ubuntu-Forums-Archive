---
title: "Wireless problems"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by thmtrxhsy on 2008-10-12
I'm sure this isn't the right place for this, but I couldn't find a better place.

On my wired home desktop computer, I have dual boot Windows XP and Ubuntu. I've been using it for a while now, and I consider myself somewhat educated in the ways of Ubuntu.

I recently bought a new laptop, which came preloaded with Vista, and is extremely slow on my laptop.

Because I loved Ubuntu so much on my computer, I put it on my laptop, completely wiping Vista.

Right from Hardy Heron, I had issues. I could not connect to my wireless internet. I did some googling, and decided to try Intrepid to see if that could help solve my problem.

Now, I can't even figure anything out. I click on the icon, click connect to other wireless network, type in my network info, and I immediately get a "Disconnected" message.

Also, all my networks are grayed out when I click on the icon as well.

Can anyone please walk me through how to fix it, I'm not very experienced at all.

Thanks

---

### Post by Ayuthia on 2008-10-12
> **thmtrxhsy said:**
> I'm sure this isn't the right place for this, but I couldn't find a better place.

On my wired home desktop computer, I have dual boot Windows XP and Ubuntu. I've been using it for a while now, and I consider myself somewhat educated in the ways of Ubuntu.

I recently bought a new laptop, which came preloaded with Vista, and is extremely slow on my laptop.

Because I loved Ubuntu so much on my computer, I put it on my laptop, completely wiping Vista.

Right from Hardy Heron, I had issues. I could not connect to my wireless internet. I did some googling, and decided to try Intrepid to see if that could help solve my problem.

Now, I can't even figure anything out. I click on the icon, click connect to other wireless network, type in my network info, and I immediately get a "Disconnected" message.

Also, all my networks are grayed out when I click on the icon as well.

Can anyone please walk me through how to fix it, I'm not very experienced at all.

Thanks

The first thing the we will need is to determine the make and model of your wireless card.  If you can go into the Terminal, please post the results of:
```
lspci -nn
```This will list out the pci cards that are in your computer.

---

### Post by thmtrxhsy on 2008-10-12
Thanks for helping me out.

lspci -nn returns:
```

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 203.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

```
There was other stuff in the beginning, but I only typed out the wireless and Ethernet cards. Let me know if you need more.

---

### Post by Ayuthia on 2008-10-12
If you are using Intrepid, go to System->Administration->Hardware Drivers and activate the wl driver and disable the b43 driver.  That should get you going.  

If you are in Hardy, go to the same place and activate the b43 driver.  You will need a working wired connection for this one though because it needs firmware to make it work.

Hope that helps!

---

### Post by thmtrxhsy on 2008-10-12
.

---

### Post by thmtrxhsy on 2008-10-12
I switched back to Hardy, finding it to difficult to find help on the forums with Intrepid.

I followed the steps here: [http://ubuntuforums.org/showthread.php?t=767372&highlight=Broadcom+4311 ](http://ubuntuforums.org/showthread.php?t=767372&highlight=Broadcom+4311 )

and got the driver to work say " In Use ".

Now, after putting in my information, I'm back where is started.

Every minute or so, I get a "Passphrase required by Wireless Network" message, even though I'm sure all my information is correct. The light on my laptop is lit, but still no connection.

Thanks

---

### Post by Kevbert on 2008-10-12
Please post the output of
```
iwconfig
```

---

### Post by thmtrxhsy on 2008-10-12
iwconfig yields:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Motorola"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
thanks

---

### Post by thmtrxhsy on 2008-10-12
Any ideas? I've been working on this for hours o.0

thanks

---

### Post by Kevbert on 2008-10-13
Check you have Unsupported updates (backports) enabled in software sources. If there is a wifi front panel switch try switching it (the wifi light may be giving a false indication that wifi is on). 
Do you know the name of your wireless firmware driver ?

---

### Post by thmtrxhsy on 2008-10-13
How can i find the name of my wireless firmware driver? Also, there is no wifi panel switch, only a button that turns off and on as i press it.

---

