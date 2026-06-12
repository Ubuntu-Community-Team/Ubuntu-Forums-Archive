---
title: "How to project my desktop after pluggin a projector to my laptop?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by AquilEus on 2010-06-08
I can't project my desktop on when I plug my laptop to a projector or screen.

This is my first post, so please let my know I do somethin wrong (I'm not native English speaker and maybe I will not use the proper vocabulary).


My problem arises when I take my laptop to college in order to do a presentation. I plug the my lapto and the projector but it doesn't show my desktop.

When I used windows it was sufficient to plug it a push a FN blue key and another key "LCD in and square"/and screen. When I did so for first time the screen in the laptop went black and it was shown in the projector. The second time I did it I could see my desktop both at my laptor screen and the projection.

I guess there will be a way to do it with Ubuntu also, but I don't know what are the words to look for information on my own; could anybody give me a clue about how can I solve it?

My laptop is an "Asus Z53Jseries" and the operating system it is running is Ubuntu 10.04 (I'm not 100% sure if it's ubuntu or Edubuntu, since I "¿upgraded?" it in the 9.10 version to Edubuntu).


Let me know if I should change somethin in my question, move it to another forum or include more information.

Thank you in advance.

---

### Post by nemilar on 2010-06-08
Take a look in the monitor/display settings (system --> preferences).  The projector should just appear as an additional monitor.

---

### Post by AquilEus on 2010-06-08
Thank you Nemilar.

When I tryed it this showed up

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

When I choose "No" a window called Monitor Preferences showed up. It has a botton that says "Detect Monitors" but it didn't work.

Then I tryed saying yes, and a window called "NVIDIA X Server Settings" appeared instead off the previous one.

There I "investigated" a little and Found:

X Server Display Configuration --> Detect Displays (This time the projector was found). I chose the projector and then pushed Configuration and there I found this options:


How should this display device be cofigured?

- Disable.
- Separate X screen (requires X restart).
-Twin View.

The second option switched of my screen and projected the image through the projector.

The third option kept my laptop's desktop and projector projects an a kind of new desktop, but it has no menu. The mouse shifts from one field to another. It was not what I expected but it fits my needs to show my presentation.

Thank you very much.

---

