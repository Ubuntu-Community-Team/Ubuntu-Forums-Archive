---
title: "Uninstalling Ubuntu and GRUB."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by djwkd on 2010-01-07
Hello all,
So - my dad's Windoze computer isn't working (software problem) and so i've reccomended that he install Ubuntu.

First, though, i need to know how to uninstall GRUB and Ubuntu. I understand that you can just format the partition that Ubuntu is on, but the MBR of the disk would still be set to use GRUB.

So - can anyone help me here?

Thanks in advance, 
Dom.

---

### Post by djwkd on 2010-01-07
Am i right in thinking that if i use MS-SYS this will uninstall GRUB, then i just need to format the Ubuntu partition?

---

### Post by netol on 2010-01-07
Yes, if you decide to install Windows in a system where GRUB is installed Windows will "repair" the MBR for you deleting GRUB. You can delete the ubuntu partition before or after the windows install.

---

### Post by premjan on 2010-01-07
So I have a simple question - I used wubi to install Kubuntu on a Windows 7 laptop (Acer 5517).  Not sure if I pulled the install CD out at the right time in the Kubuntu install sequence - I now seem to go through grub multiple times in order to boot Kubuntu.  I also have problems with the wireless lan but that's for another thread.

---

### Post by raydeen on 2010-01-07
@djwkd

Not quite sure what you're asking for here. Are you wanting to install Ubuntu over the Windows partition or uninstall Ubuntu and reinstall or repair Windows?

To be safe, if you can find an external drive, copy all your personal Ubuntu and Windows files off to it first (you should be able to do this with the Ubuntu Live CD) before trying to restore the system.

If Windows is still on the system on a different partition, you can boot up with the Ubuntu Live CD, run the Partition Manager and delete the Ubuntu partitions and then resize the Windows partition to reclaim the rest of the drive space. Then to remove Grub, you would boot with your Windows disc and go into the Recovery Console.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")

If the system is hosed and you just want to start from scratch, backup your files as mentioned above, load your Windows CD and boot from it and have it erase, format and repartition the drive. It will get rid of Grub and make a new MBR.

Hope this answers your question.

---

### Post by NoonienSoong97 on 2010-01-07
Thanks for the info. However the problem I have is a tad bit different. I decided to just post on here instead of adding another thread to the site. My problem is what to do when a version is no longer valid for updating. I am on a duel boot system right now. However in my next system wide format. I plan on installing a newer version of Ubuntu with Sun's Virtualbox for my Window needs. Instead of using duel boot.

Should I then install Win98,or XP on a smaller drive for system recover/ drive formatting purposes? Then swap out that drive once the master, slave, and any of my SATA drives are formatted properly?

---

