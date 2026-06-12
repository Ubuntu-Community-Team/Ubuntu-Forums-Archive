---
title: "Needing Help with 6600GT drivers"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by ayekay on 2009-04-16
I can't get my 6600GT working properly in ubuntu.

I did some searching and tried a few different things such as downloading drivers from nvidias website, which I tried to run thru terminal as sudo but could not open.

I tried some commands that stopped gnome and purged nvidia files, then attempted to run the driver thru the command line and couldn't open it.

Tried to download some .deb files that installed just fine, but still didn't do anything.

Help. ](*,)

---

### Post by balaknair on 2009-04-16
Hello Ayekay

The latest nVidia driver for the Geforce 6 series as per the nVidia site is 180.44
Using the drivers from the nVidia site can cause a few problems, such as having to compile the kernel module separately. If you use the version in the repositories(180.11) this will not be necessary.

If you want to use these I suggest you follow these steps(I suggest you take a print out or write them down since you'll be working from the command line)

1) Download the drivers for your architecture from
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

and save it in your Home directory

2) Open a text console by pressing ctrl-alt-F1 and log in with your user name and password

3) Stop Gnome with the command
```
sudo /etc/init.d/gdm stop
```

4) Remove the old drivers with envyng-
```
sudo apt-get install envyng-core
sudo envyng -t
```

Use the envyng text based utility to uninstall the driver(just follow the onscreen instruction that envy gives you).

Next you can install the nVidia drivers. You'll need the build-essential and linux-headers packages to compile kernel modules.

```
sudo apt-get install build-essential linux-headers-`uname -r`

```

```
sudo sh ./NVIDIA***.run
```
Just hit tab after getting as far as ./NV and the file name should autocomplete.

Choose the default options, except for the last one(about reconfiguring Xorg, choose 'yes')

Restart the GUI
```
sudo /etc/init.d/gdm start
```

Reboot

If all went normally, you should have a functional setup now.

**IMPORTANT:**
Note that if you use a driver version other than from the Ubuntu repositories(via Synaptic), you will have to repeat the above procedure each time the kernel is updated. I recommend that you stick with the drivers in the repositories.

---

### Post by The Cog on 2009-04-16
I have a 6600GT at home. All I ever do is install the package nvidia-glx-new from the Ubuntu repositories. Works fine. Google earth, Celestia, UT, UT2004, Doom3. Wastes far too much time.

Actually, with Intrepid, I can't be sure which package it used because it gave me a little icon in the system tray that said a proprietary driver was available, and I just said yes to that. I'll check when I get home.

---

### Post by ayekay on 2009-04-16
Thanks for your help, I will try that when I have time.

I am new to ubuntu , and we are learning a little bit about it in class. 

I look forward to messing around with it and learning more about the commands and what have you.

It did inform me that I needed a properitary driver, I enabled it, and nothing happened. So, I think I will be going the manual route one way or the other. :popcorn:

---

