---
title: "how to find my soundcard model"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by sunal on 2008-12-17
my soundcard is not working but i dont know how to fnd the model to ask for any help.....
thanks

---

### Post by Michael.Godawski on 2008-12-17
hi sunal, 

relax look here
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and report back :p

---

### Post by lovelyvik293 on 2008-12-17
Use the command lspci and the lshw command for the list of the hardwares in your system.

---

### Post by drs305 on 2008-12-17
These commands should give you what you want:
```

sudo lshw -C multimedia
lspci | grep "Audio" # if no hits, change to 'audio' or remove ' | grep "Audio" '

```

---

### Post by sunal on 2008-12-17
On lshw .... i get this

 description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

### Post by lovelyvik293 on 2008-12-17
You may check this 
[http://ubuntuforums.org/showthread.php?t=273800](http://ubuntuforums.org/showthread.php?t=273800)

---

### Post by sunal on 2008-12-17
im a complete noob... 
is there a hardware driver for my soundcard that i can install?
plz help

---

### Post by Michael.Godawski on 2008-12-17
Isn't the driver already installed? 
taken from the lshw output:

```
configuration:** driver=HDA **Intel latency=64 module=snd_hda_intel     
```

have you read the troubleshooting guide I posted above? and tried the steps suggested there? Feel free to ask if you do not understand the steps described there completely.

---

### Post by stefros68 on 2009-01-18
Help!

After using a script for installing a new alsa version I have lost my soundcard!

I am using an Amilo M 7400 with Ubuntu Intrepid.

My soundcard is a 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


Do you have any idea for getting it back!

---

