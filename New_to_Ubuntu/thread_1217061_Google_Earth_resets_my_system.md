---
title: "Google Earth resets my system"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by cooper77z on 2009-07-18
My computer won't work with google earth either. Every time I try to run the application, google earth, my system resets. I think it has something to do with a breach of security that google earth is perpetrating, but I am not certain. I am not trying to uninstall google earth because that would be a pain, but google earth continues to sit there on my machine as a program that doesn't work and that is suspect.

---

### Post by cooper77z on 2009-07-18
I am not typing that stuff into my terminal because I don't know what it means and I have seriously messed up my computer by typing stuff into the terminal before that I can't understand.

---

### Post by oldos2er on 2009-07-18
> **cooper77z said:**
> My computer won't work with google earth either. Every time I try to run the application, google earth, my system resets. I think it has something to do with a breach of security 

 GE will act that way if you do not have (video) 3d hardware acceleration enabled. It's nothing to do with security.

---

### Post by cooper77z on 2009-07-19
I think you are prolly correct oldos, but I don't have any idea how to enable the 3d and quite frankly google earth isn't worth possible messing up my system.

---

### Post by Malta paul on 2009-07-19
It more like your video card does not support 3D graphs. As I've just tried disabling Visual effects and running Google Earth and it worked OK. 
:)

---

### Post by 3rdalbum on 2009-07-19
> **cooper77z said:**
> I think you are prolly correct oldos, but I don't have any idea how to enable the 3d and quite frankly google earth isn't worth possible messing up my system.

What graphics card have you got, and have you tried looking in the Hardware Drivers program? (System > Administration > Hardware Drivers)

---

### Post by hyperdude111 on 2009-07-19
You need to enable your 3d drivers. Google earth will reset your DE if you don't have 3d enabled. Go System-admin-Hardware drivers.

Don't be paranoid about using terminal. It does the same as point and click just without the gui. Terminal is a very useful tool that has helped me many times.

---

### Post by cooper77z on 2009-07-19
sys-->admin--->hardware drivers does not exist. I am using a dell inspiron 1000 laptop computer. Is it possible that I don't even have a 3d video card/chip?

---

### Post by HotShotDJ on 2009-07-19
> **cooper77z said:**
> sys-->admin--->hardware drivers does not exist. I am using a dell inspiron 1000 laptop computer. Is it possible that I don't even have a 3d video card/chip?No.  I'm sure you have 3d video.  It is probably an integrated Intel video controller, which doesn't require any restricted drivers and, therefor, doesn't show up in the Hardware Drivers dialog.  You can double check, but you'll need to use the terminal (I PROMISE this command will not hurt your system):```
lspci -v | grep VGA

```
Please post back the out put of the above command, and also which version of Ubuntu you are running (Hardy? Jaunty?)

---

### Post by cooper77z on 2009-07-19
Ok, thanks for volunteering to help. I am using Hardy Server 8.04.2 with genome download. Here's the output from the command you mentioned "01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA controller])"

---

### Post by HotShotDJ on 2009-07-19
> **cooper77z said:**
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA controller])Ok... I was wrong.  You have the SIS M650 integrated video controller.  Make sure that xserver-xorg-video-sis is installed.  Do NOT try to use the outdated proprietary drivers, no matter what else you might find on a Google search. [-X

Having said that, you installed Ubuntu Server and then installed Gnome separately.  Is there a reason you did that?  How did you install Gnome?  Did you use the package "gnome-desktop?"  Remember, Ubuntu Server is not intended as a desktop distribution.  I'm wondering if there is something important missing in your Xorg set-up that is causing your problem.  Your video card SHOULD run Google Earth without a problem.

You might find it better to reinstall Ubuntu using Ubuntu Desktop, unless you have some good reason to be using the Server Edition.

---

### Post by cooper77z on 2009-07-19
I wanted to learn how to operate a server and host some of my own websites. I was pleasantly surprised at how awesome my system functioned after I installed gnome with this command "install x-window-system-core gnome and /etc/init.d/gm start

I like my system but Pitivi shuts down automatically just like google earth does. Cinelerra works fine. Can you help me on my other thread [http://ubuntuforums.org/showthread.php?t=1217634](http://ubuntuforums.org/showthread.php?t=1217634) ? Please?

I don't have any sensitive information on my computer right now.

---

### Post by HotShotDJ on 2009-07-19
Now, I think I'm getting a picture of what is going on.  You have tried to install desktop software in a piece-meal fashion, which has undoubtedly left out some very important components.

To get to a fully functioning desktop system from an Ubuntu Server installation, you should install the ubuntu-desktop package:```
sudo apt-get install ubuntu-desktop
```Once you reboot, you should have the problems with desktop apps (Google Earth, Pitivi, etc.) sorted.

Of course, it would be BETTER for you to be running Ubuntu Server on a machine dedicated to server functions and Ubuntu Desktop running on a separate machine dedicated to desktop use.  But, if that isn't an option, Ubuntu Server with gnome-desktop installed should work for you.

---

### Post by cooper77z on 2009-07-19
Thanks! I only have one machine right now. I fear that ubuntu desktop will slow my system down tremendously, so I'll leave it as is for now and store sensitive files on a cd or something.

---

