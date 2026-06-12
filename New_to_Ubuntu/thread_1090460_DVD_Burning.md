---
title: "DVD Burning"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by John Hale on 2009-03-08
Guys I'm new to linux and am after a good dvd burner that doesn't give error messages all the time I'd hop back into windows and use nero or dvd decrypter but windows is so unstable now that it barely operates currently I've tried brassero and kb3 both don't seem to want to copy these dvds

John

---

### Post by DGortze380 on 2009-03-08
> **John Hale said:**
> Guys I'm new to linux and am after a good dvd burner that doesn't give error messages all the time I'd hop back into windows and use nero or dvd decrypter but windows is so unstable now that it barely operates currently I've tried brassero and kb3 both don't seem to want to copy these dvds

John

have you installed the correct codecs?

open synaptic and install ubuntu-restricted-extras

---

### Post by taurus on 2009-03-08
What kind of DVD's are you trying to make copies?

---

### Post by John Hale on 2009-03-08
So I open synaptic package manager and where to I find that option?

---

### Post by taurus on 2009-03-08
In the Search field.  Type in the name of the package you want to install.  Then click the package to install it.

Otherwise, close synaptic and install it from a terminal with apt-get.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
However, I don't think making copies of DVD's have anything to do with codecs.

---

### Post by bryncoles on 2009-03-08
follow the instructions in this link:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and then you should be able to use k9copy to rip dvd's (of course, only to make backups of dvd's you have bought legally), and k3b to burn dvds.

---

### Post by John Hale on 2009-03-08
brasero tells me the medium is not writable and I get 33% in and kb3 just throws up read error after read error yet an month back it copyed fine in windows on nero ands been sitting in its case since will try this medibuntu

---

### Post by bryncoles on 2009-03-08
could you copy/paste the error messages into this thread please, someone cleverer than me will see them and possibly work out what's causing you grief!

and baybe start brasero from the terminal (just type its name into the terminal) to see if that encourages it ti give you an error message?

afterall, it cant hurt.... right?

---

### Post by John Hale on 2009-03-08
Trying another dvd now hopefully get the error soon and get it solver, and sorry should of read k3b

---

### Post by bryncoles on 2009-03-08
well, hopefully you wont get the error ;)

---

### Post by John Hale on 2009-03-08
still get problem while reading retrying from sector ******* now why would it play fine there are no scratched or fingerprints on the disc it copied fine in windows using nero what other packages do you suggest I try? Do i need to try a head cleaning disc? I can't think of what else to do and I've promised a copy of these dvds to a friend as I had no previous copying problems.

This is typical of the error I get I've read manufacturers use blank sectors as a copy protection scheme?

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-23-generic
Devices
-----------------------
SONY CD-RW  CRX220E1 6YS1 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

_NEC DVD+RW ND-1000A 1.01 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW] [DVD-ROM, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]
K3bDataTrackReader
-----------------------
reading sectors 0 to 2135423 with sector size 2048. Length: 2135424 sectors, 4373348352 bytes.
using buffer size of 64 blocks.
Problem while reading. Retrying from sector 1246528.
Problem while reading. Retrying from sector 1246656.
Problem while reading. Retrying from sector 1246720.
Problem while reading. Retrying from sector 1246784.
Problem while reading. Retrying from sector 1247104.
Problem while reading. Retrying from sector 1247168.
Problem while reading. Retrying from sector 1247296.
Problem while reading. Retrying from sector 1247424.
Problem while reading. Retrying from sector 1247744.
Problem while reading. Retrying from sector 1248512.
Problem while reading. Retrying from sector 1249920.
Problem while reading. Retrying from sector 1250240.
Problem while reading. Retrying from sector 1253696.
Problem while reading. Retrying from sector 1253760.
Problem while reading. Retrying from sector 1253888.
Problem while reading. Retrying from sector 1254464.
Problem while reading. Retrying from sector 1255040.
Problem while reading. Retrying from sector 1255488.
Problem while reading. Retrying from sector 1256384.
Problem while reading. Retrying from sector 1259776.
Problem while reading. Retrying from sector 1260416.
Problem while reading. Retrying from sector 1260800.
Problem while reading. Retrying from sector 1260864.
Problem while reading. Retrying from sector 1260992.
Problem while reading. Retrying from sector 1261184.
Read error in sector 1261184.
Read a total of 1261184 sectors (2582904832 bytes)

John

---

### Post by melrokz on 2009-03-08
dvd::rip is a pretty nice program I use to rip titles from my DVD. I also have a DVD9 which I wanted to convert to an ordinary DVD5 (4.7GB). I used DVD95 converter for this.

---

### Post by John Hale on 2009-03-08
Put in a lens cleaning disc and tried again and got this 

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-23-generic
Devices
-----------------------
SONY CD-RW  CRX220E1 6YS1 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

_NEC DVD+RW ND-1000A 1.01 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW] [DVD-ROM, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]
K3bDataTrackReader
-----------------------
reading sectors 0 to 1292431 with sector size 2048. Length: 1292432 sectors, 2646900736 bytes.
using buffer size of 64 blocks.
Problem while reading. Retrying from sector 1207104.
Read error in sector 1207120.
Read a total of 1207104 sectors (2472148992 bytes)

---

### Post by John Hale on 2009-03-08
melrokz just wish I was clever enough to understand the web page enough to install it

---

### Post by bailbath on 2009-03-08
> **John Hale said:**
> 

This is typical of the error I get I've read manufacturers use blank sectors as a copy protection scheme?



John

Some discs don't play well with some manufacturers recorders can be a bit of a lottery. Once you find a make that works well with yr burner best to stick with that make.
Ian

---

### Post by John Hale on 2009-03-08
Bailbath it's not a writing error it's a reading error. Melrokz I managed to install dvd:rip how do I copy with it?

---

