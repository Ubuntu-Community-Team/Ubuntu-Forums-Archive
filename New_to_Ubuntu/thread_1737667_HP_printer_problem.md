---
title: "HP printer problem"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by nifty542 on 2011-04-23
Hi, all
I am using Ubuntu 11.04. Very pleased so far. I have an HP Photosmart B109A printer, all in one. I bought this specifically because it is listed as a Linux supported printer.
I can't get the ink levels to show. I have tried inkblot. Would it be better to connect my Epson DX8400 instead? I know there is a program for ink levels for Epson printers.
I could then use the Photosmart on my Windows Xp computer.
At the moment, the HP printer will only print in black and white, but it may well be I am missing some basic step.
I have copied this from general help because I have had no reply so far.
Many thanks, in anticipation.
Regards

Nifty

---

### Post by e.jejcic on 2011-04-23
Good afternoon: I have a hp printer (C4480, all in one)with two cartridges, black and colour. I once instaolled HPLIP (from repositores) and I have a view of all things printer related. It worked well for me.
Regards from Eduardo.

---

### Post by defense13 on 2011-04-24
New to using Ubuntu, and also had some issues trying to get my HP Printer model 3050 to work.

After doing some reading on  the message board here, I went to this site below and installed an updated "HPLIP" the other day.   Once the update was configured, I am now able to successfully print and scan to the printer both directly connected and via wireless.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Hope this helps...

---

### Post by nifty542 on 2011-04-25
Hi
Many thanks for the replies.
I looked in synaptic, and HPLip is there. Tried to follow the instructions in the link provided, and it gave me cannot open desktop.
Obviously, I must have done something wrong, but not sure what.
By the way, is there no thanks button any more?

Regards

Nifty

---

### Post by coffeecat on 2011-04-25
@nifty542, you need the package hplip-gui. In classic gnome that will give you an entry called HPLIP Toolbox in System > Preferences. You should be able to find it in Unity's applications menu fairly easily. I can check my HP printer ink levels from that.

---

### Post by nifty542 on 2011-04-25
Hi, thanks for the reply. I have looked at that, but it says it's for KDE, not Gnome. I just tried to copy from the printer, without the pc turned on, and it still came out black and white. I had selected colour copying, so I am guessing my new printer is faulty. I checked the HP website, and this printer should be supported

Thanks, regards

Nifty

---

### Post by coffeecat on 2011-04-25
> **nifty542 said:**
> Hi, thanks for the reply. I have looked at that, but it says it's for KDE, not Gnome.

It doesn't say it's not for gnome. It says that it isn't based on gtk.

You obviously didn't try to install it. It works just fine in gnome as you might have guessed from my mention of classic gnome and Unity. It will pull in a few qt libraries, and then work without any fuss.

---

### Post by wep940 on 2011-04-25
Just to educate anyone who may not know, when you see GTK mentioned it is *NOT* Gnome-something-something.  GTK stands for Gimp Tool Kit and is used to develop GUI'd applications.  Don't confuse GTK with Gnome - 2 different animals.  I see this misunderstanding a lot.

---

