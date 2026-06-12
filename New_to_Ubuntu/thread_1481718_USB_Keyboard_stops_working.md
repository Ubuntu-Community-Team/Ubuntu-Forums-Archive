---
title: "USB Keyboard stops working"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by teqslamer on 2010-05-12
I have a Microsoft (natural) Ergonomic Keyboard 4000 v1.0 which loses connection frequently.  I am using a LinksKey DVI KVM 2 port switch. I have Ubunto 10.04 installed on a AMD Athros 64 3800+ system with 4G memory and 2 300G SATA HD's and a GeForce 9800 GT PCI 1G video card.

When booting up the keyboard is recognized by the bios but grub does not.

Once at the logon screen sometimes it is recognized when it is not unplugging from the KVM and directly into the desktop it is recognized again.

Once logged on occasionally the keyboard is lost and requires unplugging and replugging in to get it active again.

In the Xorg.log this error is logged:
(EE) Microsoft Natural® Ergonomic Keyboard 4000: failed to initialize for relative axes.

Any help with this would be appreciated.

---

### Post by nhasian on 2010-05-12
> **teqslamer said:**
> When booting up the keyboard is recognized by the bios but grub does not.


this is a bios issue.  you need to enter your bios and ENABLE Legacy USB for the keyboard.

---

### Post by teqslamer on 2010-05-12
Do you mean USB 1.0 as well as 2.0?

---

### Post by teqslamer on 2010-05-12
Ok went into bios and changed legacy from Auto to Enabled.  No Change!

Still no keyboard via KVM to get keyboard must use desktop USB,
Note: the Mouse has no issues working through the KVM switch.

---

### Post by nhasian on 2010-05-13
i suppose you can try a different keyboard or a different kvm switch.

---

### Post by barbobot on 2010-06-20
I am having the same issue, however none of the tips here worked. I don't know why this was marked as solved...

---

### Post by barbobot on 2010-06-20
Figured it out, this happens when a non critical Error occurs, you can fix it by re-installing ubuntu-desktop and gdm

sudo apt-get install --reinstall ubuntu-desktop gdm

---

