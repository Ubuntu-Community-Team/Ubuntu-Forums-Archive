---
title: "Is there any software support diskless boot in win xp"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by norule on 2009-10-27
I want to use ubuntu as server for storing image of client to boot diskless (without physical harddisk) by using LAN but clients will run windows xp.
Is there any software that support my requirement?
Thanks in advance.

PS. If my english makes you confuse see this link [http://www.ccboot.com/index.htm](http://www.ccboot.com/index.htm) and you will know what I mean.
The only problem is this software cost money and I want server to run on ubuntu coz I like its stability.

---

### Post by alphaniner on 2009-10-27
That page talks about iSCSI.  For that you would need a hardware iSCSI initiator.

Have you looked into PXE?

---

### Post by norule on 2009-10-27
So i have to use tftpd and dhcp for server and pxe boot lan card for client.
I want software that can handle diskless boot for windows xp.

---

### Post by norule on 2009-10-28
Please somebody help me..

---

### Post by Mark Phelps on 2009-10-28
> **norule said:**
> ... I want software that can handle diskless boot for windows xp.

Some folks here do provide SOME MS Windows support -- which you've already received -- but if that's not enough, post your concerns to a Windows XP forum.  

We're not the Windows XP experts!

---

### Post by Xianath on 2009-12-06
Look around at the FAQ section at [http://www.etherboot.org/](http://www.etherboot.org/). The short story is, you need dhcpd to give out IP addresses and the location of the boot image. tftpd-hpa will serve said boot image. The etherboot package contains the undionly.kpxe PXE image which the Etherboot/gPXE FAQs refer to, so you don't need to compile it. The iscsitarget package will give you iSCSI, which Etherboot/gPXE will emulate as a regular harddrive so you can install Windows (or any OS for that matter) diskless.

If you are lucky, you won't need to set up WinPE which is a major pain in the gluteal area. If you aren't lucky, you'll end up where I am right now, with everything working EXCEPT Windows actually booting. Thankfully, I traced it down to a Ubuntu configuration problem which I'm certain I can get help here for.

Cheers,
Peter

---

### Post by Xianath on 2009-12-08
As far as preparing a network-bootable Windows image, also take a look [here]("http://winbuilder.net"). You will still need tftpd-hpa, dhcpd and very likely iscsitarget (WinXP SP3 supports iSCSI I think), and you will probably also want samba for sharing files among boxes, eg. keep a single copy of Program Files. Needless to say, you will need to run this by legal and/or your Microsoft rep to confirm whether it's OK to do this, but technically it's not a big challenge once you have all the bits and pieces together. It's actually easier than trying to get Windows running on badly supported hardware (this is where Ubuntu CDs come in handy :) )

Cheers,
Peter

---

### Post by ukripper on 2009-12-08
> **norule said:**
> 

The only problem is this software cost money and I want server to run on ubuntu coz I like its stability.

In that case ask your client to run ubuntu or another linux distro for stability and for broader open source access. We can suggest you plenty of apps for this sort on linux platform.

---

