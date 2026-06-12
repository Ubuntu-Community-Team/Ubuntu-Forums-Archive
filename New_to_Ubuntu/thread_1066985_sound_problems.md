---
title: "sound problems"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by oz7 on 2009-02-11
hello. 
i am new in the ubuntu community. i have ubuntu 8.02 and i am having problems with the sound. i can hear the sounds in start-up and also any sound when i am using the an internet browser (like if i am watching a video on youtube), but on very bad quality (sound is really fuzzy). additionally i cant hear any sound when i want to play a track(mp3, though the default media player of ubuntu) or watch a video, like as if the laptop is on mute (but its not, so i dont want to hear any answer like, check the volume or anything). 
thats why i would like know if you could help me out with this. 
thank you in advance

---

### Post by halitech on 2009-02-11
did  you install all of the restricted media codecs? by default ubuntu doesn't install them so mp3's will appear to play but give no sound

---

### Post by Therion on 2009-02-11
Open a Terminal and use Copy and Paste to enter the following:```
sudo apt-get install ubuntu-restricted-extras
```
Follow the prompts to install some packages you need.

---

### Post by oz7 on 2009-02-12
thanks guys. that worked in terms of hearing the sounds. the other prob that still remains is that the sound is really fuzzy now. even in start-up there are problems with the quality of the sound. that problems weren't noticed before i do some updates by ubuntu.
any suggestions for that? 
thank you in advance

---

### Post by Metallion on 2009-02-12
Could you check the sound section in the control panel and set it to ALSA if it isn't set to that already?

Also which sound card do you have?

---

### Post by oz7 on 2009-02-12
> **Metallion said:**
> Could you check the sound section in the control panel and set it to ALSA if it isn't set to that already?

Also which sound card do you have?

hmmmm how do i do that? i mean how to get to control panel. sorry but i am a complete amateur:(. 
give a couple of mins to tell you about the sound card.

---

### Post by Metallion on 2009-02-12
Sorry, I'm not on an ubuntu machine now so I can't check the exact clicks. :( I think it's somewhere like System and then settings or preferences or so.

In linux mint you can just type gnome-sound-properties in a terminal. Can you try this?

---

### Post by oz7 on 2009-02-12
ok cool i found it. i changed all the settings to ALSA but still no change on the quality of the sound:(. thank you though :) i reckon we are getting close

---

### Post by oz7 on 2009-02-13
anyone any ideas????????

---

### Post by Metallion on 2009-02-13
Can you post the output of this command?
```
sudo lshw -C multimedia
```

This should show us which soundcard you have and then we can work from there.

---

### Post by oz7 on 2009-02-14
the output of this command is: 

  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Metallion on 2009-02-15
Alright thanks. That's a very similar card to mine but just a bit of a newer model. My sound was broken at first too and I solved it by adding this line to the end of the file /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=auto
```

This was a solution for my older card so I'm not sure if it will work for yours. I did a quick search for yours and found somebody suggesting this line instead:

```
options snd-hda-intel model=mitac
```

After you've added one or the other, try rebooting and see if there's any difference. Don't add both lines in there together though.

---

### Post by oz7 on 2009-02-17
> **Metallion said:**
> Alright thanks. That's a very similar card to mine but just a bit of a newer model. My sound was broken at first too and I solved it by adding this line to the end of the file /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=auto
```

This was a solution for my older card so I'm not sure if it will work for yours. I did a quick search for yours and found somebody suggesting this line instead:

```
options snd-hda-intel model=mitac
```

After you've added one or the other, try rebooting and see if there's any difference. Don't add both lines in there together though.

sorry man but every time i enter any of these two lines this message pops up:
bash: options: command not found
you sure thats the right piece of code?thanks though

---

### Post by mafsi on 2009-02-17
> **oz7 said:**
> sorry man but every time i enter any of these two lines this message pops up:
bash: options: command not found
you sure thats the right piece of code?thanks though

this is the line you forgot to read:

> I solved it by adding this line to the end of the file /etc/modprobe.d/alsa-base

you have to:

> sudo gedit /etc/modprobe.d/alsa-base

and add

> options snd-hda-intel model=mitac

at the end of the file and save the file

---

### Post by 3rdalbum on 2009-02-17
Another thing that might be causing the problem is the PCM volume control.

Right-click on the little speaker icon in the top panel and go to "Open Volume Control". The little slider that says PCM should be close to the top, but not at maximum. If it's at maximum, turn it down a little and see if this solves the problem.

---

### Post by Metallion on 2009-02-17
Indeed, I meant it as Mafsi says. Maybe i should have been a little clearer. :oops:

Let me know if any of these help. :)

---

### Post by oz7 on 2009-02-17
thanks guys for your help but it doesn't seem to work. i added the lines as you said but still the quality of the sound is crap. very fuzzy:(

---

### Post by Metallion on 2009-02-17
Hmmm I see. I'm assuming it's a laptop you have, right? On [http://www.ubuntu-fr.org/](http://www.ubuntu-fr.org/) there's a list of laptops and people who have experience installing Ubuntu on them. I've already solved quite a few issues by using that but the site is in French.

If you don't speak French, I could have a look for you if you tell me which model of laptop you have.

---

### Post by oz7 on 2009-02-17
sorry but i dont speak french yet:( my laptop is an HP Pavilion dv2500 Notebook PC

---

### Post by Metallion on 2009-02-18
I checked the website but unfortunately there's no entry for your laptop :(. Then I checked [www.linux-laptop.net](www.linux-laptop.net) but it didn't have yours either.

I did find one other thread on this forum with your exact problem and that person was pointed here => [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

That looks like a very general howto so I'm not sure if it will work for you. If I can find something else, I will let you know!

---

### Post by oz7 on 2009-02-18
thanks a lot mate. i just made some sort of configurations and it seems that the sound now is crystal clear. i just hope this is a permanent change. THANK YOU ALL FOR YOU CONTRIBUTION.especially metallion!!!

---

### Post by Metallion on 2009-02-18
Awww, it's nothing. ^_^

---

