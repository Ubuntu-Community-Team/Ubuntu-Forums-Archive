---
title: "NVIDIA Woes"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by django1fete on 2009-10-14
I run Ubuntu 9.04, and am having a hell of a time getting the Nvidia driver to work. 
When I view videos I have to use the small screen, when I expand to full screen, the browser shuts down.
When I reboot I got this error message:

[COLOR=SeaGreen]UBUNTU is running in low graphics mode
The following error was encountered:
You may need to update your configuration to solve this.
(EE) Nvidia (0) Failed to load the Nvidia Kernel Module
(EE) Nvidia (0) Abort
(EE) Screens found but none have a usable configuration[/COLOR]

[COLOR=Black]Does anyone have a suggestion/answers?

Thnx!
[/COLOR]

---

### Post by NightwishFan on 2009-10-14
In your post please explain the version of the Nvidia driver you are using, how you installed it, and your hardware (graphic card) model.

To tell us your graphic card model, open a terminal and run this command.
```
sudo lshw | grep Nvidia
```

---

### Post by ibuclaw on 2009-10-14
New Support thread created, as this is a separate issue.

---

### Post by django1fete on 2009-10-14
Thank you so much for your response!
The nvidia driver i am using is the Nvidia V 180 as recommended, it was installed by the Computer store and the card is Biostar MCP6P M2+, I dont know how to "open a terminal" and Ive d/loaded a driver from the Nvidia ppl, but cant open it(the computer cant read it)...Im in over my head here, I see that now...all I want o do is to maximize the resolution and figure out why my browser keeps closing when I try to go to Full Screen mode....
I think thats the info you needed...anyway, thanks for your help, I kinda feel like Im stranded in a Desert with no water!:)

---

### Post by phidia on 2009-10-14
A general guide on the approved way to install the nvidia proprietary driver is [here]("http://www.psychocats.net/ubuntu/nvidia"). The community docs give more detail but the above guide should be sufficient.

---

### Post by wojox on 2009-10-14
Here's a tutorial I used for installing my 173.***: [HowTo: NViDIA 185.18 Drivers in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1125400")

You can install it that way for the 180.***

---

### Post by NightwishFan on 2009-10-15
Sorry I was not here to answer, if you continue to receive problems I will try to help you. I am fairly experienced in using the Nvidia driver.

---

### Post by thiebaude on 2009-10-15
System-Administration-Hardware Drivers-choose the recommended driver-install it-reboot-gksudo nvidia-settings choose the resolution you want to use, then Save to X configutation, exit, reboot, and now see if that works.

---

### Post by JDShu on 2009-10-15
I have generally found that the easiest way is to get rid of all the nvidia drivers preinstalled into ubuntu, and then installing the driver from the website:

(replace "NVIDIA-Linux-x86_64-185.18.14-pkg2.run" with whatever the file you downloaded is called)

1. Download the driver to your desktop.
2. Press CTRL-ALT-F1
3. Login with your username and password.
4. cd to your desktop: cd ~/Desktop
5. Close X, if you are using GNOME this is : sudo /etc/init.d/gdm stop
6. Get rid of the default nvidia drivers : sudo apt-get purge nvidia*
7. now run the driver script: sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
8. Follow the instructions, it will tell you that your gcc compiler does not match but this can be ignored.
9. When finished, reboot: reboot

---

### Post by skymera on 2009-10-15
I've used Envy ever since 7.04 (Now called EnvyNG) and it's worked perfect for my 7900GS, 8800GT, HD4870, GTX260 over the past years.

It's in the repos. ```
 sudo apt-get install envyng-core 
```
then run ```
 sudo envy -t 
``` 

It might be envyng -t

---

### Post by django1fete on 2009-10-15
Ive tried a few and no luck, its still boots up in "low graphics mode" though, I have noticed under Administration I now have an Nvidia X server settings option, when I click on that the "new" error message says "[COLOR=Green]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server[/COLOR]."
Where and how would i do that? I think Im getting closer...am I? Does anybody know?:)

---

### Post by 3rdalbum on 2009-10-16
Full-screen Flash has some issues with performance and possibly reliability. You'd be better off using the Compiz "Enhanced Zoom" plugin to zoom in on the videos, which works better than using the actual full-screen function in Flash.

---

### Post by django1fete on 2009-10-16
> **JDShu said:**
> I have generally found that the easiest way is to get rid of all the nvidia drivers preinstalled into ubuntu, and then installing the driver from the website:

(replace "NVIDIA-Linux-x86_64-185.18.14-pkg2.run" with whatever the file you downloaded is called)

1. Download the driver to your desktop.
2. Press CTRL-ALT-F1
3. Login with your username and password.
4. cd to your desktop: cd ~/Desktop
5. Close X, if you are using GNOME this is : sudo /etc/init.d/gdm stop
6. Get rid of the default nvidia drivers : sudo apt-get purge nvidia*
7. now run the driver script: sudo sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
8. Follow the instructions, it will tell you that your gcc compiler does not match but this can be ignored.
9. When finished, reboot: reboot


I tried this and couldnt get patstep 4, i got an error message (no such file!)...thanks tho...I thought I had it this time!:)

---

### Post by django1fete on 2009-10-16
> **3rdalbum said:**
> Full-screen Flash has some issues with performance and possibly reliability. You'd be better off using the Compiz "Enhanced Zoom" plugin to zoom in on the videos, which works better than using the actual full-screen function in Flash.


Im learning a lot from this..but this route, doesnt give me the benefits of an enhanced video card does it? Like the hyper resolution and stuff?
Thanks...really appreciate your taking the time to help out this knuckle head!;)

---

### Post by django1fete on 2009-10-16
> **wojox said:**
> Here's a tutorial I used for installing my 173.***: [HowTo: NViDIA 185.18 Drivers in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1125400")

You can install it that way for the 180.***


Thank you for your efforts, i had a chance to look at your instructions...this is all way over my head, I dont have a degree in computer science, I dont even understand the difference between Linux and Microsoft...just way too technical and I quickly loose my way with all the codes...thanks anyway

---

### Post by ikisham on 2009-10-16
Try this:
-Click on the panel Applications>Accessories>Terminal
-a terminal window will open
-type```
sudo apt-get purge nvidia*
```
-type your password (you will not see it, just type and press enter)
-when it finishes, reboot (restart).
-when you're back, open the Terminal again and type
```
sudo apt-get autoremove
```
-type your password
-when it finishes, type
```
sudo apt-get install nvidia-glx-180
```
-after it's finished, reboot.

Then please, read [this]("http://www.ubuntupocketguide.com/download_main.html") (it's light and informative).

---

