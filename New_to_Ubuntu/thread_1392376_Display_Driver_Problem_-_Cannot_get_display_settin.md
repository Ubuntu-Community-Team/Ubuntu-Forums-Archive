---
title: "Display Driver Problem - Cannot get display settings!"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by OCN on 2010-01-28
I am using GeForce 7600 GS

Not using the Nvidia X driver message you know... I searched all over, and seen this problem on many searches but no resolve issues.

I want to be able to connect my tv, I use to be able to when I first installed Ubuntu and now IdK.. Please help!

Using GLX-185 btw too

---

### Post by OCN on 2010-01-28
Somebody has to know what I am referring too " Nvidia X-driver" problems!!

---

### Post by warfacegod on 2010-01-28
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=884161&highlight=GeForce+7600+GS]("http://ubuntuforums.org/showthread.php?t=884161&highlight=GeForce+7600+GS")

---

### Post by OCN on 2010-01-28
Didn't seem to find the clues I was looking for!

---

### Post by Easy Limits on 2010-01-28
Did you try System -> Admin -> Hardware drivers?

I have the same video card as you but I don't really understand what you are trying to do.

---

### Post by OCN on 2010-01-29
trying to install the drivers and make it work.

---

### Post by OCN on 2010-01-29
> **Easy Limits said:**
> Did you try System -> Admin -> Hardware drivers?

I have the same video card as you but I don't really understand what you are trying to do.

Thanks Easy Limits, I am now one step closer.  

However I still get this message 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by JesterDev on 2010-01-29
[http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic](http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic)

Maybe that might help.

---

### Post by vivjo on 2010-01-29
What exactly is the problem as i have ubuntu on my PC with NVDIA GEForce 650E Graphics card , i'm having no troubles at all?
Regards
Viv

---

### Post by OCN on 2010-01-29
> **JesterDev said:**
> [http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic](http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic)

Maybe that might help.

Link is not working..

---

### Post by OCN on 2010-01-29
My problem is I can't get into the display settings without this error message...  I tried as it seems everything from all the searches Ive done.  ive manage now to mirror my tv and my lcd and I am oK with that for the time but I need to be able to access nvidia control panel.



> 

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by WannabeFantasma on 2010-01-29
I had this problem before...

Not sure what I did...

Think delete everything with NVIDIA from synaptic than installed it again...
Just not sure.... 
(any command to see what I did couple of weeks ago? :D )

---

### Post by warfacegod on 2010-01-29
> **OCN said:**
> Link is not working..

Try it again. It just opened for me.

---

### Post by FinnMcCool on 2010-01-29
> **OCN said:**
> It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. .
 
Yes! I was getting that errors message when I tried to Install anything Nvidia as well! Although this isn't much help as I'm still at work and can't fiddle around.

---

### Post by OCN on 2010-01-29
Link is working now, easy to use... not helping me, I restart the X Server, I install and reinstall the nvidia drivers ugh.. effed up.

---

### Post by OCN on 2010-01-29
I give up! 

I restart and comes back in low graphics modes.

---

### Post by OCN on 2010-01-29
BLOW THIS MOTHER #$#$010! up

---

### Post by audiomick on 2010-01-29
As far as I know, this
> It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

Appears when you have enabled the nVidia drivers, and try to start the setup thing from system> preferences
The problem is, when it starts it doesn't have root privileges, which it needs in order to be able to store the xorg.conf file.

Try
```
gksu nvidia-settings
```
to see if you can do what you need there.

---

### Post by warfacegod on 2010-01-29
Some BIOS's have settings for changing the Graphics card memory. Try looking in there.

---

### Post by realzippy on 2010-01-29
> **warfacegod said:**
> Some BIOS's have settings for changing the Graphics card memory. Try looking in there.


Ignore this.
run,as suggested,[I]gksudo nvidia-settings
[/I]
but it seems as you have not installed the driver correctly.Reinstall..
(Administration/Hardware Drivers)

---

### Post by audiomick on 2010-01-29
@ warfacegod

> **realzippy said:**
> Ignore this.
run,as suggested,[I]gksudo nvidia-settings
[/I]
but it seems as you have not installed the driver correctly.Reinstall..
(Administration/Hardware Drivers)

nah nah...;)

---

### Post by warfacegod on 2010-01-29
My BIOS has a setting to change the video memory. No matter how many times I reinstall nVidia drivers or configure xorg, it refuses to run normal graphics unless that setting is correct. Period.

---

### Post by realzippy on 2010-01-29
> **warfacegod said:**
> My BIOS has a setting to change the video memory. No matter how many times I reinstall nVidia drivers or configure xorg, it refuses to run normal graphics unless that setting is correct. Period.

..so you have integrated graphics?
OP has a 7600 GT which is a PCI/AGP card,,,

---

### Post by ebharv on 2010-01-29
> **OCN said:**
> BLOW THIS MOTHER #$#$010! up

Are you running SLI? 
If so try this [post]("http://ubuntuforums.org/showthread.php?p=8389348#post8389348") then add this to the device section:
```
Option "SLI" "On"
```
or
```
Option "SLI" "Auto"
```

If nothing's working and you're using one card try this:

*** Make sure you have a way getting back to the internet first. ***

1. Go to [nVidia's driver downloads]("http://www.nvidia.com/Download/index5.aspx?lang=en-us") and download the driver to a folder.

2. Completely remove any nvidia stuff through Synaptic.

3. Open a terminal and do:
```
cd /path/to/folder/where/file/is
```
```
chmod +x NVIDIA-Linux........
```

4. Print the rest of the post then hit CRTL+ALT+F1

5. Login to the text based console.

6. Type this:
```
cd /path/to/folder/where/file/is
```
```
sudo /etc/init.d/gdm stop
```
This kills the graphical part of the OS. You can check to make sure by hitting CTRL+ALT+F7. You shouldn't see anything. Hit CTRL+ALT+F1 to get back.

7. Type this (you should still be in the folder where the file is):
```
 sudo ./NVIDIA-Linux............
```

8. Answer the questions and wait for it to finish.

9. Type this:
```
sudo shutdown -r 0
```
This should reboot your system.

I believe this is the method nVidia prefers for installation of their driver. I could be wrong though don't quote me.

---

### Post by warfacegod on 2010-01-29
> **realzippy said:**
> ..so you have integrated graphics?
OP has a 7600 GT which is a PCI/AGP card,,,

The 7600 GT is available in laptops. Would that not make it integrated?

---

### Post by audiomick on 2010-01-29
> **warfacegod said:**
> The 7600 GT is available in laptops. Would that not make it integrated?

No that's still a plug-in card. He means the mother boards with built in graphic chips. Now the BIOS thing makes sense.

---

### Post by warfacegod on 2010-01-29
> **audiomick said:**
> No that's still a plug-in card. He means the mother boards with built in graphic chips. Now the BIOS thing makes sense.

My laptop has the nVidia Geforce 5200. I can't take it out without soldering, I'd call that integrated

---

### Post by OCN on 2010-01-29
audiomick

gksu nvidia-settings
>
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I went to Admin/Hardware to upgrade the driver from glx-173 to 185 now

AGP, not SLI.

---

### Post by OCN on 2010-01-29
With the restart, came back up with a blank screen.. had to reboot and ESC to previous version with low graphics again.

---

### Post by audiomick on 2010-01-29
> **warfacegod said:**
> My laptop has the nVidia Geforce 5200. I can't take it out without soldering, I'd call that integrated

good point, and if your bios can play with it's memory it's pretty integrated, I suppose. Guess your right. (again... Damn.)

---

### Post by OCN on 2010-01-29
Activated Version  173 - as far as that I don't know... I am not going to restart or do anything cause I need advise on something new... 

Thinking in circles, writing in circles

---

### Post by OCN on 2010-01-29
Version 173 is activated but is not in use - ?! I am running in low graphics mode.

---

### Post by warfacegod on 2010-01-29
Has anybody suggested that you use EnvyNG?

```
sudo apt-get install envyng-core
```

It will search out the most appropriate drivers and ask you which one you want it to install.

---

### Post by OCN on 2010-01-29
Hey I didn't think of going to nvidia site and downloading the driver from there...

NVIDIA-Linux-x86-190.53-pkg1.run  How do I run this

---

### Post by OCN on 2010-01-29
> **warfacegod said:**
> Has anybody suggested that you use EnvyNG?

```
sudo apt-get install envyng-core
```It will search out the most appropriate drivers and ask you which one you want it to install.


I will try

---

### Post by audiomick on 2010-01-29
> **OCN said:**
> Hey I didn't think of going to nvidia site and downloading the driver from there...

NVIDIA-Linux-x86-190.53-pkg1.run  How do I run this

I think ebharv gave you complete instructions in post #24, didn't he?

---

### Post by OCN on 2010-01-29
> **warfacegod said:**
> Has anybody suggested that you use EnvyNG?

```
sudo apt-get install envyng-core
```It will search out the most appropriate drivers and ask you which one you want it to install.

Didn't work, chose the best option EnvyNG offered and blank screen came up and and had to recovery to boot in. 

> **audiomick said:**
> I think ebharv gave you complete instructions in post #24, didn't he?

I will be back in few minutes, I will try this out... I saw SLI and just past it up but I do see now that there is other good information

---

### Post by OCN on 2010-01-29
I am such a noob right now trying to learn that Post #24 is hard for me to understand... I don't understand how to launch the nvidia driver file I have with the *.run ext

---

### Post by OCN on 2010-01-29
Synaptic manager I wiped all the nvidia drivers and config files

---

### Post by OCN on 2010-01-29
Now I was finally able to run the run file, says 

ERROR: nvidia-installer must be run as root

                                       OK

---

### Post by OCN on 2010-01-29
taking a break, be back in a few... insane.. madness

---

### Post by realzippy on 2010-01-29
You will have to reinstall the nvidiadriver every kernel update if you install it manually.You can make the 195.30 driver "appear" in Administration/Hardwaredrivers by adding it's source.Open terminal,type:

[B]
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install nvidia-glx-195 nvidia-195-modaliases

[/B]

..no need for madness,a 7600 gt should run fine finally...

---

### Post by OCN on 2010-01-29
> **realzippy said:**
> You will have to reinstall the nvidiadriver every kernel update if you install it manually.You can make the 195.30 driver "appear" in Administration/Hardwaredrivers by adding it's source.Open terminal,type:

[B]
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install nvidia-glx-195 nvidia-195-modaliases

[/B]

..no need for madness,a 7600 gt should run fine finally...

Failed - restarted in low graphics mode.

---

### Post by OCN on 2010-01-29
oh no I am going insane

welcome to the dark side of the imagination 

circles circlces circles circles circles

---

### Post by warfacegod on 2010-01-29
I hate to be the one to say this but I think you may want to consider a fresh install of Ubuntu.

---

### Post by OCN on 2010-01-29
I agree, I had my fun for the last 5 months as a noob.


eh aWEIT, you think this will solve this, will I need to go though this BS when I install ubuntu over again or will it detect my video card.

---

### Post by warfacegod on 2010-01-29
> **OCN said:**
> I agree, I had my fun for the last 5 months as a noob.


eh aWEIT, you think this will solve this, will I need to go though this BS when I install ubuntu over again or will it detect my video card.

I honestly don't know.

The only thing I can say is that... well, I'm trying to come up with something more to say about this whole mess but I'm at a loss. If you reinstall just make sure your connected to the internet for it.

---

### Post by OCN on 2010-01-29
going to wait until my laptop arrives here, then I can just mess around with this machine.

---

### Post by warfacegod on 2010-01-29
Your sense of humor is much akin to my own. (circles, circles)

---

### Post by realzippy on 2010-01-30
> **OCN said:**
> Failed - restarted in low graphics mode.

What does failed mean?
any error messages during installation??

---

