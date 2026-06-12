---
title: "Jaunty and Skype"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Rrory on 2009-04-30
> 
I just installed Jaunty, and I have a problem getting Skype to work. I tried a test call and could hear ringing & the recording but then the call fails with the message:
  problem with audio capture

Could someone help me; using non-tecchie terms:)
thanks
Rory

---

### Post by PhilMize on 2009-05-01
What type of computer are you using? This makes all the difference. :)

---

### Post by Rrory on 2009-05-01
I'm using a Sony S-360 Vaio, about 4 years old.
 hardy heron worked just fine with skype on this machine

---

### Post by PhilMize on 2009-05-01
Sounds like you'll need to install ALSA drivers and compile them. I only know how to do this with Lenovo laptops, sooo your on your own for Sony. But FTR heres the post I followed to figure out the general process. Thanx to Hunter-Thomson.


> **HunterThomson said:**
> **_How to get the sound working_**

[U][B]Copy of wyth's post on Page 15 of this thread
[/B][/U]

[http://ubuntuforums.org/showthread.php?t=870681&page=15](http://ubuntuforums.org/showthread.php?t=870681&page=15)

Okay, I'm just basically reposting what is already on this Ubuntu help page and on the previous Lenovo Ideapad Y510 is GO page, but with some new tweaks. This guide is using the 1.0.18rc3 ALSA drivers, but this will/should work for other drivers.

First, you need to make sure you have the right stuff installed:

Code:

```
  sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

Next get the latest ALSA drivers; they'll be downloaded to wherever your default downloads go, but you're going to move them to a new directory. For this case, I'll use the Desktop.

    * alsa-driver
    * alsa-lib
    * alsa-utils

Next step is to create a /usr/src/alsa directory for the files and copy the tar.bz2 files to that directory; you may have this directory of you've rolled your own drivers in the past:

Code:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/Desktop/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```
    * Compile and install alsa-driver

Code:

```
cd alsa-driver* 
sudo ./configure --with-card-options=hda-codec-realtek,hda-codec-analog,hda-codec-sigmatel,hda-codec-via,hda-codec-atihdmi,hda-codec-conexant,hda-codec-cmedia,hda-codec-si3054,hda-generic
sudo make
sudo make install
```

    * Compile and install alsa-lib

Code:

```
cd ../alsa-lib* 
sudo ./configure 
sudo make 
sudo make install

```
    * Compile and install alsa-utils

Code:

```
cd ../alsa-utils* 
sudo ./configure 
sudo make 
sudo make install
```

Next find out what sound card you're using:

Code:

```
cat /proc/asound/card0/codec#* | grep Codec
```
The Y510 uses RealTek ALC888, so look for that. (This may be different if you have a newer version of the Y510 with some different hardware.)

Next you can check the ALSA-Configuration for specifics on the sound card. I found it at
Code:

```
/usr/src/alsa/alsa-driver*/alsa-kernel/Documentation/ALSA-Configuration.txt
```

Look for the section titled ALC883/888. There are many possible options, and some work better than others.

    &#8227; 3stack-6ch
    &#8227; 3stack-6ch-intel
    &#8227; lenovo-101e (Lenovo 101E)
    &#8227; lenovo-nb0763 ( Lenovo NB0763)
    &#8227; lenovo-ms7195-dig (Lenovo MS7195)
    &#8227; lenovo-sky (Lenovo Sky)
    &#8227; auto (Gets the information from BIOS)

Next to tell alsa-base what to do:
Code:

```
sudo nano /etc/modprobe.d/alsa-base
```

at the end of that file, add:
Code:

```
  options snd-hda-intel model=MODEL
```

For model=MODEL, use one of the options from above, such as:

    &#8227; options snd-hda-intel model=lenovo-sky

I found model=lenovo-sky worked beautifully and then you will have no problem with the speakers muteing with you plug in headphones.

You will want to reboot now...

```
sudo reboot
```

Then you will want to set up the default sound settings by doing this...

Open a shell and swich to the root user:

```
sudo su
```

Then set the sound up to the way you would like it at startup:
(Hint, make sure headphone is NOT muted, Frount to 100%, Surround 100%, Center 100%, LFE 100%, Side 100%, and I like to have Master set to 50% at startup.)

(Hint, use the arow keys and the "Esc" key to exit)

```
alsamixer
```

After exiting the Alsamixer, run this command to save your sound settings:

```
alsactl store
```

Then reboot:

```
reboot
```

Reboot and see if it's working. In the past, kernel updates did not break this. The surround sound features are present, the system sounds work, and the headphones automatically mute all speakers when plugged in.

_____________________________________________________________________________________



**_How to get the sound working in Arch Linux_**

In the shell:

pacman -S alsa-oss alsa-utils alsa-lib

Then add this line to the end of /etc/modprobe.conf

```
sudo nano /etc/modprobe.conf
```

```
options snd-hda-intel model=lenovo-sky
```

reboot or restart the alsa daemon

```
sudo reboot
```

Then you will want to set up the default sound settings by doing this...

Open a shell and swich to the root user:

```
sudo su
```

Then set the sound up to the way you would like it at startup:
(Hint, make sure headphone is NOT muted, Frount to 100%, Surround 100%, Center 100%, LFE 100%, Side 100%, and I like to have Master set to 50% at startup.)

(Hint, use the arow keys and the "Esc" key to exit)

```
alsamixer
```

After exiting the Alsamixer, run this command to save your sound settings:

```
alsactl store
```

Reboot and all well be working:)

---

### Post by mikewhatever on 2009-05-01
> **PhilMize said:**
> Sounds like you'll need to install ALSA drivers and compile them. I only know how to do this with Lenovo laptops, sooo your on your own for Sony. But FTR heres the post I followed to figure out the general process. Thanx to Hunter-Thomson.

This is a bad advice, IMO, and completely unnecessary. 

Rrory, go to the sound settings tab in Skype and change your capture device. You may have more then one option.

---

### Post by rajeev1204 on 2009-05-01
> **Rrory said:**
> I just installed Jaunty, and I have a problem getting Skype to work. I tried a test call and could hear ringing & the recording but then the call fails with the message:
  problem with audio capture

Could someone help me; using non-tecchie terms:)
thanks
Rory


In skype>options>audio devices change sound input to plughw 0 or 1 or 2 and it should work.


regards
rajeev

---

### Post by PhilMize on 2009-05-01
lol my B :( I just realized I way overthought that...

---

### Post by cariboo on 2009-05-01
Even if the op were to use your solution, there is no need to compile alsa from source, as it is all available in the repositories.

---

