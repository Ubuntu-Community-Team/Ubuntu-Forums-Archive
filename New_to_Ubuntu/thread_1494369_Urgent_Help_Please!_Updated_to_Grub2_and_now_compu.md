---
title: "Urgent Help Please! Updated to Grub2 and now computer won't boot"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Takkak on 2010-05-26
Hi. I followed the instructions here : [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) to upgrade my 10.04's Grub 1.5 to Grub2. Now when I turn on my computer, Grub doesn't load and only a black screen is shown. Once in a while the computer automatically reboots in the black screen.
 
Any help is appreciated, I have important files in that computer.

---

### Post by Takkak on 2010-05-26
Also: the power button on my computer no longer works.

---

### Post by Ozymandias_117 on 2010-05-26
Why did your installation have Grub Legacy to start with? 10.04 defaults to Grub 2.

Unless you have a strange setup, I would try using this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Darkness Des on 2010-05-26
I don't know why you updated, everytime I update GRUB something similar to that happens. I ended up with Grub2 anyways, it came as a part of 10.04 (clean install, after my previous Grub broke just like yours). What you can do is boot up into a LiveCD. Install Testdisk. Run that, and restore the boot sector of your Linux installation. That will revert you back to GRUB 1.5, then I suggest you keep it at that. If you REALLY need Grub2, then make a backup before you try upgrading.

---

### Post by Ozymandias_117 on 2010-05-26
> **Takkak said:**
> Also: the power button on my computer no longer works.

That would be a hardware problem separate from Ubuntu. The usual things to check first, is it plugged in, is there a problem with the power cord, is there a problem with the outlet, do you have a switch on the power supply that is off, do you have a broken surge protector between the computer and the outlet.

---

### Post by Windows Nerd on 2010-05-26
You have to re-install Grub via a live CD. It looks like [this]("http://ubuntuforums.org/showthread.php?t=1306900") user had the same problem you did. Go have a look, someone explained quite nicely how to do it better than I ever could.

Scott

Edit: If your power button doesn't work...there might be a hardware problem. Does your computer load past the BIOS?

---

### Post by Takkak on 2010-05-26
> **Ozymandias_117 said:**
> Why did your installation have Grub Legacy to start with? 10.04 defaults to Grub 2.
 
Unless you have a strange setup, I would try using this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
 
I haven't had a fresh install since 9.04 , which is why I have Grub Legacy.
 
 
Thanks for the replies, I'll see if it works

---

### Post by Takkak on 2010-05-26
Would I reinstall Grub Legacy or Grub2 with the Live CD ?

---

### Post by Takkak on 2010-05-26
> **Windows Nerd said:**
> You have to re-install Grub via a live CD. It looks like [this]("http://ubuntuforums.org/showthread.php?t=1306900") user had the same problem you did. Go have a look, someone explained quite nicely how to do it better than I ever could.
 
Scott
 
Edit: If your power button doesn't work...there might be a hardware problem. Does your computer load past the BIOS?
 
 
It loads past the BIOS, then a black screen shows up. * then the power button stops working.

---

### Post by Takkak on 2010-05-26
> **Darkness Des said:**
> I don't know why you updated, everytime I update GRUB something similar to that happens. I ended up with Grub2 anyways, it came as a part of 10.04 (clean install, after my previous Grub broke just like yours). What you can do is boot up into a LiveCD. Install Testdisk. Run that, and restore the boot sector of your Linux installation. That will revert you back to GRUB 1.5, then I suggest you keep it at that. If you REALLY need Grub2, then make a backup before you try upgrading.
 
 
Could you explain how to restore the boot sector to me please?

---

### Post by Ozymandias_117 on 2010-05-26
How far through the upgrade to Grub 2 did you get?  You would have to hold the power button for 5-10 seconds at that point, are you saying it didn't turn off after holding it in?

---

### Post by Takkak on 2010-05-26
I *finished the upgrade (I believe ..) It works for powering on, and *it turns off after holding the button for ~10 seconds.
 
 
Would the Jaunty Live CD work for this purpose ?

---

### Post by Ozymandias_117 on 2010-05-26
Do you have multiple hard drives? Is it possible you wrote the MBR to the wrong one?

---

### Post by Takkak on 2010-05-26
Actually .. I may have
 
I'm pretty computer-illiterate .. when exactly did I write the MBR ?
 
When I did the 'sudo upgrade-from-grub-legacy' there were 4 options , I picked the one with the most MB in it .

---

### Post by Ozymandias_117 on 2010-05-26
Sounds like you probably wrote to the wrong MBR... Try going into your BIOS and changing the boot order of your hard drives around.

It should display the key to enter BIOS very soon after pressing the power button. I'd say it's usually Delete or f12.

Look for something about "Boot Order" and then go into Hard drives and change them around.

There may be an option for a 1-time boot menu so you can just try the different hard drives to figure out which one it is.

---

### Post by Takkak on 2010-05-26
Can't find boot order ..
 
Thanks for all the help. I'll try some of those other methods with the live CD.

---

### Post by Ozymandias_117 on 2010-05-26
If you're trying that, you'll need a 10.04 CD.

---

### Post by Takkak on 2010-05-26
This computer has no memory left .. I tried to download it but this computer is bloated .
 
 
If worst comes to worst , would copying everything to a External Hard Drive through the Live CD work? Say, 25GB? Would it take .. days ?
 
I feel like such an idiot for attempting to upgrade Grub ..

---

### Post by Ozymandias_117 on 2010-05-26
It shouldn't take too long to copy 25 gigs. If you try to update it again, I would suggest writing the MBR to all drives; it won't hurt anything, and it could save you some frustration :D.

---

### Post by Takkak on 2010-05-26
Wow, a whole day wasted trying to upgrade Grub .. Thanks for all the help again . Attempting to download the 10.04 Live CD and burning it with .. the 9.04 Live CD . What would be the most efficient way to restore Grub with the Live CD ?

---

### Post by Ozymandias_117 on 2010-05-26
Edit: I mean after you get the 10.04 downloaded, burnt and boot to it.

Mount all your hard drives in the liveCD and post the results of ```
sudo fdisk -l
``` (That is a lower case L, not the number 1)

---

### Post by Takkak on 2010-05-26
Wow, this is terrible. I'm trying to download the ISO file to my Hard Drive but Firefox just won't listen.
 
Also
 
```
ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37c937c8
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 19272 154802308+ 83 Linux
/dev/sda2 19273 19457 1486012+ 5 Extended
/dev/sda5 19273 19457 1485981 82 Linux swap / Solaris
```
 
(That's Jaunty, because atm I can't get Lucid downloaded before I do some cleaning up on my Windows)

---

### Post by Ozymandias_117 on 2010-05-27
Um... I'm completely confused now... From what you've said upgrade-from-grub-legacy showed 4 hard drives, but fdisk -l only shows one...

---

### Post by Takkak on 2010-05-27
Shat ..
 
I wasn't really paying attention when I was upgrading

EDIT: Or I don't know how to read partitions

---

### Post by kansasnoob on 2010-05-27
I've been working on a HowTo for recovering any Ubuntu or Windows mbr with any Ubuntu Live CD:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

NOTE: pay attention only to that post, NOT the HowTo I added it to :) I just stuck it there until I have time to polish it up a bit.

Anyway, see if you can work through that with your 9.04 CD. In your case you want to mount and chroot /dev/sda1.

I'll try and check back here when time allows to see how well you could understand that.

---

### Post by Takkak on 2010-05-27
```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Output:
```
grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
New: yes
Package: grub-common
State: installed
Package: os-prober
State: installed
```

Looks like I have Grub2 installed, right?

But then when I do the next step
```
grub-install /dev/sda1
```

An error comes up ..

```
root@ubuntu:/# grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```

What to do now ?

---

### Post by oldfred on 2010-05-27
No you do not want to install to the partition sda1 but to the MBR of sda. Remove 1 from sda[COLOR=Red]1[/COLOR]

grub-install /dev/sda

kansasnoob instructions said sdX where X is the drive. that is a in your case not a1.

---

### Post by Takkak on 2010-05-27
Ok, I think I made a horrible mistake then 
 
Is it possible that I installed Grub2 on sda1 instead of sda, and that is why Grub2 isn't loading ?

Eg.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37c937c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris
```

 
Before the crash, when I did:
```
sudo upgrade-from-grub-legacy
```I believe I chose /dev/sda1 , I'm not too sure though
 
 
I installed grub2 with grub-install /dev/sda , rebooted , and it still doesn't work .
 
Thanks in advance.

---

### Post by Ozymandias_117 on 2010-05-27
> **Takkak said:**
> Is it possible that I installed Grub2 on sda1 instead of sda, and that is why Grub2 isn't loading ?


No, the upgrade command doesn't let you install GRUB to a partition.

Try:
```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda1 /mnt/root
sudo grub-install --root-directory=/mnt/root /dev/sda
```

---

### Post by Takkak on 2010-05-27
Thanks so much!
 
Grub loaded during boot .. but .. its the:
 
 
 
GNU GRUB version 1.98-1ubuntu6
 
Minimal BASH-like line editing is supported .. etc.
 
 
[COLOR=black]What to do now ?[/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]EDIT:[/COLOR]
[COLOR=black]I looked around online, and saw [/COLOR]
[COLOR=black]```
[/COLOR][COLOR=white][FONT=Bitstream Vera Sans Mono][B][COLOR=black]grub> linux  (hd0,1)/vmlinuz root=/dev/sda1
[/COLOR][/B][/FONT][/COLOR][COLOR=black][COLOR=white][FONT=Bitstream Vera Sans Mono][B][COLOR=black]grub> initrd  (hd0,1)/initrd.img[/COLOR]
[/B][/FONT][/COLOR][/COLOR][COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=black]grub> boot
```[/COLOR]**[/FONT][/COLOR]
[COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=#000000][/COLOR]**[/FONT][/COLOR] 
[COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=#000000]Would that boot my computer or further my problems ?[/COLOR]**[/FONT][/COLOR]

---

### Post by Ozymandias_117 on 2010-05-27
> **Takkak said:**
> Thanks so much!
 
Grub loaded during boot .. but .. its the:
 
 
 
GNU GRUB version 1.98-1ubuntu6
 
Minimal BASH-like line editing is supported .. etc.
 
 
[COLOR=black]What to do now ?[/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]EDIT:[/COLOR]
[COLOR=black]I looked around online, and saw [/COLOR]
[COLOR=black]```
[/COLOR][COLOR=white][FONT=Bitstream Vera Sans Mono][B][COLOR=black]grub> linux  (hd0,1)/vmlinuz root=/dev/sda1
[/COLOR][/B][/FONT][/COLOR][COLOR=black][COLOR=white][FONT=Bitstream Vera Sans Mono][B][COLOR=black]grub> initrd  (hd0,1)/initrd.img[/COLOR]
[/B][/FONT][/COLOR][/COLOR][COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=black]grub> boot
```[/COLOR]**[/FONT][/COLOR]
[COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=#000000][/COLOR]**[/FONT][/COLOR] 
[COLOR=white][FONT=Bitstream Vera Sans Mono]**[COLOR=#000000]Would that boot my computer or further my problems ?[/COLOR]**[/FONT][/COLOR]

That means you never finished upgrading to grub 2. You still had grub legacy installed.

Do you want to try to get it upgraded to grub 2 or just use your old disk to fix grub legacy?

---

### Post by Takkak on 2010-05-27
I'll .. try to upgrade it to grub2 .. so it doesn't seem like I wasted all this time ..
 
Also, I got Lucid burned to a CD and am running it right now instead of Jaunty, if that makes a difference.

---

### Post by Ozymandias_117 on 2010-05-27
```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda1 /mnt/root
sudo mount --bind /dev /mnt/root/dev
sudo mount --bind /proc /mnt/root/proc
sudo chroot /mnt/root

sudo aptitude install grub-pc

(If this doesn't install anything, use sudo aptitude reinstall grub-pc )

Hit Ok
Hit Ok

sudo upgrade-from-grub-legacy

Make sure you select all possibilities here. (Press space bar to select, press tab to get to OK and press enter)

Then, just to be certain.

grub-install --recheck /dev/sda
 (If this throws off errors, post them)

sudo update-grub
```

Then reboot

---

### Post by oldfred on 2010-05-27
Grub 1.98 is the most current version of grub2, grub2 is the name more than the version as it is the second major version of grub.

If you can use the commands to manual boot that would be great but then you need to reinstall from inside your running Ubuntu and run 
sudo update-grub

Once booted you can just run this to reinstall and update grub as it uses the partition you are running from or you do not have to mount a partition as it knows where it is.
sudo grub-install /dev/sda
sudo update-grub

Sometimes this does a little more, accept first screens and choose sda as location to install to:
sudo dpkg-reconfigure grub-pc

---

### Post by Takkak on 2010-05-27
```
root@ubuntu:/# sudo mkdir /mnt/root
mkdir: cannot create directory `/mnt/root': File exists
root@ubuntu:/# sudo mount -t ext4 /dev/sda1 /mnt/root
mount: /dev/sda1 already mounted or /mnt/root busy
mount: according to mtab, /dev/sda1 is mounted on /
root@ubuntu:/# sudo mount --bind /dev /mnt/root/dev
mount: mount point /mnt/root/dev does not exist
root@ubuntu:/# sudo mount --bind /proc /mnt/root/proc
mount: mount point /mnt/root/proc does not exist
root@ubuntu:/# sudo chroot /mnt/root
chroot: cannot run command `/bin/bash': No such file or directory
```

Do I proceed ?

---

### Post by Ozymandias_117 on 2010-05-27
> **Takkak said:**
> ```
root@ubuntu:/# sudo mkdir /mnt/root
mkdir: cannot create directory `/mnt/root': File exists
root@ubuntu:/# sudo mount -t ext4 /dev/sda1 /mnt/root
mount: /dev/sda1 already mounted or /mnt/root busy
mount: according to mtab, /dev/sda1 is mounted on /
root@ubuntu:/# sudo mount --bind /dev /mnt/root/dev
mount: mount point /mnt/root/dev does not exist
root@ubuntu:/# sudo mount --bind /proc /mnt/root/proc
mount: mount point /mnt/root/proc does not exist
root@ubuntu:/# sudo chroot /mnt/root
chroot: cannot run command `/bin/bash': No such file or directory
```

Do I proceed ?

Er... What does ```
ls /mnt/root
``` show?

---

### Post by Takkak on 2010-05-28
```
root@ubuntu:/# ls /mnt/root
boot
```

---

### Post by Takkak on 2010-05-28
> **oldfred said:**
> Grub 1.98 is the most current version of grub2,  grub2 is the name more than the version as it is the second major  version of grub.

If you can use the commands to manual boot that would be great but then  you need to reinstall from inside your running Ubuntu and run 
sudo update-grub

Once booted you can just run this to reinstall and update grub as it  uses the partition you are running from or you do not have to mount a  partition as it knows where it is.
sudo grub-install /dev/sda
sudo update-grub

Sometimes this does a little more, accept first screens and choose sda  as location to install to:
sudo dpkg-reconfigure grub-pc

```
root@ubuntu:/# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```

---

### Post by Ozymandias_117 on 2010-05-28
Reboot so you start from scratch, then go back to post #33

---

### Post by Takkak on 2010-05-28
When I did:
```
sudo aptitude reinstall grub-pc
```

It eventually led me to:
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                 &#9474; GRUB install devices:                      &#9474; 
                 &#9474;                                            &#9474; 
                 &#9474;    
[*] /dev/sda (160041 MB, ST3160812AS)   &#9474; 
                 &#9474;    
[*] - /dev/sda1 (158517 MB)             &#9474; 
                 &#9474;    
[*] - /dev/sda2 (0 MB)                  &#9474; 
                 &#9474;    
[*] - /dev/sda5 (1521 MB)               &#9474; 
                 &#9474;                                            &#9474; 
                 &#9474;                                            &#9474; 
                 &#9474;                   <Ok>                     &#9474; 
                 &#9474;                                

I chose all of them, clicked OK, then it led me to :
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; GRUB failed to install to the following devices:                          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; /dev/sda /dev/sda1 /dev/sda2 /dev/sda5                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Do you want to continue anyway?  If you do, your computer may not start   &#9474; 
 &#9474; up properly.                                                              &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; GRUB installation failed.  Continue?                                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Yes>                       <No>

---

### Post by Ozymandias_117 on 2010-05-28
Try installing on only /dev/sda and /dev/sda1

---

### Post by Takkak on 2010-05-28
```
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```


That's what shows up every time I do 'sudo update-grub'

Is that bad?

---

### Post by Ozymandias_117 on 2010-05-28
> **Takkak said:**
> ```
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```


That's what shows up every time I do 'sudo update-grub'

Is that bad?

If you're still in chroot post ```
 cat /boot/grub/grub.cfg
``` if you aren't ```
 cat /mnt/root/boot/grub/grub.cfg
```

---

### Post by Takkak on 2010-05-28
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2da5ed0c-e711-4240-b385-ec00d8fba851 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2da5ed0c-e711-4240-b385-ec00d8fba851 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2da5ed0c-e711-4240-b385-ec00d8fba851
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Cannot find list of partitions!
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Takkak on 2010-05-28
OH IT BOOTED !
 
I'm not quite sure what fixed it though ..
 
Thanks for all the help ! Scanning my drives for errors now.
 
I'll probably end up backing up all my files and having a fresh install now.



Also: Are there any commands I can use to ensure it will stay this way ?

---

### Post by Ozymandias_117 on 2010-05-28
> **Takkak said:**
> OH IT BOOTED !
 
I'm not quite sure what fixed it though ..
 
Thanks for all the help ! Scanning my drives for errors now.
 
I'll probably end up backing up all my files and having a fresh install now.



Also: Are there any commands I can use to ensure it will stay this way ?

Sorry I had to leave last night so close to the end. Yeah, looking at your grub.cfg everything looks fine, so I'd say you're good.

---

### Post by Takkak on 2010-05-29
Thanks so much !

---

