---
title: "Sound coming from both internal speakers &amp; headphones?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by summersource on 2010-03-09
When I plug in my head phones I am still getting sound from the internal speakers as well as the head phones.  I have tried different head phones and I have tried all input jacks and have messed around with the sound card settings a number of times and can not seem to figure out what the problem is. I really do not think it is a setting because occasionally when I plug in my headphones my internal speakers will switch off and play though the headphones?? I am stumped!  Unfortunately Google has not offered much information reguarding this issue, so I was hoping that someone out there could help? 
Acer Aspire 5542-5416 AMD Turion II Dual-Core M500 2.20GHz / 4GB RAM / 320GB Hard Drive/ATI Radeon HD 4200 / 802.11N /HDMI / 
I am running Ubuntu 10.9 as my only OS.

---

### Post by lidex on 2010-03-10
Work through this sound debugging page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
If you have any questions ask them here ;)

---

### Post by lotharmat on 2010-03-10
To get round this I have used alsamixer

In a terminal window just type

```
alasmixer
```

Then use the arrow keys to move to the column caller speaker (far right) then use the down arrow to take the volume down to zero.

PCM and Front will be unaffected and you should still have headphone volume.

If you alter the volume level from the desktop - for some reason the speaker volume will shoot straight back up to max.

---

### Post by summersource on 2010-03-10
went through debugging and still have the same problem.

alasmixer command not found. Any other suggestions?

---

### Post by naveedmanzoor21 on 2010-03-10
i think this will help u goto Open Volume Control and mute the PCM ...

this will mute the internal speaker and let u hear through ur Headset

---

### Post by summersource on 2010-03-10
I am not seeing PCM as an option.. Also I have just lost all sound =( it will stay up for a few mins and then its gone! I have not done anything other than what the above posters suggested. I would rather than sound from both than none at all. Oh man what have I done! Please help. Should I format?

---

### Post by summersource on 2010-03-10
]I am not seeing PCM as an option.. Also I have just lost all sound =( it will stay up for a few mins and then its gone! I have not done anything other than what the above posters suggested. I would rather than sound from both than none at all. Oh man what have I done! Please help.

---

### Post by lidex on 2010-03-10
> **summersource said:**
> went through debugging and still have the same problem.

[COLOR="Red"]alasmixer[/COLOR] command not found. Any other suggestions?

The command is:
```
alsamixer
```
Little misspelling there. Also check your "Sound & Video" menu for "GNOME ALSA Mixer", pretty much the same thing.

---

### Post by lidex on 2010-03-10
If it isn't fixed by now, We'll need more info to diagnose. Right click the alsa info script link in my signature and "save (link) as" into your user folder. Now execute this command in a terminal:
```
sudo bash utils_alsa-info.sh
``` Enter your user password when prompted. You can save it locally or upload it so copy and paste using code tags for the former; in the latter case provide a link.

---

### Post by opethfan89 on 2010-03-25
Summersource,

I have no idea if these steps will work for your Acer laptop, but I have an HP pavillion dv7 laptop and I came across [this link]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1381413") and followed willix's instructions to get my sound working properly.  I updated my driver to pulse-audio using [this wiki]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") and then followed the directions listed [here]("https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop") to fix my issue.

Again, I'm still a novice myself so I don't guarantee that anything I tell you will work. However, if you follow that 2nd link, it lists the steps to debug your sound so you will be able to give more information to those who are helping you.

Make sure you back up your files before you try anything, in case things get messed up!

Opethfan89

---

