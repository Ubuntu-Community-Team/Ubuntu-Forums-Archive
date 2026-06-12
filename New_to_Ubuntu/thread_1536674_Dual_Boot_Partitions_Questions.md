---
title: "Dual Boot Partitions Questions"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by BurningPants on 2010-07-22
I seem to have got myself in a bit of a pickle.

I tried to set up  a LM9/Windows7 dual boot and after nearly a whole day of failing  miserably I finally arrived at this point on my disk 

[IMG]file:///home/drew/Desktop/Screenshot--dev-sda%20-%20GParted.png[/IMG]

sda1 was a LM9 installation that I set up without  checking the install images' checksum (doh!  That is where all my  troubles began when I discovered I had downloaded a dodgy install ISO)

sda2  was the next to be set up with windows 7

sda6 was then created  with a checked and stable LM9 which I want to be my main OS

My  questions are

1.How do I get rid of sda1 and reallocate the space  to sda6?
2.Would I need to reassign sda6 as primary? 
3.What on  earth do I do about the boot-loader afterwards?
4.Why is sda3  (Windows 7) flagged as boot when I get LM9s' boot-loader at startup?
5.Has  anyone seen my car keys?

This is my first encounter with Linux,  and have never tried something like this on Windows either so I would  really appreciate any help I can get with this.  

Cheers
PS.   as soon as I find a good way to cross-platform video chat I would like  to get rid of sda2 (Windows 7) too.  Does that require some preparation  at this stage too.  i.e. should it be moved to someplace where it can be  more easily deleted later?

PS in case my scrrenshot doesn't work
unallocated                                   1Mb
/dev/sda1       ext4                        430Gb    
/dev/sda2           ntfs                                24.42Gb         boot 
/dev/sda3           extended                             11.34Gb
    sda5          Linux swap                    4.42Gb
    sda6            ext4                                6.57Gb              mounted at /
     unallocated unallocated                    1Mb
    sda7          Linux swap                     355Mb

---

### Post by mapes12 on 2010-07-22
It looks like you know what you're doing with partitions but this might help:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

I read somewhere that 7 and Ubu don't get along on the same machine.

---

### Post by oldfred on 2010-07-22
Windows uses a boot flag to identify which primary partition has the windows boot code in the boot sector. Grub does not need the boot flag.

You have two swaps and only need one. If you have 2GB or more of memory swap should be 2GB or slightly more than RAM if you want to hibernate.

Would need more details on exactly where partitions are on drive, but if windows is between sda1 and sda3 you will not be able to merge without major effort. It would be better easier to make sda1 into your /home or a data partition and increase  your root partition by merging with some of swap.

Whichever operating system is installed last (unless you specify otherwise) is installed to the MBR. If you want a different one you need to reinstall its boot loader into the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by BurningPants on 2010-07-22
I'm liking the sound of having sda1 as a data partition.  Though I am unsure about how to accomplish this.  Do I need to uninstall LM that is on there?  Or if I simply erase the entire contents of sda1 how would that effect GRUB?

---

### Post by oldfred on 2010-07-22
It depends on which bootloader is controlling by being in the MBR.

You can boot into your system that you want to keep and reinstall its boot loader into the MBR so you know it is in control

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I searched on google and it says your car keys are where you last left them.:smile:

---

