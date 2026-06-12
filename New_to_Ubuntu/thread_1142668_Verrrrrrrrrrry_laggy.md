---
title: "Verrrrrrrrrrry laggy"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by card_ace on 2009-04-29
i have the default open office 2.4 on my 8.10 install.  and when i try to use it its so laggy its next to useless.  almost reminds me of MS office](*,)   so i was wondering if i upgraded to 3.0 would it speed things up or just make it slower?

---

### Post by taurus on 2009-04-29
Laggy as in term of slowness or lappy as in term of graphic, scrolling?

What's the spec of your machine?

---

### Post by card_ace on 2009-04-29
laggy as in when i'm trying to use the fontwork it doesn't move with the mouse.  i try to drag it and then about 5 seconds later it actually moves when i let go of the mouse.

512 MB of DDR RAM
2261 MHz Northwood processor
i don't know what else to add, all my numbers are coming from CPUz

---

### Post by taurus on 2009-04-29
Sounds to me like a graphic lag.  What graphic card does it have and have you looked in System -> Administration -> Hardware Drivers to see if there is a driver for it?

---

### Post by y_garti on 2009-04-29
and also is your entire os slow or just the open office ?

and if you want to know whats new in open office 3 take a look in this link 

[http://www.openoffice.org/dev_docs/features/3.0/](http://www.openoffice.org/dev_docs/features/3.0/)
:)

---

### Post by card_ace on 2009-05-04
its just open office that's slow.  the entire OS is fine.  and i'm not sure how to find out what type of video card i have in linux, in windows i'm fine but at the moment i can't boot into it and check.  my bad.  can you explain how to find out?

p.s. sorry it took so long to get back to you

---

### Post by Didius Falco on 2009-05-04
To find out what kind of video card you have, open a Terminal shell and type ```
lspci | grep VGA
``` and paste the output here.

---

### Post by card_ace on 2009-05-04
```
carlton@carlton-desktop:~$ lspci i grep VGA 
Usage: lspci [<switches>] 

Basic display modes: 
-mm		Produce machine-readable output (single -m for an obsolete format) 
-t		Show bus tree 

Display options: 
-v		Be verbose (-vv for very verbose) 
-k		Show kernel drivers handling each device 
-x		Show hex-dump of the standard part of the config space 
-xxx		Show hex-dump of the whole config space (dangerous; root only) 
-xxxx		Show hex-dump of the 4096-byte extended config space (root only) 
-b		Bus-centric view (addresses and IRQ's as seen by the bus) 
-D		Always show domain numbers 

Resolving of device ID's to names: 
-n		Show numeric ID's 
-nn		Show both textual and numeric ID's (names & numbers) 
-q		Query the PCI ID database for unknown ID's via DNS 
-qq		As above, but re-query locally cached entries 
-Q		Query the PCI ID database for all ID's via DNS 

Selection of devices: 
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots 
-d [<vendor>]:[<device>]			Show only devices with specified ID's 

Other options: 
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz 
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap 
-M		Enable `bus mapping' mode (dangerous; root only) 

PCI access options: 
-A <method>	Use the specified PCI access method (see `-A help' for a list) 
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list) 
-G		Enable PCI access debugging 
-H <mode>	Use direct hardware access (<mode> = 1 or 2) 
-F <file>	Read PCI configuration dump from a given file 
carlton@carlton-desktop:~$ 
```

---

### Post by LowSky on 2009-05-04
lspci i grep VGA  is the wrong code

its  lspci | grep VGA

| is the usually above the \ on the US keyboard layout, usually near the Enter key

---

### Post by card_ace on 2009-05-04
ahh ok.  thanks for the clarification.  i'll try that again later today and hopefully have time to get back on.

---

### Post by card_ace on 2009-05-04
alright let's try this again
```
carlton@carlton-desktop:~$ lspci | grep VGA 
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) 
carlton@carlton-desktop:~$ 
```

---

### Post by card_ace on 2009-05-06
alright i went to Nvidias site and got the driver for linux.  i downloaded it to an external HDD, but now i'm not quite sure how to install it from here.  can somebody give me a line of code or some direction to go at least?

---

