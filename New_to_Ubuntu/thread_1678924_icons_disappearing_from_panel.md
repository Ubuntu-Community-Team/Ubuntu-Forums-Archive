---
title: "icons disappearing from panel"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-31
Hi All,

This is really strange.  A couple of weeks ago, I noticed that the labels showing which language my keyboard was set for were no longer showing up in the panel.  All I saw was the little keyboard indicator in the panel.  

I checked everywhere I could think of in my system (like the configuration editor and other places I found but can't remember what they are called) and everything is set to display the label of the language I'm typing in.  I also tried to change the indicator to show the flag for the language since the text labels were no longer showing up.  I couldn't get either the labels or the flags to appear.

Today, honest to God, all of a sudden the keyboard icon disappeared from the panel and was replaced with a generic international NO symbol.

[IMG]http://www.jfniendorf.org/Screenshot-1.png[/IMG] 
(The keyboard in the screen shot is the input method indicator)

I can still use the different layouts (US and Sweden), but I'd like to get the icons back.

Along the same lines, when I change input methods using iBus, I get the same generic NO symbol.  I have my system set to also let me type in Japanese.  While I can still type in Japanese, I wonder if the lack of icon is related to the lack of icon in the keyboard layouts?

Does anyone know how to fix this or has anyone had the same thing happen?  I'm really puzzled.

---

### Post by Nickjpost on 2011-01-31
Did you check the Device section of the xorg.conf? Perhaps there may be a clue there. Also, is this issue on a desktop or laptop?

---

### Post by GrouchyGaijin on 2011-01-31
> **Nickjpost said:**
> Did you check the Device section of the xorg.conf? Perhaps there may be a clue there. Also, is this issue on a desktop or laptop?

Thank you for the reply.

I'm on a laptop running 10.10.

Where would I check the xorg.conf file?

I looked in both 
```


/etc/X11/xorg.conf
/etc/X11/xorg.conf.dist-upgrade-201010102254

```
 and didn't see any mention of devices.

I booted into KDE to see if the icons worked there and they do.  So this must be a problem with gnome not finding the path all of a sudden.

I'm still puzzled.

---

### Post by Nickjpost on 2011-01-31
Sorry, I was wrong. The layout for your system can be configured in /usr/share/X11/xorg.conf.d  but that is not your issue. I was thinking of the older version of X server. I'm researching other areas. Sorry about the unnecessary confusion

---

### Post by theozzlives on 2011-01-31
Quite frequently I have my panel mess up. I just do:
```
killall gnome-panel
```
I'm not sure if this will fix your problem, but it does mine.

---

### Post by Nickjpost on 2011-01-31
What if you removed all but one keyboard layout, rebooted, then re-add the ones you had previously? Perhaps that will bring the icons back.
 
[http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/](http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/)

---

### Post by GrouchyGaijin on 2011-01-31
> **theozzlives said:**
> Quite frequently I have my panel mess up. I just do:
```
killall gnome-panel
```
I'm not sure if this will fix your problem, but it does mine.

That didn't help :-(
It was worth a shot though.

---

### Post by GrouchyGaijin on 2011-01-31
> **Nickjpost said:**
> What if you removed all but one keyboard layout, rebooted, then re-add the ones you had previously? Perhaps that will bring the icons back.
 
[http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/](http://www.howtogeek.com/howto/17508/add-keyboard-input-language-to-ubuntu/)

I'll give that a shot tonight after the kids go to sleep.

---

### Post by GrouchyGaijin on 2011-01-31
I just tried the remove layout - reboot - readd method and as soon as I added the second keyboard the NO icon appeared in the panel.

It's like the panel doesn't know where to find the icon or label.

---

### Post by GrouchyGaijin on 2011-01-31
I reinstalled the indicator applet and now everything works as it should.  Strange.

---

### Post by Irvs on 2011-02-27
> **theozzlives said:**
> Quite frequently I have my panel mess up. I just do:
```
killall gnome-panel
```
I'm not sure if this will fix your problem, but it does mine.

Cheers ozz, worked perfectly fine here! :D

---

