---
title: "No sound on Dell Mini 10 with Ubuntu 9.10"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by wellsda41 on 2009-12-02
I have Ubuntu 9.10 installed on a Dell Inspiron Mini 10 (not 10v) and I get no sound from internal speakers or earphones. Any suggestions?

---

### Post by Locke_99GS on 2009-12-02
> **wellsda41 said:**
> I have Ubuntu 9.10 installed on a Dell Inspiron Mini 10 (not 10v) and I get no sound from internal speakers or earphones. Any suggestions?

Make sure it's not muted. Sometimes I find that right after a fresh install, my audio devices are muted. I don't know why.

---

### Post by wellsda41 on 2009-12-02
I checked. The muted boxes are not checked.

---

### Post by Locke_99GS on 2009-12-02
List your PCI devices and see if the audio device is detected.

```

lspci |grep udio

```

---

### Post by wellsda41 on 2009-12-02
david@david-netbook:~$ lspci | grep udio
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD A

---

### Post by Jackyboy86 on 2009-12-02
sudo nano /etc/modprobe.d/alsa-base.conf

add 'options snd-hda-intel model=basic' to the end, and put a # 
in front of the line 'options snd-hda-intel power_save=10 power_save_controller=N'
Ctrl+o to save, ctrl+x to exit.
Reboot.
That should do it...

---

### Post by wellsda41 on 2009-12-02
> **Jackyboy86 said:**
> sudo nano /etc/modprobe.d/alsa-base.conf

add 'options snd-hda-intel model=basic' to the end, and put a # 
in front of the line 'options snd-hda-intel power_save=10 power_save_controller=N'
Ctrl+o to save, ctrl+x to exit.
Reboot.
That should do it...


I tried it. It didn't work.

---

### Post by Jackyboy86 on 2009-12-02
System>Preferences>Sound should show you what sound drivers you're using.

On the hardware tab, I'm using 'Analog Stereo output' and on the output page 'analogue headphones'

If thats the same, go to a terminal and check alsamixer.

It's a terminal volume control, check that there are no 'MM' over any of the output boxes. If there are, hit M over them, they'll turn on. Then try it.

---

### Post by wellsda41 on 2009-12-02
If thats the same, go to a terminal and check alsamixer.


I'm brand new to this. How do I "check" alsamixer?

---

### Post by joelseff on 2009-12-02
I'm about a week into this but "sudo alsamixer" gets alsa mixer.  

I have all these settings but still no sound.  I had sound until I removed my XP partition yesterday now no sound.  Funny thing was when I had XP and muted the XP there was no sound on ubuntu. Was ubuntu somehow using the XP drivers???? HELLPPP I really like ubuntu and have been using puppylinux for about a year and HATE MS!!!  Sorry for the threadjack

Joe

---

### Post by wellsda41 on 2009-12-02
> **Jackyboy86 said:**
> System>Preferences>Sound should show you what sound drivers you're using.

On the hardware tab, I'm using 'Analog Stereo output' and on the output page 'analogue headphones'

If thats the same, go to a terminal and check alsamixer.

It's a terminal volume control, check that there are no 'MM' over any of the output boxes. If there are, hit M over them, they'll turn on. Then try it.


With settings the same as you reported:
alsamixer showed a bar chart for "Master", Head Phone and PCM. All others (Front, Front Mi(2) and Mic were blank bars and several had MM, but the only ones that would change were Master and PCM. No sound.

I also tried alsamixer with output changed to Analog output. It shoew the same, except Front also had a bar chart. Still no sound.

---

### Post by joelseff on 2009-12-02
I GOT IT TO WORK!!!! I just messed with each of the levels on alsamixer and voila!  Thnks guys good luck wells! Oh you have to push the "m" key to turn on the MM levels and you can move em

---

### Post by wellsda41 on 2009-12-02
> **Jackyboy86 said:**
> System>Preferences>Sound should show you what sound drivers you're using.

On the hardware tab, I'm using 'Analog Stereo output' and on the output page 'analogue headphones'

If thats the same, go to a terminal and check alsamixer.

It's a terminal volume control, check that there are no 'MM' over any of the output boxes. If there are, hit M over them, they'll turn on. Then try it.



I di.d some serious reading and learned how to manipulate alsamixer. I now have all bar charts and no MM's. I also went back and made the suggested modifications to /etc/modprobe.d/alsa-base.conf. No matter what I do, still no sound.

---

### Post by wellsda41 on 2009-12-02
> **Jackyboy86 said:**
> System>Preferences>Sound should show you what sound drivers you're using.

On the hardware tab, I'm using 'Analog Stereo output' and on the output page 'analogue headphones'

.



What should show on the Input page?  There is no choice to select from, just a blank frame.

---

### Post by Chris Edgell on 2009-12-02
Do you want to take the time to read my thread that I just marked solved....
I'm so new too, so it all comes to the simplest terms.
Hope it works for you.

---

### Post by wellsda41 on 2009-12-03
I finally got it to work by using alsamixer and maxing output.

---

