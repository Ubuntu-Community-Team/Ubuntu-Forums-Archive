---
title: "Wifi not working on dell XPS13"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by max74 on 2015-08-02
I recently downloaded and installed Ubuntu onto my dell Xps13, however, there are no wifi options when I open up the wifi configuration panel. How do I fix this?

---

### Post by praseodym on 2015-08-02
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by max74 on 2015-08-02
Broadcom Corporation BCM4352 802.11ac wireless Network Adapter [14e4:43b1] (rev 03)

---

### Post by praseodym on 2015-08-03
Is it 14.04? 32 or 64bit?

---

### Post by max74 on 2015-08-03
Yes, it is 14.04, and 64bit

---

### Post by praseodym on 2015-08-03
Uninstall the buggy driver:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation
```

sudo dpkg -i ~/Downloads"*.deb
```
Reboot

---

### Post by max74 on 2015-08-03
After running [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rfv wl
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
I received the message: modprobe: FATAL: Module wl not found.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

After running [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source

I received the message: Unable to locate the package bcmwl-kernel-source[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-08-04
Ok, so go ahead and install what has been suggested.

---

### Post by max74 on 2015-08-04
After running the command, nothing happens. It doesn't ask for the sudo password either, it just moves the cursor to the next line and idles.

---

### Post by Vladlenin5000 on 2015-08-04
> **max74 said:**
> After running the command, nothing happens. It doesn't ask for the sudo password either, it just moves the cursor to the next line and idles.

What command?

If you're referring to the command to install what you were instructed to download and install, replace "Downloads" with the actual folder were you saved them.

---

### Post by Hadaka on 2015-08-04
Hi Max74, is your ethernet, wired connection working?
If yes then with a working wired connection open a terminal..ctrl/alt/t and do..
```
sudo apt-get update
sudo apt get-install bcmwl-kernel-source
sudo modprobe wl
```
disconnect the wired connection...boot and test.

---

### Post by gbegin on 2016-07-18
This could be an issue related to drivers not working starting with  Ubuntu's 3.19.0-65 kernel. This is caused by a change made by Canonical  whereby kernel and kernel driver signing is now being enforced when  secure boot is enabled. During the update process, when a pop-up box  asked me to review the secure boot settings, I left them as they were  (enabled, I assume). 

See:

[https://bugs.launchpad.net/ubuntu/+s...s/+bug/1574727]("https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/1574727")

and

[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1566221]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221") 

As recommended in 

[http://en.community.dell.com/techcen...613/t/19985774]("http://en.community.dell.com/techcenter/os-applications/f/4613/t/19985774")

disabling secure boot from the BIOS corrected the problem for me. 

You could also use sudo mokutil --disable-validation from the terminal.

---

