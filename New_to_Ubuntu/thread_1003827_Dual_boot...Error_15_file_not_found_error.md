---
title: "Dual boot...Error 15 file not found error"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by sajixavier on 2008-12-06
HI
i have a single ide hard disk. i have windows xp and mandriva 2009 installed. so recently i got the ubuntu 10 cd. so i tried to install ubuntu in the hard disk. i tried many ways but it didn't work that well.

Then i clear all the linux partition and start from the scratch. though i didn't remove the windows partition. then i installed the Ubuntu 10 from the live cd.i created one ex3 partition and swat partion. in the ex3 partition i configured the '/'. Everything went well. After that i installed Mandriva 2009 from live cd. there was 12gb freespace left.so i installed the mandriva 2009 in it, by configuring manual partition. i made a swap partition and / and /home partions..

so now i have two swap partion and 2 ext3 partition. ( before this i tried to install with one swap partition but it didn't work.because mandriva shows failure loading the swap partition. this was the reason i created two swap partition)

Also i installed the grub of Ubuntu in the root partition and grub of Mandriva in the MBR. Ubuntu was showed in the grub menu. Mandriva is working good. when i select the ubuntu it take me to another menu containg ubuntu, ubuntu safe, memtest and windows xp.

When i tried to load the ubuntu it showed me Error 15 : file not found.

Also mandriva can access the root partition of ubuntu. so i have the menu.lst

---

### Post by bhadotia on 2008-12-06
try [this]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD")

---

### Post by caljohnsmith on 2008-12-06
Have you made sure the UUID used for the Ubuntu entries is correct? If you do:
```
sudo blkid
```
Does that show the Ubuntu partition's UUID as 14f729d9-1a4e-452a-87e1-853fab7a5289? Also, have you checked in the Ubuntu /boot folder to make sure you have the "vmlinuz-2.6.27-7-generic" and "initrd.img-2.6.27-7-generic" files? I would start there, but let me know what you find.

---

### Post by sajixavier on 2008-12-07
where should i type ```
sudo blkid
```
I can only access Mandriva and windows xp....With mandriva i can only browse the place where ubuntu is installed ok. in Mandriva it is showing as a drive. So i can copy the contents in it..


the two files u mentioned is already there....also i am attaching the fstab file of ubuntu.

Also in the grub list of ubuntu, by pressing c and typing ```
find /boot/grub/stage1
``` i get 
```
(hd0,7)
(hd0,9)
```

---

### Post by caljohnsmith on 2008-12-07
Where ever you typed in the "fdisk" command in Mandriva, just do the same with "blkid"; fortunately, you don't have to be in Ubuntu to enter that command. Please post the results so we can check that your UUID for Ubuntu is correct. Also, is Ubuntu on sda8 like your fstab implies?

---

### Post by sajixavier on 2008-12-07
Yes ubuntu is in sda8, i checked it.

---

### Post by caljohnsmith on 2008-12-07
Can you also post the Ubuntu entry you have in your Mandriva's menu.lst that takes you to the Ubuntu menu.lst? Also, if it's not too much trouble, when you post the results, please copy/paste the results into the Ubuntu forum message box in your web browser, highlight the text, and then press the pound sign # graphic in the top portion of the message box to put "code" tags around the results (like you did in post #4); it's a lot more convenient to view it that way rather than download the attached files.

Also, go ahead and reboot, and when you get the Mandriva Grub menu, press "c" to get the Grub command line. Then type the following *without pressing enter*:
```
grub> null (hd0,7)/boot/
```
Then press TAB for tab-completion; does that show the following files:
```
vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-7-generic
```
Please let me know the results.

---

### Post by sajixavier on 2008-12-07
Ok from now i will do that.....here is the mandriva menu.lst

```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,9)/boot/gfxmenu
default 3

title linux
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=291fd4c4-3783-4cd1-9f70-0ae95327d020  resume=UUID=2a9e76bc-0dbd-4e47-872c-b4dac3393aaa splash=silent vga=788
initrd (hd0,9)/boot/initrd.img

title linux-nonfb
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=291fd4c4-3783-4cd1-9f70-0ae95327d020  resume=UUID=2a9e76bc-0dbd-4e47-872c-b4dac3393aaa
initrd (hd0,9)/boot/initrd.img

title failsafe
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=291fd4c4-3783-4cd1-9f70-0ae95327d020  failsafe
initrd (hd0,9)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10 
root (hd0,7)
configfile /boot/grub/menu.lst

```


when i type ```
null (hd0,7)/boot/
``` i got the following

```
possbile files are : System.map-2.6.27-7-generic abi-2.6.27-7- config-2.6.27-7-generic memtest86+.bin vmcoreinfo-2.6.27-7-generic vmlinuz-2.6.27-7-generic grub initrd.img-2.6.27-7-generic
```

---

### Post by caljohnsmith on 2008-12-07
I think I might know what the problem is; it might be that the Grub version you have in Mandriva isn't as recent as the one you have in Ubuntu, so Mandriva's Grub is unable to use the new "uuid" notation that the Ubuntu Grub menu.lst uses. How about changing all the entries in your Ubuntu menu.lst to instead use "root (hd0,7)":
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]root            (hd0,7)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=14f729d9-1a4e-452a-87e1-853fab7a5289 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Give that a shot and let me know what happens.

---

### Post by sajixavier on 2008-12-07
\\:D/...Cheers caljohnsmith.......it is working now...as u said i replaced the uuid with root...now i am sending this message from ubuntu....


also i need some advice from you...

I have 1.5 gb ram (512 mb+ 1 gb)...so how much swap partition should i give for  ubuntu? 

also another question..i have nvdia 6200 graphic card..when i try to install the nvdia driver, it didn't install...

also about the internet connection ....i have dsl connection..in ubuntu it is bit slow...is there any configuration that i should do in configuring dsl connection...


Once again thanx...

---

### Post by caljohnsmith on 2008-12-07
> **sajixavier said:**
> 
also i need some advice from you...

I have 1.5 gb ram (512 mb+ 1 gb)...so how much swap partition should i give for  ubuntu? 

If you don't ever plan on using hibernation, then using 1.5 or 2 GB of swap should be adequate. If you want to use hibernation though, you should probably make swap 3 GB. 
> **sajixavier said:**
> 
also another question..i have nvdia 6200 graphic card..when i try to install the nvdia driver, it didn't install...

also about the internet connection ....i have dsl connection..in ubuntu it is bit slow...is there any configuration that i should do in configuring dsl connection...


Once again thanx...
I can't really help with your video or networking problems without getting more info from you; since those are entirely different problems than your Grub problem, I would recommend starting a new thread with each of those problems, and I'm sure you'll get lots of help. Be sure to include as much information as possible though so people can help you. Cheers and good luck. :)

---

### Post by bhadotia on 2008-12-07
> **caljohnsmith said:**
> If you don't ever plan on using hibernation, then using 1.5 or 2 GB of swap should be adequate. If you want to use hibernation though, you should probably make swap 3 GB. 

Even if you use hibernation you won't need more than 3/4 of ram size a swap.
But still to be on the safe side use a swap of 1.5 GB.

---

### Post by sajixavier on 2008-12-08
Thank you guys.

---

### Post by sajixavier on 2008-12-08
Also i need to add this..i didn't mentioned earlier...
as u know i installed ubuntu and mandriva...when i was using mandriva i was not able to access the ubuntu partition at first time...i used the mandriva 2009 live cd....it was saying access is denied..i was using kde4....then when i reinstalled the mandriva i was only able to see the ubuntu partition...i couldn't edit..when u said to me to edit the menu.lst file, actually i was not able to edit the file...i could open the file, but cann't save the file....

but when i install the mandriva 2009 one (two cds)...and gnome version i was able to access and edit the ubuntu partition...do you anything about this type of problem.....

---

### Post by caljohnsmith on 2008-12-08
> **sajixavier said:**
> Also i need to add this..i didn't mentioned earlier...
as u know i installed ubuntu and mandriva...when i was using mandriva i was not able to access the ubuntu partition at first time...i used the mandriva 2009 live cd....it was saying access is denied..i was using kde4....then when i reinstalled the mandriva i was only able to see the ubuntu partition...i couldn't edit..when u said to me to edit the menu.lst file, actually i was not able to edit the file...i could open the file, but cann't save the file....

but when i install the mandriva 2009 one (two cds)...and gnome version i was able to access and edit the ubuntu partition...do you anything about this type of problem.....
That all has to do with permissions problems; in Ubuntu, to do tasks that require root privileges, you can just use "sudo" in front of the command or "gksudo" if it is a GUI program. Then you shouldn't get any "access denied" errors. For instance, to open Ubuntu's file browser "nautilus" as root user, you could do:
```
gksudo nautilus &
```
And then you have the privilege to delete/modify any file or directory that you want to, so of course be careful. I'm not sure exactly how Mandriva handles permissions when mounting a partition, but I think that is what is causing you the problems about accessing the Ubuntu partition.

---

