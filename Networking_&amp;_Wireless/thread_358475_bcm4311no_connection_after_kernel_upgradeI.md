---
title: "bcm4311:no connection after kernel upgradeI"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by dekalbave on 2007-02-10
I compiled ndiswrapper from source against kernel 2.6.17.10 following these instuctions:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

After booting with new kernel 2.6.17.11,  no wireless connection.  Is there any way to have my wireless back in the new kernel, or do I just keep booting to the old one?

TIA

---

### Post by teaker1s on 2007-02-10
check ndiswrapper-utils for latest version

---

### Post by teaker1s on 2007-02-10
In feisty mine died and when upgrading, my ndiswrapper-utils needed manually updating to ndiswrapper-utils-1.9

---

### Post by lojic on 2007-02-10
I've started a thread regarding the -11 upgrade breaking wireless. If you can offer any insight there, it would be much appreciated.

Also, it may be helpful to post your wireless hardware there so it can be collected in one thread.

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

Thanks!

---

### Post by dekalbave on 2007-02-11
> **teaker1s said:**
> In feisty mine died and when upgrading, my ndiswrapper-utils needed manually updating to ndiswrapper-utils-1.9

Actually, I never installed ndiswrapper-utils in the first place.  Still haven't, and I get great wireless when I boot to 2.6.17-10-generic.

---

### Post by matt_risi on 2007-02-11
Worst of all, I tried simply reinstalling the network card as I did for the -10 kernel, and it won't have it. This is why I dual boot folks.

---

### Post by dekalbave on 2007-02-11
> **matt_risi said:**
> Worst of all, I tried simply reinstalling the network card as I did for the -10 kernel, and it won't have it. .

That's what I was afraid of.

If anything, this shows why one should not get rid of their "old" kernel until absolutely sure the new one isn't causing any problems.

---

### Post by teaker1s on 2007-02-12
> **dekalbave said:**
> That's what I was afraid of.

If anything, this shows why one should not get rid of their "old" kernel until absolutely sure the new one isn't causing any problems.

this is what I posted a suggestion in the upgrades section, seems a fatalist attitude to remove old kernel before your sure new works

---

