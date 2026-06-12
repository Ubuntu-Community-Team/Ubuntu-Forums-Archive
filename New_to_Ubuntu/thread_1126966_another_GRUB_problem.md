---
title: "another GRUB problem"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by rfbeck on 2009-04-15
For whatever reason I had to reinstall Ubuntu Ibex x64 8.0401. I did it on dual hard drives (one with WinXP). I followed the following procedure: 
"sudo grub
find /boot/grub/stage1

root (hd 0,0)
setup (hd0)"

Then I get a message basically saying "success".

Then I exit, reboot, and I get straight to WinXP. No GRUB. Very frustrating. Especially when I had GRUB setup on dual a boot system before and it was working. 
Should I say "setup (hd1) instead? I just don't want to hose my WinXP boot process.
Please help.

---

### Post by meierfra. on 2009-04-15
What happens if you change the boot order in the bios? (That is, set the bios to boot from the Ubuntu drive)

---

### Post by rfbeck on 2009-04-16
My BIOS won't let me do that.:( I can only change the boot order of CDROMS and such.

Also, I edited my post a bit. I don't get HD(0,1) I get HD 0,0).

I know they are on two separate drives because of the sudo fdisk -l
command, also. Weird. Why do I get HD (0,0)?

One drive is SDB and the other is SDA. Does this have anything to do with it?

---

### Post by meierfra. on 2009-04-16
> My BIOS won't let me do that. I can only change the boot order of CDROMS and such.


O.k Then you will have to install grub to  the MBR of the Windows drive.
(Don't worry, that won't hurt your Windows partition, and it is fairly easy to restore your original MBR if you ever need to)

Open a terminal in Ubuntu.

```
sudo grub
device (hd0) /dev/sdb
device (hd1) /dev/sda
root (hd1,0)
setup (hd0)
quit
```

you also need to edit menu.lst, so that you can boot into Windows:

```
gksudo gedit /boot/grub/menu.lst
```


Change your Windows item to

title Windows XP
root (hd0,0)
chainloader +1


This assume that XP is on /dev/sdb1. If XP is /dev/sdb2 use (hd0,1) and so on.   Make sure to remove the "map" lines.

Save the file and reboot. Hopefully you will get the Grub menu and are able to boot into both OSs from the Grub menu.



> I know they are on two separate drives because of the sudo fdisk -l
command, also. Weird. Why do I get HD (0,0) ?

Ubuntu   does not know the actually order of the hard drives in the bios.  So it orders the drives according to its own rules. Your Ubuntu drive must be /dev/sda and your Windows drive /dev/sdb.  Grub start counting at zero. So it labels the Ubuntu drive as (hd0). Ubuntu is the first partition on that drive so the Ubuntu partition is (hd0,0).

But grub (during boot up)  sees the drives  according to the order in the bios. So  the grub at boot up thinks Ubuntu is (hd1,0).  (this is the reason you have to use the "device" lines to install Grub

---

### Post by rfbeck on 2009-04-23
Meierfra,
I've been away for a while and I just now got a chance to try your method. One problem popped up. When I type in "setup (hd0)" I get "error 12 Invalid device requested". Everything works until that point. Any ideas? Thanks for your help so far!
______
Robert

---

### Post by meierfra. on 2009-04-23
> error 12 Invalid device requested". 

Strange.  Are you sure what you didn't have any typos?
Try again. 

If your still get "error 12" after "setup (hd0)", copy  the content of the whole terminal and post it here.
Also to get a clearer picture of your setup, download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by rfbeck on 2009-04-23
I realized what I did wrong. I forgot to type the "root" command. Sorry.
The good news is I now have my GRUB menu back! The bad news is when I select the Linux option I get the message "can not mount the selected partition". Please help. I''m excited to get my Ubuntu back. Thanks again.
______
Robert

---

### Post by alphacrucis2 on 2009-04-23
> **rfbeck said:**
> I realized what I did wrong. I forgot to type the "root" command. Sorry.
The good news is I now have my GRUB menu back! The bad news is when I select the Linux option I get the message "can not mount the selected partition". Please help. I''m excited to get my Ubuntu back. Thanks again.
______
Robert

Maybe you should change your menu.lst to use the UUID of the kernel's partition rather than messing with stuff like (hdx, y). The UUID of the partition will not change.

---

### Post by meierfra. on 2009-04-23
Sorry, I'm so used to UUIDs by  now that I forgot that Ubuntu 8.04.1 still uses "root"

Do this:

At the Grub menu at boot up, select Ubuntu. But do not press "enter", press "e" instead. At the new screen, press "e" again. Change

root (hd0,0)

to

root (hd1,0)

Press "enter" to go back to the previous screen, and then press "b" to boot.

Once you booted into Ubuntu, open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change

# groot=(hd0,0)

to

# groot=(hd1,0)

Save the file. Back in the terminal

```
sudo update-grub
```

and you should be all set.

---

### Post by rfbeck on 2009-04-23
Okay, so far so good, except for one small little detail. When I hit "e" and edit "root (hd0,0)" to "root (hd1,0)" it doesn't seem to save that edit. I have to do it every time. Is there any way to save it?
Once again, thanks.
______
Robert

---

### Post by meierfra. on 2009-04-23
> it doesn't seem to save that edit.
I know. That's why you have to   do the  the rest of the instruction from my previous post  (editing menu.lst and run "sudo update-grub")

---

### Post by rfbeck on 2009-04-24
Okay I figured it out. Thanks for all your help. You are a Ubuntu guru! You have been the only one that has been able to help me get my GRUB menu back!
Many thanks.
_______
Robert

---

### Post by mbzn on 2009-04-24
sorry! i was a bit late

---

### Post by meierfra. on 2009-04-24
> Okay I figured it out. 

Great. Have fun with  Ubuntu and XP.

---

