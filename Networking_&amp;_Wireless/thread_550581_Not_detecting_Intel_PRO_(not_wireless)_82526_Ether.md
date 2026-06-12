---
title: "Not detecting Intel PRO (not wireless) 82526 Ethernet controller nor GMA 950"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by yang on 2007-09-14
I just installed Ubuntu onto a new Dell Inspiron 530, which has an Intel PRO 82526 Ethernet controller and an Intel GMA 950. Neither one of these seems to be detected by Ubuntu.

For the Ethernet controller, the only related thread I found is unresolved: [http://ubuntuforums.org/showthread.php?t=499192](http://ubuntuforums.org/showthread.php?t=499192).

There are a number of posts on the GMA 850, and a possibly-related ubuntuguide entry, but I can't try out any of those since they require that I install extra software (e.g. 915resolution), which won't work without a network connection.

Please help. Thanks in advance.

---

### Post by noob12 on 2007-09-14
Did you mean the 82562?  Can you run **lspci -nn**, find and post the line for your card?

---

### Post by yang on 2007-09-14
Sorry, you're right - I meant 82562.

```

00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:29c1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Unknown device [8086:29c2] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation Unknown device [8086:10c0] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation Unknown device [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation Unknown device [8086:2926] (rev 02)
02:00.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

```

---

### Post by noob12 on 2007-09-14
Yes it looks like that device isn't mapped and won't be claimed by the current Feisty version of the e100 driver or the e1000 driver.  I am going to check if it is mapped in the latest drivers from Intel.

---

### Post by noob12 on 2007-09-14
The device seems to be mapped in the latest e1000 driver.  This is a 10/100 device but is supported only in recent e1000 driver versions.   Examined source, but also confirmed in the README.

Download the driver source from here 
[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/9180/eng/e1000-7.6.5.tar.gz&agr=N&ProductID=983&DwnldId=9180&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/9180/eng/e1000-7.6.5.tar.gz&agr=N&ProductID=983&DwnldId=9180&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)


What kernel are you running **uname -r**?  I can give you instructions on building if you need them.

You'll need a USB jump drive to transfer stuff to the box, and some host from which you can do downloads.  If you have another Ubuntu box running the same arch and kernel with working ethernet, you can download and build on that box somewhat more easily.  Let me know if that's the case.

---

### Post by yang on 2007-09-15
I definitely need those instructions! :)

```

yang@yang-inspiron:~$ uname -a 
Linux yang-inspiron 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```

For now I'm just transfering files via a FAT partition from Vista 64-bit. (Which, incidentally, also had difficulties with the Ethernet controller; I had to download and install the Intel PRO drivers for it.)

---

### Post by yang on 2007-09-15
BTW, are you sure that's the right driver? It says it's for 82540EM Gigabit, whereas I just have a 82562 10/100.

For some reason that's the first result in the list of matches on Intel's site, but there's also this:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=998&DwnldID=2896&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=998&DwnldID=2896&strOSs=39&OSFullName=Linux*&lang=eng)

---

### Post by noob12 on 2007-09-15
Yes, I'm pretty certain.  

Here's the way I'm telling

 The e100 driver hasn't been changed since 2006 and Ubuntu has the latest version, and your card isn't supported by e100.

I'm looking at the e1000 sources and the device ids supported by the driver are in one of the headers.  I'm also looking at the README that is in the package I pointed you to.  Try downloading it and extracting it.  You can read the README and look for your card mentioned there, but the definitive thing is the device id that we got from your lspci listing and the kernel source.

I'm about to post a HOWTO on building e1000 when you have no network yet.  It will also have an attachment of pre-built versions for the i386 architecture (which should work for you).  Give me another 15 minutes or so, and I'll post you a pointer to that.

Then if you have more trouble, I can help you out.  You'll be the first person to try it I think.

---

### Post by noob12 on 2007-09-15
OK.  Try this thread now [http://ubuntuforums.org/showthread.php?p=3370406](http://ubuntuforums.org/showthread.php?p=3370406)

---

### Post by yang on 2007-09-15
Holy crap.

OK. I'll be back and let you know what happened.

Thanks.

---

### Post by noob12 on 2007-09-15
Note that you can try the easy way (just need to download and install the pre-built versions).

[This thread was solved by the HOWTO.  Correspondence continues on the HOWTO thread here: [http://ubuntuforums.org/showthread.php?p=3370406](http://ubuntuforums.org/showthread.php?p=3370406).]

---

