---
title: "Graphics default back to motherboard???"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by SteveFJ on 2010-02-07
Hi,
I'm new to Ubuntu, but liking it much so far.

The installed graphicscard is an nvidia 8500GT. The driver has been installed.

I appear to have a couple of minor issue with the graphics though:

It defaulting back to the motherboard graphics when the pc is shutdown and started again.

I am also unable to save my preferred screen resolution configuration as it is not parsing. I get the following message:

 > Failed to parse existing X config file '/etc/X11/xorg.conf'

Any advice to address these issues would be most appreciated.

Thank you.

---

### Post by Hetor on 2010-02-07
Post your xorg.conf
Type "gedit /etc/X11/xorg.conf" or "less /etc/X11/xorg.conf" in the terminal.

---

### Post by SteveFJ on 2010-02-07
Hi Hetor, thank you for your reply.

xorg.conf:

> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by TeoBigusGeekus on 2010-02-07
The settings of nvidia cards are better configured via nvidia-settings
```
sudo apt-get install nvidia-settings
```
Then
```
gksudo nvidia-settings
```
Your changes should be permanent then.

---

### Post by SteveFJ on 2010-02-07
hi, thank you for your reply. I have just tried that and got the following:

> VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

---

### Post by TeoBigusGeekus on 2010-02-07
```
gksudo gedit /etc/X11/xorg.conf
```
Remove the whole screen part - your file should look like this
```
Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Default Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection
```
Save, exit and then run the nvidia-settings as root again.

---

### Post by SteveFJ on 2010-02-07
Hi, I've just done that and rebooted.

I got a message on start up stating that the monitor wouls be running in low graphics mode

I've now tried to look at the nvidia server settings and got the following message:

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I'm not entirely sure what I should do there.

I got the following when I just entered that in the terminal:

> Using X configuration file: "/etc/X11/xorg.conf".

PARSE ERROR: Parse error on line 9 of section Device in file
             /etc/X11/xorg.conf.
             Unexpected EOF. Missing EndSection keyword?


ERROR: Unable to write to directory '/etc/X11'.

---

### Post by NCLI on 2010-02-07
Try deleting everything in the xorg.conf file(After copy-pasting it to another document as a backup), then run the command again.

---

### Post by TeoBigusGeekus on 2010-02-07
Run 
```
gksudo nvidia-xconfig
```

---

### Post by SteveFJ on 2010-02-07
Hi thanks for your reply. No joy there either I'm afraid.

---

### Post by SteveFJ on 2010-02-07
This is wht I get when I run 
> gksudo nvidia-xconfig

> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

WARNING: No Screen specified, constructing implicit screen section.


WARNING: No Layout specified, constructing implicit layout section using
         screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add
         new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add
         new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the
         layout; using the first keyboard device.

---

### Post by TeoBigusGeekus on 2010-02-07
Ok, run now
```
gksudo nvidia-settings
```

---

### Post by SteveFJ on 2010-02-07
I then get this message as the nvidia x server settings loads

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by TeoBigusGeekus on 2010-02-07
Reboot and run it again.

---

### Post by SteveFJ on 2010-02-07
Thanks very much for your help. That appears to have sorted it.

Most appreciated. :D
[URL="http://ubuntuforums.org/member.php?u=504094"]
[/URL]

---

