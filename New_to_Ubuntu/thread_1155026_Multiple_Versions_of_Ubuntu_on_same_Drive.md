---
title: "Multiple Versions of Ubuntu on same Drive"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by jkomikaze on 2009-05-10
Can someone help me out?

I have a 8.04 LTS version installed and running.  My wife and kids are using this as their primary computer (no more windows ... yeah).  I would like to continue to try new verions of Ubuntu, but keep this "Primary One" intact.

1.) Can I use the same Hard Drive and partition off space for my new test area?

2.) If so can I use the same /home and /swap partitions for both installs or do I need new ones.

3.) If not would you recommend using another Hard Drive on the same box or keep the testing of new versions to a different "test box" and leave my "production box" alone?

Any advice or recommendations that you have would be greatly appreciated.

Thanks

_______________________________________________________
[B]AMD Phenom X4 9550 64 Bit @ 2.2 GHz - Ubuntu 8.04.02
XFX 8200 GeForce MB - 8 GB Corsair XMS2 DDR2
DVD-RW Drive 20X - Seagate 500 GB SATA
[/B]

---

### Post by Bodsda on 2009-05-10
> **jkomikaze said:**
> Can someone help me out?

I have a 8.04 LTS version installed and running.  My wife and kids are using this as their primary computer (no more windows ... yeah).  I would like to continue to try new verions of Ubuntu, but keep this "Primary One" intact.

1.) Can I use the same Hard Drive and partition off space for my new test area?

2.) If so can I use the same /home and /swap partitions for both installs or do I need new ones.

3.) If not would you recommend using another Hard Drive on the same box or keep the testing of new versions to a different "test box" and leave my "production box" alone?

Any advice or recommendations that you have would be greatly appreciated.

Thanks

_______________________________________________________
[B]AMD Phenom X4 9550 64 Bit @ 2.2 GHz - Ubuntu 8.04.02
XFX 8200 GeForce MB - 8 GB Corsair XMS2 DDR2
DVD-RW Drive 20X - Seagate 500 GB SATA
[/B]

Hi,

Yes you can use the same drive. And as long as you have a separate /home partition then there is no need to create a new one.

When installing your new system, select manual partitioning, create a new partition to use as / and then select your original /home partition as /home, but make sure that no format flag is set on the /home partition. 

After you have installed your new system you may find that it has become the default in which case you will have to change it by editing the default value in ```
xorg.conf
``` or you can use BUM (Boot up manager)

Hope this helps,

Bodsda

---

### Post by Elfy on 2009-05-10
Personally I would use a sperate home for it - nothing to stop you adding a new partition and installing to it, it will use the exisiting swap.

I would though make sure that I installed the grub for your 'test' setups to their own partitions, I believe that the last page of the install procedure has the Advanced option - here you can change the grub location.

Then I would add the new install to the existing hardy install's grub with a chainloader, if your new install was on sda6 (hd0,5 for grub) you could add 

title Testing
root  (hd0,5)
chainloader +1

---

### Post by Sir Jasper on 2009-05-10
Hi,

I have both Ubuntu and Xubuntu on the same drive with only one swap file.

I'm not sure that's it's a good idea to have only one Home partition, especially as you can use a Home directory on your second installation.

My 2nd installation went without a hitch but I would clone your existing installation just in case things go wrong.

My regards

As it happens I have triple boot with two internal drives. My original drive is only used for Windows with the second drive for Linux, which has a FAT 32 partition for dual storage/backups.

---

### Post by ikisham on 2009-05-10
Hi forestpixie, I thought I could drop in instead of opening another thread:

I have another o.s. in a second hd and its grub was installed in / directory so i use the original (ubuntu's) grub. Its reference in the menu.list is
```
title		MEPIS at sdb1, newest kernel
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/sdb1 nomce quiet splash vga=791 resume=/dev/sdb2 
initrd		/boot/initrd.img
boot
```

my question is: could it be like the following? Or does that only apply to ubuntu versions?
```
title		MEPIS at sdb1, newest kernel
root		(hd1,0)
chainloader  +1
```

thanks.

---

### Post by markbuntu on 2009-05-10
You can install as many OSs as you have partitions for on one hard drive. There are some important things you need to do to avoid problems. 

Install the new OS and install its grub in the same partition as the new OS. Then you can chainload the new grub from the one on the MBR using lines like in the previous post. This will avoid problems with kernel updates etc.

Also, most OSs (Ubuntu,Fedora,Debian...) will reformat any swap partitions and change their UUIDs so you need to update the /etc/fstab in the old OS with the new UUID of swap or it will not get recognized and used.

You can find the UUIDs with 

sudo blkid

A separate /home it is not necessarily a good idea to share between distros as it contains many /.config files which can be different for different application versions. You might be better off with a /mystuff partition to hold your persoanl stuff that can be mounted in your /home directories.

---

### Post by ikisham on 2009-05-11
Ok! I'll try to see what happens.

And thanks for the broad tips.

---

### Post by bodhi.zazen on 2009-05-11
Here is a nice thread on multibooting :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

Personally I have gone to configfile (rather then chainloading)

---

### Post by jkomikaze on 2009-05-12
> **bodhi.zazen said:**
> Here is a nice thread on multibooting :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

Personally I have gone to configfile (rather then chainloading)

Thanks for the awesome link <bodhi.zazen> that really answers most of my questions.

Thanks to everyone else for your suggestions.

I haven't had time to implement yet ... but I will be soon :P

[B][CENTER]______________________________________________________________________
AMD Phenom X4 9550 64 Bit @ 2.2 GHz - Ubuntu 8.04.02
XFX 8200 GeForce MB - 8 GB Corsair XMS2 DDR2
DVD-RW Drive 20X - Seagate 500 GB SATA[/CENTER][/B]

---

