---
title: "Text Mode Screen Resolution"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by CosmicFlux on 2009-08-29
Hey,


Is it possible to change the default screen resolution in a text-mode tty? Or, say, if you wanted to start Ubuntu without XWindows?


Cosmic

---

### Post by loomsen on 2009-08-29
Hello.

Yes, sure it is.

Add 
```
vga=ask
``` 
to your kernelline and you'll be prompted at the next boot, showing some default values. You may enter 
```
scan
```
then if you need more resolution settings.

However, you should bear in mind or write down the number corresponding to your desired setting, and then make it a default.

For example, this is my commandline 
> 
[COLOR="Navy"]docter[~][/COLOR] cat /proc/cmdline 
rhgb vga=0x365 acpi_osi="Linux"
[COLOR="Navy"]docter[~][/COLOR] 


The notifications may either be in vga, extended or vesa compliant values.
This is, 

0x365 sets my display to 1440x900x24,
869   does the same

So if your line lists a versa driver, you will most probably have to use HEX annotation.

See the kernel doc package for further specifications.
> 
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/VGA-softcursor.txt
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/svga.txt
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/video-output.txt
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/power/video.txt
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/power/video_extension.txt

and
> 
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/x86/boot.txt
/usr/share/doc/kernel-doc-2.6.30.5/Documentation/x86/x86_64/boot-options.txt


---

### Post by CosmicFlux on 2009-08-30
Ok, great. 

How do I add vga=ask to the cmdline?

My cmdline output is as follows;

***root=UUID=42d0d1e7-95f6-4561-96aa-09a808aa37b7 ro quiet splash ***

Regards,

Cosmic

---

### Post by CatKiller on 2009-08-30
> **CosmicFlux said:**
>  How do I add vga=ask to the cmdline?

```
sudo nano /boot/grub/menu.lst
```

---

### Post by loomsen on 2009-08-30
And &#8593; should be a line with default options.

Like 

defopts=

Don't uncomment it, it will be parsed as is. Add the proper value, hit ctrl + x to save and close it and run 

sudo update-grub

Reboot, keep in mind which resultion fits your setup, reopen grub and add the proper value.

And don't forget to update-grub afterwards.

---

### Post by CosmicFlux on 2009-08-31
OK, thanx. That worked brilliantly. Until I rebooted that is. I then got no display at all.

My file says;

#defops=vga=323

When it was set to vga=ask and I selected number 323 from the list, it worked but when I added the value 323 to the file I get no display.

Any ideas?

Is it possible to change the font colour to all one colour, say green or red?? I know you can do it in the graphical terminal by editing .bashrc, but is it possible to do in the actual command-line, say tty1?


Cosmic

---

### Post by loomsen on 2009-08-31
Hi.

It's not 323 but 0x323

Thats the hexadecimal notation.

vga=0x323

*edit*
@bashrc

The "graphical terminal" is only a wrapper for the shell, so both will read .bashrc. Your shell prompt will look the same if you login with your account, regardless of runlevels.

---

### Post by CosmicFlux on 2009-09-01
OK, so by editing .bashrc I can effect changes to the default command line too, even if I started Ubuntu up to run as just command line?

I've looked at the colour codes but I can't seem to figure out how to make the colour apply to ALL output rather than just the prompt.

Cosmic

---

### Post by loomsen on 2009-09-01
Alright, it's probably easiest to implement some generic code you can easily refer to later on.

Here's an example I have in my bashrc
```

# ======== Custom prompt
# Define colors for readability
#black="\[\033[0;30;49m\]"
#blackgrey="\[\033[30;47m\]"
_red="\[\033[31;49m\]"
#green="\[\033[32;49m\]"
#yellow="\[\033[33;49m\]"
_blue="\[\033[34;49m\]"
#magenta="\[\033[35;49m\]"
#cyan="\[\033[36;49m\]"
#white="\[\033[37;49m\]"
r_color="\[\033[0m\]"           # Reset color
#clr="\[\033[K\]"                # Clear to the end of the line

if [ ${UID} -eq 0 ]; then
    user="$_blue\u"
else
    user="$_red\u"
fi
        
PS1="$user[\w]$r_color "
unset user r_color _red _blue

```

See the r_color? As the comment reveals, that's the code to unset a color to it's default. 
I don't know why you would want to set everything to a different color, cause I actually use it for better readability and to quickly find the last command if I have to scroll back a whole bunch of line or so.
Well, and most important to colorize my root prompt differently so I won't screw anything up. To achieve this, you will have to add it to your global bashrc tho, as you'd have to include a UID test.

You can see above.

So, one time environment settings &#8594; .profile
Shell/terminal settings which apply upon every shell login &#8594; .bashrc
And there's another file .bash_profile, which actually is the same as .profile. It will be executed only once, if it exists at all.

So, configuring your color should go into .bashrc, while for example loading your video device settings would go into .bash_profile (.profile)

If you want to include different colors too, it's pretty obvious why this has to be configured globally (&#8594; /etc/bash.bashrc for example)

---

### Post by CosmicFlux on 2009-09-01
Hmm OK, I've had a partial success. After setting the 'PS1=$' statement to include the colour code for bright green I now have the colour I want. The thing is, before logging in the colour is the default white. Can I change this to green also?

Cosmic

---

### Post by portalfan01 on 2009-09-01
dude thats cheesy LOL :KS

---

### Post by CosmicFlux on 2009-09-01
Ah, I've figured out that it's GRUB that controls the booting. All the boot info that appears in white is from GRUB right? So, is there any colour options I can specify in menu.lst to make all the boot text green?


Cosmic

---

### Post by loomsen on 2009-09-01
So you want something like

[[img]http://www.ubuntu-pics.de/thumb/23495/shot_34_4nK7Gu.png[/img]](http://www.ubuntu-pics.de/bild/23495/shot_34_4nK7Gu.png)
This?

It is possible, yes. But I'm usually trying to avoid booting, so I dont care, cause at best I will see that screen only once in a couple of days ;)

You shouldnt bother neither, your system does (or, lets put it should) reorganize files (based on the sysv scripts) and with some app i forgot the name of reordering your bootscripts. Plus, while booting, your system is usually under pretty high load. If you wanna do yourself a favor, ship it....

---

### Post by CosmicFlux on 2009-09-01
Not quite like that. EVERYTHING green. Like all text. But maybe you're right.

---

### Post by CosmicFlux on 2009-09-05
I basically wanted to re-create the look and feel of the old monochrome monitors. Y'know, before they'd developed monitors that could display multiple colours.

Byt as you say, if it's a hog on system resources then maybe it's better left!


Cosmic

---

### Post by Liolikas on 2009-09-05
setterm -foreground green
More tweaks:
man setterm

---

