---
title: "dual boot Fedora 14 and Maverick"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by beew on 2010-12-05
I am going to install Fedora 14 to make a dual boot with Ubuntu 10.10. I know there are installation tips and trouble shooting information scattered all over the forum on this topic. But I just need someone to either confirm the following is correct and point out if there is any mistake that needs correction. Ubuntu is already installed. 

1.Partition hard drive to carve out a partition for Fedora.

2.Install Fedora into the new partition, choose advanced/manual installation.

no need for swap because there is already swap in the Ubuntu installation and only one swap area is needed no matter how many Linux OSes are installed on same hard drive.

3. Choose not to install any bootloader (I read it on the forum somewhere, but I am not sure if Fedora's installer would allow that)

4. After installation  is completed boot into Ubuntu and run "sudo update-grub" This will find Fedora and create an entry for it in the boot menu.

Finally, I am going to install Fedora14 and all the information I gathered is for earlier versions of Fedora. If there is any new information that I need to be aware of, please let me know.  Thanks.

---

### Post by wojox on 2010-12-06
That's how I have done it. If #3 fails and installs Fedora's bootloader (which it shouldn't) you can always reinstall Grub2 from a Live-CD.

[Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

