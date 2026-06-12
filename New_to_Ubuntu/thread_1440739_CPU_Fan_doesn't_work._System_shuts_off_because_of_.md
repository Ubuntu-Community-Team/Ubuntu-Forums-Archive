---
title: "CPU Fan doesn't work. System shuts off because of high temps."
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Markus01 on 2010-03-27
I have a Toshiba Satellite L355D with AMD Turion X2 Dual-Core Mobile RM-72 2.10 GHz. Insyde H2O BIOS version 1.5. and integrated ATI Mobile Radeon Graphics Card. 

Since going from windows 7 to Ubuntu 9.10 my cpu temps get very high when using cpu intensive applications. My system shut down because of high temps and that's when I noticed that the fan didn't kick in to cool it down. When I booted the system back up the fan ran full blast even when the temps were down to about 38C. To get the fan to go back down I had to reboot the system and then when I tried using applications again the temp went back up and again with the fan not kicking in unless I reboot. I tried an omnibook fix but it did not work. Please HELP

I also have latest updates and fresh install of Ubuntu and latest version of Grub. I'm pretty sure it has something to do with the CPU itself or the BIOS or both.

---

### Post by 2hot6ft2 on 2010-03-27
From Synaptics info
> Toshiba laptop utilities

This is a collection of utilities to control a Toshiba laptop. It includes
programs to turn the fan on and off, to view the power mode, and to set
the supervisor password.

Note that these utilities work with APM features in the Toshiba BIOS.
If your laptop's BIOS only supports ACPI and not APM, then toshutils will
probably not work for you. Toshiba's newer models tend to support ACPI
only, and therefore toshutils will not work with them.


toshutils
Get it from Synaptic or use
```
sudo apt-get install toshutils
```
to install it
or toshset
> Access much of the Toshiba laptop hardware interface

Toshset is a command-line tool to allow access to much of the
Toshiba laptop hardware interface developed by Jonathan Buzzard. It can do
things like set the hard drive spin-down time, turn off the display
and set the fan speed without the help of the kernel.
Toshset requires an experimental version of the toshiba_acpi kernel module
with an ACPI-enabled kernel. Otherwise it works only if the laptop supports
the old APM BIOS. (The last of these was produced something like 5 years ago)
Please read README.Debian how to install the experimental version of the
toshiba_acpi kernel module. (Ubuntu users don't need it)

This package also includes the Toshsat1800-irdasetup by Daniele Peri.  It
can be used to configure IrDA for laptops with ALI1533 bridge (LPC47N227
SuperIO), smc-ircc and not initializing BIOS (tested on Toshiba Satellite
1800-514).  Homepage: [http://www.csai.unipa.it/peri/toshsat1800-irdasetup/](http://www.csai.unipa.it/peri/toshsat1800-irdasetup/)

or fnfx
> fnfx enables owners of Toshiba laptops to change the LCD brightness,
control, the internal fan and use the special keys on their keyboard
(Fn-x combinations, hot-keys). The internal functions will give the
possibility to map the Fn-Keys to functions like volume up/down, mute,
suspend to disk, suspend to ram and switch LCD/CRT/TV-out. These
functions heavily depend on the system and/or kernel configuration.
You will need at least a kernel (v2.4.x, v2.5.x, v2.6.x) with ACPI and
Toshiba support (CONFIG_ACPI and CONFIG_ACPI_TOSHIBA).

---

### Post by Markus01 on 2010-03-28
I'm new to Ubuntu. I don't know how to use toshutils. I have them installed as well as toshset, but I don't know how to use them. Help?

---

### Post by Markus01 on 2010-03-28
My cpu fan does not work on my Toshiba Satellite L355D laptop.

Specs are AMD Turion X2 Dual-Core Mobile RM-72 2.10 GHz. Insyde H2O BIOS version 1.5 
Integrated ATI Radeon HD 3100 Graphics. Ubuntu 9.10, GNOME 2.28.1, Kernel 2.6.31-20-generic.
I installed Gkrellm and gnome sensors applet. I also installed toshutils and toshset and fnfxd. I don't know how to use toshutils or toshset or fnfxd. I'm new to linux and really need help. My system keeps overheating. 

How do I use toshutils? How to control fan manually?

---

### Post by 2hot6ft2 on 2010-03-28
I don't have a Toshiba so I don't have them installed or know how they work. They are probably command line utilities so you'll have to look at their manuals by reading them in a terminal.
Each one works the same. You scroll down to read it and hit the letter "Q" (case doesn't matter so lower case works too) to quit the manual or help pages before closing the terminal.
The commands that start with "man" are for the manual.
Those that end with --help are the help pages.
Open a terminal
Applications > Accessories > Terminal
and run
```
man toshutils
```
```
toshutils --help
```
```
man toshset
```
```
toshset --help
```
```
man fnfxd
```
```
fnfxd --help
```

Mods. This thread should be merged with this one. (Same OP and same topic)
**CPU Fan doesn't work. System shuts off because of high temps.**
[http://ubuntuforums.org/showthread.php?p=9041845](http://ubuntuforums.org/showthread.php?p=9041845)

---

### Post by 2hot6ft2 on 2010-03-28
Mods. This thread should be merged with this one. (Same OP and same topic)
**CPU fan not working on Toshiba laptop**
[http://ubuntuforums.org/showthread.php?p=9041842](http://ubuntuforums.org/showthread.php?p=9041842)

---

### Post by overdrank on 2010-03-28
Threads merged :)

---

### Post by steve161 on 2010-03-28
I posted this fix in an earlier thread.  It worked for my Toshiba L305 laptop.  There was mixed success for others that tried it.  

 Open /etc/default/grub as root. Look for the line that ends with quiet splash. Add acpi_osi=\\\"Linux\\\"  to the line so it looks like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

Then run sudo update-grub from the terminal.  Reboot.

If it does not work for you,  just remove acpi_osi=\\\"Linux\\\"  and again run sudo update-grub from the terminal and reboot.  Just make sure you are careful with the quotation marks.

---

### Post by Markus01 on 2010-03-28
When I try to run toshset as super user I get a line that says
 
required kernel toshiba support not enabled
 
What do I do to enable it?

---

### Post by cbecker78 on 2010-03-29
> **Markus01 said:**
> When I try to run toshset as super user I get a line that says
 
required kernel toshiba support not enabled
 
What do I do to enable it?

I could be wrong here, but I believe the insyde Bios does not allow the toshset to work... that was the conclusion I came to when I was trying to installand use that myself (don't remember where I saw that at).

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```^^That code (using the "acpi_etc." on the same line as quiet splash may be the right way to do it in the new grub, as opposed to what I sent you in the pm where I was suggesting adding it on a separate line.

@Steve: are the "\\\"s necessary? I assume those are to escape the quotes?  So maybe it would be worthwhile to try with and without the backslashes? Just wondering here.

---

### Post by steve161 on 2010-03-29
I had to use it with grub1 on other distros with my laptop, without the ///'s.  However, that did not work on grub2, so I found the posted fix on another linux site.  The reason for the ///'s is that grub2 will not recognize the quotation marks without it.
As i stated earlier, it worked for some but not others.  Anyway, it is easy to remove if it does not work.

---

### Post by Markus01 on 2010-04-01
I need to update the BIOS for InsydeH2O BIOS. Can someone explain how to do it? Does anyone know where to get the update?

I tried the Insyde technologies website, but didn't see a link for updates. I saw on old threads from other websites that other people were able to update their BIOS. Also it can't have an .exe windows format.

---

### Post by cbecker78 on 2010-04-02
go to this page: [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp)

click on product support, then select your product details, then click "go", then click on the download tabs.  You can find your bios updates (if any are available) there.  Use the drop downs to refine search by "all operating systems" and "bios".  If a higher version is of your bios is not available, there's a chance it may not be stable on your pc.(Highest upgrade for mine was Insyde V1.5.  easiest installation method is from within windows if you still have that installed.

[s]the download will come with a readme file detailing the instructions for the different methods you can use to flash it.[/s]

I take it none of the "acpi_osi=Linux" stuff helped?  Also, did you make sure you capitalized the "L" in linux?

Best of luck!

edit:  does not come with a readme file like I thought.  I'll have to look where I found those instructions..

edit2: well, I do not see it right off and have to run for the weekend.... If you can't do it from windows, I think the method is from withing the bios screen or else booting from a cd or flash drive that has the bios executable on it..

if you brouse the net, you can find some instructions.  **Take all of the precautionary warnings very seriously!  You CAN brick your laptop if you don't do it right.**

---

### Post by MasterFenrir on 2011-01-20
I am reviving quite an old thread here, but my question is..
How do I use Toshutils? I have installed it, but I don't know how to use it..

---

### Post by dmizer on 2011-01-20
> **MasterFenrir said:**
> I am reviving quite an old thread here, but my question is..
How do I use Toshutils? I have installed it, but I don't know how to use it..

Unless you have an older PIII Toshiba laptop, the toshutils won't work for you. The toshutils were built specifically for a BIOS that was not equipped for ACPI.

If you have such a laptop, then the best way to configure toshutils is to run it from the CLI. Here's some info on that: [http://ubuntuforums.org/showthread.php?p=4007319](http://ubuntuforums.org/showthread.php?p=4007319)

---

