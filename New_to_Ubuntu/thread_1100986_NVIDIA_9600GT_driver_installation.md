---
title: "NVIDIA 9600GT driver installation"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by arod529 on 2009-03-19
**This problem has been solved. Thanks to all who contributed.**

OK So I am usually good with computers but this is driving me mad!:mad: I've got Ubuntu 8.1 and XP Pro dual booting on a single drive.(The problem computer isn't connected to the internet) All goes well but I can't figure out how to install the video drivers for my NVIDIA GeForce 9600GT made by PNY.

   So, I've got *NVIDIA-Linux-x86-180.29-pkg1.run.txt* and *NVIDIA-Linux-x86-173.08-pkg1.run.txt*(both from the NVIDIA site) but can't seem to run either one. If I double click the file and tell it to *run in terminal* it uncompresses the contents but then says that the installer must be run as root. If I open a terminal and type *sh filename* it says that it can't open it. 

   I've spent several hours for about three days scanning the forums and can't find anything to help.](*,)All I've found is alot of things that I can't get to work and some people saying "Thanks works good".

---

### Post by arod529 on 2009-03-19
One more thing,(Laugh all you want)what are the tags for?

---

### Post by jlochhead on 2009-03-19
You do not need to do this that way.

System > Preferences > Hardware Drivers - pick the 177 driver (2 available), click the activate button, wait for it to install (less than a minute) and restart your computer.

I have the 9600M GT and it works fine.

---

### Post by kanikilu on 2009-03-19
See if this page helps for manually installing the Nvidia drivers:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by kanikilu on 2009-03-19
> **jlochhead said:**
> You do not need to do this that way.

System > Preferences > Hardware Drivers - pick the 177 driver (2 available), click the activate button, wait for it to install (less than a minute) and restart your computer.

I have the 9600M GT and it works fine. Correct me if I'm wrong, but wouldn't that require a working internet connection, which he apparently doesn't have on that machine?

---

### Post by jlochhead on 2009-03-19
These drivers have been tested for you by the Ubuntu Developers and made into packages so they are easy to install.

They are not the latest... but the latest ones will come when they are ready. I have tried the latest and there is very little difference.

To install it the way you are trying you have to log in without X11 (graphics running). Easiest way to do this is by using the recovery entry in the grub menu and choosing the terminal option.

Then you must:

cd /directory/where/the/run/script/is
chmod +x <run-file-name>
./<run-file>

Then follow the instructions.

This is not for beginners; and in most cases is not worth doing even for intermediate/advanced users.

Since the drivers have to be compiled against your current kernel the drivers will break every time you update the kernel. Meaning you will have to do this again.

---

### Post by jlochhead on 2009-03-19
> **kanikilu said:**
> Correct me if I'm wrong, but wouldn't that require a working internet connection, which he apparently doesn't have on that machine?

Ah didn't read that bit.

The instructions are above, anyway.

---

### Post by ktrnka on 2009-03-19
Simple way to run the Nvidia*****.run is hit ctrl+alt+F1 and login. Change to the directory where Nvidia.run is located. 

We need to stop X so we can just run

```
sudo /etc/init.d/gdm stop
``` or

```
sudo /etc/init.d/kdm stop
``` if running Kubuntu

then run the installation script like so:

```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```

Then just answer the questions.

That should be it

Oh and start gdm after with:

```
sudo /etc/init.d/gdm start
```

---

### Post by arod529 on 2009-03-19
WOW. Thanks for the quick replies.

However,(q the doom music) I can't even run the first line of code. It gives me an error message that says "cp: cannot stat ' /ect/X11/xorg.conf': No such file or directory" but I found the directory and file. If I copy the file to the desktop and change the name by adding the *.backup* extention and then try to move it back to the origional folder it says I don't have permission.

---

### Post by ktrnka on 2009-03-19
You don't need to go through all the stuff located in the [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Just run nvidia's script as I have described above

---

### Post by Nightstrike2009 on 2009-03-19
This should work for you I am a bit unorthodox compared to the rest but these work for me.

These files are required for nvidia 180 driver in ubuntu 8.10:

[COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu2_all
nvidia-180-kernel-source_180.11-0ubuntu1~intrepid1_i386
nvidia-glx-180_180.11-0ubuntu1~intrepid1_i386
nvidia-settings_177.78-0ubuntu2.1_i386[/COLOR]

The one below is the modaliases one;
[COLOR="SeaGreen"]nvidia-180-modaliases_180.11-0ubuntu1~intrepid1_i386.deb[/COLOR]

And these for compizconfig:

[COLOR="SeaGreen"]compizconfig-settings-manager_0.7.8-0ubuntu3_all
python-compizconfig_0.7.8-0ubuntu1_i386[/COLOR]

Hope this helps 

Website is [http://packages.ubuntu.com/intrepid-updates/nvidia-180-kernel-source]("http://packages.ubuntu.com/intrepid-updates/nvidia-180-kernel-source") there is a search box for the file names at the top of this page. Download (Via windows and copy to USB stick or similar) and install all deb files (by right-clicking in linux) its important you install them all and dont miss any out, then go Hardware drivers (wizard from gnomes menu list) select 180 driver and restart. This works for me :)

PS: Nvidia 180.11 is more up-to-date than the 177 driver.

---

### Post by arod529 on 2009-03-19
> **jlochhead said:**
> These drivers have been tested for you by the Ubuntu Developers and made into packages so they are easy to install.

They are not the latest... but the latest ones will come when they are ready. I have tried the latest and there is very little difference.

To install it the way you are trying you have to log in without X11 (graphics running). Easiest way to do this is by using the recovery entry in the grub menu and choosing the terminal option.

Then you must:

cd /directory/where/the/run/script/is
chmod +x <run-file-name>
./<run-file>

Then follow the instructions.

This is not for beginners; and in most cases is not worth doing even for intermediate/advanced users.

Since the drivers have to be compiled against your current kernel the drivers will break every time you update the kernel. Meaning you will have to do this again.

AWESOME!! One more thing. The installer starts but tells me I'm running in *runlevel 1* but says that some things will not install correctly and suggests switching to *runlevel 3*.

Should I stay in *runlevel 1* or switch to *runlevel 3*. I really don't know what these runlevels represent.:P

Thanks Guys

---

### Post by jlochhead on 2009-03-19
Ah, I think I just ignored that warning. It did not seem to cause any problems. If you want to be sure Ktrnka's post will get you into run level 3. They are basically doing the same thing just with different run levels.

> **ktrnka said:**
> Simple way to run the Nvidia*****.run is hit ctrl+alt+F1 and login. Change to the directory where Nvidia.run is located. 

We need to stop X so we can just run

```
sudo /etc/init.d/gdm stop
``` or

```
sudo /etc/init.d/kdm stop
``` if running Kubuntu

then run the installation script like so:

```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```

Then just answer the questions.

That should be it

Oh and start gdm after with:

```
sudo /etc/init.d/gdm start
```

---

### Post by jlochhead on 2009-03-19
To summarise for you using the other guys post:

1) Login as normal.
2) Open a terminal.
3) sudo /etc/init.d/gdm stop
4) sudo -i
5) cd to/directory/with/the/run/file
6) chmod +x <run-file>
7) ./<run-file>
8) Follow instructions.
9) exit
10) sudo /etc/init.d/gdm start

Also I do not think it is a problem (as they are scripts) but I do not think that .txt is supposed to be on the end of the file name. I think that firefox added it for you because it didn't recognise the file type.

---

### Post by arod529 on 2009-03-19
Hey, it worked!!!

Thanks all for the help.
The desktop booted way faster and the fancy screensavers with the ants ran way smoother.(As opposed to about one step every ten minuites.):lolflag:

By the way, I ignored the warning.

---

### Post by arod529 on 2009-03-19
> **jlochhead said:**
> 
Also I do not think it is a problem (as they are scripts) but I do not think that .txt is supposed to be on the end of the file name. I think that firefox added it for you because it didn't recognise the file type.

Interesting note about the *.txt* at the end of the filename. But I put it in with the <filename> entry and it all worked just fine.

---

### Post by jlochhead on 2009-03-19
> **arod529 said:**
> Interesting note about the *.txt* at the end of the filename. But I put it in with the <filename> entry and it all worked just fine.

Yea it is a script, as far as I know the terminal doesn't care about the file name as long as it recognises the file as a script; not sure if this is always the case so it is better to be safe than sorry.

---

### Post by ktrnka on 2009-03-19
> **jlochhead said:**
> To summarise for you using the other guys post:

1) Login as normal.
2) Open a terminal.
3) sudo /etc/init.d/gdm stop
4) sudo -i
5) cd to/directory/with/the/run/file
6) chmod +x <run-file>
7) ./<run-file>
8) Follow instructions.
9) exit
10) sudo /etc/init.d/gdm start

Also I do not think it is a problem (as they are scripts) but I do not think that .txt is supposed to be on the end of the file name. I think that firefox added it for you because it didn't recognise the file type.


Not exactly.....

Corrected Version:

1) Login as normal.
2) Change to runlevel 3 with ctrl+alt+F1 ( if you open a terminal within gnome, it will disappear after running the next command)
3) sudo /etc/init.d/gdm stop
4) sudo -i
5) cd to/directory/with/the/run/file
6) chmod +x <run-file>
7) sh <file> (specifically for Nvidia cause it doesn't know the .run is a shell script)
8) Follow instructions.
9) sudo /etc/init.d/gdm start

---

