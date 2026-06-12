---
title: "Issues with FN keys - Ubuntu 10.04"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by AXBX7C on 2010-04-30
Hello!

I just updated to 10.04 and I'm experiencing issues with my function keys supposed to control screen brightness on my Asus UL30a It worked fine in 9.10...

When I do a acpi_listen command to listen to my function keys (e.g. to increase brightness) it gives me back three different results not just one. I guess it thinks I just pressed three keys at once. The other function keys seem to work fine. I don't use Ubuntu's power manager but a custom xbacklight script. Could that be the cause of my problem? Sorry if this question is stupid but I'm quite new to Ubuntu...


Any suggestions? Thank you!

---

### Post by agarciamog on 2010-04-30
I've got the same issue. I've seen the bug reported, but I haven't found a solution.

Essentially holding doing the FN key and increasing or decreasing the brightness either, doesn't work or its random.

Anyone have any ideas?

---

### Post by agarciamog on 2010-05-01
I found a solution.

Its a matter of adding the following snipet to grub

_[SIZE=5]**Solution**[/SIZE]_

Open up Terminal and enter the following
```
sudo gedit /etc/default/grub
```Look for the line that says GRUB_CMDLINE_LINUX and add this
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```Save it and then update Grub
```
sudo update-grub
```Reboot :)

---

### Post by AXBX7C on 2010-05-01
You just made my day! Thank you a lot!

Even though I don't understand what your solution did...

---

### Post by ttanev on 2010-05-02
> **agarciamog said:**
> I found a solution.

Its a matter of adding the following snipet to grub

_[SIZE=5]**Solution**[/SIZE]_

Open up Terminal and enter the following
```
sudo gedit /etc/default/grub
```Look for the line that says GRUB_CMDLINE_LINUX and add this
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```Save it and then update Grub
```
sudo update-grub
```Reboot :)

Tried that, but it didn't worked for me :( 
I am trying to resolve the almost same issue on the girlfriend's notebook Asus X56TR with M51TR motherboard /the same model line/. Every other function key is working well, but when I try to set different brightness it locks up everything, one of the cores stays at constant 100% usage and the only thing I can do is the known disaster reboot (alt+prtsc/sysrq + R, S, E, I, N, U, B)
The version is Lucid Lynx Final 64bit release, the type of installation was upgrade from Karmic. In Karmic the function keys worked well including brightness without the "disable touch pad" key, now touch pad key works but nor brightness, nor the ambient light sensor enable/disable (Fn + A).

Edit: For me the issue isn't ending only with brightness, if I try to put the computer on battery /unplug the AC/ behaves the same - one of the cores at 100% -> disaster reboot... If someone have any idea I'll be very thankful, cause I'm out of :)

---

### Post by AXBX7C on 2010-05-03
Strange... It did work for me...

Someone suggested to update to a newer kernel (From the launchpad team):

Quote:

"After upgrading to some more recent kernel (.33, .34rc6 atm) all the
issues with non-working brightness controls / Fn keys were gone as well.
You can get recent kernel from the Mainline ppa:
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 

 
As a sidenote, i think my battery lasts way longer with .34 - powertop
shows power draw below 6W sometimes. I never had such figures with
9.10 / kernel .31."

Unquote

You may want to try this...

---

### Post by AXBX7C on 2010-05-04
I removed the [solved] marker because the posted solution doesn't work for everyone.

Anyone who can confirm that a kernel update solves this issue?

Thank you for contributing!

---

### Post by eidex on 2010-05-05
agarciamog's solution works for me (UL30A-QX065V)

thanks a lot!

---

### Post by ed anger on 2010-05-05
Guys! It should work for everyone! First it didn't work for me, but I've noticed that the problem is with quotation marks in added line:

GRUB_CMDLINE_LINUX=”acpi_backlight=vendor”

Replace quotation marks from this line (in /etc/default/grub) with quotation marks that you type yourself. It has worked for me!

---

### Post by ttanev on 2010-05-07
> **ed anger said:**
> Guys! It should work for everyone! First it   didn't work for me, but I've noticed that the problem is with quotation   marks in added line:

GRUB_CMDLINE_LINUX=”acpi_backlight=vendor”

Replace quotation marks from this line (in /etc/default/grub) with   quotation marks that you type yourself. It has worked for me!
Tried this as soon as I red it, but didn't worked for me /Asus M51TR/. I   even misread it the first time, so tried also without quotes at all :)

> **AXBX7C said:**
> Strange... It did work for me...

Someone suggested to update to a newer kernel (From the launchpad  team):...

...

You may want to try this...

That worked like charm, thanks :)
The new issue is that fglrx become broken with the rc6 kernel and even  cannot install binary driver at all from anywhere. [s]Tried to set radeonhd, but  now I'm at ubuntu loading screen with no movement ahead. Probably will  do a clean install and restore the settings... It was not too much to  set after the installation anyway.[/s] And because I forgot to delete xorg.conf had some trouble, but know everything is okay :) The RadeonHD is really matured a lot since last time I tried it the last time and the battery time is okay too with .34rc6. Thanks again! Solved for me too.

---

### Post by sbike on 2010-05-07
For anyone that has the backlight working with the Fn + F5 and Fn + F6 keys could you answer these questions?

1) Which UL30?  (A, Vt, or ?)
2) Which kernel (Default lucid?  Something newer from PPA?  Which?)
3) Which GPU are you using (if a Vt)?
4) Which driver?  (Default lucid, noveau, proprietary nvidia?)
5) Did you apply the acpi_backlight=vendor grub tweak?
6) Do you see the alpha blended brightness display when changing the
   brightness?
7) Does the brightness actually change?

---

### Post by ckankiewicz on 2010-05-10
Has this issue been figured out? I have a UL80VT and can't change my brightness.  I get the brightness indicator, but the brightness never actually changes.

---

### Post by AXBX7C on 2010-05-10
@sbik:

1) Ul30A
2) Default kernel, 2.6.33 I guess
3) onboard...
4) see 3)
5) yes
6) yes
7) yes

---

### Post by Orcie on 2010-05-12
How do I update my kernel to .34rc6?

Just curious about the power consumption no 9.9 watts in laptopmode


FYI:

1) Which UL30? A
2) Which kernel Default lucid?
3) Which GPU are you using intel
4) Which driver? Default lucid
5) Did you apply the acpi_backlight=vendor grub tweak? Yes
6) Do you see the alpha blended brightness display when changing the
   brightness? Yes
7) Does the brightness actually change? YES

---

### Post by agarciamog on 2010-05-12
1) Which UL30? A
2) Which kernel? 2.6.32-22
3) Which GPU are you using (if a Vt)?
4) Which driver? Default lucid
5) Did you apply the acpi_backlight=vendor grub tweak? yup
6) Do you see the alpha blended brightness display when changing the
   brightness?yes
7) Does the brightness actually change? Sporadically

---

### Post by loko on 2010-05-31
Well,

for me the solution works. I have an ul30a.

Just a tip. I use burg instead of grub.

so you have to put ```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

in the file ```
/etc/default/burg
```

Edit: do not forget to sudo update-burg after editing the file

---

### Post by swraman on 2010-06-03
This thread ROCKS! :popcorn:

This method also works for the Asus U81A laptop.  I have a U81A, and 2 things have to be done in order for the fn keys screen brightness to work:

1) update the BIOS to version 210.  This Bios hasn't been released yet, but I used the U80 BIOS as they are essentially the same hardware, but the U81A was exclusive to Best Buy.  
2) use the method described in this thread.

Thanks a bunch!!

---

### Post by golkran on 2010-07-16
For users like me which this method didn't work. I found a new method working on Asus PC.
check here and modify your GRUB_CMDLINE_LINUX_DEFAULT
 [http://www.webupd8.org/2010/05/enable-fn-keys-on-your-asus-eeepc-and.html](http://www.webupd8.org/2010/05/enable-fn-keys-on-your-asus-eeepc-and.html)

---

### Post by Subcon86 on 2010-07-28
Hey I have a Toshiba Satellite M45-S331, and my function keys don't work either. I've tried the options in this thread, but none of them have worked for me. Is there anything else I can do to fix the issue?

---

### Post by aveminus on 2010-08-09
This is what worked for me.Thanx Silvan :)

1. Find out the vendor string used by hal:
$ lshal | grep system.hardware.vendor
(In my case: system.hardware.vendor = 'Sony Corporation )
2. Find out the product string:
$ lshal | grep system.hardware.product
(In my case: system.hardware.product = 'VGN-CR35G_R' )
3. Open /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi in an editor with root privileges
4. Add this line
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="Sony Corporation">
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="VGN-CR35G_R">
<!-- needed since the acpi video module reports it handle the events, but it don't work on this machines-->
<merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
</match>
</match>
5. Reboot!

---

### Post by D4v1dw1r7h on 2010-09-03
> **ed anger said:**
> Guys! It should work for everyone! First it didn't work for me, but I've noticed that the problem is with quotation marks in added line:

GRUB_CMDLINE_LINUX=”acpi_backlight=vendor”

Replace quotation marks from this line (in /etc/default/grub) with quotation marks that you type yourself. It has worked for me!


This worked for me aswell on my ASUS UL20a! I am very happy to see the community pull through with so much great info!

---

### Post by mfox on 2010-09-12
Thanks everyone for contributing these potential fixes, but unfortunately, I still don't have backlight control (or if I do, I don't know how to implement it).  I just bought a Toshiba NB305 netbook, and am running UNR Lucid.  I have tried installing the Toshiba laptop utilities, fnfx and fnfx-client, doing the two recommended modifications to grub (acpi_backlight=vendor; acpi_osi=linux) including changing the quote signs, and also aveminus' modifications to the /usr/share/hal ,,, file.  Hitting the Fn-F6 or Fn-F7 keys still don't affect the brightness on my netbook.

I'm wondering if it has to do with the acpi_backlight=vendor line.  Should the word, "vendor" be replaced with the actual vendor (TOSHIBA in my case)?  Or is there some other way of changing the brightness besides using the Fn keys?

---

### Post by josebama on 2010-10-14
well, I still have this problem with the brightness keys under Maverick with an Asus UL30A. I have tried all the solutions named here but none works at all for me. With the first one, the brightness controls are still weird but now the don't "queue" and I can use the other Fn keys even if there are brightness actios (up or down) waiting...

I also tried with the 32 bits version, with Linux Mint, Lucid... and nothing new happens. I am thinking about installing Karmik because I have read that there it worked well. Is there any issue about UL30A+Karmik that I should know?

Meanwhile I find any workaround or solution I will keep the brightness at max...

---

### Post by pashilkar on 2010-10-15
The solution mentioned by [golkran]("http://ubuntuforums.org/member.php?u=1113607") works for Acer Aspire 4736 with Ubuntu 10.04.
In  /etc/default/grub, modify the corresponding line as, 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

---

### Post by DeadLOK on 2012-01-24
Just a quick thank you, solved my brightness control this way :D

---

### Post by oldos2er on 2012-01-24
Closed, necromancy.

---

