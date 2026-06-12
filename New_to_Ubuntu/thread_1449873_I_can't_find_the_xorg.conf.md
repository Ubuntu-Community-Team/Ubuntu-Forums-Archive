---
title: "I can't find the xorg.conf"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Alexx86 on 2010-04-08
Hey,
I'm trying to disable my touchpad while I'm coding, and stumbled over this page:
[http://digitalgraphy.wordpress.com/2007/11/17/how-to-disable-touchpad-on-linux/](http://digitalgraphy.wordpress.com/2007/11/17/how-to-disable-touchpad-on-linux/)
Maybe this will be enough, since it's only the click-on-tapping that's bothering me:
[http://www.linuxquestions.org/questions/ubuntu-63/disable-touchpad-tap-to-click-692353/](http://www.linuxquestions.org/questions/ubuntu-63/disable-touchpad-tap-to-click-692353/)

Anyway, I can't find my xorg.conf to edit it!
I looked up man xorg.conf and searched in every "default" folder, I even did
find / -name "xorg.conf"
which produced NO result. That's odd...

I'd be happy if anyone knows what's going on here.. thanks in advance!

---

### Post by undecim on 2010-04-08
There is no Xorg.conf in newer versions of ubuntu. All hardware detection is done automatically.

If you want to disable the touchpad while typing, I think you can do that from the mouse settings.

---

### Post by Alexx86 on 2010-04-08
I'd like to have a little script that does it in a second, since I'm switching between coding, browsing and chatting regularly.
Do you have any idea on how to find out how to do this?

/edit: Ah, nevermind. I found the mouse settings and just unchecked "enable touchpad clicking".
Thanks a lot :)

---

### Post by Azrael3000 on 2010-04-08
Well if you go to your Mouse settings System > Preferences > Mouse the third tab should be Touchpad. There the first setting is called "disable touchpad while typing". Is this not enough for you?

Btw. you can always add your own xorg.conf into /etc/X11 and Ubuntu will use it.

---

### Post by Calash on 2010-04-08
> **undecim said:**
> There is no Xorg.conf in newer versions of ubuntu. All hardware detection is done automatically.

If you want to disable the touchpad while typing, I think you can do that from the mouse settings.

You sure about that.  I just did a double check and I still have one in /etc/X11/

I have not worked with the Netbook Remix so that may be the difference.

---

### Post by undecim on 2010-04-08
> **Calash said:**
> You sure about that.  I just did a double check and I still have one in /etc/X11/

I have not worked with the Netbook Remix so that may be the difference.

You sure that you didn't create it at some point?

Maybe due to some specific hardware? I had one in mine when I was using the proprietary ATI drivers, but I'm pretty sure I added it myself. Since switching to the open source drivers, I've been able to remove it.

---

### Post by bshosey on 2010-04-08
If you had an older version of ubuntu that had xorg.conf and did an upgrade it will still have an xorg.conf after upgrade. And yes for a fact you can still use customized xorg.conf file. I do on 2 machines. Did it with 9.10 and doing it now with 10.4

Now I am only customizing for video and not mouse

---

### Post by Calash on 2010-04-08
> **undecim said:**
> You sure that you didn't create it at some point?

Maybe due to some specific hardware? I had one in mine when I was using the proprietary ATI drivers, but I'm pretty sure I added it myself. Since switching to the open source drivers, I've been able to remove it.

I have FGLRX installed from the Hardware Drivers app, so that may be it.  I never edited the file myself on this machine, it is a fairly clean 9.10 x64 install.


Learn something new every day :)

---

