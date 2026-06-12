---
title: "How to mute sound on Internel-speaker..?"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by Linyx on 2011-01-06
[SIZE=2]I have internal-speaker which i don't want to use now...i want to use only head-phones, but when i set the Output to [/SIZE]**[SIZE=2]Analog-[/SIZE]**[SIZE=2]**headphones**, their isn't sound and when i select the output to "**Analog Output**" ,then sound Appear on both Speaker and Headphones, ....

How to set the sound **only** on Headphones(**not speake**r)...?

Check out the** screen-shot** as well of my Output tab in sound-Preference..


In Addition i had Kubuntu also, In Kubuntu i had Muted the Speaker and it works well, but when i try to mute the speaker from ALSA-MIXER in Ubuntu, then sound wouldn't appear on head-phone as well....

Any solution...?
[/SIZE]

---

### Post by Linyx on 2011-01-06
[SIZE=2]Update:- 
I have Select the "**Front**" Level to high, and now Sound only appear on my HEAD-PHONE..........


Edit:- But now i have to raise the Front-Level on ***every-boot*** , Every time when i restart PC, the Front level become **mute** again, and i have to Un-mute it again Every time, its really annoying....I want to save this sittings **permenently**... How to do this....?
[/SIZE]

---

### Post by Linyx on 2011-01-09
bump

---

### Post by Linyx on 2011-01-10
bump

---

### Post by 101011010010 on 2011-01-10
Hello.
Have you tried post 2, in this thread?

[http://ubuntuforums.org/showthread.php?t=1656671](http://ubuntuforums.org/showthread.php?t=1656671)

I hope this helps.

---

### Post by Linyx on 2011-01-10
thanks for reply but that didn't fix...

I raise the front level up and save it by the given Command, but when i reboot, Front again seems to be mute....Check out the screen-shot.

Another Question, In terminal how can i **Un-mute** the Front....?because in terminal it shows me "**MM**" under front tab,....

---

### Post by Daniel0108 on 2011-01-10
> **Linyx said:**
> thanks for reply but that didn't fix...

I raise the front level up and save it by the given Command, but when i reboot, Front again seems to be mute....Check out the screen-shot.

Another Question, In terminal how can i **Un-mute** the Front....?because in terminal it shows me "**MM**" under front tab,....

Have you tried:
```
sudo alsactl store
```
after un-muting in alsamixer ?

Yours,
Daniel

---

### Post by Linyx on 2011-01-10
I have tried that..but thats doesn't work for me.....I don't know what i am missing :(


I just have muted my speaker....

---

### Post by uRock on 2011-01-10
Try this. It is what I used to stop the internal speaker in the past. > **t4thfavor said:**
> Explanation:
Removes the pcspkr module from the kernel (requires sudo for elevated privs.)
```

sudo rmmod pcspkr

```Prevents the module pcspkr from getting loaded on boot by adding an entry to the file /etc/modprobe.d/blacklist.conf
```

sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"

```

---

### Post by Linyx on 2011-01-10
1st Command gives me this:-

```
sudo rmmod pcspkr
[sudo] password for assassin: 
ERROR: Module pcspkr does not exist in /proc/modules
```

```
sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"
```
**Still getting sound from Speaker**.

The Problem i have is, when i mute my Speaker from Alsa-mixer , my "**front**" also mute and when i **Un-mute** it and reboot, then it Mute again by itself....

If i Choose Analog-Output in the Sound-option ,then Sound appear on speaker as wel as Head-phones and on reboot, it doesn't change...!!

---

### Post by Linyx on 2011-01-11
When i select "**Analog Output**" then sound doesn't change on Re-boot, but when i Select "**Headphones**" in Sound Properties, it Automatically Become Mute when i restart...

---

