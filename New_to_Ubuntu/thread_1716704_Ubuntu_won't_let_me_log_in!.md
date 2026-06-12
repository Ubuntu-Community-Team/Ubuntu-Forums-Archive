---
title: "Ubuntu won't let me log in!"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by ADeadCat on 2011-03-28
I'm currently running Ubuntu 10.10, and whenever I try to start up the computer, it boots fine, but it won't let me get past the login screen. All it does is display the username; it won't even show a password field. At this point though, all I really care about is recovering some files I have on the computer

---

### Post by matt_symes on 2011-03-28
Hi

You can recover your files using the LiveCD. Copy and paste them onto another hard drive or usb stick.

Another technique that should work is to boot into the command line by changing the boot options in grub. Login  in at the command line. Typing startx should then, hopefully, bypass gdm.

Your issues with gdm can be looked at after you have rescued your files ;)

Kind regards.

---

### Post by ADeadCat on 2011-03-28
And if I couldn't make a live CD? 
And I tried stopping gdm
sudo /etc/init.d/gdm stop
and manually restarting the x-server
startx
but then the usb ports don't work

---

### Post by matt_symes on 2011-03-28
Hi

> **ADeadCat said:**
> And if I couldn't make a live CD? 

Can you make a live usb ?

> 
And I tried stopping gdm
sudo /etc/init.d/gdm stop
and manually restarting the x-server
startx
*but then the usb ports don't work*

That's odd. I have just tested it on my machine and USB worked perfectly. I did it a slightly different way though.

I booted to the recovery console and started X that way. Be very careful if you use that method though.

If not, it may just be that you need to manually mount your USB but, as i said, i did not have that issue.

Kind regards

---

### Post by ADeadCat on 2011-03-28
I can't make one because I don't have access to a cd/usb with enough storage space. And I have a couple of questions for you: how do you boot into recovery mode, and how do you manually mount a usb?

---

### Post by matt_symes on 2011-03-28
Hi

> **ADeadCat said:**
> I can't make one because I don't have access to a cd/usb with enough storage space. 

That's a shame as it is the easiest way.

> And I have a couple of questions for you: how do you boot into recovery mode,

This is probably the safest method and does not use root access.

Reboot your PC. At the grub screen where you get to choose your kernel you want to boot into, press the **e** key.This  allows you to **e**dit  the kernel command line.

Look for the line that says some thing like (it may not be exactly the same)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash
```

and add the word **text** at the end (notice the word text added at the end)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash **text**
```

Press ctrl + x to continue booting.This will boot you into text mode. Enter your user name and password when instructed. Then type

```
startx
```

This  will start X without GDM. You might get some error about your keyring. Ignore them as you are only coping off your files.

> and how do you manually mount a usb?

Insert your USB device into a port. If it's not automounted open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Enter your password. It will not be echoed to the screen. This is normal.

This will list your connected devices. Find your USB device and then mount it. In this case, i am going to assume it's sdb1

```
sudo mkdir /media/key
sudo mount /dev/sdb1 /media/key
```

Copy your files across. When finished unmount the device.

```
sudo umount /media/key
```

If your still not sure how to mount your usb device post the output of

```
sudo fdisk -l
```

when your USB device is plugged in. Then either i or someone else will tell you the command you need.

Kind regards

---

### Post by ADeadCat on 2011-03-28
It all works fine until ```
mkdir /media/key
```
All it says is: ```
mkdir: cannot create directory `media/key': Permission denied
```

---

### Post by matt_symes on 2011-03-28
Hi

> **ADeadCat said:**
> It all works fine until ```
mkdir /media/key
```
All it says is: ```
mkdir: cannot create directory `media/key': Permission denied
```

My type on my earlier post. I will amend it now.

You need to use sudo in front of all those commands

```
sudo mkdir /media/key
sudo mount ...
```

Enter your passwork when asked.It will not be echoed to the screen. This is normal.

Don't forget to unmount after you have copied the files.

```
sudo umount /media/key
```

Kind regards

---

### Post by ADeadCat on 2011-03-28
Now it won't let me move any files to it; it says that I don't have permission. Any suggestions?

---

### Post by matt_symes on 2011-03-28
Hi

Try changing ownership of the mount point.

```
sudo chown <your_user_name>:<your_user_name> /media/key
```

Change <your_user_name> to be, well, your username. As an example mine would be

```
sudo chown matthew:matthew /media/key
```

Kind regards

---

### Post by ADeadCat on 2011-03-28
When I try that, it just comes up with
```
chown: changing ownership of `/media/key': Operation not permitted
```

---

### Post by ADeadCat on 2011-03-28
It says that it belongs to root

---

### Post by matt_symes on 2011-03-28
Hi

What exactly did you type ? Post the entire line you entered.

Is the USB device still mounted ? What file system is on the usb stick?

Kind regards

---

### Post by ADeadCat on 2011-03-28
```
sudo chown walker:walker /media/key
```
And yes, the usb device is still mounted

---

### Post by ADeadCat on 2011-03-28
"File system type: msdos"

---

### Post by matt_symes on 2011-03-28
Hi

> **ADeadCat said:**
> ```
sudo chown walker:walker /media/key
```
And yes, the usb device is still mounted

That looks alright to me. Try unmounting the USB device and trying again.

```
sudo umount /media/key
sudo chown walker:walker /media/key
sudo mount ....
```

Have a quick read through this

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Read the section of manually mounting devices. It might be a case of using permissions when mounting the device.

BTW: Did you boot into the command line and type startx ?

Kind regards

---

### Post by iiiears on 2011-03-28
gksudo nautilus 

 ((Gnome Kit) graphical super user do, Manages permissions and .lock-foo* files best with nautilus and other graphical applications.)

sudo -s nautilus 

(may work but it presents a few risks to .lock files and owner permissions, etc.)

---

### Post by matt_symes on 2011-03-29
Hi

> **iiiears said:**
> gksudo nautilus 

 ((Gnome Kit) graphical super user do, Manages permissions and .lock-foo* files best with nautilus and other graphical applications.)

sudo -s nautilus 

(may work but it presents a few risks to .lock files and owner permissions, etc.)

Yes. Good idea. I was going to suggest that method if we can't get the mount point and permissions working correctly. We should not need to do that though.

Kind regards

---

### Post by ADeadCat on 2011-03-29
Thank you so much for all your help, it finally worked!:)

---

### Post by d3v1150m471c on 2011-03-29
if your end goal is only to recover files then boot, hold shift till you get your grub menu and then open a root shell. insert a media device, if it doesn't mount...mount it. then cp (copy) your files to the device. done and done.

---

### Post by matt_symes on 2011-03-29
Hi

> Thank you so much for all your help, it finally worked!

Did you want help trying to fix your login screen.

> if your end goal is only to recover files then boot, hold shift till you get your grub menu and then open a root shell. insert a media device, if it doesn't mount...mount it. then cp (copy) your files to the device. done and done.

I totally agree. It's what i would have done. However, my aim was to try to keep away from the terminal. It's only after auto mounting was not working in  X that we had to resort to the terminal.

Kind regards

---

