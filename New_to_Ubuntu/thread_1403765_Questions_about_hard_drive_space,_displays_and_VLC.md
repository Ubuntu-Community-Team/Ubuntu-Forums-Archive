---
title: "Questions about hard drive space, displays and VLC, and joystick support"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by rklpro on 2010-02-10
New to Linux... maybe you can help!

Okay, first issue.  I've been using Linux for about a week and downloading some tv and movies since my TV broke at home.  However, apparently I've run out of space.  It seems like there's a limit on how much stuff I can put into my home folder.  I think I'm capped at 40gb but my system has room for about 100gb more.  I'm not dual booting with windows-- Linux only machine now.  Is there a way to change this?  Is this even an error?

Next... I run a Samsung N120 netbook with a 10" display.  My 22" Acer external gave me some trouble at first but I eventually got the system to read my display with the correct resolution.  However, when I try to run VLC, you can see maybe five pixels of the program at the very top of the netbook screen, not the external monitor.  I can only run VLC properly with an 800x600 reso and mirrored screen images.  I've done a lot of research on the forums about this but couldn't find anything specific enough to my problem.

Lastly, I want to get a usb gamepad running so I can mostly play VBA and ZSNES.  I have a Logitech Cordless RumblePad 2... I could care less about the rumble function working properly-- I just want to use the controller.  Is there any replacement for the JSCalibrater I've read about?  Any other methods of getting this to work?  If not, does anyone know about gamepads that do work on this distro?

Thanks a lot for your help in advance.  Have a nice day!

---

### Post by AntonioPT on 2010-02-10
1 - Can you show me the output of ```
sudo fdisk -l
``` ?
3 - Try installing the QJoyPad or rejoystick packages from PlayDeb.net repository. Then configure the mapping (e.g: button 3 on joystick = up arrow) of the joystick.

---

### Post by rklpro on 2010-02-10
Command output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72ae165a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris


I will try one of the programs you listed.  

Thanks very much.  :)

---

### Post by AntonioPT on 2010-02-10
Show me the output of df, please.

(Thanks, I'm here to help :))

---

### Post by AntonioPT on 2010-02-10
And sudo tune2fs -l /dev/sda1 too, please... (sorry, I forgot)

---

### Post by rklpro on 2010-02-10
DF

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            150902080  36427528 106809140  26% /
udev                    508624       284    508340   1% /dev
none                    508624       804    507820   1% /dev/shm
none                    508624        88    508536   1% /var/run
none                    508624         0    508624   0% /var/lock
none                    508624         0    508624   0% /lib/init/rw


The other one

Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          c77883a2-ce9b-46ba-879f-e7a62243f424
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9584640
Block count:              38327065
Reserved block count:     1916353
Free blocks:              28618610
Free inodes:              9366311
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1014
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue Feb  2 00:20:07 2010
Last mount time:          Wed Feb 10 16:39:52 2010
Last write time:          Wed Feb 10 16:39:52 2010
Mount count:              19
Maximum mount count:      21
Last checked:             Tue Feb  2 00:20:07 2010
Check interval:           15552000 (6 months)
Next check after:         Sun Aug  1 01:20:07 2010
Lifetime writes:          30 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       86
Default directory hash:   half_md4
Directory Hash Seed:      9758e370-a25a-4310-ae8a-5211203ac67c
Journal backup:           inode block

---

### Post by AntonioPT on 2010-02-10
Sorry, but I don't know what's causing the 1st problem...

---

### Post by rklpro on 2010-02-10
Well, thanks for trying... About the gamepad question... seems my controller works with ZSNES well, maybe natively.  Won't read for VBA.  I downloaded rejoystick to try and combat this problem and I'm not sure if I'm mapping it correctly.  I'm just typing in the current keycode I've got specified in VBA.  Is this right?  And I do realize that this takes me way past being a simple newbie.  :)

---

### Post by kmsalex on 2010-02-10
if your using a paid servase to download the movies are you shour you have't hit the download limit. have you tryed creating a folder on your desktop and trying to save it there?

---

### Post by freebeer on 2010-02-10
I'm still a bit of a noob, but is it possible that his .Trash is taking up a lot of space - especially the root .Trash folder?  That one's not so apparent.

---

