---
title: "Backing Up... without an OS or any software"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Old Newville on 2010-07-28
Maybe I'm Don Quixote here, but my system is fried leaving me with a Live CD and a Command Line. Neither is proving to be very helpful to me. My mission impossible is to retrieve my poor files from the hard disk with the fried OS so I can erase it and do a clean install.

Good news -- I have a backup internal hard disk. So I have 2 hard drives of 160 GB.

Bad News -- My Ubuntu 10.04 has fallen to the "Gnome Power Manager" default configuration error. I can only boot into a command line. No OS, no desktop. Nothing.

I have to figure out how to get my files (mainly the Home directory) off HD 1 and onto HD 2, so I can erase HD 1 and reinstall Lucid. I can't do this from the Live CD because it doesn't have correct permissions and chmod at the command line was bashed. (I must have entered it incorrectly although I took it straight from Ubuntu Documentation.)

Any suggestions? I don't have time to do any fiddling because the end of the month is approaching! My wife and I use the computer for work. We depend on Ubuntu. I promised her the computer would be running by 7/29 (tomorrow).

---

### Post by Sir Jasper on 2010-07-28
Hi,

As it's a business and a small amount of money (approx €40 less tax relief)) may be of insignificant consequence - google hdclone.

My regards

---

### Post by oldos2er on 2010-07-28
"I can only boot into a command line. No OS, no desktop. Nothing."

Does this mean you only get a grub> prompt? 

"I have to figure out how to get my files (mainly the Home directory) off HD 1 and onto HD 2, so I can erase HD 1 and reinstall Lucid. I can't do this from the Live CD because it doesn't have correct permissions"

How exactly are you trying to get your files (with the LiveCD?) You should be able to mount your internal hard disks by running```
sudo mkdir /media/disk1
sudo mount /dev/sda1 /media/disk1
``` or by running Gparted (via the menus System, Administration, Gparted, if I recall correctly). If either way isn't working, I'd check the integrity of the LiveCD.

---

### Post by JustinR on 2010-07-28
Well just bootup a live CD, mount your hard drive and just copy the files over.

If its giving you an error when you open the hard drive then type go into a terminal (Applications > Accessories > Terminal) and type in 'gksudo nautilus', type in your password, and then navigate to your hard drive.

---

### Post by Old Newville on 2010-07-28
The computer boots as far as the login screen. I get an error message that reads, "Install Problem! The configuration defaults for the Gnome Power Manager have not been installed correctly."

If I hit Contr-Alt-F1, I get a command line where I can login. It even tells me I have email. Just no desktop or Thunderbird with which to read it! Only a black screen and white letters. If I was a programmer, I'd probably know how to work around that, but I'm not.

I learned today that the power manager error  can't be solved. I posted this error at Launchpad and the reply was  "reinstall." So I figured the system was hosed beyond repair.

After I opened this thread I got an idea and decided to install Lucid on HD 2. Now I've got a dual-boot setup where I can choose between the other broken system or the new one. Maybe this will give me some new idea of how to fix the original system. Any ideas? I'm not really looking forward to spending weeks tweaking a new install!

And yes, I can access HD 1 from HD 2, so I'm able to retrieve my files if I absolutely need to erase HD 1.

---

### Post by oldos2er on 2010-07-28
Ok. When you said you could only boot to a command line, no OS, that threw me. If you're getting a login prompt, the OS is loaded.

If you were told there's no solution for the gnome-power-manager bug other than to reinstall, I'm not sure there's much hope.

---

### Post by Old Newville on 2010-08-02
I ended up installing Lucid on a backup hard drive, booting from there and pulling my files over. Then I reinstalled Lucid on the first drive. Now I have 2 bootable drives. Probably not a bad idea if Ubuntu is subject to fatal errors requiring reinstallation.

---

### Post by muteXe on 2010-08-02
Can I ask what was wrong with the suggestion on post#4?
Why did you have to go install an OS on another drive to get your files?

Cheers,
mute

---

