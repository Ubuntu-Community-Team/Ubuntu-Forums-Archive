---
title: "ethernet (nvidia mcp51) link is down"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Sav on 2007-12-15
Hi, I installed gutsy on my pavillion dv6000 (turion x2 54 + nvidia mcp51 chipset) and the ethernet link is down.
It's strange because if run lspci the network controller is listed, but it's like the cable is broken.
I noticed that when I power on the laptop the link is up (green lights on the interface and on the router) and when the kernel starts to load the link goes down.
I tried many parameters like

noapic nolapic irqpoll pci=routeirq (the bios is buggy)

with no results.

It's weird beacuse I already got gutsy fully functional, but before I upgraded from feisty.

Now, with a clean install, I got this strange problem.

Any ideas?

---

### Post by Sav on 2007-12-16
up

---

### Post by Sav on 2007-12-17
Yesterday I installed feisty, and the ethernet worked.
After I ugraded to gutsy and the link went down again.
Using in gutsy the old kernel it's a good workaround but I have problems with the restricted drivers.
Anyone?

---

### Post by njparton on 2007-12-17
sounds like a forcedeth issue.

what happens after the following:

```
sudo modprobe forcedeth
```

or try the following to remove and then re-insert the forcedeth driver module:

```
sudo rmmod forcedeth
sudo modprobe forcedeth
```

What do you mean by "the bios is buggy"?

---

### Post by Sav on 2007-12-17
I tried as you suggested but it didn't work.

The bios of the laptop is bugged, like many others.
To boot correctly I have to pass to the kernel the following parameters:

nolapic irqpoll pci=routeirq

---

### Post by njparton on 2007-12-17
Hmm, well then unless you can get your BIOS sorted out it may not be solvable?

Maybe someone else can help...

---

### Post by Sav on 2007-12-17
I think is a kernel problem.
With feisty all was good.

---

### Post by MaxGom on 2008-01-31
Hi,

I am experiencing the same problem on a Nec Desktop that uses the same nVidia chipset. In my case too, the ethernet lights are on for a few seconds just after power-on, and then the lights turn off forever! The problem seemed to be exactly the same when I was using openSuSE 10.3.

Thank you for any help,
Maxime

---

