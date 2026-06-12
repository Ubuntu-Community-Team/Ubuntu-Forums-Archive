---
title: "Cannot Enable Visual Effects"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by gecus on 2009-03-15
Hello, I am running Intrepid Ibex with a nVidia FX5500 graphics card.
I looked at another thread and figured you might need this information:

Contents of /etc/X11/xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Also:

```
john@john-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

Any extra information that is required I will be happy to provide.

---

### Post by got_milk? on 2009-03-15
> **gecus said:**
> Hello, I am running Intrepid Ibex with a nVidia FX5500 graphics card.
I looked at another thread and figured you might need this information:

Contents of /etc/X11/xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Also:

```
john@john-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

Any extra information that is required I will be happy to provide.

Why exactly can't you enable visual effects? Do you get an error message? If so, what does it say?

---

### Post by gecus on 2009-03-15
> **got_milk? said:**
> Why exactly can't you enable visual effects? Do you get an error message? If so, what does it say?

When I try to enable them, it loads for a sec and then a pop-up alert says "! Desktop effects could not be enabled. [OK]"

---

### Post by got_milk? on 2009-03-15
> **gecus said:**
> When I try to enable them, it loads for a sec and then a pop-up alert says "! Desktop effects could not be enabled. [OK]"

It looks like you have your NVIDIA drivers installed, are they the latest version?

Assuming you're on 32-bit, the link for your latest drivers is:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

---

### Post by gecus on 2009-03-15
> **got_milk? said:**
> It looks like you have your NVIDIA drivers installed, are they the latest version?

Assuming you're on 32-bit, the link for your latest drivers is:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

I've run into this problem:
```
john@john-desktop:~/Desktop$ sudo sh NVIDIA-Linux-x86-180.29.pkg1.run
[sudo] password for john: 
sh: Can't open NVIDIA-Linux-x86-180.29.pkg1.run

```

---

### Post by overdrank on 2009-03-15
> **gecus said:**
> I've run into this problem:
```
john@john-desktop:~/Desktop$ sudo sh NVIDIA-Linux-x86-180.29.pkg1.run
[sudo] password for john: 
sh: Can't open NVIDIA-Linux-x86-180.29.pkg1.run

```

Should be ```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```not a period before pkg1
You will also need to exit X before installing```
sudo /etc/init.d/gdm stop
```

---

### Post by gecus on 2009-03-16
> **overdrank said:**
> Should be ```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```not a period before pkg1
You will also need to exit X before installing```
sudo /etc/init.d/gdm stop
```

When I am in the installer it says:
```
Warning: The NVIDIA GeForce FX 5500 GPU installed in this system is already supported through the NVIDIA 173.14.xx legacy Linux graphics drivers.
```

---

### Post by Gannon8 on 2009-03-16
You may need the legacy driver instead of the up-to-date one.
Or you have the legacy one already installed

---

### Post by mvalviar on 2009-03-16
1. Download the latest driver as instructed above.

2. Close other applications except a terminal window. Then on the terminal:
```
 sudo killall gdm 
```

3. Hit Ctrl-Alt-F1 to switch to another terminal. Log-in and go to the directory where you saved the file you downloaded from nvdia which is usually ~/Desktop.

4. Type ```
./NVIDIA-Linux-x86_64-180.06-pkg2.run
``` and just follow the prompt. I may display some messages but just let it go about its business and it should be fine.

5. Once the installation has finished you can just type startx and enter.

---

### Post by gecus on 2009-03-16
> **mvalviar said:**
> 1. Download the latest driver as instructed above.

2. Close other applications except a terminal window. Then on the terminal:
```
 sudo killall gdm 
```

3. Hit Ctrl-Alt-F1 to switch to another terminal. Log-in and go to the directory where you saved the file you downloaded from nvdia which is usually ~/Desktop.

4. Type ```
./NVIDIA-Linux-x86_64-180.06-pkg2.run
``` and just follow the prompt. I may display some messages but just let it go about its business and it should be fine.

5. Once the installation has finished you can just type startx and enter.
Same error.

---

### Post by kgas on 2009-03-16
you can add the following to xorg.conf file

Section "Extensions"
         option "composite" "Enable"
EndSection

and this may help to the visual effects variations.

---

### Post by gecus on 2009-03-16
> **kgas said:**
> you can add the following to xorg.conf file

Section "Extensions"
         option "composite" "Enable"
EndSection

and this may help to the visual effects variations.

Didn't work :[

---

### Post by prvteprts on 2009-05-05
Hello, I finally got my NVidia FX 5500 working after around 2 months of trying out different things. Hope this can help.

I would suggest using the 173-glx driver. What happened in my case is every time I try to install that and then restart, I get a blank screen instead of the login screen.

I was able to get the ATI graphics on my laptop working properly with effects and all. I compared the two xorg.conf files and what I found out was, the NVidia setup's xorg did not have a line which indicates what PCI bus ID it was on. So I typed in the terminal:

lspci | grep -i vga

I got something like this:

00:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

I then installed the 173 driver from Hardware Drivers. It would normally ask for a reboot or something. After rebooting, sure enough I got the blank screen. I restarted, booted into recovery mode. In recovery mode, I went to the root prompt then typed:

sudo nano /etc/X11/xorg.conf

I added the lines:

BusID	"PCI:0:5:0"
Option	"NvAGP" "0

under the "Device" section right after the Identifer line. I have tried doing this before to no avail becauase I was probably adding these statements in the wrong place. So "Device" should look like this, of course with the BusID value dependent on your situation:

Section "Device"
	Identifier	"Configured Video Device"
	BusID	"PCI:0:5:0"
	Option	"NvAGP" "0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

I think the problem is, the NVidia card can't be "detected" without the BusID line. Try it out and inform us of the outcome.

---

### Post by entr3p on 2009-06-04
What you can do is simply disable the blacklist. Worked for me no problem.


[Fix Intel graphics on Ubuntu 9.04 - Enabling visual effects]("http://www.learningubuntu.com/articles/fix-intel-graphics-ubuntu-904-enabling-visual-effects")

---

