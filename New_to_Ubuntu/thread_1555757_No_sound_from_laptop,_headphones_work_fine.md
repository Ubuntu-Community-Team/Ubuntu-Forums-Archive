---
title: "No sound from laptop, headphones work fine"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-18
I just installed Ubuntu 10.04 last night on a compaq Presario CQ62.
Everything seems to work fine except sound.  I can get no sound from the main speakers, but the headphones work.  

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I enabled the user sound, checked all the setting under system sound, nothing is muted.  When I disable the only sound card, the headphones stop working.

Any suggestions?

---

### Post by scorp123 on 2010-08-18
Does the sound work OK with Windows?

I have a Fujitsu-Siemens laptop that has the same symptoms like your's. The big difference: We know for sure that in my case the malfunction is caused by defective hardware. My 3-year old daughter tripped over the power cable and *wooooosh* ... Isaac Newton took over and my laptop got up close and personally introduced to gravity and the wonders of what happens when a small mass (= laptop) gets spontaneously accelerated into a big mass (= Earth) ... 

Since then: No sound. And the laptop's plastic casing is clearly damaged.

I too still get sound from the headphones ... but no sound whatsoever from the loudspeakers, _NO MATTER_ which OS I use: BSD, Linux, Windows ... none of them can produce sound.

So it would be interesting to know if your laptop got dropped too (accidents happen ...) and if other OS such as Windows in fact can still produce sound ... ?

Just to be sure it's not a hardware defect.

---

### Post by Sleven7 on 2010-08-18
Windows sound "did" work, before I wiped it out with the new Ubuntu install. No more windows, yea!!!

 This is a brand new laptop, less than a week old.  This is not a big issue, as I like the sound quality of the headphone better than the system speakers.  Would like to have it work properly thou.

---

### Post by scorp123 on 2010-08-18
> **Sleven7 said:**
>  This is a brand new laptop, less than a week old. 

I entered the hardware info you supplied in your first posting into Google ... and look what I found:
[http://ubuntuforums.org/showpost.php?p=6269834&postcount=7](http://ubuntuforums.org/showpost.php?p=6269834&postcount=7)

The person in that posting seems to have the same sound chip like you ... and the settings in that posting seemed to help? So it can't hurt to try ... ?


There are still a few bugs to be ironed out, but the last posting in that bug report suggests that the new release (out in October) should fix those issues:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/274424)

---

### Post by Sleven7 on 2010-08-21
Thank you for all the help. Being brand new to Linux and Ubuntu is a little un-nerving. I managed to find the file

 /etc/modprobe.d/alsa-base:

and open it, only to find out that it is read only file.  I was unable to make any modification to the file.  Not sure how to make the changes.  ???

---

### Post by BrockStrongo on 2010-08-21
> **Sleven7 said:**
> Thank you for all the help. Being brand new to Linux and Ubuntu is a little un-nerving. I managed to find the file

 /etc/modprobe.d/alsa-base:

and open it, only to find out that it is read only file.  I was unable to make any modification to the file.  Not sure how to make the changes.  ???

Try "sudo gedit /etc/modprobe.d/alsa-base "
  typing this into terminal will allow you to edit the read only file. 
 You could also try running alsamixer from terminal and check to see if anything is muted. I had this same problem with a toshiba laptop and it was because one of the main channels was muted.

---

### Post by Sleven7 on 2010-08-21
"sudo gedit /etc/modprobe.d/alsa-base

worked great, was able to edit the file.  I added the

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

to the end of the options that were already in the file (was not sure where to paste them)
rebooted and still have no sound on the main speakers, headphones are still working fine.

I ran alsamixer like you said, all the volume meters were turned up.   

Any more suggestions?  did I insert the 3 option lines in the correct place?

---

### Post by BrockStrongo on 2010-08-21
[http://ubuntuforums.org/archive/index.php/t-1439408.html](http://ubuntuforums.org/archive/index.php/t-1439408.html)

this link has instructions on for installing some linux backports. this seems to get sound working. 

You might also want to try booting from a live disk to check if this is a hardware compatibility issue, or something botched during install.

this is the post that seems most relevant
ust did the following:
sudo aptitude install linux-backports-modules-alsa-lucid-generic Got this as a result, 


The following NEW packages will be installed:
linux-backports-modules-alsa-2.6.32-19-generic{a} 
linux-image-2.6.32-19-generic{a} 
confirmed and installed, rebooted as well. However, no menu on grub to select a specific kernel. and no sound after restart.

This solution solve my problem after rebooting all I had to do is unmute the speaker from the panel.
Thanks.

---

### Post by Sleven7 on 2010-08-21
Thank you very much Brockstrongo

sudo aptitude install linux-backports-modules-alsa-lucid-generic

did the trick, I now have sound from the main speaker.  It may well be my imagination, but the sound quality sounds better than it did with Windows 7.

I want to thank everyone for helping resolve this issue.

---

### Post by hasanrauf on 2011-01-20
Man for me i cannot hear from my laptop.

Headphones works fine I am having Sony Vaio please help.

---

### Post by hasanrauf on 2011-01-20
Man for me i cannot hear from my laptop.

Headphones works fine I am having Sony Vaio please help.

---

### Post by hasanrauf on 2011-01-20
Man for me i cannot hear from my laptop.

Headphones works fine I am having Sony Vaio please help.

---

### Post by hasanrauf on 2011-01-20
Man for me i cannot hear from my laptop.

Headphones works fine I am having Sony Vaio please help.

---

### Post by hasanrauf on 2011-01-20
Man for me i cannot hear from my laptop.

Headphones works fine I am having Sony Vaio please help.

---

