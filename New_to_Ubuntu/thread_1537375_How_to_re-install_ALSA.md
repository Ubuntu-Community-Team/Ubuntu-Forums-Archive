---
title: "How to re-install ALSA?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by puca mor on 2010-07-23
Hi, very little need to tell you i'm a beginner here.. :rolleyes:

Anyway, having a little (read 'a lot of') trouble with the sound.

First I am running Ubuntu 10.04, on a HP dv6-1210sa.

When i installed the sound was working, but the mic was not. Not a big problem, but since i use skype quite  a bit i thought i'd try to fix it. 

It was going ok, i was changing settings, then reverting according to needs - altering the alsa conf. 

However, in my ignorance i seem to have deleted the ALSA files. Or something similar - i say that because so far as i can tell, i still have ALSA drivers, libs etc - but if i type 'alsamixer' in the terminal it will say 'cannot open mixer: No such file or directory' 
Also, if i open sound prefs now, it has no soundcards listed.

I have tried using this guide [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") amongst others to reinstall the ALSA stuff.. but it doesn't seem to have brought things back to the starting position... and i think my actions are probably not improving the situation. 

I also tried to revert using 'asoundconf-gtk' - but it replies that 'you need at least one ALSA sound card!' 

The 'sudo lshw' command shows the soundcard as follows:

*-multimedia UNCLAIMED
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:d2310000-d2313fff

 Any help or advice you could give me would be much appreciated.

Thanks :)

---

### Post by j7%&lt;RmUg on 2010-07-23
Ok, assuming you know how to use the terminal:

```

sudo apt-get remove alsa-utils
sudo apt-get remove alsamixer
sudo apt-get install alsa-utils
sudo apt-get install alsamixer

```

That (as far as i know) should do what you need, if not post back here.

---

### Post by puca mor on 2010-07-23
Thanks for the suggestion Nisshh, unfortunately no luck.
The remove & install worked with alsa-utils... 

but when i try to remove alsamixer i get this:

'Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer'

the same if i try to install it...

Any further ideas?

---

### Post by j7%&lt;RmUg on 2010-07-23
oops, my fault sorry, alsamixer is IN the alsa-utils package.

Can you try running alsamixer again?

---

### Post by puca mor on 2010-07-23
afraid i just get the following: 

```
michael@soilseDo:~$ alsamixer
cannot open mixer: No such file or directory

```

[Edit]
I'm giving 'Getting the ALSA drivers from a *fresh* kernel' a go. I'll see if that helps.

---

### Post by puca mor on 2010-07-23
Right, so.. it appears that i have managed it.

Sound is back, the microphone is working... and damned if i know how i did it! 

Seems perhaps installing drivers from fresh kernel, then changing things about worked... when in doubt, just keep entering code??:o

---

### Post by drziddo on 2013-01-13
This broke everything related to audio for me. 
However, it was easily solved running this script:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

More info here: [http://ubuntuforums.org/showthread.php?t=2099204](http://ubuntuforums.org/showthread.php?t=2099204)

---

### Post by oldos2er on 2013-01-13
Old thread closed.

---

