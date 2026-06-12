---
title: "Brightness control problem"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by llakais on 2010-06-21
Hey everyone,

I'm having trouble changing the brightness of my screen ever since I installed the driver for my NVIDIA card.

Basically when I use the brightness control settings on my keyboard, the little scale notifier in the upper-right-hand corner changes, but the actual screen brightness does not.  Even more curiously, whenever I reboot, Ubuntu runs at the brightness that was set previous to booting, but I can't change the brightness level beyond that.

It works fine on Windows, so I don't think it's a hardware issue (I'm using 10.04).

I tried the fix described here:
[http://ubuntuforums.org/showthread.php?t=1468734](http://ubuntuforums.org/showthread.php?t=1468734)
but all it did was mess with the driver and screw up the graphics.  I changed the grub file back and used backed up graphics settings and managed to get my graphics back under control, but no luck with the brightness setting.

Sorry to bother you guys and thanks in advance for any advice you might have.

---

### Post by MyR on 2010-06-21
I probably can't help you myself, but I can suggest posting your computer make & model as well as your graphics card make & model.

---

### Post by llakais on 2010-06-21
> **MyR said:**
> I probably can't help you myself, but I can suggest posting your computer make & model as well as your graphics card make & model.
Whoops.

My laptop is a Lenovo Thinkpad T410, and my graphics card is a NVIDIA NVS 3100m Graphics 256MB DDR3 with AMT.

Not sure what all that means, but hopefully it helps.

Thanks!

---

### Post by maizuddin35 on 2010-06-21
does your keyboard on your laptop show something that can increase the brightness of you screen?

---

### Post by warfacegod on 2010-06-21
Lucid's Power Manager has brightness sliders in it if I'm not mistaken. Go to: System> Prefs.> Power Management

---

### Post by llakais on 2010-06-21
> **maizuddin35 said:**
> does your keyboard on your laptop show something that can increase the brightness of you screen?
Yes, although the buttons require the press of a function key ("Fn") to change the brightness.  When I do this, the indicator shows the brightness level changing on the slider, but the actual screen brightness doesn't change.

> **warfacegod said:**
> Lucid's Power Manager has brightness sliders in it if I'm not mistaken. Go to: System> Prefs.> Power Management
Tried this too with the same result.  I can set the brightness slider however I want, but that doesn't affect the brightness of the actual screen.

Thanks for the replies though, guys, I really appreciate it.

---

### Post by warfacegod on 2010-06-22
If you are by any chance using a Toshiba, getting the package fnfxd from Synaptic can help. Possibly toshutils might help as well.

Or use the Terminal:

```
sudo apt-get install fnfxd
```

```
sudo apt-get install toshutils
```

---

### Post by BennBuntu on 2010-06-22
I'm on same laptop. Brightness stopped working when I installed nvidia driver. See here. [http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M]("http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M")

Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```

to your /etc/X11/xorg.conf under devices section. Make sure the quotation marks are the same as if you type them.

---

### Post by llakais on 2010-06-23
> **BennBuntu said:**
> 
Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```

to your /etc/X11/xorg.conf under devices section. Make sure the quotation marks are the same as if you type them.

**THANK YOU THANK YOU THANK YOU!!!**

This worked perfectly - such an easy fix, too.  Thanks to all of you guys for all your time.  It's so great that they're people willing to help like this.  :-D

---

### Post by mojotexas on 2010-09-19
Sadly, this solution did not work for me. I have edited the xorg.conf file so that it looks like this:

```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Any other thoughts?

---

### Post by warfacegod on 2010-09-19
Have a look here: [http://ubuntuforums.org/showthread.php?t=88611&highlight=viao+brightness](http://ubuntuforums.org/showthread.php?t=88611&highlight=viao+brightness)

Reply #157 looks promising.

---

### Post by JackSchnippes on 2010-09-26
Thanks @BennBuntu! I'm happy there is an easy solution! :)

---

### Post by thegnu on 2010-10-16
> **mojotexas said:**
> Sadly, this solution did not work for me. 

...

Any other thoughts?

did you restart X?  i'm on a T510 with Maverick installed, and it worked for me.

---

### Post by antido on 2010-12-09
Thanks! This worked!

---

### Post by lazyacre on 2011-02-21
Brillant Thanks..... thinkpad T410 ubuntu

---

### Post by anshuiitk on 2011-03-29
I have T410s and 10.10, changing the xorg.conf and adding 'Option "RegistryDwords" "EnableBrightnessControl=1"' works perfectly fine with me.
Thanks,

---

### Post by Madchuckles on 2011-09-21
Awesome, fixed my problem.

---

### Post by snake_eyes on 2011-09-21
> **BennBuntu said:**
> I'm on same laptop. Brightness stopped working when I installed nvidia driver. See here. [http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M]("http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M")

Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```

to your /etc/X11/xorg.conf under devices section. Make sure the quotation marks are the same as if you type them.

Excellent advice...... (Y)

---

### Post by schmandr on 2012-04-30
Hey guys!

I'd like to try the proposed solution (adding Option "RegistryDwords" "EnableBrightnessControl=1" to xorg.conf) on Ubuntu 12.04. Now, there is no xorg.conf file on my system, and I read that it isn't needed anymore. Is there a different configuration file where I can add this option, or what is the solution in this case?

Thanks for your help!

---

### Post by soumadeep on 2012-05-04
I am having the same problem with 12.04.My system has no xorg.conf file.Is there any other solution????

---

### Post by wM6lYlji on 2012-09-12
me to...

---

