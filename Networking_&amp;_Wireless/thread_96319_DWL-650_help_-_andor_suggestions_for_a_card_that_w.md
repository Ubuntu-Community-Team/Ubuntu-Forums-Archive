---
title: "DWL-650 help - and/or suggestions for a card that work!"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by Reaped In Half on 2005-11-28
Ok, so I bought a D-link DWL-650 and ubuntu won't recognize it.  To my knowledge I've tried everything except for recompiling the kernel because I've only been using linux for a few months now, and to be quite honest, I have no clue how to do so.  I'm getting kind of fed up with this card.  If anyone can help me with the card, that'd be great, but if it seems useless, what card would give me the least amount of headaches?

edit: I know, lovely typo in the thread title.

---

### Post by Lambert on 2005-11-28
Go to the wireless troublshooting guide link in my address and see if that helps. 

Is it a 650 or 650+ as there are different chipsets used by each of these and then even different revisions use different chipsets.

If it's a 650 I show it being a prism2 chipset using the linux-wlan-ng driver.

After you go through that guide, if you can't get it working post back details of what you tried and some of the outputs of commands that are in that guide.

As for a card that works, in the guide there is a section on drivers and a list of drivers in breezy. Find a card using one of those chipsets/drivers and it shouldn't be a problem. I use a dwl-g650 which is an atheros chipset and uses the madwifi driver. Worked out of box for me with open wep setting.

---

### Post by jafenske on 2005-11-28
I'm using a DWL-650+ and with an open access point it works great.  It's when I try to use WPA, I have problems.  It's a Atheros 5212 chipset the madwifi drivers work best.  There are some madwifi howtos in the wiki...I think.  When I get home from work I'll post those links.

---

### Post by jafenske on 2005-11-28
Will you run

```
lsmod
```

So we can see if the correct modules are loaded...

The links I have assume that your device is working... Lets get it working first

---

### Post by Reaped In Half on 2005-11-29
Thanks everyone for your help.  Here's the output for a bunch of different commands listed on the wireless troubleshooting guide. (I'm only pasting the relevant sections of output to make it easier on you guys. Thanks again.)

**sudo lshw**
 *-network UNCLAIMED
          description: Ethernet controller
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 1
          bus info: pci@02:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:10800000-108001ff irq:11

**lspci -v**
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
        Subsystem: D-Link System Inc: Unknown device 3302
        Flags: medium devsel, IRQ 11
        I/O ports at 4000 [disabled] [size=256]
        Memory at 10800000 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: <available only to root>

**lspci -n**
0000:02:00.0 0200: 10ec:8180 (rev 20)

**sudo iwconfig**
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

**sudo ifconfig**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3687431 (3.5 MiB)  TX bytes:3687431 (3.5 MiB)



Ok, this is obviously using ndiswrapper which i did load using modprobe.  Still nothing... I used a win xp driver for the realtek8180 chipset. ndisgtk still says that no hardware is loaded, and the network activity monitor has a red error symbol on it.

---

### Post by orbinick on 2005-11-29
Try this Windows Driver for RTL8180 based cards. It is working for me better than the one on the DLink CD. Use the *.INF file to install with ndiswrapper and DO NOT forget to keep the *.sys file in the same folder as the INF.

---

### Post by Reaped In Half on 2005-11-29
I have to be the dumbest person on the planet... I had that driver, but separated the.inf file from the .sys file.... it recognized it right away.  I just activated it, so we'll see if that works.  It appears to have not found a link as only the one led is blinking... I'll try the troubleshooter, and report back if I have any problems... Thanks everyone for your help.

---

### Post by orbinick on 2005-11-29
the one I posted works even at boot and with both 686 and 386 kernels.

---

### Post by Reaped In Half on 2005-11-29
Ok, when I do **iwconfig**, it gives me all zeros for the access point, but when I do **iwlist wlan0 scan**, it shows the router's address.  also, **ifconfig** doesn't give me an IP address.  I can't give up now, I at least got it recognized and working! any more suggestions?

---

### Post by orbinick on 2005-11-29
which one did you wrapped? the one you had or the one I posted?

---

### Post by Reaped In Half on 2005-11-29
the one I had, but it was the exact same file.

---

### Post by Reaped In Half on 2005-11-29
Ahhh finally it works... all I did was in network properties, switch the network name to default... my network monitor still doesn't work, but oh well I guess.

Edit: nevermind, fixed that too.  Thankyou everyone for your help!

---

### Post by carlosqueso on 2005-11-29
@ orbinick:  the driver you posted wraps beautifully with my DWL-650 rev. M card....thank you much :-D

---

### Post by orbinick on 2005-12-02
You're welcome. It was hard to find so I posted it where it matters.

---

### Post by SyvanX on 2006-02-15
[QUOTE=orbinick]Try this Windows Driver for RTL8180 based cards. It is working for me better than the one on the DLink CD. Use the *.INF file to install with ndiswrapper and DO NOT forget to keep the *.sys file in the same folder as the INF.[/QUOTE]

Sorry to bump an old topic, but I couldn't get it to work with the DLink Driver, and this RTL8180 driver worked perfectly after a reboot.

Thanks

---

### Post by quattroman on 2007-08-25
bumping an old thread again...

i did the ndiswrapper for the file posted here, for the  DLink dwl-650 m with the RTL8180L chipset (?)

thing is that when I click install after choosing the inf, nothing happens. nothing installs. this is for a xubuntu dell laptop.

thanks in advance for any help.

---

