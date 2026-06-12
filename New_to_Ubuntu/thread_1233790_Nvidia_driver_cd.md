---
title: "Nvidia driver cd"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by jdc.84 on 2009-08-07
Hi,

I have an Nvidia 512mb Graphics card in my HP xw4600 Workstation.

I've just installed the new Ubuntu 9.04 with all the updates.

The computer will not resume from suspend. When i try to wake it up all i get is one of the fans goes into overdrive and a blank screen.

There are a lot of threads saying that the problem is due to the graphics card driver. 

I found one that claims to have the answer but i'm unsure as to use it:
[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=7743944#post7743944
[/COLOR]

I have the original Nvidia driver cd that came with the computer; is there no way of using this instead of the freesource one?

Tnanks,
John

---

### Post by thezood on 2009-08-07
> **jdc.84 said:**
> Hi,

I have an Nvidia 512mb Graphics card in my HP xw4600 Workstation.

I've just installed the new Ubuntu 9.04 with all the updates.

The computer will not resume from suspend. When i try to wake it up all i get is one of the fans goes into overdrive and a blank screen.

There are a lot of threads saying that the problem is due to the graphics card driver. 

I found one that claims to have the answer but i'm unsure as to use it:
[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=7743944#post7743944
[/COLOR]

I have the original Nvidia driver cd that came with the computer; is there no way of using this instead of the freesource one?

Tnanks,
John

You can't install a Windows driver in Ubuntu but you can use the restricted driver supplied by NVIDIA instead of the opensource one. Try System -> Administration -> Hardware drivers and see if you can install the restricted NVIDIA driver. If not, report back and we'll take it from there.

---

### Post by theozzlives on 2009-08-07
The CD most likely only has Windows drivers. I downloaded my driver from the NVIDIA web site.

---

### Post by jdc.84 on 2009-08-07
Ok the driver that's being used at the mo is:
"NVIDIA accelerated graphics driver (version 180) [recommended]"

I can choose one other from the hardware drivers box and that's the "version 173"

I need to reboot into windows for the NVIDIA website to be able to scan my graphics card...

---

### Post by mapes12 on 2009-08-07
> **jdc.84 said:**
> Ok the driver that's being used at the mo is:
"NVIDIA accelerated graphics driver (version 180) [recommended]"

I can choose one other from the hardware drivers box and that's the "version 173"

I need to reboot into windows for the NVIDIA website to be able to scan my graphics card...There should be an option the make sure that recommended driver (version 180) is "Activated". Is it?

---

### Post by jdc.84 on 2009-08-07
Yes the 180 version is active.


I've just been on the nvidia website and downloaded the driver for my Quadro FX1700:  NVIDIA-Linux-x86-185.18.31-pkg1.run

When i try to open it, it says:
"Could not open the file /home/john/Desktop/NVIDI…ux-x86-185.18.31-pkg1.run using the Unicode (UTF-8) character coding."

---

### Post by jdc.84 on 2009-08-07
ha! didn't realise the sunglasses dude was '8' with a bracket!

---

### Post by thezood on 2009-08-07
> **jdc.84 said:**
> Yes the 180 version is active.


I've just been on the nvidia website and downloaded the driver for my Quadro FX1700:  NVIDIA-Linux-x86-185.18.31-pkg1.run

When i try to open it, it says:
"Could not open the file /home/john/Desktop/NVIDI&#8230;ux-x86-185.18.31-pkg1.run using the Unicode (UTF-8) character coding."

Are you sure you need the new version? The 180 version is also NVIDIA and not open source. I too never got suspend to work in Ubuntu on my NVIDIA based machine (graphics & chipset) and I tried several driver versions. It works perfectly on my Intel based machine, though. If you're absolutely sure you need 185.18.31, you need to open a terminal, and type this:
```

cd ~/Desktop
chmod +x ./NVIDI&#8230;ux-x86-185.18.31-pkg1.run
./NVIDI&#8230;ux-x86-185.18.31-pkg1.run

```
If you do this, you need to check for driver updates yourself since Ubuntu will no longer be able to d this for you. 

Also, I think there's something wrong with the file name here in the post but you get the picture. Just copy and paste the correct file name.

---

### Post by 3rdalbum on 2009-08-07
> **thezood said:**
> If you're absolutely sure you need 185.18.31, you need to open a terminal, and type this:
```

cd ~/Desktop
chmod +x ./NVIDI&#8230;ux-x86-185.18.31-pkg1.run
./NVIDI&#8230;ux-x86-185.18.31-pkg1.run

```

Not quite, couple of problems there.

Install the Linux headers and Build Essential:

```
sudo apt-get install linux-headers build-essential
```

Remove the old driver:

```
sudo apt-get remove --purge nvidia-*
```

Log out and press Control-Alt-F2. Log into this new text terminal. Type:

```
sudo -i
killall gdm   (this kills the X server)
cd ~/Desktop
chmod +x NV   (now press Tab and it will autocomplete)
./NV   (press Tab to autocomplete)

```

Answer Yes to everything. When it's done:

```
sudo gdm
```

And you'll be able to log in and use your new driver.

You need to reinstall the driver every time you update the kernel. That's why it's better to use the repository version.

---

### Post by jdc.84 on 2009-08-07
Ah right thanks for the help. I really am a complete beginner at this.

Based on the last two posts from, 'thezood' and '3rdalbum', I've decided to give the fix a go on the thread mentioned at the top of this one first before intalling the new driver.

___________________________ 

I have completed the first step: POST_VIDEO=true to false

The post then says another line specifically for Nvidia users, but i do not know what it means:
[COLOR="Blue"]> A note: Nvidia users will need to add this to their device section of their /etc/X11/xorg.conf file
code:
```
Option "NvAGP" "1"
```[/COLOR]
Any ideas? I tried typing, /etc/X11/xorg.conf, into terminal but the response was 'access denied'

---

### Post by 3rdalbum on 2009-08-07
> **jdc.84 said:**
> 

I have completed the first step: POST_VIDEO=true to false

The post then says another line specifically for Nvidia users, but i do not know what it means:
[COLOR="Blue"][/COLOR]
Any ideas? I tried typing, /etc/X11/xorg.conf, into terminal but the response was 'access denied'

You need to open the /etc/X11/xorg.conf file, as root (it's a system-wide location), in a text editor.

Easiest way to do that is:

```
gksudo gedit /etc/X11/xorg.conf
```

gksudo makes the rest of the command run as root
gedit is a text editor

I don't know if the NvAGP bit will really help you - your card is probably PCI-E, not AGP.

---

### Post by jdc.84 on 2009-08-07
Ok. Trying to install the new driver using your instructions.

All went well untill i tryed to get the desktop directory :

Typed: cd ~/Desktop
and it just said bad directory or something

any ideas?

---

### Post by 3rdalbum on 2009-08-07
> **jdc.84 said:**
> Ok. Trying to install the new driver using your instructions.

All went well untill i tryed to get the desktop directory :

Typed: cd ~/Desktop
and it just said bad directory or something

any ideas?

Sorry I think that should just be:

```
cd Desktop
```

(capitalisation is important, and I'm assuming the installer is on the desktop)

As you might have gathered, if you can learn a bit of command-line it will help you in Linux. You can get by without it, but it helps a lot for these sorts of scenarios.

---

### Post by jdc.84 on 2009-08-09
Right, i've managed to get the file to try and open but it simply says it needs to be open in root and doesn't work

Any ideas?

---

### Post by jdc.84 on 2009-08-09
(i mean all the instructions were followed and the file opened in the way you instructed)

---

