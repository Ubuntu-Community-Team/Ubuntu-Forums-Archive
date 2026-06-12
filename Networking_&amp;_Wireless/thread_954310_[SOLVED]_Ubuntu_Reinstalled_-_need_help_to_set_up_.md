---
title: "[SOLVED] Ubuntu Reinstalled - need help to set up Wireless again!"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-10-21
Hi,
I reinstalled Ubuntu 8.04 on my pc.
I had to connect to my wireless modem/router via an RJ45 cable in order to download software and get the wireless set up again.

I had the Wireless working perfectly before the reinstall!

I downloaded NdisWrapper and installed the .inf driver for my D-Link G122.
In NdisWrapper it says: 
Hardware Present: Yes

Eventually the wireless was up and running.

I shutdown the pc.

Then later I went back to Ubuntu and started up and the wireless adaptor was not being detected. In NM-Applet there was only Wired and Point to Point connections being picked up and no wireless being detected.

Is there somethnig about blacklisting I need to do?

Please help. Thanks.

---

### Post by DFlame on 2008-10-21
Looks like you forgot to add ndiswrapper to the startup modules.

```
sudo gedit /etc/modules
```

Pop that into a terminal window. In the text file that loads, add "ndiswrapper" (on a new line, without the quotes), save and close. This will make ndiswrapper load on startup, and hopefully correct the prob. You can also manually load the module with:

```
sudo modprobe ndiswrapper
```

I'm not aware of any blacklisting that needs to take place with this card, but call back if there's problems with the instructions above :)

DFlame

---

### Post by Rytron on 2008-10-21
> **DFlame said:**
> Looks like you forgot to add ndiswrapper to the startup modules.

```
sudo gedit /etc/modules
```

Pop that into a terminal window. In the text file that loads, add "ndiswrapper" (on a new line, without the quotes), save and close. This will make ndiswrapper load on startup, and hopefully correct the prob. You can also manually load the module with:

```
sudo modprobe ndiswrapper
```

I'm not aware of any blacklisting that needs to take place with this card, but call back if there's problems with the instructions above :)

DFlame


Hi DFlame,
I tried both methods and neither worked. Its bizarre that my wireless was working but then just vanishes.
:confused:

---

### Post by Ayuthia on 2008-10-21
It sounds like something is not blacklisted.  Can you post the results of lshw -C network and ndiswrapper -l?

---

### Post by Rytron on 2008-10-21
> **Ayuthia said:**
> It sounds like something is not blacklisted.  Can you post the results of lshw -C network and ndiswrapper -l?

Hi Ayuthia,
Here are the 2 outputs:

```
:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
```



```
:~$ ndiswrapper -l
dr71wu : driver installed
	device (07D1:3C03) present (alternate driver: rt73usb)
```

---

### Post by Ayuthia on 2008-10-21
> **Rytron said:**
> Hi Ayuthia,
Here are the 2 outputs:

```
:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
```



```
:~$ ndiswrapper -l
dr71wu : driver installed
	device (07D1:3C03) present (alternate driver: rt73usb)
```

The lshw -C network does need a upper case C or else it will give you that message.  It does look like rt73usb is the driver that might be conflicting.  You can try the following to see if it helps (it will only work for the current session):
```
sudo modprobe -r rt73usb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```

EDIT:
By the way, did you try the rt73usb module to see if it worked with your device?

---

### Post by Rytron on 2008-10-21
When I used a capital C in the first command I got a message saying Warning you should run this as super user and then it did not give an output.

The driver I have in Ndiswrapper is the dr71wu driver.

How do I use the rt73usb module?

Here is more output:

:~$ sudo modprobe -r rt73usb ndiswrapper
:~$ sudo modprobe ndiswrapper
:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


I dont know where the rt73usb is coming from as it is not amonst the windows drivers I have.
The dr71wu driver was perfect before my reinstall of Ubuntu so I reckon that should stay.

This is driving me crazy.

---

### Post by Ayuthia on 2008-10-21
> **Rytron said:**
> When I used a capital C in the first command I got a message saying Warning you should run this as super user and then it did not give an output.

The driver I have in Ndiswrapper is the dr71wu driver.

How do I use the rt73usb module?

I forgot that this is a usb device so it might not show up in lshw.  Try the following:
```
sudo modprobe -r ndiswrapper rt73usb
sudo modprobe rt73usb
sudo iwlist scan
```If it shows any wireless sites, then the driver works.

---

### Post by Rytron on 2008-10-21
Cheers buddy. It works.
I will note all these steps for future reference.

Just one more question:
How can I make my Usb adaptor be wireless ready everytime I boot up?

I can put in the code you gave me:
```
sudo modprobe -r ndiswrapper rt73usb
sudo modprobe rt73usb
sudo iwlist scan
```

This is awkward to put in every time I boot into Ubuntu though.

Again, I really appreciate all your help Ayuthia & DFlame.

---

### Post by DFlame on 2008-10-22
Rytron, go back to /etc/modules as I showed you earlier. If ndiswrapper is still there, delete it from the line and replace it with rt73usb. Then save.

That should load up the correct driver and stop ndiswrapper from loading instead. Thanks to Ayuthia for putting this thread in the right direction.

DFlame

---

### Post by Rytron on 2008-10-22
Works like a charm.

:popcorn:

---

