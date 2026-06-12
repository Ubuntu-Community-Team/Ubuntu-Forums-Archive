---
title: "System has turned to toast"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Loki*PI on 2011-04-01
Over night my Lucid installation has turned to toast. Each time I tried to bring up the system it degraded more. At first a couple apps stopped working. Then on boot 'mounting /dev/disk -- /root failed' started coming up. I brought up a live CD and tried some of the tests and fixes I found on forum. Nothing showed an error, but the system isn't coming up. Also I'm seeing disk drive for /tmp not ready on boot. The Live CD is no longer making a network connection, not seeing the network card. 

This sound like the OS is just degrading or more like a hard ware problem? Could be the hard drive failing?

Anyone seen this before?

Thanks

---

### Post by Grenage on 2011-04-01
> **Loki*PI said:**
> Over night my Lucid installation has turned to toast. Each time I tried to bring up the system it degraded more. At first a couple apps stopped working. Then on boot 'mounting /dev/disk -- /root failed' started coming up. I brought up a live CD and tried some of the tests and fixes I found on forum. Nothing showed an error, but the system isn't coming up. Also I'm seeing disk drive for /tmp not ready on boot. The Live CD is no longer making a network connection, not seeing the network card. 

This sound like the OS is just degrading or more like a hard ware problem? Could be the hard drive failing?

Anyone seen this before?

Thanks

This sounds like a failing hard drive; backup anything you need, if you still can.

---

### Post by Hedgehog1 on 2011-04-01
+1 on backing up what data you can.  It sounds like a failing hard drive to me as well.

***The Hedge***

:KS

---

### Post by Loki*PI on 2011-04-01
Yes that is what I'm thinking too. I'm recovering what I can and will get a new HD tomorrow.  Thanks for the responses.

---

### Post by IHeequ5i on 2011-04-01
It concerns me that the Live CD cannot see the network card. I'm not sure how a failing hard drive could cause that.

---

### Post by Grenage on 2011-04-01
You're right, it won't; do you know what network card you have?

---

### Post by _joecrawford on 2011-04-01
I agree with the bet that it is your hard drive.  I would not worry about the network card until you get the HDD backed up and squared away.

---

### Post by Loki*PI on 2011-04-01
Yes I'm wondering about that too. I've tried two different Live CD same problem, no network connection.

Tried lshw but only says there is a 100 Mbit ethernet adapter.  At least it saw it.  Ethernet adapter is on the mother board.

I have no trouble accessing the hard drive, copying off files. It seems more like GRUB is corrupted than the hard drive has failed. 

That still doesn't explain the network not work. 

Open to suggestions.  :-)

---

### Post by Loki*PI on 2011-04-05
Resolved sort of.  I bought a new hd and downloaded live 10.04 iso. I've rebuilt the system. 

I still don't know if it was the hd, as I can still access it and what tests I've run show it to be ok. Perhaps something started to corrupt the boot and other required files. Each time I was able to bring up the system more and more functions and applications failed.

---

### Post by Grenage on 2011-04-05
> **Loki*PI said:**
> Resolved sort of.  I bought a new hd and downloaded live 10.04 iso. I've rebuilt the system. 

I still don't know if it was the hd, as I can still access it and what tests I've run show it to be ok. Perhaps something started to corrupt the boot and other required files. Each time I was able to bring up the system more and more functions and applications failed.

Most likely, yes.  A progressive failure isn't uncommon, where more and more sectors become corrupt; an arm can fall out of alignment (amongst other things) and it just wrecks more and more data as it goes.

---

