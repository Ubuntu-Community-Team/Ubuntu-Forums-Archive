---
title: "Linux on HP Pavillion dv4 1280us"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by hiranpm on 2009-07-14
Hi!

I've installed  Ubuntu on my laptop  HP Pavillion dv4 1280us, but theres no drivers for linux on HP's site. 

The mother board is Compal 30f7.

Everything is working well. The only problem is the audio... it doesn't work, and I don't know where to download the audio driver.

Plz someone help me!!

I need this answer as soon as possible.

Thank you!

---

### Post by margni on 2009-07-14
Could you run lspci from a terminal -  lspci |grep Audio 

and paste it back here so someone could take a look at it to see what sound card you have?

That's the first step to get help.

Second, when you say no sound does that include getting system sounds i.e. login/logoff etc?  Do you have anything muted or not turned up with Ubuntu's sound mixer?

Hope that gets you started.

---

### Post by nhasian on 2009-07-14
you dont need to download anything from HP's website.  can you give us the output of the following commands from the terminal?
```

lshw -C multimedia
```

```
lsb_release -a
```

---

### Post by aesis05401 on 2009-07-14
> **margni said:**
> *snip*... Second, when you say no sound does that include getting system sounds i.e. login/logoff etc?  Do you have anything muted or not turned up with Ubuntu's sound mixer? *snip* ...

I run a different model of the same computer line.  alsa mixer was defaulted to mute for some reason - and I thought my sound was broken until I checked alsa-mixer.

Just my .02c.  If anyone knows why this happens I would love to know.

---

### Post by hiranpm on 2009-07-15
> **nhasian said:**
> you dont need to download anything from HP's website.  can you give us the output of the following commands from the terminal?
```

lshw -C multimedia
``````
lsb_release -a
```

lshw -C multimedia
 *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

---

### Post by nhasian on 2009-07-15
hello hiranpm,

you have the same intel audio chipset that i have and it looks like its loading the correct driver, so you should be getting sound.

Can you click on the speaker icon next to the time on the menu bar and open up the volume control?  check to make sure the volume sliders are up and nothing is muted.

---

### Post by gubertoli on 2009-07-27
Hello Everybody...
I have the same laptop and the same info...

root@drwxr-ubuntu:/home/drwxr# lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

root@drwxr-ubuntu:/home/drwxr# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

But my case is that when the Ubuntu starts the sounds frozen (its like a loop sound that dont stop) then I have to kill the process: 
3125 ?        SL     0:00 /usr/bin/aplay -q -N /usr/share/sounds/question.wav

Then if I start any mp3 at the Totem its not work. Any sugestion ? Thanks Everybody!

---

### Post by gubertoli on 2009-07-29
After that the sound doesnt work anymore... :confused:

---

### Post by gubertoli on 2009-08-09
up :confused:

---

