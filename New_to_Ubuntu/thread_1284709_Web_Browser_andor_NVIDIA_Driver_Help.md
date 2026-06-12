---
title: "Web Browser and/or NVIDIA Driver Help"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by JonNeon on 2009-10-06
Ok, so I am obviously a new Ubuntu user or I wouldnt be here...lol I have been having problems with the firefox web browser. The web page text is really tiny, and if I blow it up at all, the images become really pixelated and kinda stuttery (on some web sites, but not others, like ubuntu). I have an NVIDIA 9500 vid card. I have hardware drivers installed v180. I have downloaded the 185.18.36 pkg 1 from NVIDIA's site. However, I cant figure out how to install them. If anyone has the time to help, it would be greatly appreciated. Please take it slow though and really break it down for me...I've only been using this OS for like 3 days and feel completely lost. I'm having a good time though! And, I am really enjoying Ubuntu and look forward to learning more. Anywho, thank you in advance for your patience, understanding and any help you may be able to offer! P.S. I am using the 9.04 version of Ubuntu...forgot to say that...lol

---

### Post by thiebaude on 2009-10-06
To install the nvidia drivers goto-System-Administration-Hardware Drivers, and let ubuntu search for the drivers and when it does find driver(s) pick the one that says recommended.And the open up- in a terminal, because you have to do this as root to save it as root, gksudo nvidia-settings and once in the settings choose the resolution you want and the refresh rate,and then click Apply and the click save to X configuration file and then quit, and then i would restart.I had to do the same I have a nvidia geforce 8400 gs card.for my card i chose the recommended driver which was 180.

Hope this works

---

### Post by JonNeon on 2009-10-08
> **thiebaude said:**
> To install the nvidia drivers goto-System-Administration-Hardware Drivers, and let ubuntu search for the drivers and when it does find driver(s) pick the one that says recommended.And the open up- in a terminal, because you have to do this as root to save it as root, gksudo nvidia-settings and once in the settings choose the resolution you want and the refresh rate,and then click Apply and the click save to X configuration file and then quit, and then i would restart.I had to do the same I have a nvidia geforce 8400 gs card.for my card i chose the recommended driver which was 180.

Hope this works

Well, I had installed the 180 driver package that was recommended by Ubuntu. I did go through all the steps you outlined here. The problem seems worse now :confused: I was trying to install what appears to be a newer release from nvidia, v185.18.36, but now that I have it downloaded, I cant really figure out how to get it installed. I have it saved to my desktop at the moment, but cant seem to get it to run the setup wizard. I love this OS so far...but these glitchy pixelated webpages are killing me!...lol...Anyone who is patient enough to hold my hand through this, please help! Thank you so much!

---

### Post by advocate 21 on 2009-10-08
could be compiz.
get ccsm from synaptic then look at all the blur options.
if its clicked, unclick it and check.
hope this helps...

---

### Post by cariboo on 2009-10-08
I really don't understand why you are trying to install a new driver just to make the font size larger in Firefox. Why not just go to Edit-->Preferences-->Content, and change the font and size to something that is more readable.

I personally use DejaVu at 18 pt.

---

### Post by JonNeon on 2009-10-08
> **cariboo907 said:**
> I really don't understand why you are trying to install a new driver just to make the font size larger in Firefox. Why not just go to Edit-->Preferences-->Content, and change the font and size to something that is more readable.

I personally use DejaVu at 18 pt.

It's not just font size. If you'll notice on my original post, I said that the images become really pixelated if I try to blow it up at all. If I leave it the way it originally wants to load, the writing is too small to see.

---

### Post by JonNeon on 2009-10-08
> **advocate 21 said:**
> could be compiz.
get ccsm from synaptic then look at all the blur options.
if its clicked, unclick it and check.
hope this helps...

Thank you so much for your reply, I'm going to bed now, but I'll give it a try tomorrow and see if it helps. Again, thank you for your help!

---

