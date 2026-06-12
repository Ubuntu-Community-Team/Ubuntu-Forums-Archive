---
title: "NVidia Drivers not... working?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by mattsw104 on 2009-01-02
This is my first few hours using linux, ever.. I just installed it onto my hard drive next to vista 64 bit. Just updated everything and installed NVidia drivers 117 and rebooted. Now whenever I boot up I'm in a DOS version of Ubuntu and I'm not quite sure what I'm doing wrong.

I'll say again, I've never used linux or Ubuntu before, but from what I've seen I'm happy with it and would like to learn. 

I am able to log into Ubuntu but its... well.. DOS, help gives me commands but I can't see them all because it gives me so many and I can't scroll up. What would the command be to start the OS? I believe I saw something saying that the driver failed to display on all of the resolutions. Something about my bios doesn't have an apeture hole... It scrolls too fast for me to read.

Windows Vista Home Premium 64 bit.
Ubuntu 8.10
AMD Phenom 9850
ASUS SLI-Delux
4GB Corsair
200 GB Harddrive
NVidia GeForce4 8800 GTS (2x SLI)
Creative Soundblaster X-Fi

---

### Post by sad_iq on 2009-01-02
Ok...here goes...the "DOS version of Ubuntu" is called a CLI (command line interface) and it should allow you to login and use your computer.    
  First off...to see the messages that you say you cannot read press SHIFT+PgUp...maybe you can see the error message, if not after a login type ```
dmesg
``` to see them again. 
  Second...type ```
sudo nano /etc/X11/xorg.conf
``` and look for theese lines: ```
Section "Device" 
 Driver         "nvidia"
```
 If you don't have nvidia in the Driver part change it(it should be "nvidia"), to save it press CTRL+x then follow the instructions :)
 Reboot your computer and it should be ok.
 Then you'll have to search theese forums on how to enable SLI since I don't have any experience with that :(

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> Ok...here goes...the "DOS version of Ubuntu" is called a CLI (command line interface) and it should allow you to login and use your computer.    
  First off...to see the messages that you say you cannot read press SHIFT+PgUp...maybe you can see the error message, if not after a login type ```
dmesg
``` to see them again. 
  Second...type ```
sudo nano /etc/X11/xorg.conf
``` and look for theese lines: ```
Section "Device" 
 Driver         "nvidia"
```
 If you don't have nvidia in the Driver part change it(it should be "nvidia"), to save it press CTRL+x then follow the instructions :)
 Reboot your computer and it should be ok.
 Then you'll have to search theese forums on how to enable SLI since I don't have any experience with that :(

well... I got to the xorg.conf menu. Its empty...?

---

### Post by mattsw104 on 2009-01-02
btw, thank you for responding ^_^ people here seem to be very helpful and friendly

if it means anything, I've tried to look through other threads and done some google searches for people having a hard time with the GUI loading up. When I enter the command 'startx' I end up with an error and "Fatal server error: no screens found"

Also I have no clue as of yet how to do anything in 'root'

---

### Post by sad_iq on 2009-01-02
Make sure you don't replace Capital letters with normal ones..."X" is not "x" in linux!

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> Make sure you don't replace Capital letters with normal ones..."X" is not "x" in linux!

its typed correctly. it's empty

---

### Post by 3rdalbum on 2009-01-02
Try typing this into the terminal (not into the Xorg.conf file):

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you if you want to automatically choose a graphics driver, tell it NO, and then choose the "nvidia" driver. After the program finishes and you are brought back to your terminal, type sudo reboot.

If you still have the problem, try the procedure again but this time choose the "nv" driver.

---

### Post by mattsw104 on 2009-01-02
> **3rdalbum said:**
> Try typing this into the terminal (not into the Xorg.conf file):

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you if you want to automatically choose a graphics driver, tell it NO, and then choose the "nvidia" driver. After the program finishes and you are brought back to your terminal, type sudo reboot.

If you still have the problem, try the procedure again but this time choose the "nv" driver.

Its only asking me stuff about my keyboard setup..

---

### Post by User X on 2009-01-02
I am pretty new myself but I would like to share with you the way I added my NVIDIA drivers because it was easy for me to do, and its more GUI based.

Open Synaptic Package Manager

->System ->Administration -> Synaptic Package Manager

You will be prompted to enter your password.

Search for "envyng"

Mine comes back with three entries:

envyng-core
envyng-gtk
envyng-qt

Select the envyng-gtk  (assuming you are running the Gnome Desktop Environment) and mark it for instalation.  It will probably also highlight envyng-core and that is OK.

Choose "Apply"

Ubuntu should download and install the components you need automatically

When its finished open terminal

->Applications ->Accessories ->Terminal

and type:

> envyng -t

You will get a text based auto-installer for NVIDIA/ATI drivers.  Follow the onscreen instructions to the letter and it will download the drivers you need and install them for you.  On reboot you should be all set.  If this doesn't work please remember I am new also...

---

### Post by sad_iq on 2009-01-02
Hmm..forgot about envy :(
 But since he cannot get the GUI(Graphical User Interface) he can't follow your instructions...so here goes:
 After you login to your CLI do the folowing:
 ```
sudo apt-get install envyng-gtk
```
 That will install that program without all the aditional clicks and stuff :P
 Then do ```
sudo envyng -t
``` and follow the instructions(I never used envy in text mode...so I assume it requires sudo powers)

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> Hmm..forgot about envy :(
 But since he cannot get the GUI(Graphical User Interface) he can't follow your instructions...so here goes:
 After you login to your CLI do the folowing:
 ```
sudo apt-get install envyng-gtk
```
 That will install that program without all the aditional clicks and stuff :P
 Then do ```
sudo envyng -t
``` and follow the instructions(I never used envy in text mode...so I assume it requires sudo powers)

I'm getting "TypeError: list indices must be integers"

---

### Post by sad_iq on 2009-01-02
> **mattsw104 said:**
> I'm getting "TypeError: list indices must be integers"

It seems you have a run into some bugs (with envy and your SLI)setup...
[https://bugs.launchpad.net/envy/+bug/292173](https://bugs.launchpad.net/envy/+bug/292173) has a solution, but it requires the removal of 1 videocard to be fixed(donno if that's a solution in your case), or the ability to have a GUI to test the other methods without the need to remove 1 videocards.
 
 Method 2 from the link in that page sugests the removal of your current nvidia driver and installing the driver from the NVIDIA webpage.We'll try to do it without all the clicks and such :(
 This should be dangerous because I have no idea how to revert the changes(if it would fail for me I would reinstall...so don't do this just yet...wait for someone with some more skills to give you a better answer!!!)

 This should remove every nvidia related driver/app installed in your system(hopefuly):
 ```
sudo apt-get remove --purge nvidia-* && sudo rmmod nvidia
```
Then ```
sudo apt-get install build-essential
``` to install the necesary tools.
 Now...we need to download the videocard driver from the web page:
 For 32 bits only:
 ```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run
```
 For 64 bits only:
 ```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/NVIDIA-Linux-x86_64-177.82-pkg2.run
```
 After you downloaded your driver you need to give it execute permissions:
 ```
chmod +x NVIDIA (press TAB to autocomplete)
```
 To install the driver type:
 ```
sudo sh NVIDIA(press TAB to autocomplete)
``` and follow the instructions it gives you.Also...allow it to generate a new xorg.conf file
 Reboot and it should work...if not you need to see if theese new drivers created an xorg.conf file:
 ```
sudo nano /etc/X11/xorg.conf
``` and look for a line that has ```
Section "Device"
    ..............
    Driver "nvidia"
    .............
EndSection
``` if nvidia is not in the Driver line change it, and add(if missing)  **Option "sli" "auto"** under the driver line.
 I really hope this works for you :)

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> It seems you have a run into some bugs (with envy and your SLI)setup...
[https://bugs.launchpad.net/envy/+bug/292173](https://bugs.launchpad.net/envy/+bug/292173) has a solution, but it requires the removal of 1 videocard to be fixed(donno if that's a solution in your case), or the ability to have a GUI to test the other methods without the need to remove 1 videocards.
 
 Method 2 from the link in that page sugests the removal of your current nvidia driver and installing the driver from the NVIDIA webpage.We'll try to do it without all the clicks and such :(
 This should be dangerous because I have no idea how to revert the changes(if it would fail for me I would reinstall...so don't do this just yet...wait for someone with some more skills to give you a better answer!!!)

 This should remove every nvidia related driver/app installed in your system(hopefuly):
 ```
sudo apt-get remove --purge nvidia-* && sudo rmmod nvidia
```
Then ```
sudo apt-get install build-essential
``` to install the necesary tools.
 Now...we need to download the videocard driver from the web page:
 For 32 bits only:
 ```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run
```
 For 64 bits only:
 ```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/NVIDIA-Linux-x86_64-177.82-pkg2.run
```
 After you downloaded your driver you need to give it execute permissions:
 ```
chmod +x NVIDIA (press TAB to autocomplete)
```
 To install the driver type:
 ```
sudo sh NVIDIA(press TAB to autocomplete)
``` and follow the instructions it gives you.Also...allow it to generate a new xorg.conf file
 Reboot and it should work...if not you need to see if theese new drivers created an xorg.conf file:
 ```
sudo nano /etc/X11/xorg.conf
``` and look for a line that has ```
Section "Device"
    ..............
    Driver "nvidia"
    .............
EndSection
``` if nvidia is not in the Driver line change it, and add(if missing)  **Option "sli" "auto"** under the driver line.
 I really hope this works for you :)

Thank you, this has given me alot of progress I think, seeing as now I have an xorg.conf file. I still can't seem to start into the GUI. I have heard that a command to do so would be 'startx' all that this does is give me 
```
(==) Using config file: "/ect/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) No devices detected.

Fatal server error: 
no screens found
giving up.
xinit: Connectioni refused (errno 111): unable to connect t x server
xinit: No such process (errno3): Server error.
xauth: error in locking uthority file /home/mattsw104/.Xauthority
```

I still feel that I'm 'doing it wrong':P

---

### Post by sad_iq on 2009-01-02
> **mattsw104 said:**
> Thank you, this has given me alot of progress I think, seeing as now I have an xorg.conf file. 
I still feel that I'm 'doing it wrong':P
  First of...let's see if your nvidia module is loaded...type this:
```
sudo lsmod | grep nvidia
```...mine gives this output: ```
sadiq@omerta:~$ sudo lsmod|grep nvidia
nvidia               7224948  26 
i2c_core               31892  1 nvidia
agpgart                42184  2 nvidia,intel_agp
sadiq@omerta:~$ 

```
 Yours should be similar...if it doesn't give you anything try to load that module:
 ```
sudo modprobe nvidia
```and type ```
dmesg
``` to see if anything happened(the last few lines should do it)
  Next...look in xorg.conf...is there a **Driver "nvidia"** line? Have you added **Option "sli" "auto"** under it?? Is there any line that could relate to **sli**??(just to check :P)
 And (hopefully) last do :
 ```
sudo nano /etc/X11/xorg.conf
``` and put a **#** infront of the line that says  **Load           "type1"**...that should coment that line out and get rid of the (EE) error message
 Try **startx** again after that and see how it goes :)

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> First of...let's see if your nvidia module is loaded...type this:
```
sudo lsmod | grep nvidia
```...mine gives this output: ```
sadiq@omerta:~$ sudo lsmod|grep nvidia
nvidia               7224948  26 
i2c_core               31892  1 nvidia
agpgart                42184  2 nvidia,intel_agp
sadiq@omerta:~$ 

```
 Yours should be similar...if it doesn't give you anything try to load that module:
 ```
sudo modprobe nvidia
```and type ```
dmesg
``` to see if anything happened(the last few lines should do it)
  Next...look in xorg.conf...is there a **Driver "nvidia"** line? Have you added **Option "sli" "auto"** under it?? Is there any line that could relate to **sli**??(just to check :P)
 And (hopefully) last do :
 ```
sudo nano /etc/X11/xorg.conf
``` and put a **#** infront of the line that says  **Load           "type1"**...that should coment that line out and get rid of the (EE) error message
 Try **startx** again after that and see how it goes :)

Ok. I'm getting:
```
nvidia             7815496  0
i2c_core             36128  2 nvidia,i2c_nforce2

```

Ok, I don't think that sudo modprobe nvidia did anything. but the last few lines of dmesg are as follows:
```
 [ 25.960001] Bridge firewalling registered
[25.960156] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[30.160271] NET: Registered protocol family 17 
```

And in xorg.conf yes, there is nvidia and sli just like you said.
could it have anything to do with Device0 overlapping?

---

### Post by mattsw104 on 2009-01-02
> **sad_iq said:**
> 
 And (hopefully) last do :
 ```
sudo nano /etc/X11/xorg.conf
``` and put a **#** infront of the line that says  **Load           "type1"**...that should coment that line out and get rid of the (EE) error message
 Try **startx** again after that and see how it goes :)

After putting the '#' in front of Load "type1" I still get (EE) No devices detected. And still no screens are found. :-/

I do thank you for your help and time thus far, it is appreciated.

my skype is mattsw104 if you or anyone else feels like troubleshooting in real time. ^_^ +the ability to see my screen from a webcam may help

---

