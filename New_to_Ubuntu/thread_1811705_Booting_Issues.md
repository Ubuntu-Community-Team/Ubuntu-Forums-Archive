---
title: "Booting Issues"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Pyprokid on 2011-07-25
Hello! :)

I am having an issue with my Ubuntu that I am hoping you guys could help me address. :biggrin:

I installed Ubuntu two days ago. Sense I have noticed improved performance, sleeker more elegant GUI, and a seemingly more stable system... except for when I reboot the system.

I reboot it, and I get a blank purple screen, I wait a while but nothing seems to happen. After a LONG time, still nothing so I decide to try another boot, this time I get a screen with a selection of different boots, Ununtu Generic, Recovery Mode, and a few other things  I can't remember. :-k

I click on the normal boot option and it takes about 5 minutes to get to the log in screen. 
I would like to be able to boot once and get it without any errors. :cool:

Probably something obvious and I look dumb...:lolflag:

Any help is GREATLY appreciated. 

-Matt

---

### Post by MG&amp;TL on 2011-07-25
The screen with lots of different thing like:

'Ubuntu, 2.x generic'
Ubuntu, 2.x generic, recovery mode'
memtest86+
Windows

Is the GRUB screen. You use it to pick your OS. If you dual-booted, that's normal, but if you didn't, you've got a problem. Did you click 'install alongside windows'? on the ubuntu installer?

---

### Post by drs305 on 2011-07-25
Matt,

Welcome to Ubuntu.

What you are describing as far as menu selection sounds like you have a single OS. The first time it boots directly without displaying a menu, but when the boot fails it displays the Grub 2 (bootloader) menu the second time.

So the bootloader is working as it is designed to. The problem is with the OS. Are you able on the second boot to get into your system (even if it takes a while to get there)? If so, you may need to install the driver for your video card, if you have one.

If you are using Natty, click the upper left icon, type in 'Additional Drivers' and click on the link that appears and see if there is a driver for your video card.

If this doesn't work, you can also try altering the menu when it appears on the second boot. Highlight the first entry, press 'e' to enter the edit mode, and cursor to the end of the line starting with "linux". 

At the end of the line should be "quiet splash" and perhaps "vt.handoff=7". Use the backspace key and remove all of these and add **nomodeset**
Press CTRL-x to boot and see if it boots to the Ubuntu desktop. If so, again try to install drivers using the Additional Drivers option.

---

### Post by Pyprokid on 2011-07-25
Drs305, 

Thank you very much you for your post! :D
I did as instructed and it said "No proprietary drivers are in use on this system." 
What course of action should I take from here?

---

### Post by drs305 on 2011-07-25
> **Pyprokid said:**
> Drs305, 

I did as instructed and it said "No proprietary drivers are in use on this system." 
What course of action should I take from here?

Do you have a separate video card on your system? If not, then the Addl Drivers section could very well be empty.

Did adding 'nomodeset' change the way the system booted? That switch instructs the kernel not to load extra modules during boot - modules that might be causing conflicts and interrupting the normal boot process.

Unfortunately I'm not an expert on most booting issues once the bootloader passes control over to the kernel. Let's see if someone comes along who is...

---

### Post by Pyprokid on 2011-07-25
Doh! 

I overlooked what you said earlier about 

```

nomodeset

```

I just did that and it addressed the problem nicely. Warmest thanks! :P:P:P

---

### Post by drs305 on 2011-07-25
> **Pyprokid said:**
> Doh! 

I overlooked what you said earlier about 

```

nomodeset

```

I just did that and it addressed the problem nicely. Warmest thanks! :P:P:P

The way you edited the Grub 2 menu is non-persistent. It won't stick and you will have to repeat the procedure on the next boot.

You can make it permanent by adding it to one of the Grub 2 configuration files. You will have to edit the file as root:

```
gksu gedit /etc/default/grub
```

Modify this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to *
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Save the file, then update the menu with:
```
sudo update-grub
```

* Removing "quiet" will now display lots of text as the system boots. It's possible that you can simply *add* 'nomodeset' to the existing line. Normally we recommend removing these other entries, but if you don't want to see the text, you can see if it works with two or all three entries on the line (for example: quiet nomodeset). If you want to try it, I'd leave just 'nomodeset' and then play with adding the others on the linux line during boot to experiment, since these won't be saved if it doesn't work.

Back to the main issue:
By using 'nomodeset' you are disabling one or more modules that are causing your system problems. In this case, you may be disabling more modules than necessary, and you may be able to do some troubleshooting to see specifically which module is causing this problem. (Out of my area of expertise though)

---

### Post by Pyprokid on 2011-07-25
Okay, done. :KS
Once again, thanks a bunch this was very helpful and easy to understand. :)


Sincerest thanks, 
-Matt            :popcorn:

---

