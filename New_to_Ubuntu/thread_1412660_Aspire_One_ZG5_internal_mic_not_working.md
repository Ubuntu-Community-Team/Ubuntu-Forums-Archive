---
title: "Aspire One ZG5 internal mic not working"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by AndresM on 2010-02-21
Hello all,

i searched the web for a while now. Things I found were either too complicated or not applicable. 

I have an acer aspire one zg5 that has internal mic, speakers and camera. All seemed to be working fine until sudenly the mic didn't work. I tried it on SKYPE and on the default recorder tool of ubuntu with no success. 

If I plug in external mic it works fine. 

To be fair at one point it seemed that the mic was capturing something (using the sound settings) but I had the input volume set to max. When I listened to this with the recorder it was just a small hum/crackle and yes I was yelling at it at this point. 

Any help pointing me in the right direction would be very appriciated. 

PS: How do you know it's not the actual mic that is broken?
PS: this mic was working fine (used for skype) for a while, but suddenly stopped working. I cannot pinpoint when it started failing to know if I had misconfigured anything.

Thanks!

---

### Post by souta95 on 2010-06-17
I had the same issue.  To fix it I had to install the package pavucontrol (search for it in synaptic).

It will create an icon in the "Sound and Video" category, open it up and go to the Input Devices tab.  Set the "Internal Audio Analog Stereo" to move the sliders independently, then mute one of the sliders and set the other as needed.  In skype options you will probably have to tell it not to automatically adjust mixer levels.

On a side note, ZG5 isn't the model that is normally used to designate this netbook (even though that is what the sticker says underneath).  Mine is an AOA 150 (but also has the ZG5 designation), the actual model is on a white sticker underneath in the format AOA 150-XXXX

---

### Post by AndresM on 2010-06-18
Many thanks! I'll give it a go today! wow, you actually had to look for this post. It was from ages ago!

---

### Post by souta95 on 2010-06-18
No Problem!  I forgot to mention that I did it using Ubuntu 10.04 LTS, but I imagine it would work if you're still using 9.10 (the latest version at the time of your post).  

Also, I didn't really dig to find the post, it was in a Google search when I was looking for a solution.  I saw that nobody had replied, so I figured I would add what had fixed it for me.  I forget what site it was that led me to the actual solution, though.

---

### Post by AndresM on 2010-06-18
great stuff! haven't tried skype yet but at least I know the Mic is working for the ubuntu sound recorder. 

Thanks!

---

