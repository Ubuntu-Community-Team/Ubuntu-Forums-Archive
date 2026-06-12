---
title: "possible to triple boot??"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by maldonw on 2010-04-28
Hello all
I have a question I had my pc with 2 OS systems vista and fedora. I just install ubuntu on another partiton I made with the assumption that when the pc booted I would have the choice of the 3. Call it a newbie mistake but that assumption was wrong. I can see only ubuntu and vista not fedora. Is there a fix for this so that I can choos from all 3.

dont know if this helps but here is what i get from the blkid command
[COLOR=Red]/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="748888D7888898EE" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="421bb4fb-4849-4f84-9500-2ffa6323b200" TYPE="ext4" 
/dev/sda5: UUID="XE9LSD-xGNl-paqR-ZkHt-HoCi-uGHy-i3P463" TYPE="LVM2_member" 
/dev/sda6: UUID="8fc80104-f559-49d5-8a99-7cef50108e32" TYPE="ext4" 
/dev/sda7: UUID="bfebe264-12a0-40ae-85f4-b595ea40124e" TYPE="swap"

[COLOR=Black]my best guess is that sda5 or sda3 are for fedora but i could be wrong[/COLOR]
[/COLOR]

---

### Post by limey_rick on 2010-04-28
Which version of Ubuntu did you install? Fedora is definitely on /dev/sda5 as Fedora uses a LVM setup so it is probably on /dev/sda3 as you say.  

When you boot into Ubuntu, have you tried to run:

> sudo update-grub

This should find your fedora installation and add it to the GRUB boot menu. If you tried this already, did GRUB not find this installation?

---

### Post by P4man on 2010-04-28
Its certainly possible, and I would expect grub2 to see fedora and add it to the menu as well. Hardly a noob mistake, more like a bug (assuming you didnt wipe the fedora partition while installing ubuntu).

What happens when you run

```
sudo os-prober
```

---

### Post by maldonw on 2010-04-28
to answer both posts:
when i did sudo grub-update i got the following and i restarted to check and it didnt work.

wilfredo@wilfredo-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

as far as the other post this is the output i got after i ran sudo os-prober

wilfredo@wilfredo-laptop:~$ sudo os-prober
[sudo] password for wilfredo: 
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows Vista (loader):Windows1:chain

---

### Post by oldfred on 2010-04-28
some links to related issues:

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

[http://ubuntuforums.org/showthread.php?t=1367305](http://ubuntuforums.org/showthread.php?t=1367305)
If the linux has no bootloader, the os-prober will look for the kernel file name that starts with vmlinu[zx] and the initrd file name that starts with initrd.

See Kansasnoob comments 40 & 42 Install grub 1.98  & to fix major grub issues
here was a BIOS option setting in the boot loader device selection in the Fedora installer. Comment #44
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

---

### Post by maldonw on 2010-04-28
> **limey_rick said:**
> Which version of Ubuntu did you install? Fedora is definitely on /dev/sda5 as Fedora uses a LVM setup so it is probably on /dev/sda3 as you say.  

When you boot into Ubuntu, have you tried to run:

> sudo update-grub

This should find your fedora installation and add it to the GRUB boot menu. If you tried this already, did GRUB not find this installation?
to answer you question I am using the latest ubuntu 9.10
and no grub did not find fedora

---

### Post by xumuk37 on 2010-04-28
Add this at /boot/grub/grub.cfg

menuentry "Fedora (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,1)' #boot partition UUID here
	search --no-floppy --fs-uuid --set home_uuid_here
	linux /[COLOR="Red"]vmlinuz26[/COLOR] root=/dev/sda3 ro  
	initrd /[COLOR="red"]kernel26.img[/COLOR]
}

 if you paste your
```
ls /boot
```
 here I'll give you the grub entry all done

And answering your question: Yes, it's possible... by the way I have tree OS's on my lap: Arch, Ubuntu and Win7

---

### Post by P4man on 2010-04-28
> **xumuk37 said:**
> Add this at /boot/grub/grub.cfg

Would be worth testing for sure, but any changes to grub.cfg will be lost the next time grub is updated. Long live grub2. You should add those lines somewhere else and run grub-update, but I dont know by heart.

---

### Post by maldonw on 2010-04-28
> **xumuk37 said:**
> Add this at /boot/grub/grub.cfg

menuentry "Fedora (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,1)' #boot partition UUID here
    search --no-floppy --fs-uuid --set home_uuid_here
    linux /[COLOR=Red]vmlinuz26[/COLOR] root=/dev/sda3 ro  
    initrd /[COLOR=red]kernel26.img[/COLOR]
}

 if you paste your
```
ls /boot
``` here I'll give you the grub entry all done

And answering your question: Yes, it's possible... by the way I have tree OS's on my lap: Arch, Ubuntu and Win7
is this the code you asked for ?

[COLOR=Red]wilfredo@wilfredo-laptop:~$ ls /boot
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-21-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-21-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-21-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic[/COLOR]

[COLOR=Black]also another noob question how do it edit grub.cfg?  thanks[/COLOR]

---

### Post by xumuk37 on 2010-04-28
P4man, this was for try... for do it permanent you have to create similar in /etc/grub.d

maldonw, better do ls -l /boot  ... I don't see the Fedora kernel image over there...

---

### Post by maldonw on 2010-04-28
> **xumuk37 said:**
> P4man, this was for try... for do it permanent you have to create similar in /etc/grub.d

maldonw, better do ls -l /boot  ... I don't see the Fedora kernel image over there...
here you go

wilfredo@wilfredo-laptop:~$ ls -l /boot
total 27420
-rw-r--r-- 1 root root  629174 2009-10-16 14:03 abi-2.6.31-14-generic
-rw-r--r-- 1 root root  629853 2010-03-24 07:31 abi-2.6.31-21-generic
-rw-r--r-- 1 root root  111371 2009-10-16 14:03 config-2.6.31-14-generic
-rw-r--r-- 1 root root  111349 2010-03-24 07:31 config-2.6.31-21-generic
drwxr-xr-x 2 root root    4096 2010-04-28 16:30 grub
-rw-r--r-- 1 root root 7650183 2010-04-28 15:23 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root 7656595 2010-04-28 15:51 initrd.img-2.6.31-21-generic
-rw-r--r-- 1 root root  128796 2009-10-23 12:11 memtest86+.bin
-rw-r--r-- 1 root root 1664737 2009-10-16 14:03 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root 1668296 2010-03-24 07:31 System.map-2.6.31-21-generic
-rw-r--r-- 1 root root    1196 2009-10-16 14:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root    1196 2010-03-24 07:33 vmcoreinfo-2.6.31-21-generic
-rw-r--r-- 1 root root 3890400 2009-10-16 14:03 vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root 3901472 2010-03-24 07:31 vmlinuz-2.6.31-21-generic

---

### Post by xumuk37 on 2010-04-28
sorry, man, I forgot to ask you for you also post your /boot/grub/grub.cfg

---

### Post by maldonw on 2010-04-28
> **xumuk37 said:**
> sorry, man, I forgot to ask you for you also post your /boot/grub/grub.cfg


hope this is what your looking for 

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 8fc80104-f559-49d5-8a99-7cef50108e32
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8fc80104-f559-49d5-8a99-7cef50108e32
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=8fc80104-f559-49d5-8a99-7cef50108e32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8fc80104-f559-49d5-8a99-7cef50108e32
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=8fc80104-f559-49d5-8a99-7cef50108e32 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8fc80104-f559-49d5-8a99-7cef50108e32
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8fc80104-f559-49d5-8a99-7cef50108e32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8fc80104-f559-49d5-8a99-7cef50108e32
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8fc80104-f559-49d5-8a99-7cef50108e32 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 20378f114179a3dd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 748888d7888898ee
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by P4man on 2010-04-28
> I don't see the Fedora kernel image over there...

these would be on the fedora partition; wouldnt they? unless the OP has a boot partition; but then ubuntu is not using that.

---

### Post by xumuk37 on 2010-04-28
P4man,you're right... so, maldonw, give me ls -l /boot of fedora partition XD .. and for future installations: it's better create a separate /boot partition)

---

### Post by maldonw on 2010-04-28
> **xumuk37 said:**
> P4man,you're right... so, maldonw, give me ls -l /boot of fedora partition XD
how would I find that ? if you mean I have to get into fedora thats the problem i cant. unless i am misunderstanding you

---

### Post by xumuk37 on 2010-04-28
```
sudo mkdir /fedora
sudo mount /dev/sda? /fedora
```

---

### Post by oldfred on 2010-04-28
You should be able to mount your fedora from your Ubuntu.

Bot this will show your entire system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by cuberts on 2010-04-28
> **maldonw said:**
> Hello all
I have a question I had my pc with 2 OS systems vista and fedora. I just install ubuntu on another partiton I made with the assumption that when the pc booted I would have the choice of the 3. Call it a newbie mistake but that assumption was wrong. I can see only ubuntu and vista not fedora. Is there a fix for this so that I can choos from all 3.

dont know if this helps but here is what i get from the blkid command
[COLOR=Red]/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="748888D7888898EE" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="421bb4fb-4849-4f84-9500-2ffa6323b200" TYPE="ext4" 
/dev/sda5: UUID="XE9LSD-xGNl-paqR-ZkHt-HoCi-uGHy-i3P463" TYPE="LVM2_member" 
/dev/sda6: UUID="8fc80104-f559-49d5-8a99-7cef50108e32" TYPE="ext4" 
/dev/sda7: UUID="bfebe264-12a0-40ae-85f4-b595ea40124e" TYPE="swap"

[COLOR=Black]my best guess is that sda5 or sda3 are for fedora but i could be wrong[/COLOR]
[/COLOR]
of course it is possible, and its just that it will add one more booting choice on the GRUB menu.

---

### Post by xumuk37 on 2010-04-28
OP, did you solve it yet?

if not ```
sudo find / -name *boot*|grep grub
```

---

### Post by xumuk37 on 2010-04-28
bump

---

### Post by maldonw on 2010-04-29
> **xumuk37 said:**
> bump
  sorry i hard to go to work and didnt have time to try yesterday. however becuase i had an issue with windows i had to burn an image of my hard drive that just had vista and fedora so I started a fresh install of ubuntu in an newly created partition. This created a bit of a different problem. grub now sees all 3 OS's however when i try to boot fedora I get the following error : [COLOR=Red]you must load kernel first[/COLOR] [COLOR=Black]it then kicks me back to the grub page to choose another OS[/COLOR].  I loaded ubuntu and did a sudo blkid and got this 

[COLOR=Red]wilfredo@wilfredo-laptop:~$ sudo blkid
[sudo] password for wilfredo: 
/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="b8ebdef5-19a0-4a0e-b37c-d87928281842" TYPE="ext4" 
/dev/sda3: LABEL="Fedora-12-i686-L" UUID="c89d7967-25aa-44e0-8ecd-6d21e57d6797" TYPE="ext4" 
/dev/sda5: UUID="a91f19e1-b82c-4a9e-b49b-9cced833c1cf" TYPE="ext4" 
/dev/sda6: UUID="1db22484-abdd-440c-912b-b859ef12ea87" TYPE="swap" 
wilfredo@wilfredo-laptop:~$ 
[/COLOR]
any ideas??

---

