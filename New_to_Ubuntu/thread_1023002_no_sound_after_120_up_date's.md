---
title: "no sound after 120 up date's"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by sunshine2 on 2008-12-27
i have no experince at all of the ubuntu. (this is my friends notebook)so if possible any advice needs to be very simple as i will not have a clue as to what i am doing.

my friend has only had this notebook about 2 weeks and after the 2nd or 3rd time of turning it on she got asked to do the up date's all 120 of them (i dont know what the up date's where) but ever since she done this, she can not get any sound and when you click on for the volume control it comes up with. 

"the volume control did not find any elements and/or devices to control. this means eather that you don't have the right GStreamer plug-ing installed, or that you don't have a sound card configured"

double click comes up with.
"no volume control GStreamer plugins and/or devices found"

now i know that she did have sound on it as she was showing me the diffrent things on it when she first got it and there was sound then, any help on this would be very welcom as i am now stumped as to how to sort it out and i am not normaly beaten by these things but this one has well and truley got me :confused:

thank you in advance for any help

PS: it is a Toshiba NB100

---

### Post by halitech on 2008-12-27
open a terminal and post back the results of
```
aplay -l
```
```
lspci
```
```
lshw -C sound
```

---

### Post by eagle416 on 2008-12-27
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by linux_tech on 2008-12-27
what is output of ```
aplay -l
```

If you are familiar with using alsamixer, this command will will show all the alsamixer settings

```
alsamixer -D hw:0
```

check all volume settings, make sure nothing is muted

Also to open volume control type:
```
gnome-volume-control
```

you can also use Gnome-alsamixer, but you will need to install it first.


```
sudo apt-get install gnome-alsamixer
```

---

### Post by sunshine2 on 2008-12-27
> **halitech said:**
> open a terminal and post back the results of
```
aplay -l
```

invalid option -- 1

```
lspci
```

command not found 

```
lshw -C sound
```

comand not found

---

### Post by sunshine2 on 2008-12-27
i have done aplay -l and it is saying that "no soundcards found" which i cant under stand as there was sound on there before up date's were done

---

### Post by halitech on 2008-12-27
this is strange, unless something happened to the physical hardware there is no reason why it shouldn't be listing it. I'm wondering, is it a usb sound card by chance?

also, when you did the second command, did you do -l (lower case L) or -1 (the number one?)

---

### Post by sunshine2 on 2008-12-27
lower case l

---

### Post by halitech on 2008-12-27
something must be borked if basic commands like lspci aren't found. go back to the terminal and do this
```
sudo apt-get install lshw
```

ps. thats a lower case L

---

### Post by sunshine2 on 2008-12-27
I think it might be a case of her taking it back to where she got it from

---

### Post by sunshine2 on 2008-12-27
i have done that do i need to re-start as it has install something

---

### Post by halitech on 2008-12-27
no need to restart like you do with windows. try the command again
```
lshw -C sound
```

---

### Post by neu2buntu on 2008-12-27
```
sudo apt-get install --fix-missing
```  try this ,maybe your update broke packages or ```
sudo dpkg --configure -a
``` to reconfigure any unconfigured packages

---

### Post by sunshine2 on 2008-12-27
it has come up with 

WARNING: you should run this program as super-user.
*- multimedia unclamed
description: audio device
product: 82801G (ICH7 family) high definition audio controller
vendor: intel corporation 
ect....

but it is still saying thah there is no GStreamer plugins and/or devices found

---

### Post by halitech on 2008-12-27
here is mine

```
*-multimedia            
       description: Multimedia audio controller
       product: ES1370 [AudioPCI]
       vendor: Ensoniq
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=ENS1370 latency=32 maxlatency=128 mingnt=12 module=snd_ens1370
```

do you see a line about configuration that lists a driver?

---

### Post by sunshine2 on 2008-12-27
configuration: latency=0 and that is all it has got

---

### Post by halitech on 2008-12-27
strange.... try the 2 steps that neu2ubuntu posted, maybe they will re-install whatever modules are missing and then reboot. if that doesn't work, something else is going on

---

### Post by sunshine2 on 2008-12-27
i have done both of what neu2ubuntu said and re-started it but it is still saying the same

---

### Post by halitech on 2008-12-27
I'm guessing that since it is a laptop that she is not using an external card of some sort like a usb card or a pcmcia card?

---

### Post by sunshine2 on 2008-12-27
no she is not using any of thoes she would not know how to as if anything goes wrong with any of there computers they ask me (even to put an antivirus on them)

---

### Post by halitech on 2008-12-27
ok, try this from the terminal

```
sudo alsaconf
```
see if this will find and configure the sound card

---

### Post by sunshine2 on 2008-12-27
command not found

---

### Post by sunshine2 on 2008-12-27
thank you very much for trying to help me with this problem. i think she is going to take it back to where she got it from as cant seem to get the problem sorted out.

ps: if you do think of any thing else to try please let me know

---

### Post by halitech on 2008-12-27
one of the updates must have killed alsa which is responsible for sound on the system. you could try reloading alsa
```
sudo apt-get remove alsa-base alsa-utils linux-sound-base && sudo apt-get install alsa-base alsa-utils linux-sound-base
```

beyond this, not really sure what else to suggest

---

### Post by neu2buntu on 2008-12-27
here is the command to reload alsa ```
/sbin/alsa force-reload
```you might have to do this as sudo(not sure)....hope this helps man
```
sudo /sbin/alsa force-reload
```

---

### Post by motio on 2008-12-28
read the instruction on the url
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
i hope this will help you
it work fine for me

---

