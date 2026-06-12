---
title: "Sound does't work on Ubunu 10.10"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by /&lt;ruger on 2011-04-21
Hi all, I installed Ubuntu 10.10 a few day ago on my desktop pc but I can't get any sonud from my speakers. Please realise that im totally new in all this, i'm only familiar with Windows and don't know much about any Linux distro. I tried downloading some audio drivers for my motherboard (i have GIGABYTE GA-965P-DS3 motherboard) but instalation for some reason failed. After some troubles I gave up and decided to cry for help :| . Can anyone tell me where can i get drivers compatible with Ubuntu and how to instal it, i would appreciate. 
PS: Please don't laugh on my thred and sorry for my bad english :D

---

### Post by LinXNut on 2011-04-21
Hi Ruger, and welcome!

It was a good choice to choose Ubuntu since it is the best user friendly distrobution of linux out there! 

**1. Goto Applications ---> Accessories ---> Terminal**

**2. Copy and paste the code below into the terminal...**.

```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
```**3. Basically just press "y" for everything, and it will splurt out a link for you to go to on the web.**

** 4. Copy and paste that link in the forums here....**

If you need any more help feel free to ask! :P


Also, most (not all) of the drivers you download from the web will most likely not work, or have many issues with Linux. It is always good to update your linux box and drivers through the terminal or software center.

---

### Post by TheTopHat on 2011-04-21
I don't like making new threads when there is something so similar to my problem already up, especially on the front page, so I'll jump on this if you don't mind.

My speakers and headphone jacks have random, unpredictable fits of working and not working. But the problems seem to vary between the following:


[LIST]
[*]I boot up and everything works fine.
[*]Speakers work fine, but if I plug in my headphones there is absolutely no response. The speakers keep working, the headphones have no sound.
[*]If all works well, or relatively well, logging into a different account will mess everything up.
[*]On one occasion, only the headphones worked. If I unplugged them there was no sound at all.
[/LIST]

I've gone to sound preferences and turned all the volumes up (to no more than 100% I might add, I heard that doing otherwise could be problematic), but the problem is very random and nothing was ever fixed. I've googled around a bit, but I couldn't even find an answer from the last three years, and what I found overall did nothing.

Here's that link: [http://www.alsa-project.org/db/?f=b006766071735c992c066efa2793ac07601a2952](http://www.alsa-project.org/db/?f=b006766071735c992c066efa2793ac07601a2952)

Edit: Also, my laptop's microphone doesn't work either. It's not even recognized in the 'Output' tab in Sound Preferences.

I appreciate any help anyone may be kind enough to provide. This major, and some other minor problems, are the only thing keeping me from uninstalling WIndows 7.

---

### Post by /&lt;ruger on 2011-04-22
@ LiXNut

Thx for reply, I did everything how you said and got this in my terminal:

--2011-04-22 12:03:20--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-04-22 12:03:21--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247       149K/s   in 0.2s    

2011-04-22 12:03:22 (149 KB/s) - `alsa-info.sh' saved [27247/27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : splurt out^C
petar@petar-965P-DS3:~$ 

[COLOR="Red"]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
What should I do next?

---

### Post by gradinaruvasile on 2011-04-24
Your mobo is not that new it and its sound card should be supported by alsa (do not mess around with drivers until is not really necessary).

So:

Paste here the output of:

lspci

Then

launch 'alsamixer' in a terminal, resize the terminal to show everything (the default playback tab) and make a screenshot of it (alt+printscreen) and attach it to your post.

Also right-click on the volume icon, select properties, make sure everything is unmuted, volume is up and check the hardware tab where you should set the card to stereo output/analog input.

---

### Post by /&lt;ruger on 2011-04-25
Thank you all for help, my friedn came yesterday and fixed my sound problem, i appreciate for your help.

Cheers :P

---

### Post by gradinaruvasile on 2011-04-25
What was the issue? You know, for others who might have it.

---

### Post by cynkronyze on 2011-04-26
> **LinXNut said:**
> Hi Ruger, and welcome!

It was a good choice to choose Ubuntu since it is the best user friendly distrobution of linux out there! 

**1. Goto Applications ---> Accessories ---> Terminal**

**2. Copy and paste the code below into the terminal...**.

```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
```**3. Basically just press "y" for everything, and it will splurt out a link for you to go to on the web.**

** 4. Copy and paste that link in the forums here....**

If you need any more help feel free to ask! :P


Also, most (not all) of the drivers you download from the web will most likely not work, or have many issues with Linux. It is always good to update your linux box and drivers through the terminal or software center.

HI,

I posted a thread over at the Absolute Beginners Talk, when i found this one,

I followed your step of typing this in the terminal : -

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

and got this link : -

[http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6]("http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6")

Please Help.

---

### Post by gradinaruvasile on 2011-05-02
> **cynkronyze said:**
> HI,

I posted a thread over at the Absolute Beginners Talk, when i found this one,

I followed your step of typing this in the terminal : -

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

and got this link : -

[http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6]("http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6")

Please Help.


Please use new threads because different hardware/drivers may have different problems and different solutions.

---

