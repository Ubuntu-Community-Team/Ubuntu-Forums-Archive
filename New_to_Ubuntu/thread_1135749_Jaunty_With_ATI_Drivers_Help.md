---
title: "Jaunty With ATI Drivers Help?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Syndacate on 2009-04-24
I installed Jaunty last night, the OSS drivers were decent, but it left yellow glyphs wherever there was white, and I couldn't figure out how to set the OSS driver to "radeon."

I have a Radeon 9800SE w/ 128MB.

I used the ATI driver installation guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I used the 9.1 catalyst drivers.

and when I got to the ```
sudo aticonfig --initial -f 
``` command it gave me a "*No supported adapters detected*"

I tried restarted the X server and then realized my entire X server is hosed, and I need to reinstall.

I should have my nvidia card back in < 1 month, but I'm trying to get the ATI drivers working in the  mean time.  Anybody have any successful installation of some good drivers for that series?  I mean the OSS weren't horrible, they were able to run at my monitor's native res, but I rather have regular drivers.

Any help is greatly appreciated.  Thanks.

---

### Post by Mortus Pryde on 2009-04-24
Firstly Jaunty uses a new version of X? that does not support drivers any older than 9.4. Your other problem is that the 9800 series are no long supported on the 9.4 driver. Your only option is the open source drivers or to downgrade to the 8.** versions for the time being sadly.

Sorry I can not be of any more help, though it would be nice if there was a solution to get decent 3D support on older ATI cards.

---

### Post by Hospadar on 2009-04-24
Fear not!

First off, let's un-hose your X server:

1) Boot up
2) Get to the point where your X server is failing
3) Ctrl-Alt-F1 to get to text-mode virtual terminal
4) Log in
5) Reconfigure X server to default settings```
sudo dpkg-reconfigure -phigh xserver-xorg
```6) Restart your X server and see if it works (gdm is the gnome graphical login manager, restarting it cleanly and effectively restart X)```
sudo /etc/init.d/gdm restart
```7) If all is well, continue, if not, you are indeed hosed and it's probably easiest at this point to re-install

Once you have reached a state of non-hosed-ness:
Can you install the drivers from the restricted drivers manager? System->Administration->Hardware Drivers
I did it this way for my gf's lappy that has an ati card and it worked like a dream

If that is no good, come back here and ask for more help

---

### Post by Aq32 on 2009-04-27
One problem I have is that by default Compiz worked fine with my Jaunty but it wasn't using 3D acceleration. So when I tried to use Envyng Jaunty wouldn't load up that led to me uninstalling Envyng's ATI drivers and Jaunty couldn't use compiz any more.

Also, in previous versions of Ubuntu my graphics card had a propriety/restricted version but in Jaunty there doesn't seem to be any. The only device shown is my wifi driver which works perfectly (afaik).

I assume Jaunty was originally using open source drivers for my ATI Xpress (1150 or 200m) graphics card so how would I reset it to that point where I could use Compiz again?

EDIT:
Actually I got it working again. Apparently setting the xorg.conf to use "radeon" does the trick instead of "fglrx" (which I never got working) or the very low graphics "vesa". Hope this helps other ATI users!

---

