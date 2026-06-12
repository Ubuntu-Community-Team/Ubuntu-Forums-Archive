---
title: "No boot menu after an error-free install - multi-boot"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by MichaelGld on 2010-06-16
I have a system running Windows XP Pro SP2 installed on one drive. I installed 10.04 on a second hard drive. I got to the end of the install with no errors and rebooted. It reboots into Windows as usual. There is no boot menu, no Grub, nothing. I have done this twice with the same results.

I am attaching a snapshot of my Disk Manager screen from Windows. Ubuntu is installed on disk 0.

What did I do wrong and how do I fix it? I'd like to boot up to a choice of OS's.

Thanks

---

### Post by ubunterooster on 2010-06-16
This will help even though you installed Windows first. Just remember to stick GRUB on the Windows drive

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by yetiman64 on 2010-06-16
> **MichaelGld said:**
> I have a system running Windows XP Pro SP2 installed on one drive. I installed 10.04 on a second hard drive. I got to the end of the install with no errors and rebooted. It reboots into Windows as usual. There is no boot menu, no Grub, nothing. I have done this twice with the same results.

I am attaching a snapshot of my Disk Manager screen from Windows. Ubuntu is installed on disk 0.

What did I do wrong and how do I fix it? I'd like to boot up to a choice of OS's.

Thanks

Sounds as though grub2 is installed to the MBR of the second drive and not sda (windows drive).

**1-**My first suggestion would be to look in your BIOS settings (usually delete or F2 when booting) and see if you can get the BIOS boot order to look at the Ubuntu drive 1st (where there should be an entry for windows - but if Windows is missing and you find you can boot Ubuntu, then it's as simple as running "sudo update-grub" from an Ubuntu terminal to have it find Windows and install an entry for it).

*_**2-**If changing the BIOS bootorder fails__ or other problems occur_*, then from a live cd download and run the **[Boot_info_script]("http://ubuntuforums.org/showthread.php?t=1291280")** , this link is a good guide by UF member louieb, to downloading and using the script, courtesy of UF member meierfra. This script gives detailed information of your boot setup and files (try the BIOS boot order change 1st though).

---

### Post by MichaelGld on 2010-06-18
The BIOS adjustment you recommended worked like a charm! Thanks for the help.

---

### Post by yetiman64 on 2010-06-18
> **MichaelGld said:**
> The BIOS adjustment you recommended worked like a charm! Thanks for the help.

You're welcome MichaelGld, and could you mark this thread as solved? Thanks. To do this check the last link in my sig, cheers, yetiman64.

---

