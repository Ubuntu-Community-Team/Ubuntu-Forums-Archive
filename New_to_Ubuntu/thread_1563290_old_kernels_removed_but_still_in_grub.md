---
title: "old kernels removed but still in grub"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by dfor50 on 2010-08-28
This is just a housekeeping problem as my system is working fine. Whenever the kernels are updated it gets added to my grub2 menu. I remove the oldest ones via synaptic but some have lingered in grub's menu. When I search synaptic for a specific kernel(2.6.31-14 for instance) nothing comes up and ubuntu tweak has nothing either. I have tried the command line (there was a post for removing via the terminal but that did'nt work. I also deleted grub2 and reinstalled it but it added that old kernel back (as well as the others). Any ideas?

---

### Post by drs305 on 2010-08-28
Make sure both the kernel *and* header files are removed. You can do a search in synaptic for the specific kernel version (for instance 2.6.32-23) to see what still might be hanging around.

You can also inspect /boot/grub/grub.cfg to see which script is finding the kernel (10_linux or 30_os-prober). If it's in the 30_os-prober section, Grub 2 may be finding an old menu list or grub.cfg in another partition. In that case, you would need to find the file which contains the entry and either edit it or delete it, or find the kernel which still may be residing in another partition.

---

### Post by ssulaco on 2010-08-28
In the terminal,use..```
sudo apt-get remove --purge X.X.XX-X-*
```
where X is the Kernel you want to remove,the * is the wildcard and will pull both kernel and header files and drop it from the grub list
note....keep the "2" most recent kernels, so that you have an extra known good kernel to boot from

---

### Post by dfor50 on 2010-08-29
> **ssulaco said:**
> In the terminal,use..```
sudo apt-get remove --purge X.X.XX-X-*
```
where X is the Kernel you want to remove,the * is the wildcard and will pull both kernel and header files and drop it from the grub list
note....keep the "2" most recent kernels, so that you have an extra known good kernel to boot from

Hi, Thanks but this is what happens :
=@angry1:~$ sudo apt-get remove --purge 2.6.31-14
[sudo] password =: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-14
@angry1:~$

My mistake, I tried it with the wildcard but same result.

---

### Post by dfor50 on 2010-08-29
Thanks drs305, it looks like 10_linux is finding the file :

[I]menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3553854e-edd2-4ffc-b4a2-0d1cb482c99b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3553854e-edd2-4ffc-b4a2-0d1cb482c99b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic[/I]
[I]}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 3553854e-edd2-4ffc-b4a2-0d1cb482c99b
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3553854e-edd2-4ffc-b4a2-0d1cb482c99b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}[/I]
Is there anything I can do?

---

### Post by DougieFresh4U on 2010-08-29
Silly question but have you tried terminal
```

sudo update-grub2
```

Also, any other partitions on your machine?
Just a thought.

---

### Post by dfor50 on 2010-08-29
> **DougieFresh4U said:**
> Silly question but have you tried terminal
```

sudo update-grub2
```

Also, any other partitions on your machine?
Just a thought.

Hi,
I tried it again..........
 [I]@angry1:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sdc1
Found Ubuntu 10.04 LTS (10.04) on /dev/sdc5
done
 @angry1:~$ [/I]

I appreciate any help DougieFresh4U. It will end up being some dumb thing I've done or haven't done.

---

### Post by Silent Warrior on 2010-08-29
I don't have a clear picture of how you tried to remove the kernels... Did you launch Synaptic, browse through the unfiltered list ('All') to 'linux-', or just search for the specific kernel image and remove that? You know, there are a ton of headers and metapackages and things you'll want to clean out besides the image...

My method when moving from one kernel to the other is to, as I mentioned above, launch Synaptic, without any filter whatsoever moving down to 'linux' (clicking in that pane and typing 'linu' is often enough in my case). Once there, I go through the list carefully and look for entries mentioning the undesired kernel-version (linux-kernel-headers, linux-lbm, linux-kernel-image -generic this and that). Yep, it does take a few minutes every time, and the removal kicks mkinitrd into action a few times - depending on how much I'm removing - as well as update-grub, so mind that you don't attempt this when you have to catch a bus or something...

---

### Post by ssulaco on 2010-08-29
> **dfor50 said:**
> Hi, Thanks but this is what happens :
=@angry1:~$ sudo apt-get remove --purge 2.6.31-14
[sudo] password =: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-14
@angry1:~$

My mistake, I tried it with the wildcard but same result.
did you add the hyphen at the end followed by the asterisk,
retry with sudo apt-get remove --purge 2.6.31-14-*

---

### Post by dfor50 on 2010-08-29
Hi ssulaco,

Tried it then:

@angry1:~$ sudo apt-get remove --purge 2.6.31-14-*
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-14-*
@angry1:~$ 

Same result.

---

### Post by MattBD on 2010-08-29
Looks like you aren't entering the right package names to me. To see what exact kernel packages you have installed, try running the following:
```
dpkg -l | grep linux
```
For instance, mine came up with this:
```
matthew@nebuchadnezzar:~$ dpkg -l | grep linux
ii  lib32v4l-0                            0.6.4-1ubuntu1                                  Collection of video4linux support libraries (32 bits)
ii  libselinux1                           2.0.89-4                                        SELinux runtime shared libraries
ii  libv4l-0                              0.6.4-1ubuntu1                                  Collection of video4linux support libraries
ii  linux-firmware                        1.34.1                                          Firmware for Linux kernel drivers
ii  linux-generic                         2.6.32.24.25                                    Complete Generic Linux kernel
ii  linux-headers-2.6.32-24               2.6.32-24.41                                    Header files related to Linux kernel version 2.6.32
ii  linux-headers-2.6.32-24-generic       2.6.32-24.41                                    Linux kernel headers for version 2.6.32 on x86/x86_64
ii  linux-headers-generic                 2.6.32.24.25                                    Generic Linux kernel headers
ii  linux-image-2.6.32-24-generic         2.6.32-24.41                                    Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-generic                   2.6.32.24.25                                    Generic Linux kernel image
ii  linux-libc-dev                        2.6.32-24.41                                    Linux Kernel Headers for development
ii  linux-sound-base                      1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
ii  pptp-linux                            1.7.2-4                                         Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                              2:3.63+dfsg-2ubuntu3                            Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                            2.17.2-0ubuntu1                                 Miscellaneous system utilities
```
The packages you need to remove should be all the linux-headers and linux-image ones (I think you're supposed to not touch the linux-headers-generic and linux-image-generic ones, though - certainly I haven't removed them but the older kernels are still gone from my Grub).
Once you remove this using sudo apt-get purge, Grub should reconfigure itself automatically.

---

### Post by dfor50 on 2010-08-29
Hi Mattbd

here is the result:
[[COLOR="Blue"][I]I]sparker@angry1:~$ dpkg -l | grep linux
ii  libselinux1                           2.0.89-4                                        SELinux runtime shared libraries
ii  libselinux1-dev                       2.0.89-4                                        SELinux development headers
ii  libv4l-0                              0.6.4-1ubuntu1                                  Collection of video4linux support libraries
ii  linux-firmware                        1.34.1                                          Firmware for Linux kernel drivers
ii  linux-generic                         2.6.32.24.25                                    Complete Generic Linux kernel
ii  linux-headers-2.6.32-24               2.6.32-24.41                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-24-generic       2.6.32-24.41                                    Linux kernel headers for version 2.6.32 on x
ii  linux-headers-generic                 2.6.32.24.25                                    Generic Linux kernel headers
rc  linux-image-2.6.32-22-generic         2.6.32-22.36                                    Linux kernel image for version 2.6.32 on x86
rc  linux-image-2.6.32-23-generic         2.6.32-23.37                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-24-generic         2.6.32-24.41                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                   2.6.32.24.25                                    Generic Linux kernel image
ii  linux-libc-dev                        2.6.32-24.41                                    Linux Kernel Headers for development
ii  linux-sound-base                      1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
ii  pptp-linux                            1.7.2-4                                         Point-to-Point Tunneling Protocol (PPTP) Cli
ii  syslinux                              2:3.63+dfsg-2ubuntu3                            Bootloader for Linux/i386 using MS-DOS flopp
ii  util-linux                            2.17.2-0ubuntu1                                 Miscellaneous system utilities
[/I][/I][/COLOR]

The problem kernels don't show up but appear on grub.

---

### Post by PocketDog on 2010-08-29
In Synaptic, quick search for 'linux-image-generic' and click the 'installed version' tab twice to search for those in descending order.
Right-click the ones you don't want and 'completely remove'. Click apply.
All unwanted older kernels will be removed, along with their entries from Grub (1 or 2).

See screenshot for my kernel entries

---

### Post by dfor50 on 2010-08-29
> **PocketDog said:**
> In Synaptic, quick search for 'linux-image-generic' and click the 'installed version' tab twice to search for those in descending order.
Right-click the ones you don't want and 'completely remove'. Click apply.
All unwanted older kernels will be removed, along with their entries from Grub (1 or 2).

See screenshot for my kernel entries

Hi pocketdog,

That's how I tried to get rid of the kernels in the first place. The thing is they don't show up in synaptic but are still in grub. I could just edit the grub file (not recommended) but the files would still be somewhere. here is a shot of synaptic and an earlier post shows the grub menu. Maybe it's a bug.

 [[IMG]http://a.imageshack.us/img291/5076/synaptic.png[/IMG]](http://img291.imageshack.us/i/synaptic.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Edit: kernel 2.6.31-14 (for instance) is in grub but not in synaptic.

---

### Post by drs305 on 2010-08-29
The kernel you are having problems with is, I believe, from Karmic. If you did an upgrade from Karmic, check to see if you have an old menu.lst file stuck in your /boot or /boot/grub folder. If you do, delete it and update-grub. You can do a search for a menu.lst file on your Ubuntu drive with this command:
```
sudo find / -type f -name menu.lst
```

---

### Post by dfor50 on 2010-08-30
> **drs305 said:**
> The kernel you are having problems with is, I believe, from Karmic. If you did an upgrade from Karmic, check to see if you have an old menu.lst file stuck in your /boot or /boot/grub folder. If you do, delete it and update-grub. You can do a search for a menu.lst file on your Ubuntu drive with this command:
```
sudo find / -type f -name menu.lst
```

Hi again,
Nothing happens when I type that code.
[COLOR="Blue"][I]sparker@angry1:~$ sudo find / -type f -name menu.lst
sparker@angry1:~$ 

[/I][/COLOR]

However, if I do a search from the applications/accessories it turns up a menu.1st file for Memtest only.

[COLOR="Blue"]*Sample /boot/grub/menu.lst entry for memtest86*[/COLOR]

I checked the boot and boot/grub file and there was no menu.1st file. I don't think I did upgrade but did a re-install. Not 100% sure though. Thanks for taking the time to help.

---

### Post by Baldrick_NZ on 2010-08-30
> **PocketDog said:**
> In Synaptic, quick search for 'linux-image-generic' and click the 'installed version' tab twice to search for those in descending order.
Right-click the ones you don't want and 'completely remove'. Click apply.
All unwanted older kernels will be removed, along with their entries from Grub (1 or 2).

See screenshot for my kernel entries

Actually, a bit off-topic, but how did you get the mac lookalike windows PocketDog?

---

