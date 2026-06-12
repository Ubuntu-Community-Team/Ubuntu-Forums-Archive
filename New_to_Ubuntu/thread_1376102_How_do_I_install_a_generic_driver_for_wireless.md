---
title: "How do I install a generic driver for wireless?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Vin75 on 2010-01-08
Hi,
Quick Question...

I have been using the Windows Wireless Drivers application to try and get my wireless working on my laptop and reading some threads, followed a suggestion of booting my live CD and seeing if the laptop could then connect to my wireless network. I was kind of surprised to find that instantly, I could connect to my home wireless access point. 

All I want to do is get the linux airo driver back in its place now that I no longer want to troubleshoot the windows wireless drivers,

Any suggestions?

 *-network:1 UNCLAIMED
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=4
       resources: ioport:8000(size=256) memory:c0214000-c0217fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)

---

### Post by Methuselah on 2010-01-08
If the device worked on the LiveCD it should have worked when you installed Ubuntu.
So I don't understand why you were installing windows drivers in that case.
Using the windows wireless drivers is a last resort sort of hack.

Is the LiveCD version of Ubuntu same as the one you installed?
In any event, if you followed ndiswrapper instructions and blacklisted the linux driver in /etc/modprobe.d/blacklist you have to undo that.
I am not 100% clear on the sequence of events you described but hopefully that helps a little.

---

### Post by Vin75 on 2010-01-08
Thanks Methuselah,

I didn't follow the ndiswrapper instructions as I checked the blacklist and I had not disabled the airo driver. 

Background: When I first installed Ubuntu 9.1 a few days ago managed to connect to the wireless network without a problem. Then when it updated the build using the update manager, I had nothing but problems. I then had some guidance about trying the windows driver, and I have been able to see the access points, but not able to connect to them. Originally, I could not see the access points, but when I connected to a hidden network it was fine. 

So I would just like to get back to that original state with the airo driver in place.

Any further advice?

---

### Post by Methuselah on 2010-01-08
Open a Terminal.
Try **sudo modprobe airo**
If the device comes to life you might need to add airo to /etc/modules for it to stck on reboot.
Not sure why it stopped happening automatically if it was working before.

---

### Post by Vin75 on 2010-01-08
Thank you.
You were correct - it did not stick on reboot, so I have now added it to the module file.
And now I recall why I went through all of this in the first place...
My wireless antenna would not turn on when the kernel (apologies if my terminology is incorrect) updated from .14 to .16. For the life of me, there was nothing I could do to get it back on. I am using an IBM T42. I have gone through all the processes of updating the firmware in windows, changing the settings in Windows to keep the antenna on at all times, etc... and the only thing that seemed to work was using the ndiswrapper windows drivers. 

But, if I boot from the CD, the wireless antenna is on and although I cannot see any access points, I can still connect manually to my home network.

Right now, my antenna is showing off. If I unplug my network cable, it doesn't come on. The IBM Fn+F5 key combo to turn wireless on does not work. If I try to connect to hidden network, nothing happens. 

Output of lshw -c network is:

 *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:14:a4:0e:96:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0214000-c0217fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)

Where to from here?

---

### Post by Methuselah on 2010-01-08
I've never had one of these laptops that disable their wireless so I'm flying blind but here goes...

What happens if you enter

```

sudo iwlist eth1 scan

```

In the terminal.

I'm likely not going to be much help from here on in.
But someone else might have ideas.

---

### Post by Vin75 on 2010-01-08
How's this for odd...
So my wireless antenna is off...
I go to "Create NEW wireless network", enter in the SSID and *bang* - my antenna is turned on and it fails to connect. But the antenna remains on. I then connect to the wireless network again, and in 10 seconds I am online.

So I am now finally sorted!!

I guess moving forward, I will have to manually connect (twice) to connect to the wireless network, but if that is all the pain I have to go through to avoid Microsoft then I can deal with it!!

Thanks for your help Methuselah - I will mark the thread as solved.
Vin

---

### Post by Methuselah on 2010-01-08
Maybe if you did the scan it would have turned on as well.
I'm glad something worked out though!

---

