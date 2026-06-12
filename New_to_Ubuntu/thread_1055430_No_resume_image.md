---
title: "No resume image"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by peterpanchamp on 2009-01-30
So, I'm completely new to this system. I just installed 8.10 and everything was going fine, I installed all the updates and tried to install nvidia drivers(177 I think). When I reboot I get this message.

kinit: No resume image, doing normal boot...


When I try to start the xserver I end up with:
Fatal server error: 
no sreens found
giving up. 

The giving up part is a nice touch, since that's what I feel like doing at the moment. Any help would be extremely appreciated.

---

### Post by yeats on 2009-01-30
the kinit: no resume image is not a problem - that just means the system did not find a "saved state" to load (like when you set your computer to hibernate/suspend, for instance).

The xserver problem is where you should concentrate your efforts :-).  I've fixed this on 8.04 but apparently 8.10 uses a different configuration.  Perhaps my answering this will move your question to the top of the forum ;-).

---

### Post by lukedupree on 2009-02-01
I have exactly the same problem and it occured the same way. I would guess it's related to the nvidia drivers but as i am new to Linux I have no idea where to go with this. How can I get xserve back, that is the gui correct? I dont get any knit. i can login in the shell but can't bring up the gui. I am running 8.10, I was running 8.04 LTS but had sound issues I could not recolve. I also have Suse 11.1 installed and have had no issues like this. Any help?

---

### Post by Crafty Kisses on 2009-02-01
If you post your hardware specs (monitor, mouse, keyboard, graphics card) and the output of:
```
cat /etc/X11/xorg.conf
```Either I or somebody else can assist you further.

---

### Post by vikramaditya on 2009-02-01
If you can boot into recovery mode, remove your previous nvidia driver installation.  Then, restart _in recovery mode again_ and choose the option to "fix X" (something like that).  This takes only a second or so and returns no visible benefit.  Then, finish booting, open Terminal and paste
```
sudo apt-get install envyng-gtk
```
Hit your "Enter" key and type your password at the prompt( if you're unfamiliar with Terminal, don't be alarmed that nothing appears to happen while you're typing the password - that's normal).  Hit the "Enter" key again and, at the next pause/prompt, type the letter y, press Enter key again and wait for the entire process to finish.  Restart normally whilst reciting a small prayer to "Magneto", the god of ghost-free reception.  If he smiles upon your endeavours, you'll have a functional installation when it's all over.  Good hunting! :)

---

### Post by Victormd on 2009-02-05
I'm having the exact problem. Ultimately I formated and re-installed 8.10 and after running the updates and installing restricted drivers, the problem came back. This started after I installed my second graphics card (going for SLI). I know it's related to the graphics card but not really sure what to do. I've tried recovery mode, repair broken package, x-fix (don't remember the actual name) option and nothing seems to work. I checked my xorg.conf and it looks just like the "failsafe" xorg in /etc/X11.

If anyone has any suggestions, please let me know.
Thanks!

---

### Post by Victormd on 2009-02-06
Bump...

---

### Post by lukedupree on 2009-02-06
Well since i can't get Ubuntu to come up in GUI I can't get the system specs reported by Ubuntu, mostly because I don't know how. But i can tell you what my system is.

Mainboard - ASUS M3N32-D 750a Chipset, not using onboard graphics
AMD Phenom Quad Core 2.6 GHZ 125w Processor
Dual - PNY Nvidia Gforce 9800 GT graphics cards currently setup with SLI cable in place. (may be the hole problem, but not willing to make hardware changes to run Ubuntu)
4 GB Kingston DDR2 ram
1 Segate SATA 400GB 7200 HD
1 IDE Segate 120GB 5400 HD

Ubuntu 8.10 is installed on the IDE drive as well as Suse 11.1

Vista, XP and Windows7 beata on the SATA

Also, I didn't follow how to uninstall the Nvidia drivers in the shell. Not sure uninstalling the drivers will be worth while anyway. Without the drivers there is no high end graphics functionality in Ubuntu 8.10. It keeps asking me if I want to install the driver to enable the effects. 

I absolutely love the look and feel of Ubuntu, hope i can get this resolved.

Thanks

---

### Post by Victormd on 2009-02-06
> **lukedupree said:**
> Mainboard - ASUS M3N32-D 750a Chipset, not using onboard graphics
AMD Phenom Quad Core 2.6 GHZ 125w Processor
Dual - PNY Nvidia Gforce 9800 GT graphics cards currently setup with SLI cable in place. (may be the hole problem, but not willing to make hardware changes to run Ubuntu)
4 GB Kingston DDR2 ram
1 Segate SATA 400GB 7200 HD
1 IDE Segate 120GB 5400 HD

My setup is very similar to this (except ASUS M3N72 and 2xGeforce 8800GT) and even though SLI has been incorporated in Ubuntu for a while, this is where the problem is.

I haven't tried uninstalling the Nvidia drivers yet but instead, installed the latest (180.22) and still no luck...

I'm going to try a few things before giving up on 8.10 and going to Jaunty (9.04) alpha.

---

### Post by Victormd on 2009-02-06
Ok, after some searching and testing, I found out that all I need to do is add two lines to xorg.conf... yep, 2 lines. Assuming that you installed the restricted driver, restarted and got this error, all you have to do is boot into recovery mode, drop to root and edit your xorg.conf. First:
```
sudo lspci | grep VGA
```
and this will output something like:
> 0[COLOR="Red"]**2**[/COLOR]:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
0[COLOR="Red"]**3**[/COLOR]:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
Remember the hightlighted number (2 or 3 - these may or may not be different on your computer), then edit xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
and under [COLOR="Red"]**Section "Device"**[/COLOR] include:
> BusID "PCI:X,0,0"
Option "sli" "auto
where the [COLOR="Red"]**X**[/COLOR] in the first line is the number you acquired earlier (2 or 3).

If you played around with it as much as I did, then it's probably a good idea to do a clean install and include the above lines before rebooting (after installing the restricted drivers). If you don't want to reinstall, try adding the lines to xorg.conf anyway and that should work as well...
Hope this helps.

---

### Post by lukedupree on 2009-02-07
Well I went back to 8.04 hardy. It works great with the video but the sound is corrupted, sounds garbeled. That's why I went to 8.10 in the first place was the issue with 8.04 sound. Starting to feel like I'm on a windows PC. Always somehting. I'll mess around with the sound and see if i can fix it. Otherwise i may just stick to SUSE 11.1. If I get the time to re install 8.10 I'll give your fix a try.

Oh and my MB is a m3n72-D, I just had a type-o previously. Have you ran 8.04 on that board?

---

### Post by bixejo on 2009-02-07
My desktop computer is also equipped with a NVIDIA graphics card. When I tried to upgrade to Ubuntu 8.10 (I'm currently running 8.04) I got a warning pop-up window saying that there is no NVIDIA controller working properly in 8.10, and gave me the chance of canceling the upgrade process, and of course that's what I did indeed.


I don't know more details, but I would suggest you to keep on running Ubuntu 8.04 LTS instead of 8.10 and somehow trying to fix the sound issue.


 Good luck,

---

### Post by kansasnoob on 2009-02-07
> **lukedupree said:**
> Well I went back to 8.04 hardy. It works great with the video but the sound is corrupted, sounds garbeled. That's why I went to 8.10 in the first place was the issue with 8.04 sound. Starting to feel like I'm on a windows PC. Always somehting. I'll mess around with the sound and see if i can fix it. Otherwise i may just stick to SUSE 11.1. If I get the time to re install 8.10 I'll give your fix a try.

Oh and my MB is a m3n72-D, I just had a type-o previously. Have you ran 8.04 on that board?

I'd almost bet that the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

will get your sound issue straightened out.

I've also experienced frustration over the new xorg in Intrepid. In my case regarding Openchrome drivers!

I could always fix it in Hardy but not in Intrepid.

---

### Post by Kain000 on 2009-02-21
> **Victormd said:**
> I'm having the exact problem. Ultimately I formated and re-installed 8.10 and after running the updates and installing restricted drivers, the problem came back. This started after I installed my second graphics card (going for SLI). I know it's related to the graphics card but not really sure what to do. I've tried recovery mode, repair broken package, x-fix (don't remember the actual name) option and nothing seems to work. I checked my xorg.conf and it looks just like the "failsafe" xorg in /etc/X11.

If anyone has any suggestions, please let me know.
Thanks!

bump I have this EXACT senario, when I put in my 2nd card (nvidia geforce 9600) for SLI this problem occors and nothing seems to fix it, when I take it back out things are back to normal

sudo lspci shows both cards however.

not a clue what to do

---

### Post by spliffeh on 2009-02-23
I have the same problem, replicated twice on a fresh 8.10 install. Using two Geforce 7800 GTX.

Not impressed with 8.10 right now, it's wasted alot of my time.

---

### Post by Kain000 on 2009-02-23
hold on now, 

alright dude I figured it out just like an earlier post said, but not exactly how he/she entered it.

```
sudo lspci | grep VGA
```

this will give you your two video cards and their bus id's.

now we have to tell xorg what card to treat as primary, that is why it's having trouble.



```
sudo gedit /etc/X11/xorg.conf
```

at the bottom under the title "section device" add a line that says
```
BusID: 03:00.0 
```
or what ever bus id the card you want to be primary showed to have.

this is from memory of sat morning about 4Am so when I get home tonight I will give you the actuall snipit from my xorg.conf file.

---

### Post by Kain000 on 2009-02-23
alright as promised here is the device section from the xorg.conf file

```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	BusID "03:00:0"
EndSection
```

---

### Post by abstortedminds on 2009-03-24
Hi,

I had the same issue...
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	BusID	"07:00:0"
	Option	"sli" "auto"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "nvidia"
	Option "NoLogo"		"True"
	BusID	"05:00:0"
	Option "sli" "auto"
EndSection
```

In order to enable SLI do I create a Section "Device" for both cards?
If so, what is different for each Section "Device"

I also noticed you mentioned the Option "sli" "auto" line.
Does this go in both Section "Device" ?

I will continue testing in the meantime and report my findings here.

---

### Post by Kain000 on 2009-03-25
> **abstortedminds said:**
> Hi,

I had the same issue...
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	BusID	"07:00:0"
	Option	"sli" "auto"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "nvidia"
	Option "NoLogo"		"True"
	BusID	"05:00:0"
	Option "sli" "auto"
EndSection
```

In order to enable SLI do I create a Section "Device" for both cards?
If so, what is different for each Section "Device"

I also noticed you mentioned the Option "sli" "auto" line.
Does this go in both Section "Device" ?

I will continue testing in the meantime and report my findings here.

I believe what you need to do is have only one section "device" to tell xorg what card is primary, (use the one that your monitor is plugged into) and use it's bus id.    

Include the option sli auto like you have above but you only need to include one.

---

### Post by Owosso on 2009-11-04
> **Kain000 said:**
> alright as promised here is the device section from the xorg.conf file

```

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    BusID "03:00:0"
EndSection
```

Thank you, thank you, a MILLION THANK YOU's. I'm new to Linux, had this problem, and your post saved me hours of hassle. If it weren't for you, I would've reformatted Linux off my computer for good.

Needless to say, this snippet of text worked perfectly.

---

