---
title: "s-video help please"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by summersource on 2010-07-07
I gave my parents my old gateway notebook and installed Ubuntu 10.9. They are wanting to watch movies via s-video on their tv... and it is not giving a screen display (black, sound works. It is connected properly. I do not have this notebook with me. I would just like to have a few suggestions to relay for a possible solution.  Thanks!

Video Card is Intel Graphics Media Accelerator 950

---

### Post by summersource on 2010-07-07
bump  Any thoughts?

---

### Post by AAccount on 2010-07-07
Did you install drivers from Intel? Usually (just like in windows) there is a control panel that lets you setup multiple screens. Once you find the control panel, follow these setups:

1: Go to main menu in system-->perferences
2: Find the entry for the control panel and copy that
3: Open a terminal and type sudo (thing you copied)
4: In the control panel it is easy to see how to setup 2 screens
5: Save the new configuration
6: type "sudo service gdm restart" in the terminal (note this step will bring you back to the login screen but both monitors will be enabled).

This is how I use my NVidia graphics card to watch SVideo. NVidia and ATI have graphics control panels that make it easy to setup dual monitors. Never tried Intel graphics.

If you get the second screen working launching a video is a bit different than windows. In windows you can open Windows Media Player and just move it to the other screen. In Linux you must move your mouse to the other screen, open a run prompt (usually ALT+F2 but I use WinKey+R) and type nautilus. Navigate to where your movie is and click on it.

---

### Post by summersource on 2010-07-07
Thank you will give this a try the video card worked out of the box but I will double check maybe something is missing... I will run though this with them thanks again! Will update soon.

---

### Post by S.R on 2010-07-07
Should be a screen to CRT F key that works via the FN button to switch where it send the video signal .... not even sure if it would work with Ubuntu Best of luck.

---

### Post by summersource on 2010-07-08
Ok I am just going though the steps here to make sure I understand them. I looked for the control panel type entry and I do not see a control panel? Where do I go from here and any what am I copying?  Thanks for your help!

---

### Post by AAccount on 2010-07-08
The control panel entry is in system->preferences or system->administration. It will be very clear if you have one. ATI's is called ATI Catalyst Control Center and NVidia's is called NVidia XServer Settings (I think). You must first install Intel's proprietary grapics drivers (if they exist). If they do not exist, you may be out of luck or have to configure it through config text files (which I have never done). Personally, I try to buy a computer with ATI or NVidia graphics because they have working drivers (but NVidia has better linux drivers).

See the screenshot for what the control panel would look like. This is what my ATI panel looks like. I have circled what you would copy if you find the entry (don't use amdcccle, that is for my graphics card).

---

