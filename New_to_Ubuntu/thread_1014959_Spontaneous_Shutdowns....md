---
title: "Spontaneous Shutdowns..."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Checkhovian on 2008-12-18
Hello, I've been running Ubuntu for several months now, although still know very little about it. Yesterday my computer start shutting down in mid-task for no apparent reason. It's done it about half a dozen times now, and there doesn't seem to be any programs in common - once I was watching a DVD, once working in a word processor, once browsing the internet, etc. Just all of the sudden it shows me the Ubuntu shutdown screen and shuts itself off. I know that my laptop in general is prone to overheating, but this doesn't seem to be caused by overheat.

I'm running Hardy 8.04, and no software has changed at all in the last month except for that I installed the libdvdread3 package a couple days ago according to the directions [here](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

Please help! This is getting really annoying.

---

### Post by Paqman on 2008-12-18
Your machine could be overheating.

To check the temperatures you can either open your BIOS to the hardware monitoring page and watch them (they should stay stable at 30-60 deg C)

Alternatively, install sensors-applet and right click on a panel to add a hardware temp monitor to it. You may need to run this command to recognise all your sensors:
```
sudo sensors-detect
```

---

### Post by fistfullofroses on 2008-12-18
Also check your system logs ~.^

---

### Post by Checkhovian on 2008-12-18
Thanks for your replies. I checked the logs and it seems like every time the computer shuts down, it's because of a "signal 15." Any idea what signal 15 means or how to fix it?

---

### Post by kanikilu on 2008-12-18
[http://linux.die.net/man/7/signal](http://linux.die.net/man/7/signal)

Says 15 is "termination signal". Not really sure what exactly that means or how it's related, but...

Can you post that portion of that log?

---

### Post by Checkhovian on 2008-12-18
> Dec 17 22:06:20 dell-laptop kernel: [ 1854.469173] ACPI: Critical trip point
Dec 17 22:06:20 dell-laptop kernel: [ 1854.642752] pidgin[6176]: segfault at 10 rip 7f63fc0fb203 rsp 40e81120 error 4
Dec 17 22:06:20 dell-laptop kernel: [ 1854.642819] pidgin[6073]: segfault at 10 rip 7f63fc0fb203 rsp 7fff055bce80 error 4
Dec 17 22:06:22 dell-laptop kernel: [ 1856.179029] ACPI: Critical trip point
Dec 17 22:06:25 dell-laptop kernel: [ 1858.588986] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 17 22:06:26 dell-laptop exiting on signal 15

That's from the last shutdown last night, I think the only thing I had running at the time was Pidgin for IM....

Any ideas?

---

### Post by Paqman on 2008-12-18
See if you can locate some other shutdowns in the logs. You want to see if you're getting the same Pidgin segfault and/or the ACPI problem.

My money's on ACPI personally, which would point more towards a hardware problem. Did you try monitoring the temperature like I suggested?

---

### Post by Checkhovian on 2008-12-18
Well, I do get the same Pidgin fault, but since I've got pidgin set to autorun pretty much whenever my computer's on, it doesn't surprise me. I'll shut off pidgin and see if it makes a difference.

I did add the sensor applet, and have been keeping an eye on it. Seems like my computer runs pretty hot to begin with. Since I started watching, it's hovered between 59 and 63 degrees, and I haven't heard my cooling fan kick in yet, but I also haven't had any more spontaneous shutdowns. Thanks for your help... I'll keep an eye on my temperature.

If the problem is that my computer is overheating, though, is there anything I can actually do about that, besides getting a new one?

---

### Post by decoherence on 2008-12-18
> **Checkhovian said:**
> If the problem is that my computer is overheating, though, is there anything I can actually do about that, besides getting a new one?

> Dec 17 22:06:22 dell-laptop kernel: [ 1856.179029] ACPI: Critical trip point

betcha it is overheating, given that log entry.

If you're comfortable with this, take the case off while the computer is running. Confirm that all the fans are spinning -- be sure to check the one in your power supply as well (though the PSU clicking off probably wouldn't trip ACPI)

Remove any extraneous dust from the fans. Be sure to follow the proper electro-static safeguards (ground yourself, don't do it on a carpet, take off all your clothes, whatever)

Also, did you build this machine or do a processor upgrade on it? If so, you may need to re-apply some thermal paste between the CPU and the heatsink.

--OOPS just realized you're on a laptop. Buy a can of compressed air and shoot it in to the heatsink in short bursts, or take it to a technician who will take it apart and blow out the heatsink for you. Overheating is a common problem on certain laptops, especially Pentiums. The usual cause is that the heatsink is so dusty, the fan can no longer blow air through it.

---

### Post by Checkhovian on 2008-12-18
It's actually a laptop, not a desktop, sorry, I should have specified that earlier. It's a Dell Inspiron 1525. Anyway I can check that the fan is still working?

---

### Post by kanikilu on 2008-12-18
This bug report may be of interest: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/213818](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/213818)

Though most people there seem to have a mention of "Critical temperature reached" in their logs...

---

### Post by fistfullofroses on 2008-12-18
"ACPI: Critical trip point" -- That is a temperature related problem, I think. I would check my processor load, graphics load, hd read/writes and seak times, and I would check the voltage coming in from the wall too...

---

### Post by Checkhovian on 2008-12-18
Well, as I type this, my temperature sensor read 76 C, and the cooling fan has not kicked in yet. I'm guessing that this means my laptop is overheating itself and that the fan isn't working properly...

---

### Post by fistfullofroses on 2008-12-18
correct.
most likely, ur fan should have kicked around 60 or 65 degrees

---

### Post by Paqman on 2008-12-19
> **Checkhovian said:**
> 
If the problem is that my computer is overheating, though, is there anything I can actually do about that, besides getting a new one?

Send it in for a servicing. Most laptop repairs specialist will open it up and clean all the fluff out from the inside for minimal cash. It should get cleaned out at least once a year. You'd be amazed at how badly a bit of fluff can degrade your cooling.

Besides, if your fans really aren't running, you need to get it repaired anyway.

You could do it yourself, but laptops can be tricky to disassemble if you don't know exactly how yours fits together. If you can find an overhaul manual (not a users manual) on the internet you might be able to get it apart pretty easily.

---

