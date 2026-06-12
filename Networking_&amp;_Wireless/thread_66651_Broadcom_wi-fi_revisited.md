---
title: "Broadcom wi-fi revisited"
date: 2005-09-17
forum: Networking &amp; Wireless
---

### Post by qferret on 2005-09-17
I've followed every wireless thread I could find here (as well as anything else I googled up...).

jonny's was probably the most helpful...I did make some progress from that.

The main hurdle remains though. I can get through all steps through "modprobe ndiswrapper" with no errors, but no interface ever gets created (wlan0)...

It seems like EVERYTHING is getting installed and configured without errors (dmesg even tells me that the driver bcmwl5 is loaded), but I have no interface to bind to. ](*,) 

I'm stumped. Any suggestions welcome. Need more info, just ask (I'd post more now, but there are NO errors to know what part is failing...) :roll:

Dell Latitude D600, TrueMobile 1350 wlan, Breezy preview (w/ all available updates)

---

### Post by qferret on 2005-09-22
Aw c'mon.... noone has any nudges in the right direction as to how to create the wlan0 interface? :?:

---

### Post by mlomker on 2005-09-22
**ndiswrapper -l** indicates that the driver is loaded and working?

At that point **iwconfig** should see the interface.  If it doesn't then post the output of **dmesg | tail** after you've modprobed the driver.

---

### Post by qferret on 2005-09-24
Thanks for taking pity on a fellow Minnesotan ;-)

Here is the output of the 3 requested commands:

jmc@oe7078:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
jmc@oe7078:~$ sudo modprobe ndiswrapper
Password:
jmc@oe7078:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jmc@oe7078:~$ dmesg | tail
[4294727.571000] eth0: no IPv6 routers present
[4294729.304000] Bluetooth: Core ver 2.7
[4294729.304000] NET: Registered protocol family 31
[4294729.304000] Bluetooth: HCI device and connection manager initialized
[4294729.304000] Bluetooth: HCI socket layer initialized
[4294729.807000] Bluetooth: L2CAP ver 2.7
[4294729.807000] Bluetooth: L2CAP socket layer initialized
[4294729.878000] Bluetooth: RFCOMM ver 1.5
[4294729.878000] Bluetooth: RFCOMM socket layer initialized
[4294729.878000] Bluetooth: RFCOMM TTY layer initialized
jmc@oe7078:~$

Unless it's thinking my broadcom NIC is a Bluetooth device, I'm still stumped...

---

### Post by skirkpatrick on 2005-09-24
I've had a problem with my son's Acer Broadcom wifi that still haven't resolved.  Everything seems to be running but it won't see the Access Point.  I think the radio isn't getting turned on but haven't figured out a way to do it.

---

### Post by dcraven on 2005-09-24
If you are using Hoary, try [this wiki page](https://wiki.ubuntu.com//SetupNdiswrapperHowto). If you are using Breezy, then I'm stumped, as it comes with the newer version of ndiswrapper that is needed for the Broadcom chipsets.

Cheers,
~djc

---

### Post by mlomker on 2005-09-25
> bcmwl5          driver present, hardware present


I'd try a couple different windows drivers.  There are more than one for that card and some work better than others.

After glancing at the wiki, perhaps you missed the **ndiswrapper -m** part?

---

### Post by qferret on 2005-09-25
Nope.....did the -m bit

I tried bcmwl5 and bcmwl5a from the version I have with the same results.

I'll find a couple of other versions of the driver and give it a go.


btw....skirkpatrick, I'm not familiar with Acer's, but I'd check the wireless options in the BIOS to make sure it's enabled.

---

### Post by redactech on 2005-09-25
Silly question : 

did you check the "hardware" switch of the wifi card ?

just in case, because dmesg will show it anyway. My Acer has a front button that is in the way...

---

### Post by skirkpatrick on 2005-09-26
I'm using Hoary but I manually built the latest ndiswrapper code.

There's no BIOS setting and it works fine in Windows.  Pushing the front button appears to do nothing.

---

### Post by dancavallaro on 2005-09-26
My driver CD only came with one driver... can someone post (or post links to) some alternative drivers?

I was having the same problem, with no interface being created and the "no wireless extensions" but when I did a ndiswrapper -l, it only said "driver present"... it didn't also say "hardware present". I have a WPC54G v.3

---

### Post by mlomker on 2005-09-26
> I have a WPC54G v.3

I was referring to Broadcom cards, which do have a variety of drivers floating about because Broadcom doesn't make the driver.  For Linksys you'd get the driver from them.  The version of ndiswrapper that comes with Hoary isn't the latest, but I'm not sure which version of Ubuntu you have.  [Linksys driver.]("http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1125638812437&pagename=Linksys%2FCommon%2FVisitorWrapper")

What is the output of **lspci**?  Post the lines that start with **Network**.  Some of those cards use an ACX chipset and others use the Broadcom, which requires ndiswrapper.

---

### Post by dancavallaro on 2005-09-26
lspci -v gives me:

0000:02:00.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

Subsystem: Linksys: Unknown device 0048
Flags: fast devsel, IRQ11
Memory at 10800000 (32-bit, non-prefetchable) [disabled] [size=8k]

---

### Post by dancavallaro on 2005-09-26
Wow I don't know what I did, but I somehow got it to work.

---

### Post by qferret on 2005-09-29
Yes!!!!!

Different version of the driver took care of the issue.
wlan0 was created, and I am posting using my wireless connection.
Thanks mlomker :D

btw.... dmesg doesn't show the bluetooth references now....so I do think the first driver was somehow making the laptop think it was a bluetooth device.

R102319.exe from Dell downloads did the trick for my D600 Latitude.

---

### Post by skirkpatrick on 2005-10-02
All my problems are now resolved: [http://www.ubuntuforums.org/showthread.php?p=383723#post383723](http://www.ubuntuforums.org/showthread.php?p=383723#post383723)

---

### Post by qferret on 2005-10-02
Crud......

kernel upgrade borked it again.

Back to square 1, but at least I know what to look for now  ;-)

---

### Post by mlomker on 2005-10-03
> kernel upgrade borked it again.
Back to square 1, but at least I know what to look for now  ;-)

One of the downsides of kernel modules (such as ndiswrapper) is that they have to be compiled for each kernel individually.  You could use the 'lock' option in Synaptic to keep it from upgrading the kernel.  I have other kernel modules (ATI drivers, VMWare, etc) and sometimes they have to be redone with an update and sometimes not...it depends upon what gets changed.

---

