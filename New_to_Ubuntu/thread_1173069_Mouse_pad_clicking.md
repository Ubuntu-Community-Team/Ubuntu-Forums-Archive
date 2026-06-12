---
title: "Mouse pad clicking?"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by kd0afk on 2009-05-29
I can't seem to find where to disable mouse clicking by tapping on the mouse pad. I know where to find it in ubuntu and in kubuntu there is a thing in system settings that controls the mouse and keyboard but in the mouse section there is nothing about changing the clicking style. Please, someone clear this up for me, maybe I am just missing it.

thanks.

---

### Post by Hospadar on 2009-05-29
You could try using gsynaptics to configure your touchpad.  I've never used it before but it is apparently a tool to configure synaptics touchpad (which is what most laptops have) options.

---

### Post by LowSky on 2009-05-29
To clear things up -- The mouse pad you keep refering to is called a trackpad or touchpad..  A mouse pad is the term for a pieces of cloth or plastic you keep under a conventional mouse.

---

### Post by kd0afk on 2009-05-29
> **Hospadar said:**
> You could try using gsynaptics to configure your touchpad. I've never used it before but it is apparently a tool to configure synaptics touchpad (which is what most laptops have) options.
 
Any idea how to make and make install it? I was able to compile it but when I entered 'make' and then 'make install' I got errors.

---

### Post by taavikko on 2009-05-29
> **kd0afk said:**
> Any idea how to make and make install it? I was able to compile it but when I entered 'make' and then 'make install' I got errors.

why build from source, when it's available from the repositories?

```
sudo apt-get install gsynaptics
```
Note: it's bit obsolete from 9.04 on, use gpointing-device-settings
```
sudo apt-get install gpointing-device-settings
```

---

### Post by JK3mp on 2009-05-29
Definately install from repo's. Less dependencie issue's... ;)

---

### Post by Gen2ly on 2009-05-29
'man synaptics'

synaptics is the driver for the touchpad.  You can enter settings for your touchpad in your xorg.conf.  Look for Touchpadoff (i think) in the man-page.  gsynaptics does the same thing by invoking the driver.  gsynaptics is a gnome app but no big deal really and would be easier to use if you're new.

---

### Post by kd0afk on 2009-05-29
> **taavikko said:**
> why build from source, when it's available from the repositories?

```
sudo apt-get install gsynaptics
```Note: it's bit obsolete from 9.04 on, use gpointing-device-settings
```
sudo apt-get install gpointing-device-settings
```

This brings me to a question; I like the installing from the repositories but how does one know what to inter into the command line to get a program from the repositories? Is there a list somewhere?

---

### Post by OffAxis on 2009-05-29
previously you would edit the xorg.conf file and add a line to the synaptics section that read 
```
 Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable
```

From 8.04 on up hal controls the input devices, so you've got to add an .fdi file to here /etc/hal/fdi/policy to control your touchpad, or use the xinput commands.

Here is a much better write-up than I could muster:
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by OffAxis on 2009-05-29
> This brings me to a question; I like the installing from the repositories but how does one know what to inter into the command line to get a program from the repositories? Is there a list somewhere?
if you're on the command line you can use aptitude.

```
aptitude search <package name>
```

the command supports wildcards, so if you have an idea of the package name you can usually find it.

---

### Post by kd0afk on 2009-05-29
> **OffAxis said:**
> if you're on the command line you can use aptitude.

```
aptitude search <package name>
```the command supports wildcards, so if you have an idea of the package name you can usually find it.
thanks, I am learning allot.

---

### Post by kd0afk on 2009-05-30
I installed gsynaptics because when I did an aptitude search on gpointing I got nothing. I went to System>Preferences>Touchpad I got this error:  [COLOR=Red]GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
[/COLOR]So I went into terminal to edit xorg.conf and there was nothing about SHMConfig. in that file and I can't even find XF86Config.

---

