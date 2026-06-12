---
title: "Another installation of Ubuntu on External Hard Drive..."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by hatorade on 2009-03-19
So I have been reading these forums for hours, as well as doing Google Searches, and I can't find an answer to my question that I can understand.

Background: I installed Ubuntu on my WD Passport external harddrive. Initially, my understanding is that I had GRUB installed on my main internal hard drive (when I booted windows, with the external plugged in, GRUB came up fine and asked me to choose between XP and Ubuntu. When I restarted the comp without the drive in, I got a GRUB error 21, which I think means it couldn't read the Ubuntu files it wanted from the external.).

At that point, I searched some forums, and came to here [http://ubuntuforums.org/showthread.php?p=6452340](http://ubuntuforums.org/showthread.php?p=6452340), which in essence told me I should do the following: 

```
first opening a terminal (Applications > Accessories > Terminal) and then doing:

[CODE]sudo grub
grub> find /boot/grub/stage1
```

The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:

```
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

Please post the output of all the above commands, then reboot, set your BIOS to boot the external Ubuntu drive, and you should get the Grub menu. If that works OK, you can also restore a Windows equivalent MBR to your Vista drive by doing:

```
sudo lilo -M  /dev/sda mbr
```[/CODE]

After the second step (grub> commands) I restarted,with the external drive plugged in, and everything worked. Not sure what this step actually did. Then I followed the last step, restarted, and now GRUB never shows up, with external plugged in or not. 

Does anyone know how I can get GRUB to come back up when I boot up, and have the solution to what I want to do. As many others, I want my computer to boot into Windows default when no external is plugged in, and when this external is plugged in I want GRUB to run. 

Another problem I am suspicious about is my computer's ability to boot from an external drive. I have Phoenix BIOS, and when it initially starts I chose to reorder where it should boot from. Currently, it's left bay (CD, I imagine), external device, and internal, and then some others, including USB stick. So I imagine external devices counts as the USB drive I'm trying to work with. However, when I press a different command during boot up, which lets me pick exactly which one of those options I want to boot from in that particular instance, external devices does not show up when the external drive is plugged in. 

When I have the BIOS set to boot up in this order, I have another problem when the external is plugged in. With all of the above happening too, when I boot up now, Windows defaults with no GRUB (as I mentioned). However, frequently, when I have the external with GRUB plugged in (this also happens with my iPod...) I get a quick blue screen of death (too fast to read) shortly after the windows XP load screen and my computer restarts. This makes me question my computer's ability to boot from a USB device.

Does anyone think they can help me? Again, what I want is my computer to boot windows when this external drive is not plugged in automatically, and when the drive is plugged in go into GRUB so I can pick.

Thank you so much for you help and I'm sorry if this has been posted before I couldn't find an example exactly like mine or close enough to help me.

---

### Post by hatorade on 2009-03-19
Can anyone help??

---

### Post by hatorade on 2009-03-21
any help??

---

