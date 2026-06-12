---
title: "Low graphics mode error"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by SEECo on 2010-09-11
Hi some days ago i have installed ubuntu 10.04 and got very impressed. I made it very beautiful by themes wallpapers wally, but i wanted to change the login window everybody said that go to system>administration>login window. But when i get there i felt very strange it wasn't there than i tried to install a software called gpe-login. I thought after installing it the login window will come there but during installation the computer restarted but when it restarted he showed me the low graphics mode error.Than anyone said me to run a command:
sudo dpkg-reconfigure -phigh xserver-xorg;


But he said me to run this command in terminal but my ubuntu doesn't go further than the dialog box of low graphics mode error.
Please help

---

### Post by SEECo on 2010-09-11
Plz reply

---

### Post by SEECo on 2010-09-11
Ok just tell me something about the error.

---

### Post by SEECo on 2010-09-11
Can anyone tell me to how to fix low graphics error.

---

### Post by jtarin on 2010-09-11
> **SEECo said:**
> Can anyone tell me to how to fix low graphics error.
Possibly,You will have to supply some information for us to do that. Are you comfortable using the terminal, command line?
What make and model of computer do you have? Do you know the graphics card/chipset make and model number? Do you boot using GRUB2? Is this a dual boot setup?

---

### Post by SEECo on 2010-09-11
I only got this
Intel Dual processor
nvidia graphics card 5500 model no
512 mb ram
40 gb hard drive
and my computer is a server system
anything else

---

### Post by jtarin on 2010-09-11
Enter this command in the terminal
```
lspci
```and post the results.

---

### Post by SEECo on 2010-09-11
how can i login in my account after the dialog box appears.

---

### Post by jtarin on 2010-09-11
> **SEECo said:**
> how can i login in my account after the dialog box appears.You failed to answer all my questions in my first post.I don't have enough information to help you with that.

---

### Post by SEECo on 2010-09-11
In that post i told you to ask what you want tell me what you want.

---

### Post by adit on 2010-09-11
> run this command in terminal but my ubuntu doesn't go further than the dialog box of low graphics mode error
Boot from ubuntu livecd.  From livecd open terminal.

---

### Post by jtarin on 2010-09-11
> **jtarin said:**
> Possibly,You will have to supply some information for us to do that. Are you comfortable using the terminal, command line?
What make and model of computer do you have? Do you know the graphics card/chipset make and model number? **_[COLOR="Red"]Do you boot using GRUB2? Is this a dual boot setup?[/COLOR]_**This and also what dialog are you speaking of...your login screen?

---

### Post by SEECo on 2010-09-11
After doing that what to do which command to run

---

### Post by SEECo on 2010-09-11
Yes i am using GRUB2 but i am not on a dual boot. And the dialog box is about the low graphics mode error.

---

### Post by adit on 2010-09-11
> After doing that what to do which command to runCreate a new directory /mnt/disk
```
sudo mkdir /mnt/disk
```Find out the partition where your ubuntu is installed.  For example if it is /dev/sda3, then type
```
sudo mount /dev/sda3 /mnt/disk
```then
```
chroot /mnt/disk
```then type whatever command you want to run on the system installed on your hard disk.  As you said in post#1
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jtarin on 2010-09-11
When Grub appears try selecting the Rescue Mode kernel line.

---

### Post by SEECo on 2010-09-11
can you tell me to how to find out the partiotion where i installed ubuntu

---

### Post by SEECo on 2010-09-11
Sorry i didn't remind it.

---

### Post by SEECo on 2010-09-11
I don't have dual boot so the grub doesn't appears.

---

### Post by adit on 2010-09-11
Post the output of
```
sudo fdisk -l
```

---

### Post by SEECo on 2010-09-11
After running chroot /mnt/ disk
It said cannot change root directory

---

### Post by adit on 2010-09-11
> cannot change root directoryAdd sudo before the command
```
sudo chroot /mnt/disk
```

---

### Post by SEECo on 2010-09-11
Look what had happened
ubuntu@ubuntu:~$ sudo mkdir /mnt/disk
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt/disk
mount: /dev/sda already mounted or /mnt/disk busy
ubuntu@ubuntu:~$ sudo chroot /mnt/disk
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$

---

### Post by JohnHeikkila on 2010-09-11
Looks like it's already mounted. Open nautilus when you've booted from Live-CD and on the left, you should see your locations, and there should be your filesystem mounted
Example:
[img]http://i14.photobucket.com/albums/a338/agro1986/Illustrations/boab-053.png[/img]

But anyways, if you want to fix the errors and you have a Nvidia graphics card, boot your PC in recovery mode (When the PC is starting, press Esc or hold Shift when the _ sign is flashing, then select Recovery mode and when the recovery mode has loaded, go to the root console), and then type "sudo nvidia-xconfig"

If you don't have an Nvidia card, do the same as above but instead of the nvidia-xconfig, do "sudo dkpg-reconfigure xserver-xorg".

---

### Post by SEECo on 2010-09-11
I am using live CD can u tell me to how when press ESC of to hold Shift.

---

### Post by SEECo on 2010-09-11
How to make the grub screen appear.

---

### Post by jtarin on 2010-09-11
> **SEECo said:**
> How to make the grub screen appear.

Hold SHIFT at boot to show the menu.

---

### Post by adit on 2010-09-12
> I am using live CD can u tell me to how when press ESC of to hold ShiftRemove the livecd.  Boot from harddisk.  Keep holding shift key from the time you power on your computer till you get the grub menu.
From the grub menu select recovery and boot into recovery mode.

---

### Post by SEECo on 2010-09-13
Hi can anyone tell me to how to get rid of low graphics mode error in ubuntu 10.04. I got this error many times and installed a new os. Now i want that it do not come again what should i ave to do.

---

### Post by Gone fishing on 2010-09-13
Probably you need to install and enable the proprietary drivers for your video card. 

Administration > Hardware Drivers

---

### Post by SEECo on 2010-09-13
I installed it in my every single ubuntu operating system but it stil gave me the error.

---

### Post by realzippy on 2010-09-13
Can you tell us *which* driver you have installed?
Which ubuntu version do you use?
Which graphics card?

---

### Post by SEECo on 2010-09-13
I have a priorety driver version 193
ubuntu 10.04
Nvidia fx 5500

---

### Post by realzippy on 2010-09-13
Best thing to do is to run:

```
sudo nvidia-bug-report.sh
```

in the terminal.The command creates a bug report containing most interesting log files.
Can you attach the created file (should be in your home directory)?

---

### Post by SEECo on 2010-09-13
Is it secure.

---

### Post by SEECo on 2010-09-13
I have attached

---

### Post by realzippy on 2010-09-13
There is everything ok in the log files.
You should be able to select many different resolutions.
I do not see any problem,if the "low graphics error" did not occur since you reinstalled,I guess it will never.You seem to have installed the nvidia-drivers with System/Administration/HardwarDrivers,so if you run a kernel update,the nvidia kernel module will also get updated.
Correct me,if you have a problem now....

---

### Post by SEECo on 2010-09-13
Is my computer a good one. Can i be able to install some screensavers, Themes login screens, Icons.

---

### Post by realzippy on 2010-09-13
The file is only about graphics.Your nvidia card is old,but should be able to enable desktop effects;means 3D openGL applications (compiz,games,..)will work.
All screensavers ,icons and themes will work also.

---

### Post by SEECo on 2010-09-14
If the graphics error happened what should i do.

---

### Post by jtarin on 2010-09-14
If you have concerns about your graphics card be careful about adding things.Keep track of what you do so it can be undone if you need too. Example...install a theme....you get an error. Uninstall the theme see if the error goes away. You have to maintain a balance between your hardware and software.

---

### Post by SEECo on 2010-09-14
What if after install a theme i get an error the i delete the theme what if the error remains.
???????????????????

---

### Post by jtarin on 2010-09-14
You worry to much....enjoy what you have while you have it.

---

### Post by SEECo on 2010-09-15
Hey jtarin can you be my friend so i could have a contact with you when the error happens

---

### Post by jtarin on 2010-09-15
Only when that error happens...no other errors allowed.

---

### Post by lisati on 2010-09-18
Threads merged

---

