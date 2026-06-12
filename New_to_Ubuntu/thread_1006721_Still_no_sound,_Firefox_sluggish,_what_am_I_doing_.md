---
title: "Still no sound, Firefox sluggish, what am I doing wrong?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by dgtlkttn on 2008-12-09
Hi there,

I've just installed 8.10 this morning and have been going at it for 10 hours now. I still can't get any sound and have been searching for some way to fix it. 

I did [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") and I can now stream video, play DVD's & CD's, but there is still no sound.

My comp is AMD x2 64 bit, nvidia geforce 8100 , 6 channel audio, with 2gb ram which seems to be struggling at the moment.

I've found this [[COLOR="Blue"]page[/COLOR]]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intelv") but have no idea where to start with actually implementing it. 

I'm still loving linux but very close to losing the plot at the moment. 

Can anyone help please?

Thanks for reading.

---

### Post by anim on 2008-12-09
run the command
```
lspci
```

and paste the output here, I'll see what I can do.

---

### Post by dgtlkttn on 2008-12-09
> **anim said:**
> run the command
```
lspci
```

and paste the output here, I'll see what I can do.

Hi anim thanks, here ya go :)

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8100 / nForce 720a (rev a2)
digitalkitten@digitalkitten:~$ 



Cheers!

---

### Post by porchrat on 2008-12-09
Have you installed the apporpriate video drivers yet? Could be the reason Firefox is so sluggish.  Normally the drivers Ubuntu comes with are rubbish.

---

### Post by dgtlkttn on 2008-12-09
> **porchrat said:**
> Have you installed the apporpriate video drivers yet? Could be the reason Firefox is so sluggish.  Normally the drivers Ubuntu comes with are rubbish.


Hi,

I did find and try to install drivers from the nvidia site, but once downloaded, was only a text document which I have no idea how to use. Sorry I must sound completely useless!!

---

### Post by Sealbhach on 2008-12-09
Hi, for the sound, I would suggest working through this guide here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It should pinpoint your problem.


.

---

### Post by dgtlkttn on 2008-12-09
> **Sealbhach said:**
> Hi, for the sound, I would suggest working through this guide here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It should pinpoint your problem.


.

Thank you, I'll try that :)

---

### Post by porchrat on 2008-12-10
> **dgtlkttn said:**
> Hi,

I did find and try to install drivers from the nvidia site, but once downloaded, was only a text document which I have no idea how to use. Sorry I must sound completely useless!!

OK well that could definitely be the reason that firefox appears sluggish.  I imagine that when you scroll down the page you get screen tearing (Lines across the screen where the image seems to be splitting)?  Those are usually caused by inferior graphics drivers.

You can go to the nvidia homepage to download the appropriate driver for your card and OS (Linux 32bit or 64bit depending on which version of 8.10 you installed).  The nvidia website has an area where you merely fill in your card and OS details.  You'll find it [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Your card seems to be a Geforce 8200.

I don't run an Nvidia, but if they are anything like ATI they should actually come bundled in a linux-based install package.  If not it is easy to install them manually (there are plenty of guides both here on the forums and elsewhere).

Another option is to try envyng, but I don't know if they support the new Xorg 7.4 running on 8.10 (by the way make sure the driver you download has support for Xorg 7.4 or else it won't run on ubuntu 8.10).

Hope this helps

---

### Post by dgtlkttn on 2008-12-10
> **porchrat said:**
> OK well that could definitely be the reason that firefox appears sluggish.  I imagine that when you scroll down the page you get screen tearing (Lines across the screen where the image seems to be splitting)?  Those are usually caused by inferior graphics drivers.

You can go to the nvidia homepage to download the appropriate driver for your card and OS (Linux 32bit or 64bit depending on which version of 8.10 you installed).  The nvidia website has an area where you merely fill in your card and OS details.  You'll find it [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Your card seems to be a Geforce 8200.

I don't run an Nvidia, but if they are anything like ATI they should actually come bundled in a linux-based install package.  If not it is easy to install them manually (there are plenty of guides both here on the forums and elsewhere).

Another option is to try envyng, but I don't know if they support the new Xorg 7.4 running on 8.10 (by the way make sure the driver you download has support for Xorg 7.4 or else it won't run on ubuntu 8.10).

Hope this helps

Hi, 

Yes, I've been experiencing the screen tearing, which makes it very hard to scroll pages and follow them, Good quality video is playing at what looks like 5fps too.

Thank porchrat, I'll give it a go, and post back here with results. :)

---

### Post by dgtlkttn on 2008-12-11
> **dgtlkttn said:**
> Hi, 

Yes, I've been experiencing the screen tearing, which makes it very hard to scroll pages and follow them, Good quality video is playing at what looks like 5fps too.

Thank porchrat, I'll give it a go, and post back here with results. :)

I tried to install the drivers from the nvidia site, no joy. I really don't understand syntx. everything is just going way over my head! I've also ended up having to do a fresh install, so I'm back to square one. Tried installing the nvidia drivers from system>admin>hardware drivers. Which left me with a flickering white overlay on top of the screen. Uninstalled that driver and now running with restricted drivers again. I still have no sound. 

Its a hay-uge ask, but I need a step by step guide to be able to do this, my n00b-ness radiates like a skelped ****. So sorry for being a pain in the butt.

Many thanks for reading

---

### Post by porchrat on 2008-12-11
OK firstly let us know is the version you installed a 32bit or 64bit version of 8.10?

It makes a difference as to which driver you should install.

Keep in mind though that I know next to nothing about nvidia drivers as I seem to always end up running ATI.

It seems like the driver that you get from the nvidia site will have a filename that looks similar to this: NVIDIA-Linux-x86_64-177.82-pkg2.run (this is the 64bit version, but it still serves to demonstrate what you would need to do, please replace this filename with the name of the .run driver you've downloaded)

Download it to your desktop using your internet browser.  Then open a console window (to do this open the menu in the top left corner of the screen Applications --> Accessories --> Terminal).  Then type these commands:

```
cd ~/Desktop
sudo chown username:username NVIDIA-Linux-x86_64-177.82-pkg2.run
sudo chmod u+x NVIDIA-Linux-x86_64-177.82-pkg2.run
```

Where "username" is the name of the user you're logging in as.

Those commands will ensure that the file belongs to your user and that your user has permission to execute it.

It should then merely be a case of running the program you've downloaded by using the following command:

```
./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

It should then be a case of following the instructions.

If it doesn't work then you will probably need to download a few packages, but lets cross that bridge when we come to it.  For now try those commands.

Remember that you are messing with the graphics of Ubuntu and there may be consequences such as the GUI being unable to load.  In the event of that happening do not despair it can be reset using this command (you may want to write this one down in case you can't access the forums due to the lack of a GUI):

```
sudo dpkg-reconfigure xserver- xorg
```

---

### Post by dgtlkttn on 2008-12-11
> **porchrat said:**
> OK firstly let us know is the version you installed a 32bit or 64bit version of 8.10?

It makes a difference as to which driver you should install.

Keep in mind though that I know next to nothing about nvidia drivers as I seem to always end up running ATI.

It seems like the driver that you get from the nvidia site will have a filename that looks similar to this: NVIDIA-Linux-x86_64-177.82-pkg2.run (this is the 64bit version, but it still serves to demonstrate what you would need to do, please replace this filename with the name of the .run driver you've downloaded)

Download it to your desktop using your internet browser.  Then open a console window (to do this open the menu in the top left corner of the screen Applications --> Accessories --> Terminal).  Then type these commands:

```
cd ~/Desktop
sudo chown username:username NVIDIA-Linux-x86_64-177.82-pkg2.run
sudo chmod u+x NVIDIA-Linux-x86_64-177.82-pkg2.run
```

Where "username" is the name of the user you're logging in as.

Those commands will ensure that the file belongs to your user and that your user has permission to execute it.

It should then merely be a case of running the program you've downloaded by using the following command:

```
./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

It should then be a case of following the instructions.

If it doesn't work then you will probably need to download a few packages, but lets cross that bridge when we come to it.  For now try those commands.

Remember that you are messing with the graphics of Ubuntu and there may be consequences such as the GUI being unable to load.  In the event of that happening do not despair it can be reset using this command (you may want to write this one down in case you can't access the forums due to the lack of a GUI):

```
sudo dpkg-reconfigure xserver- xorg
```


OK, found the driver, its on my desktop, and this is the output from terminal:

digitalkitten@digitalkitten:~$ cd ~/Desktop
digitalkitten@digitalkitten:~/Desktop$ sudo chown NVIDIA-Linux-x86-177.82-pkg1.run
[sudo] password for digitalkitten: 
chown: missing operand after `NVIDIA-Linux-x86-177.82-pkg1.run'
Try `chown --help' for more information.


I can't get any further, whats missing?

---

### Post by juanoleso on 2008-12-11
You want:

```

sudo chown digitalkitten NVIDIA-Linux-x86-177.82-pkg1.run

```

You should be able to continue from there.

---

### Post by dgtlkttn on 2008-12-11
> **juanoleso said:**
> You want:

```

sudo chown digitalkitten NVIDIA-Linux-x86-177.82-pkg1.run

```

You should be able to continue from there.

I'm either getting "missing operand" or "no such file or directory" which i dont understand, seeing as I've already confirmed its there, and I want to use it. I have checked for any typos, and nothing. argh!

---

### Post by juanoleso on 2008-12-11
```

cd /home/digitalkitten/Desktop
sudo chown digitalkitten ./NVIDIA-Linux-x86_64-177.82-pkg2.run
sudo chmod u+x NVIDIA-Linux-x86_64-177.82-pkg2.run

```

If it is on your desktop, first change directory (cd) to your desktop, then modify the owner (chown).  When you reach the point
```

sudo chown digitalkitten ./NVID

```
if you hit tab it should fill the rest in.  If it doesn't fill in, then you may be in the wrong folder.

also, if it is on your desktop, you can right click on it, then go to permissions tab then make sure executable is checked and make sure that the owner says digitalkitten.

Then try and run.

---

### Post by dgtlkttn on 2008-12-11
> **juanoleso said:**
> ```

cd /home/digitalkitten/Desktop
sudo chown digitalkitten ./NVIDIA-Linux-x86_64-177.82-pkg2.run
sudo chmod u+x NVIDIA-Linux-x86_64-177.82-pkg2.run

```

If it is on your desktop, first change directory (cd) to your desktop, then modify the owner (chown).  When you reach the point
```

sudo chown digitalkitten ./NVID

```
if you hit tab it should fill the rest in.  If it doesn't fill in, then you may be in the wrong folder.

also, if it is on your desktop, you can right click on it, then go to permissions tab then make sure executable is checked and make sure that the owner says digitalkitten.

Then try and run.

Thank you! :) That was working and I was into the gui for installing it, then stopped and said I need to be in root. I also changed the permissions.

Still no cigar! LOL

---

### Post by Michael.Godawski on 2008-12-11
What about:
```
sudo chmod a+x NVIDIA-Linux-x86_64-177.82-pkg2.run
./NVIDIA-Linux-x86_64-177.82-pkg2.run

```

---

### Post by dgtlkttn on 2008-12-11
> **Michael.Godawski said:**
> What about:
```
sudo chmod a+x NVIDIA-Linux-x86_64-177.82-pkg2.run
./NVIDIA-Linux-x86_64-177.82-pkg2.run

```

Thanks guys! :) It just keep chucking out that I need to install invidia drivers as root. Ther permissions are all done, I've done everything that you've said, but it just keep telling me the same thing, Only option after that is to press ok.

This is the output afterwards...

digitalkitten@digitalkitten:~$ cd ~/Desktop
digitalkitten@digitalkitten:~/Desktop$ sudo chmod u+x NVIDIA-Linux-x86-177.82-pkg1.run
digitalkitten@digitalkitten:~/Desktop$ ./NVIDIA-Linux-x86-177.82-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 177.82.............................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
digitalkitten@digitalkitten:~/Desktop$

---

### Post by juanoleso on 2008-12-11
> **dgtlkttn said:**
> then stopped and said I need to be in root.

```
sudo ./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

or right click file then open with...
put in "gksu"

after that, not sure.

---

### Post by Michael.Godawski on 2008-12-11
```
sudo chmod a+x NVIDIA-Linux-x86_64-177.82-pkg2.run
./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

I do not know but I posted
**a+x**

and your posted command has **u**+x. Perhaps it is not important but please execute the commands exactly as they are posted. thx

---

### Post by dgtlkttn on 2008-12-11
> **Michael.Godawski said:**
> ```
sudo chmod a+x NVIDIA-Linux-x86_64-177.82-pkg2.run
./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

I do not know but I posted
**a+x**

and your posted command has **u**+x. Perhaps it is not important but please execute the commands exactly as they are posted. thx



Thanks again, Tried it that way, but its not working. Its still saying it needs to be installed as root.

---

### Post by Michael.Godawski on 2008-12-11
Then try what was suggested one post earlier by juanoleso

```
sudo ./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

---

### Post by dgtlkttn on 2008-12-11
> **Michael.Godawski said:**
> Then try what was suggested one post earlier by juanoleso

```
sudo ./NVIDIA-Linux-x86_64-177.82-pkg2.run
```

Thank so much for your patience. I ended up having to shut down x server and doing it that way

ctrl+alt+F1

sudo ./NVIDIA-Linux-x86-177.82-pkg1.run

took me to the installation and bobs your aunty :)

Unfortunately, I'm left with a white overlay on top of my screen and its flickering like mad.

I've pretty much had enough for tonight, Thank you again so much for being patient with me.

---

### Post by porchrat on 2008-12-12
> **dgtlkttn said:**
> Thank so much for your patience. I ended up having to shut down x server and doing it that way

ctrl+alt+F1

sudo ./NVIDIA-Linux-x86-177.82-pkg1.run

took me to the installation and bobs your aunty :)

Unfortunately, I'm left with a white overlay on top of my screen and its flickering like mad.

I've pretty much had enough for tonight, Thank you again so much for being patient with me.

OK seems like a graphics issue.  You will probably find that it is pretty common with nvidia cards.  I could research it for you, but as I mentioned previously I have had limited experience with nvidia cards so it will probably be faster to create another thread with a title something like "white flashing screen with nvidia 8200" or something (in absolute beginners as there people will give you assistance that is easier to follow for a new user).  You'll probably find there is a setting you'd need to change in your Xorg.conf or something.

Just for interests sake the difference between "u+x" and "a+x" is that the "u" means that is only adds execute permissions ("x") to that file for the user that owns the file, while the ("a") means it adds execute permissions to that file for all users that access your system.  So in short it doesn't make a difference whether you use "a" or "u" as you would still be able to execute (in windows they usually call it "run") the .run file, but it is generally a better practice (security-wise) to keep only your user able to access things that your user is dealing with, and deny permissions to other users.

If you're interested in learning more about permissions in linux you can start [here]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") (if you are going to use ubuntu then you will need to learn these things at some point)

Sorry I could'nt have been more help.

---

### Post by dgtlkttn on 2008-12-12
Thanks porchrat, thats a great help :)

I'll go and post a query for the flickering screen, I'm close to having a nosebleed lol

I've already been looking for some solutions in the forums and hopefully will get it sorted today. Once I can look at the screen for longer than a minute or so, I think a bit of educational research on my part wouldn't go a miss ;)

Thank you again, your help has been much appreciated!

---

