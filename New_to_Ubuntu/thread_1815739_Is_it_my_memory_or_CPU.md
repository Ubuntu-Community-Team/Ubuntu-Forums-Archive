---
title: "Is it my memory or CPU"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by pdlethbridge on 2011-07-31
I'm thinking I only need more memory but some programs  like xjig  sometimes pause, and I've seen this  happen with installing in ubuntu software center.































is it my memory or CPU I have a dedicated video card and don't use the on-board graphics It would double to 4 gigs or could this just be a slow athlon  processor

---

### Post by karlson on 2011-07-31
> **pdlethbridge said:**
> I'm thinking I only need more memory but some programs  like xjig  sometimes pause, and I've seen this  happen with installing in ubuntu software center.































is it my memory or CPU I have a dedicated video card and don't use the on-board graphics It would double to 4 gigs or could this just be a slow athlon  processor

What does top show?

---

### Post by idoitprone on 2011-07-31
If your athlon came out after 2003, then I will say it is your memory.

 You dont need more memory, but you need faster memory. How old is your memory? 
[http://en.wikipedia.org/wiki/Random-access_memory#Memory_wall](http://en.wikipedia.org/wiki/Random-access_memory#Memory_wall)
People do not understand that memory these days is so dawm slow. There are multiple types of memory to conpensate for that slow transferrate. It might be a bottleneck for your cpu. 

I hope you this give the speed of your memory
```
sudo dmidecode --type 17

```or else it time to open your computer and read to us your speed of the ram.

---

### Post by quadproc on 2011-07-31
There could be several things happening to cause slow or erratic performance.  The first thing that comes to my mind is swapping; I suggest running the System Administration System Monitor to see if any of the system resource usages are spiking during the hiccups.  If your system is using any swap memory then it would probably help to increase the size of RAM so that the system does not need to swap.

quadproc

---

### Post by idoitprone on 2011-07-31
> **quadproc said:**
> There could be several things happening to cause slow or erratic performance.  The first thing that comes to my mind is swapping; I suggest running the System Administration System Monitor to see if any of the system resource usages are spiking during the hiccups.  If your system is using any swap memory then it would probably help to increase the size of RAM so that the system does not need to swap.

quadproc

he has 4 gb of memory. I highly doubt that he is swapping. Unless, he is opening many bloated apps at once

---

### Post by pdlethbridge on 2011-07-31
here is the info you asked for


Handle 0x0011, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: SN0
	Asset Tag: SN0
	Part Number: None

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size:[COLOR="Red"] 2048 MB[/COLOR]
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: DDR2
	Type Detail: None
	Speed: 800 MHz (1.2 ns)
	Manufacturer: 2C00000000000000
	Serial Number: SN1
	Asset Tag: SN1
	Part Number: 16HTF25664AY-800J1

---

