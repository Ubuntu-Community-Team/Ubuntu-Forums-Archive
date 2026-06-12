---
title: "To hp 6515b users (3)"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-07
Hi I'm 6515b user.


my laptop is hp 6515b in 8.04 ubuntu
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
I installed ubuntu in 'noapic nolapic acpi=off' status 

It's my card..
The important thing is that I can't turn on the wireless lan.
Because The wireless switch is a kind of touchpad switch(useless) not analogtic switch(I prefer analog). The switch is not working in ubuntu. It did work well in Vista.

I really want to turn on my wireless.
I really want to see the blue light.

---

### Post by prshah on 2008-04-07
> **kjman83 said:**
> Hi I'm 6515b user.
my laptop is hp 6515b in 8.04 ubuntu
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
I installed ubuntu in 'noapic nolapic acpi=off' status 
Because The wireless switch is a kind of touchpad switch(useless) not analogtic switch(I prefer 


Your switch will automatically start working once you install the CORRECT driver, either local or NDISwrapper.

For BCM94311 you will need to use NDISwrapper. Do you have the driver files? if so ```
sudo ndiswrapper -i whatever.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

will get everything, including your BLUE light, going.

Post here if you need more details. The above is just a summary assuming you know everything.

---

### Post by kjman83 on 2008-04-07
kjman83@guinness:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
kjman83@guinness:~$ sudo ndiswrapper -m
module configuration already contains alias directive

kjman83@guinness:~$ sudo modprobe ndiswrapper
kjman83@guinness:~$ 
kjman83@guinness:~$ 


I did like this..
but nothing changed.

can't find the wireless network

---

### Post by prshah on 2008-04-07
> **kjman83 said:**
> kjman83@guinness:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
kjman83@guinness:~$ sudo ndiswrapper -m
module configuration already contains alias directive

kjman83@guinness:~$ sudo modprobe ndiswrapper
kjman83@guinness:~$ 
kjman83@guinness:~$ 
I did like this..
but nothing changed.

can't find the wireless network

After the modprobe command, try using your switch and it should work. If it doesnt work, you probably have the wrong driver loaded. The below commands will give us more useful information if your wireless is _still_ not working:

```
lspci | grep -i wireless
sudo ndiswrapper -l
sudo lshw | grep -i -A 3 -B 3 wireless

```

---

### Post by dmizer on 2008-04-07
please ... stop making new threads.  work from one thread until you get your issue resolved:

[http://ubuntuforums.org/showthread.php?t=744769](http://ubuntuforums.org/showthread.php?t=744769)
[http://ubuntuforums.org/showthread.php?t=746012](http://ubuntuforums.org/showthread.php?t=746012)
[http://ubuntuforums.org/showthread.php?t=744338](http://ubuntuforums.org/showthread.php?t=744338)
[http://ubuntuforums.org/showthread.php?t=748149](http://ubuntuforums.org/showthread.php?t=748149)
[http://ubuntuforums.org/showthread.php?t=743989](http://ubuntuforums.org/showthread.php?t=743989)

i don't know which thread to post in to get you help.

---

