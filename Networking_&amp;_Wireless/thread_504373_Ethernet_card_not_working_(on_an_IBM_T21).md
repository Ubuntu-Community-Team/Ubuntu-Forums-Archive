---
title: "Ethernet card not working (on an IBM T21)"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by RobMBaker on 2007-07-19
OK, I recently installed Xubuntu Feisty on my brother's IBM T21 - and managed to find the fix for X hanging on boot ...
Now I have a problem with the ethernet card. Being quite an old machine, the built-in ethernet is long dead (doesn't function in Windows either, and is not even detected as hardware). So, my brother has been using a Xircom (model unknown, although I could possibly find out) ethernet card; which works fine in Windows 2000, but not in Xubuntu.
My dmesg output shows that the card is recognised, but it can't connect to my router (which, I should note, works fine with my other laptop that I'm using to post this, running Ubuntu Feisty). It just says that no DHCP offers are available (also should point out that there are PLENTY of free IPs in my router's DHCP pool).

I'll post my dmesg, lspci -vv, ifconfig and anything else that anyone thinks is useful as separate posts; so this one is just 'the problem'.This is really annoying me, as I had a similar problem with the built-in ethernet on my own laptop, but the fix was simply NOT using 'noapic' on boot (so now my USB occasionally hangs, but that's another issue)!

edit: There is no mention of any Ethernet controller ('dmesg | grep Ethernet' returns nothing) from 'lspci -vv'; which suggests neither the PCMCIA ethernet card nor the on-board ethernet are being detected properly.
Also, I just realised that lspci is not the correct command to use; but 'lcpcmcia' - which shows that Socket 1 Device 0 is using xirc2ps_cs, which I believe is the appropriate driver.

---

### Post by RobMBaker on 2007-07-19
So, transcribing the output of ifconfig:-

eth0           Link encap:Ethernet   HWaddr 00:10:A4:9F:12:03
                  inet6 addr: fe80::210:a4ff:fe9f:1203/64 Scope:Link
                  UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
                  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                  TX packets:0 errors:7 dropped:0 overruns:0 carrier:0
                  collisions:0 txqueuelen:1000
                  RX bytes:0 (0.0 b)   TX bytes:8181 (7.9 KiB)
                  Interrupt:3 Base address:0x300

eth0:avah  Link encap:Ethernet   HWaddr 00:10:A4:9F:12:03
                  inet addr: 169.254.3.141   Bcast:169.254.255.255   Mask:255.255.0.0
                  UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
                  Interrupt:3 Base address:0x300

lo               Link encap:Local Loopback
                  inet addr:127.0.0.1   Mask:255.0.0.0
                  inet6 addr: ::1/128 Scope:Host
                  UP LOOPBACK RUNNING   MTU:16436   Metric:1
                  RX packets:6 errors:0 dropped:0 overruns:0 frame:0
                  TX packets:6 errors:7 dropped:0 overruns:0 carrier:0
                  collisions:0 txqueuelen:1000
                  RX bytes:510 (510.0 b)   TX bytes:510 (510.0 b)

---

### Post by RobMBaker on 2007-07-19
Output from dmesg | grep eth0 (otherwise it'll be far too long):-

eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:9F:12:03
eth0: media 10BaseT, silicon revision 4
eth0: no IPv6 routers present
NETDEV WATCHDOG: eth0: transmit timed out
eth0: transmit timed out
[those last two lines repeat another 6 times]
eth0: MII link partner: 45e1
eth0: MII selected
eth0: media 100BaseT, silicon revision 4
eth0: MII link partner: 45e1
eth0: MII selected
eth0: media 100BaseT, silicon revision 4


I can post other parts of dmesg if anyone thinks it's relevant, but as I have to transcribe it to my laptop WITH the working internet connection; it takes a while ...

---

### Post by Alanlives on 2007-07-21
Can anyone help with this?

Thanks in advance :KS

---

### Post by RobMBaker on 2007-07-22
Does anyone have the faintest idea about this one?
It's really a vital issue, as without the internet working; the whole thing is useless; and I'm going to have to put Win2k Pro back on ... NOT looking forward to that ](*,)

---

### Post by Alanlives on 2007-07-25
Bump. Any ideas at all? PCMCIA settings? :confused:

---

### Post by mips on 2007-07-25
What is the IP address of your router ?

---

### Post by RobMBaker on 2007-07-25
LAN-side address is 10.0.0.2

I have it set up as a DHCP server, using addresses 10.0.0.3-99 or something similar. It all works fine with the other 3 Ubuntu boxes in the house ...

---

### Post by meheheh on 2007-07-25
Really??

I guess I'm lucky then. I'm using a ThinkPad T21 2647-9AU with Intel combo modem/ethernet card and the ethernet works fine, and X did not hang.

---

### Post by mips on 2007-07-25
I'll have a look later, very late here right now.

---

### Post by RobMBaker on 2007-07-26
Thanks mips.

And yes, looks like you were lucky meheheh! This laptop's been a hassle for me ... my other machines have all just 'worked' (with a few minor glitches that were soon fixed) - so i guess I was due for some hard work :p

---

### Post by mips on 2007-07-28
Sorry, have not been in for a while but will try and get back to you.

---

### Post by Alanlives on 2007-08-13
Shameless bump!

---

### Post by Thasaidon on 2007-08-15
Does anyone have a solution yet?

I'm trying to get Ubuntu 7.04 server running on my Toshiba Satellite 4070CDS with the same Xircom 10/100 +56K modem pcmcia module.
I also have a Sweex (Realtek 8139 chipset) pcmcia card inserted which is correctly seen, so it's not the pcmcia slot.
The Xircom does work with Freesco Linux, so it's not the Xircom either...

---

### Post by Alanlives on 2007-08-17
Thanks Thasaidon,

Hmm... are Xircom cards lacking support in Ubuntu / Xubuntu, perhaps?

---

### Post by mips on 2007-08-17
Try [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)  and look at kopt=root/dev/hda1 ro acpi=off apm=on

---

### Post by Thasaidon on 2007-08-17
Well, I managed to get things going...
The Xircom (in my laptop) uses IO's which were not being scanned automatically for hardware.
So I changed a config file (not sure anymore which one, but I'll try to retrace my steps)
then Booted Ubuntu, but still nothing...
However, if I remove both cards and then re-insert them (Xircom first, then my Realtek)... poof!
things work ok!

This does mean however, that after a reboot (power failure etc...) I need to manually remove and re-insert both pcmcia cards to get things going again...

---

### Post by RobMBaker on 2007-08-30
Thanks mips, but we've tried the stuff on that Wiki before ... no joy :(

As it's getting close to term time again, I guess it's back to Windows 2k for the time being (or permanently, for this laptop) ... :confused:

---

### Post by Alanlives on 2007-09-05
I just noticed an Avahi error (highlighted red in the shutdown scripts). I therefore thought that Avahi was a bad egg and removed it.

This hasn't fixed the main problem - that the T21 doesn't appear to 'see' the Xircom ethernet card.

Another thing I have noticed is that my brother's (fully working) Ubuntu 7.04 system displays the DHCP connection as 'eth0', but mine simply says 'Wired Connection: DHCP'. Is there any way to manually set up eth0 (rather than relying on auto-detection)?

:confused:

---

### Post by Thasaidon on 2007-09-05
Just edit your **/etc/network/interfaces** file, look for the *eth0* part and then add this:
```
auto eth0
iface eth0 inet static
address <ip>
netmask <netmask>
gateway <default gateway>
```
replace the  **<...>** stuff with the desired settings
save the file and that should do the trick

---

### Post by wschnering on 2007-09-10
Using the manual config for eth0 allows my zircom card to work with fiesty. It might be possible that the inclusion of the modem on the same card is causing the issue. 

Also check the forums to see if their are any known config issues with the PCIMIA hardware for that particular model. If the memory is not  properly allocated an address for the hardware, this could also be a cause

Dont give up! Adapt and over come

---

### Post by RobMBaker on 2007-12-05
I believe I tried connecting it with manual settings, it just seems that the kernel (or higher software) can't communicate with the card itself. It's not that the card won't connect to the gateway, it's that the laptop doesn't seem to recognise the card properly ... although it does automatically load the driver for the xircom card ...

Will give it another go, just in case though.

---

### Post by RobMBaker on 2008-01-12
Problem was eventually solved by using a 3-com ethernet card, instead of the Xircom.
Must be an issue with the drivers for the Xircom - as it works in Win2k Pro with no problems.

Thanks everyone for your contributions/help.

---

