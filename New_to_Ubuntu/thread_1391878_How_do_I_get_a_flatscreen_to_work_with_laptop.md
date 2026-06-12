---
title: "How do I get a flatscreen to work with laptop?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by theopneustos on 2010-01-27
I loaded Ubuntu CE 9.10 on my HP Pavillion laptop. Up till now, I used this laptop with XP home edition like a desktop PC and have a seperate 19" screen (Genisat 9005L) So, the laptop is mostly closed while I use the flatscreen, so convenient. 

When I start Ubuntu, the flatscreen (plugged into the VGA port) just flickers a purple array of colours, but the laptop's screen functions well. 

I am an absolute beginner with Ubuntu, is there any solution? How can I get the flatscreen to work?

---

### Post by moody_mark on 2010-01-27
Hi, open up your laptop so your have a workable screen, go to the "System --> Preferences --> Display" menu, you'll open up a dialog box for display preferences, you should see the two screens in there. You can click on the screen and change the resolution size and such the like.

---

### Post by warfacegod on 2010-01-27
You may need to go to: System> Admin.> Hardware Drivers and activate the recommended video driver.

---

### Post by theopneustos on 2010-01-27
> **moody_mark said:**
> Hi, open up your laptop so your have a workable screen, go to the "System --> Preferences --> Display" menu, you'll open up a dialog box for display preferences, you should see the two screens in there. You can click on the screen and change the resolution size and such the like.
I tried this, on your advise, but it only shows 1 screen. Try as i like, it doesn't detect the flatscreen

---

### Post by theopneustos on 2010-01-27
> **warfacegod said:**
> You may need to go to: System> Admin.> Hardware Drivers and activate the recommended video driver.
I tried, but when I search for drivers, i just get the reply "No propriety drivers are in use on this system".
It also doesn't show any drivers listed.

---

### Post by tom.swartz07 on 2010-01-27
> **theopneustos said:**
> I tried, but when I search for drivers, i just get the reply "No propriety drivers are in use on this system".
It also doesn't show any drivers listed.

What video card do you have?

Also, could you make sure the cable is plugged in, open a terminal and type ```
xrandr
``` and copy/paste the output here?

---

### Post by warfacegod on 2010-01-27
> **theopneustos said:**
> I tried, but when I search for drivers, i just get the reply "No propriety drivers are in use on this system".
It also doesn't show any drivers listed.

You probaly need to enable Restricted Extras in Software Sources.

An alternative to Hardware Drivers is EnvyNG:

```
sudo apt-get install envyng-core
```

---

### Post by theopneustos on 2010-01-29
> **warfacegod said:**
> You probaly need to enable Restricted Extras in Software Sources.

An alternative to Hardware Drivers is EnvyNG:

```
sudo apt-get install envyng-core
```
I entered this line as you instructed, and i got the following reply: (I copied and pasted the reply:)

sudo apt-get install envyng-core
[sudo] password for jannie: 
Sorry, try again.
[sudo] password for jannie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-core

Is there a way to install proprietry drivers? The program says no such drivers is installed.

---

### Post by theopneustos on 2010-01-29
> **tom.swartz07 said:**
> What video card do you have?

Also, could you make sure the cable is plugged in, open a terminal and type ```
xrandr
``` and copy/paste the output here?
My video card is a Nvidia Geforce Go 7400

---

### Post by audiomick on 2010-01-29
Did you check, as warfacegod suggested, that "restricted" is enabled in your package sources? You didn't mention it.

---

### Post by dolphinaura on 2010-01-29
32 bit
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

64 bit
[http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html)

---

### Post by theopneustos on 2010-01-29
> **audiomick said:**
> Did you check, as warfacegod suggested, that "restricted" is enabled in your package sources? You didn't mention it.
Yes, that box is enabled

---

### Post by Greenwidth on 2010-01-29
See driver posting above (by dolphinaura)

You will need to stop gdm before installing.

CTRL + ALT + F1 - to switch to tty1

sudo service gdm stop - to stop gdm

sudo sh path/to/driver/NVIDIA_blah_blah.run

---

### Post by Greenwidth on 2010-01-29
Another way is to add the nvidia ppa to your software sources, which is probably better as when you get a kernel upgrade you won't have to reinstall them.

ppa:nvidia-vdpau/ppa

open synaptic:
System > Admin > Synaptic

settings tab:
Repositories

Other software > add
paste ppa:nvidia-vdpau/ppa

reload

search for nvidia-190

mark for install

---

### Post by theopneustos on 2010-01-29
People, I am quite frustrated. I have just loaded Ubuntu, don't have a handle on all the commands, and without my flatscreen my laptop (battery not working) its screen too small for my eyes. I just want to get this flatscreen working, so i can see better! I downloaded that Nvidia file on the link, but now I don't know where Ubuntu stores it... Please give me that info?

---

### Post by audiomick on 2010-01-29
there should be a "downloads" folder in your home folder. It should be in there.

---

### Post by theopneustos on 2010-01-29
> **Greenwidth said:**
> Another way is to add the nvidia ppa to your software sources, which is probably better as when you get a kernel upgrade you won't have to reinstall them.

ppa:nvidia-vdpau/ppa

open synaptic:
System > Admin > Synaptic

settings tab:
Repositories

Other software > add
paste ppa:nvidia-vdpau/ppa

reload

search for nvidia-190

mark for install
Thanks Greenwidth! This one worked! Thanks everyone. I appreciate. Keep up the good work! 
Now I can start learning Ubuntu....:D

---

### Post by Wizard of Cause on 2010-03-08
I'm not sure if this is the right place to ask, but I'm experiencing a similar problem getting my LCD TV to connect to my laptop via S-video.

I am working with an ATI Radeon x1200 graphics card. Whenever I try to update the drivers, it still can't find the s-video port.

Can anyone help?

---

### Post by colmeweb on 2010-08-21
Hi everybody,
I did everything in

 					Originally Posted by **Greenwidth** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8744736#post8744736") 				
 				[I]Another way is to add the nvidia  ppa to your software sources, which is probably better as when you get a  kernel upgrade you won't have to reinstall them.

ppa:nvidia-vdpau/ppa

open synaptic:
System > Admin > Synaptic

settings tab:
Repositories

Other software > add
paste ppa:nvidia-vdpau/ppa

reload

search for nvidia-190

mark for install


but when I searched for nvidia-190 it wasn't there. Anybody got any advice that could help

Thanks
[/I]

---

