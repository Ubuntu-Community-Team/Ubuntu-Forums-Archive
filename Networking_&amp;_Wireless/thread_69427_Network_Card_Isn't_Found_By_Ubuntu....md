---
title: "Network Card Isn't Found By Ubuntu..."
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by Chrisitian3807 on 2005-09-26
It is ENCORE ENL832-TX-ICNT Network Card...It is not detected by Ubuntu...It comes with Linux drivers but i am not willing to risk re-installing Windows XP :rolleyes: My Specs are K6 334Mhz 254 PC66 RAM and 2MB Onboard Video 4.3 Ultra DMA HDD (HP 4440)...The card work great with Windows...:( Oh and will Ubuntu run fast on my PC? Surprisinly Win XP works great for my PC after eye-candy is turned off............

---

### Post by mlomker on 2005-09-26
Yup, I turn all of that eye candy off first thing...regardless of how fast the machine is.

Post the output of **lspci** and we'll try to figure out what driver it needs.

---

### Post by Chrisitian3807 on 2005-09-26
I haven't physically installed Ubuntu...I either use a Live CD or go through Ubuntu Install and...**So do I have to boot the Live CD and try that out**:eek: ?

Where do I type Ispci? In terminal?

---

### Post by mlomker on 2005-09-26
> Where do I type Ispci? In terminal?

Yup.

---

### Post by Chrisitian3807 on 2005-09-26
15min. later:rolleyes: i started LiveCD and it said something like *bad command line etc...:confused:

---

### Post by mlomker on 2005-09-26
That was an **L**.

---

### Post by Chrisitian3807 on 2005-09-26
Ohhhhhh.:mad: I'll be back in 20...:(

---

### Post by Chrisitian3807 on 2005-09-26
0000:00:00.0 Host Bridge Sis 5582/5597

0000:01:00 ISA SIS etc

0000:00:01:1 IDE

*Ethernet Sudance Technologies Uknown Device 0200 rev3

That is what I memorized...Is that enough to help?

---

### Post by mlomker on 2005-09-27
> That is what I memorized...Is that enough to help?

Nope.  One of them should have started with **Network**.

Here's mine:

```

Network controller: Intel Corp.: Unknown device 4223 (rev 05)

```

The output of **dmesg | eth** would tell us something if it had tried to load a driver.

Example:

```

eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, 00:03:0d:33:cc:f0.

```

If you have a fast Internet connection then I'd recommend download a copy of Knoppix.  It's a bit easier to deal with than the Ubuntu liveCD.

---

### Post by az on 2005-09-27
[QUOTE=Chrisitian3807]0000:00:00.0 Host Bridge Sis 5582/5597

0000:01:00 ISA SIS etc

0000:00:01:1 IDE

*Ethernet Sudance Technologies Uknown Device 0200 rev3

That is what I memorized...Is that enough to help?[/QUOTE]


Open up a terminal and type

sudo modprobe sundance

(There is a module for sundance ethernet cards.)

Then, go to the networking tool and see if you can configure the ethernet connection.

---

### Post by Chrisitian3807 on 2005-09-28
[QUOTE=azz]Open up a terminal and type

sudo modprobe sundance

(There is a module for sundance ethernet cards.)

Then, go to the networking tool and see if you can configure the ethernet connection.[/QUOTE]
Typed "sudo modprobe sundance" nothing happened......:( 

Mlomker:I will post the results of "Network" and "dmesg l eth" under lspci later on..gotta go rest

---

### Post by Chrisitian3807 on 2005-09-28
OK I think I got it I typed Lspci and got 0000:00:0c.0 Ethernet Controller: Sundance Technologies Inc. : Unknown Device 0200 (rev31)

When I typed dmesg / eth : (-c) (-n level) 9-s bufsize)

So does that help?:D

---

### Post by mlomker on 2005-09-28
> Typed "sudo modprobe sundance" nothing happened......:( 


Might want to try **dmesg | tail** after doing the modprobe and see if there are any interesting messages.  That does sound like the correct driver.

---

### Post by Chrisitian3807 on 2005-09-28
[QUOTE=mlomker]Might want to try **dmesg | tail** after doing the modprobe and see if there are any interesting messages.  That does sound like the correct driver.[/QUOTE]

That button you pressed between dmesg and tail, what is it? The "L" button?Sorry to sound noobish...And my only fear of Linux is of d/l packages'applications...like rpm or tar and links to help me out on this?

---

### Post by mlomker on 2005-09-28
That's the pipe character.  Typically the Shift key plus the key above the Enter key.

RPM's are used in redhat.  Debian uses the .deb files.  Installing things from source (the .tar files) gets a bit more challenging.  [This]("http://www.ubuntuforums.org/showpost.php?p=346777&postcount=6") is the usual process after untaring the file.

If you haven't read the ubuntguide, below, then I'd recommend reading the whole thing.

---

