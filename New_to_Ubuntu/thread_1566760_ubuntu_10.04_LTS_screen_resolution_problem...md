---
title: "ubuntu 10.04 LTS screen resolution problem.."
date: 2010-09-02
forum: New to Ubuntu
---

### Post by lolzywut on 2010-09-02
Hi, I have an HP G60 laptop. I have ubuntu dual booted with windows vista. My graphics card is (according to lspci anyway) VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

The problem is that the screen resolution is widescreen in some cases. First of all when I am booting, grub is widescreen. Second of all when I use fluxbox about half of the screen on the side is cut off. Here's a picture: 

[http://i56.tinypic.com/zjgitz.png](http://i56.tinypic.com/zjgitz.png)

Also, transparency does not work. So obviously I have some graphic issues on here. I believe it's caused by the kernel, because I had the EXACT SAME PROBLEM with linux mint 9.0 isadora about a week ago. How can I fix this? Are there some drivers I need or something like that? By the way I booted with nomodeset when I booted the livecd due to the common blank screen problem. Thanks for any advice.

---

### Post by Cypress421 on 2010-09-02
In System -> Preferences -> Monitor, is the right resolution set?

---

### Post by lolzywut on 2010-09-02
I'm not really sure how you tell if it's set right. It's on 1366 x 768 (16:9). Is that right? It looks fine on GNOME. Any other resolutions below just keeps getting more blurry

---

### Post by Cypress421 on 2010-09-02
If that is the native resolution, then its fine. Next try System -> Administration -> Hardware Drivers. If there is a proprietary driver, try and enable it. Reboot and see if that fixes it.

---

### Post by lolzywut on 2010-09-02
"No proprietary driver are in use on this system"

---

### Post by Cypress421 on 2010-09-02
If there are any drivers listed, enable them. Other wise if GNOME works fine, have you adjusted any of Fluxbox's settings?

---

### Post by lolzywut on 2010-09-02
What kind of settings would I change? If I change the wallpaper it works, and by works I mean it takes up the whole screen. So that problem can be fixed but the transparency doesn't work. I don't think it has to do with fluxbox because grub is also widescreen when it shouldn't be

---

### Post by Cypress421 on 2010-09-02
Adjust the resolution in fluxbox, or change back to GDM (Gnome Display Manager). You could also try an alternative desktop such as KDE. If your screen is widescreen it should remain widescreen.

---

### Post by lolzywut on 2010-09-02
adjusting it in fluxbox does the same thing it does in gnome. It just makes things worse. I don't know if my computer is widescreen or what but it isn't normal that it would do this right? Plus I had ubuntu 9.04 about a month ago (on the same laptop)  and that never happened.

---

### Post by Cypress421 on 2010-09-02
You might need to compile the latest Intel drivers. I don't use Intel, so try posting a thread in the Hardware forum.

---

### Post by lolzywut on 2010-09-02
Thanks, I'll go post there. You helped alot thank you :KS

---

### Post by jtarin on 2010-09-02
Is this your model? Says Nvidia Graphics.

---

