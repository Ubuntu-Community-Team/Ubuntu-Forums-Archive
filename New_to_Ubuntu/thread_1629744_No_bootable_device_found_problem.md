---
title: "No bootable device found problem"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-11-24
I have Ubuntu 10.04 loaded exclusive on my Acer ONE travel PC. 

My problem is this:

At initial boot up I recv the following:

For Atheros PCIE Ethernet Controller v1.0.0.5(01/22/09)
check Cable connection
PXE-E63 Error while initializing the NIC
PXE-MOF: Exiting Intel PXE ROM
No bootable device - insert boot disk and press any key

While then I hit cntl-alt-del the system reboots to my loaded OS w/o problem (OR) I press F2 during initial boot up tab over to the BOOT tab where I find the following:

1. Network Boot: Atheros Boot Agent
2. IDEO: ST9160314A5 (or maybe S)
3. IDE1: 
4.USB FDD
5.USB HDD
6.USB CDROM

I then hit F10 and the system again will reboot and properly load the OS.

Problem is I have to do this little song/dance EVERY TIME I turn the PC on. What gives?

---

### Post by arochester on 2010-11-24
You will probably find that your boot order can be changed. Moved up or down in priority? Some can be disabled altogether? 

On my machine I can either access the BIOS and change boot order there, or separately enter the Boot Order (F2 or F12 in my case). The BIOS is better and more final.

Why should you want a network boot first??? I disabled network boot. I don't have it and don't need it.

---

### Post by Amockineuropa on 2010-11-24
Which should I use?

---

### Post by chamira on 2010-11-24
Change the order of your boot configuration so that it checks the CD Rom first - allows you to boot from CD & repair system &etc

Then - the Hard-drive with Ubuntu on

You will need to change the Boot config order and possibly the hard disk order as well, move the Ubuntu drive to the top of the list.

---

### Post by Amockineuropa on 2010-11-24
Problem resolved.

---

### Post by chamira on 2010-11-24
How did you fix it? 

By the way you need to mark the thread as 'solved' as well.

And I think there is a another thread you have with the same problem so close that off too.

---

