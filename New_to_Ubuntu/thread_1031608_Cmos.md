---
title: "Cmos"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by steak5 on 2009-01-05
Hi everyone:

I'm a newbie.

I need help with accessing system setup utility.(cmos)

Is there a way to access it via command line?

I have tried eyerything I know of, but I cant get in.

Steak
cts

---

### Post by donkyhotay on 2009-01-05
CMOS is part of your system hardware (BIOS). Generally it's not accessible from the operating system. Most motherboards will have a prompt saying 'press del for setup' or something similar when they first turn on (before the GRUB screen). If so just do that and you're into your CMOS. Some motherboards don't have this handy hint at which point you need to find out how to do. Generally once you find out what type of motherboard you have a simple google search will turn up how to access it's CMOS. Be careful though, CMOS is very powerful and doing the wrong thing can mess your system up.

---

### Post by steak5 on 2009-01-05
Thank you donkyhotay:

The problem is the mobo does not show post.

The del key does not work.

I flashed, cleared, changed battery, power supply, and still cant access.

---

### Post by halitech on 2009-01-05
see here for more info about CMOS

[http://en.wikipedia.org/wiki/CMOS](http://en.wikipedia.org/wiki/CMOS)

I believe you are actually trying to get into the BIOS
[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

---

### Post by halitech on 2009-01-05
> **steak5 said:**
> Thank you donkyhotay:

The problem is the mobo does not show post.

The del key does not work.

I flashed, cleared, changed battery, power supply, and still cant access.

it does not the POST or doesn't show anything?

---

### Post by donkyhotay on 2009-01-05
> **halitech said:**
> it does not the POST or doesn't show anything?

Not all motherboards display POST or allow direct access to CMOS setup/BIOS. I have a laptop thats this way and in order to make changes normally made through the BIOS (such as boot from a CD) I have to press and hold a specific key when it boots up and then it performs that ONE action on that single boot (it's really lame). It originally came with some special proprietary software that is supposed to allow me to make these changes but you can only run the software when the computer is fully booted (and generally if I'm messing with BIOS it's because I can't boot) and it's windows only (of course). This is very rare though and although I've seen a few others that don't display how to access setup my laptop is the only system I've ever seen to not have a built-in hardware setup. If we knew what type of motherboard you have we might be able to tell you how to get into your setup.

---

### Post by oilchangeguy on 2009-01-05
try the F1 key. if that does not work, reboot the computer. hold down the esc key, you should get a keyboard error, and be prompted to press a key to enter setup. why do you need to get into the bios?

---

### Post by oilchangeguy on 2009-01-05
> **steak5 said:**
> Thank you donkyhotay:

The problem is the mobo does not show post.

The del key does not work.

I flashed, cleared, changed battery, power supply, and still cant access.

i doubt you have actually flashed the bios, since you don't know how to even enter the bios. and done improperly, you'd end up with a boat anchor. cleared, cleared what? changed the battery, that has nothing to do with pressing the proper key to enter the bios, and the power supply for sure has nothing to do with the bios. please advise why you need to enter the bios.

---

### Post by Malalo on 2009-01-05
Also, you could try Google : "BIOS+access+(your machine's maker and model)"
You should find answers as to how to get into the BIOS on your machine.

---

### Post by steak5 on 2009-01-05
I actualy have flashed the bios several times.
The mobo is a asus k8ne-deluxe
feature is alt+f2 built in recovery.
I have tried several versions to no avail.
I need to adjust boot sequence and see frequency settings because something is screwed up.

---

### Post by LowSky on 2009-01-05
could be a bad capacitor if the thing wont post, or badly seated RAM, or a burnt out processor.

---

### Post by oilchangeguy on 2009-01-05
> **steak5 said:**
> I actualy have flashed the bios several times.
The mobo is a asus k8ne-deluxe
feature is alt+f2 built in recovery.
I have tried several versions to no avail.
I need to adjust boot sequence and see frequency settings because something is screwed up.

there's no way you have flashed the bios. you don't even know how to enter the bios. you should consider taking it to a repair shop so they can show you how to get into the bios. do you even know what flashing the bios is?

---

### Post by steak5 on 2009-01-05
Thanks oilchangeguy:
 The truth is I do know how to get in the bios.
the board has a built in feature for recovery via alt+f4
I have downloaded and flashed several versions. 

Here is the main problem. When I boot if I do not hold down the esc, del alt+..., or some other key the os will not load and I get a out of frequency range message on my monitor. I have been jacking with it for several months now trying to fix it. I am starting to susspect a corupted video card bios or something.:confused:

---

### Post by bwallum on 2009-01-05
Hi Steak5, Happy New Year to you.

The CMOS holds the instructions that are contained in your BIOS chip. The CMOS remains 'alive' through that flat battery on your motherboard. If you want to change the instructions on the BIOS chip you 'flash' it with new instructions. This involves using a special programme run within a limited operating system from a removeable bootable source, usually a floppy disc but could be a cd and could even be a usb memory stick on those (later) machines that allow for booting from a usb stick.

So, have you 'flashed' the BIOS? is the question the posts are asking I think.

To access the CMOS you need to press a particular key. Usually this is the 'del', 'F1', 'F2' 'F10', or 'esc' key. You repeatedly press the key after turning the machine on and before the operating system (in Ubuntu before grub kicks in) starts up. You can safely press all the above keys in turn to try and get access to the CMOS.

When you save any changes to the CMOS they stay in the CMOS. The BIOS chip can only be changed by 'flashing' it with the above mentioned process.

It would help if you could clarify if you are trying to recover from a bad 'flashing' or not.

Regards
Bob

---

### Post by bwallum on 2009-01-05
Another thought...when you say the os will not load, do you mean the desktop doesn't come up because the 'out of frequency range' error prevents display of the desktop?

This error can occur when changing monitors, typically from a crt to a lcd. The high refresh rate of the crt is retained by the xserver (screen display software) configuration and when it comes across a monitor that can't handle the refresh rate (lcd screens are typically lower) then it jibs if you are using a proprietory driver such as nvidia. You need to get back to the default vesa driver.

If so get into grub (press esc when prompted or wait for the menu to appear) then select recovery mode. You will be offered a recovery menu, try xfix and resume. If no joy then next time use the terminal option and type in "sudo nano /etc/X11/xorg.conf" without the quotation marks (note the x is an upper case X).

Look for the screen section and find the 'driver' item. Delete 'nvidia' and replace with 'vesa'. Save with ctrl x. That should get you up and running with the desktop and from there you can reload the nvidia driver.

---

### Post by steak5 on 2009-01-05
Thank you bwallum

I will let you know what happens.

---

### Post by steak5 on 2009-01-05
Thank you bwallum

I will let you know what happens.

---

### Post by steak5 on 2009-01-05
I typed in the command ...conf, but I do not understand how to use it. I cant see a line thet says driver anywhere. I see screen
but I cant make sence of how to execute anything

---

### Post by ales_klaus on 2009-01-22
Sorry, I have no help for you, but your post is useful to me to submit the community a strange problem I have with my CMOS.
I have installed ubuntu lxde in my old pc (bought in January 2000), and it works greatly. I also changed the motherboard battery (and had to re-set CMOS clock).
My problem now is that the lxde clock always shows a time which is 1 hour later than the CMOS clock.
If I correct the OS time (from terminal, sudo date "..."), and then re-boot, I find CMOS clock set 1 hour earlier than the right time. If I correct CMOS clock, then I find OS clock set 1 hour later than the right time...
How can I set the ultimate agreement between CMOS and lxde times?
Thanks to all

---

### Post by unutbu on 2009-01-22
Have you tried something like this?
```
date
sudo date --set="Thu Jan 22 07:43:34 EST 2009"
sudo hwclock --systohc
```

The "date" command shows the OS date/time. 
The "date --set" command sets the OS date/time. 
Both these commands can be omitted if you have a GUI way of setting the OS date/time.
The "sudo hwclock --systohc" command sets the Hardware Clock to the current OS date/time.

---

### Post by mcduck on 2009-01-22
> **steak5 said:**
> I actualy have flashed the bios several times.
The mobo is a asus k8ne-deluxe
feature is alt+f2 built in recovery.
I have tried several versions to no avail.
I need to adjust boot sequence and see frequency settings because something is screwed up.

If I remember right the key to enter BIOS setup on K8N-E (and Deluxe version as well) is Del..

If it's not, Asus usually includes that kind of information in the motherboard's manual, you can download one from Asus website if you haven't got it..

---

### Post by ales_klaus on 2009-01-22
> **unutbu said:**
> Have you tried something like this?
```
date
date --set="Thu Jan 22 07:43:34 EST 2009"
sudo hwclock --systohc
```

The "date" command shows the OS date/time. 
The "date --set" command sets the OS date/time. 
Both these commands can be omitted if you have a GUI way of setting the OS date/time.
The "sudo hwclock --systohc" command sets the Hardware Clock to the current OS date/time.

I've tried, but nothing changes (except that I set the right time only to the System clock).
The code ```
date --set="Thu Jan 22 07:43:34 EST 2009"
``` works only by "sudo".

---

### Post by mcduck on 2009-01-22
> **ales_klaus said:**
> Sorry, I have no help for you, but your post is useful to me to submit the community a strange problem I have with my CMOS.
I have installed ubuntu lxde in my old pc (bought in January 2000), and it works greatly. I also changed the motherboard battery (and had to re-set CMOS clock).
My problem now is that the lxde clock always shows a time which is 1 hour later than the CMOS clock.
If I correct the OS time (from terminal, sudo date "..."), and then re-boot, I find CMOS clock set 1 hour earlier than the right time. If I correct CMOS clock, then I find OS clock set 1 hour later than the right time...
How can I set the ultimate agreement between CMOS and lxde times?
Thanks to all

Which version of Ubuntu are you running? 8.04 and older versions assume that your CMOS clock is running in UTC instead of local time.. (It's traditional in Unix systems)

In case you are indeed running older Ubuntu you can configure Ubuntu to consider CMOS time to be same as local time by adding following code to the end of /etc/default/rcS file:
```
# Set UTC=yes if your system clock is set to UTC (GMT)
UTC=no
```
(If you already have that entry just make sure it's set to "no").

gksudo gedit /etc/default/rcS"

---

### Post by Tomatz on 2009-01-22
> **oilchangeguy said:**
> i doubt you have actually flashed the bios, since you don't know how to even enter the bios. and done improperly, you'd end up with a boat anchor. cleared, cleared what? changed the battery, that has nothing to do with pressing the proper key to enter the bios, and the power supply for sure has nothing to do with the bios. please advise why you need to enter the bios.

He hasn't flashed the bios as in used a bootable FD. Most new boards have a small amount of flash memory on them to cache bios updates till the PC is rebooted. All you have to do is download a .exe from the manufacturers site.

**@bwallum**

```
Bios keys are usually:

Del

f1

f2

and the boot menu is usually accessed by using esc.

```



What i think the problem is, is that the "legacy usb" option is not switched on in the bios so you cant use the usb keyboard at boot/post.

Try using an old PS2 keyboard (round connector with pins). That should work ;)

---

### Post by jerome1232 on 2009-01-22
You lcd monitor display's out of range while post is happening? (I don't see how a post screen can exceed an lcd monitors limits, usually it's 640x480 and at a sane refresh rate)

Has it always done this with the current lcd monitor? Do you have a crt monitor you can try hooking up?

Have you reset cmos? (Usually a jumper on the mother board says "cmos" on it, you just move it over one peg wait a few seconds and move it back. All bios settings will be  reset to default. Alternatively you can unhook the power supply and unhook the battery then go have lunch. When your done hook it all back up bios should revert to factory settings.

---

### Post by ales_klaus on 2009-01-22
I'm running 8.10 (plume-lxde desktop) version. It should be set to CET (but I'm not sure).
In fact, in /etc/default/rcS I find UTC="yes"

I will try the gksudo gedit /etc/default/rcS

---

### Post by ales_klaus on 2009-01-22
I use gksudo..., but after i've typed my password nothing happens...:(

---

### Post by mcduck on 2009-01-22
> **ales_klaus said:**
> I use gksudo..., but after i've typed my password nothing happens...:(

Sorry, my mistake.. LXDE's default text editor is leafpad..

This should work for you:
```
gksudo leafpad /etc/default/rcS 
```

(If it doesn't just use comamnd line editor nano "sudo nano /etc/default/rcS", do the change and pres Ctrl-X to save & exit)

---

### Post by ales_klaus on 2009-01-22
> **mcduck said:**
> Sorry, my mistake.. LXDE's default text editor is leafpad..

This should work for you:
```
gksudo leafpad /etc/default/rcS 
```

(If it doesn't just use comamnd line editor nano "sudo nano /etc/default/rcS", do the change and pres Ctrl-X to save & exit)

Thank you very much, my problem has been solved! Yes, lxde uses leafpad (shame on me: I had to think to that!) :D

---

