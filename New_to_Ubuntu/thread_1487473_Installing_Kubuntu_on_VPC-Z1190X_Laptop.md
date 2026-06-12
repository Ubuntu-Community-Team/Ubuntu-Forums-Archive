---
title: "Installing Kubuntu on VPC-Z1190X Laptop"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Zithras on 2010-05-19
I just got in a Sony Z series laptop and am trying to install Kubuntu on  it.

Relevant specs:
i7 processor
dual graphics card (Intel/1 GB NVidia)
4x 128 GB SSD

The first problem i had was that the system had a RAID0 made out of the 4  disks.  I broke that down (2 days of effort before I finally figured  out a solution for THAT one, seeing as how Sony sends no OS install  discs, only Recovery discs to be used with the drives in RAID), and have  Windows 7 Ultimate x64 installed and working fine on drive 1.  Drives  3-4 are NTFS formatted to use as storage.  Drive 2 is currently  unformatted.

I want to dual-boot Kubuntu and install it on drive 2.  (and likely use  it as my main operating system).

I downloaded and burned the Live CD (Intrepid Impala, 10.04), and it  loads the menu where it asks me to use it as a live OS or install  Kubuntu, and whenever I try and install Kubuntu (or use it Live, for  that matter), the screen goes nuts, showing some weird psychedelic color  pallette and making it basically impossible to see what I am doing.

I have spent the last day googling, and have found various solutions  concerning graphics switching, black screens, touchpad issues, wifi  issues, and other annoyances.  However, no one seems to have been flat  out unable to install Ubuntu (Kubuntu in my case).  The closest I got to  my problem was a 'black screen' issue.

If anyone has a similar laptop, or has faced a similar problem (wacky  colors when trying to install), please could you help me out!  I love  the specs on this laptop (no one else is making 13 inch laptops that are  nearly this powerful), but will likely return it if I cannot install  Ubuntu at all.  I wasn't sure If I should ask for help in the ubuntu  forums or the Kubuntu forums, so I posted on both :D  The only other  time I installed Ubuntu (old Dell laptop, Ubuntu, Feisty Fawn), it went  off without a hitch, so I'm really hoping this an easy problem that's  simply showing up due to my inexperience.

Thanks,
Zithras

---

### Post by cariboo on 2010-05-19
Once you are at the initial Live CD screen, the one with the man and keyboard at the bottom press the any key to see the menu.

Press F6 and select nomodeset, then continue on to the desktop.

---

### Post by Zithras on 2010-05-21
Nope - no luck with f6 disabling acpi, apis, nomodeset, etc. - still won't install OR work as a live CD.  I'm not really worried about the Windows bootloader on the other drive - it's easy to fix.

How do I access a text-only install mode - maybe that'll work?

Edit: I found this link, and was also linked there by a mailing list: [http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/](http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/)  This seems a bit much for an inexperienced linux user to bite off, but I'll try poking through it and see if that works over the next few days...expect questions below.

---

### Post by Zithras on 2010-05-22
Still trying to dualboot Win 7 and Kubuntu on a Sony VPC-Z1190X laptop.  Installed Lucid Lynx in text mode via the alternate CD, grub and Windows 7 are both working fine.  Still trying to get Kubuntu running.

Okay I followed the instructions on here: 
[http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/](http://questier.com/2010/04/26/ubuntu-10-4-lucid-lynx-on-sony-vaio-vpcz11x9e/)
including the steps under the 6/5/10 update.

When Grub starts, I get the following boot options: 
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Ubuntu, with Linux 2.6.32-20-generic
Ubuntu, with Linux 2.6.32-20-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

Options 1-4 won't boot (black screen on startup), even if I start with a 8.04 live cd first as suggested. (They'll give me a command prompt if I select that option, but no graphics)

Option 5 (the 20-generic) will also give a black screen if booted directly, but will give me a command prompt if I replace 'quiet splash' with 'single nomodeset i8042.nopnp' and then boot.
If I then enter 'sudo /etc/init.d/kdm start' at the command prompt I will get a KDE login screen, with a working touchpad.
However, when I enter my login name and password, and try to login, the screen briefly flashes black, and brings me back to the login screen.

Trying to get Kubuntu working on this machine is driving me NUTS (and taking up huge amounts of time)!  Windows works great, but I would MUCH rather use Kubuntu as my default OS.

Any ideas?

Thanks,
Zithras

(note: the machine does not have the drives in RAID, so this is not an issue here)

---

### Post by antithesis2010 on 2010-06-06
I have this exact same laptop and trying to get Ubuntu installed.  I've spent 32 hours straight and recently another 8 hours to no avail.

Were you ever able to get this working?

---

