---
title: "Serious problem regarding graphics"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by null.byte on 2009-04-04
Hello... I just installed Ubuntu on my AMILO PRO laptop... From the installation screen, the resolution was 1600x1200... When I entered the system... 1600x1200 again, with Refresh rate 0hz... I tried to change it and weird lines appeared on the screen, it was unusable... I had to reconfigure xserver-xorg.

Can anyone please tell me how to enable the VIA graphic card and get my maximum laptop resolution (1024x768 )? Thanks! (PS: It does not appear in the Restricted Hardware)

---

### Post by b@sh_n3rd on 2009-04-04
check this link to see if you can solve your problem; [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
"open chrome" is the driver used for VIA graphic cards in ubuntu. You can also check the official site for any more info at: [http://www.openchrome.org](http://www.openchrome.org)
Hope this helps.

---

### Post by null.byte on 2009-04-04
Okay, but how do I fix the resolution problem? Is the most annoying of them all!

---

### Post by b@sh_n3rd on 2009-04-04
srry, im not all that familiar with the VIA chipset. Ubuntu 8.10 doesn't have the VIA driver installed by default it seems (Hardy did, 8.04), so u've gotta install it manually. There are several bug issues on that too which can be found on the community documentation (the link). Ubuntu wouldn't be able to set the Res. without knowing how to. This is done by the driver. In this case IF the driver WASN'T installed. Im not sure about Jaunty though. I tried my best to help u mate, Good Luck. :)

---

### Post by null.byte on 2009-04-04
Thanks a lot bash_nerd. 

Anybody more familiarized with VIA?

---

### Post by b@sh_n3rd on 2009-04-04
Hey, you can try this. From the mentioned section of the community documentation.

> ...in the Section "Screen" add or modify the SubSection "Display" to include the Virtual setting to suit your screen: 

```
SubSection "Display"
   Virtual 1280 800
EndSubSection
```



---

### Post by null.byte on 2009-04-04
Hmm... it works like a charm. Thanks...

I specified in xorg.conf that the device driver is "openchrome" and it is still sluggish... and Compiz doesn't enable...

---

### Post by b@sh_n3rd on 2009-04-04
Okay, If you looked at the community documentation, it shows how to install the openchrome driver as well as enable 3D acceleration. I'm afraid you've gotta set that as well. By default, you've only got 2D. Just check the "openChrome and 3D" section. Hope this works. :)

---

### Post by Agent.Logic_ on 2009-04-04
Hi null.byte,

Unfortunately, openchrome doesn't support 3D rendering directly, so compiz effects can't be enabled, and applying some themes look really crappy! I also have a VIA chipset, and it was hell before I could figure out a way to stop Ubuntu from hanging after GDM loaded. b@sh_n3rd provided emotional support through my ordeal, you could say LOL! I'm reading a bit about 3D acceleration on shitty video adapters like the one I've got, and will update you on it once I find something.

---

### Post by null.byte on 2009-04-04
Thanks a lot bash_nerd and agent.logic! :) I have a 512 mb ram, and 64 vram laptop... it is pretty sluggish.

---

### Post by Agent.Logic_ on 2009-04-05
Hi null.byte,

If you have information about your laptop monitor's refresh rate (or a range of rates it supports), you can specify it in the xorg.conf file. Regarding 3D, I haven't had much luck. Wherever I go with threads discussing about openchrome 3D, there are always people who can't seem to get it to work. I'm left to assume it is just not possible in openchrome, because VIA never released much info about it's chips. But you could try the directions given in [this thread](http://www.tkarena.com/forums/linux-arena/37584-cant-enable-visual-effects-ubuntu-8-04-a.html). Try adding openchrome to the compiz whitelist, although that didn't work for me. As an alternative, try the [VIA Linux Portal](http://linux.via.com.tw/support/downloadFiles.action). If you are lucky, you might find official drivers from VIA for your graphics card model. Good luck mate, let us know how it goes.

---

### Post by null.byte on 2009-04-05
Well, glxinfo says that Direct Rendering is enabled, and the string is: [I]Software Rasterizer. :|

EDIT:[/I] One thing is sure: it doesn't work how it would must... XP was running slightly faster than Ubuntu, and when I watch a movie in VLC, the sound crackles... How can it be that XP was faster than Ubuntu? Damn that driver... it is very troublesome :( I am getting mad.

*EDIT2:*What's Mesa? Anybody tried it?

---

### Post by Agent.Logic_ on 2009-04-05
Same here mate. It tells me that direct rendering is enabled ("yes"), but my current theme looks really crappy from the one I have on my desktop. Haven't tried running a video yet, but I can't even f***in' play Solitaire normally because the mouse pointer keeps disappearing when I hover above a card! Blame VIA for being so secretive about their "precious" chips.

Regarding Mesa, it is an open source implementation of OpenGL, which provides 3D rendering. It is usually already installed in your system (it was installed in mine). I don't know how it works, but my guess is that openchrome automatically tries to make use of it. I haven't had much luck getting any info on that. The OpenChrome community page says that 3D rendering doesn't always work, and that if you are on a laptop, your options are very limited. :(

---

### Post by null.byte on 2009-04-05
Hey, to fix the mouse problem add "SWCursor" to the options of the "Device" section in /etc/X11/xorg.conf.

```

    Section "Device"
        Driver    "openchrome"
        Option    "SWCursor"    "true"
    EndSection

```

---

### Post by Agent.Logic_ on 2009-04-05
Ah yes, that fixes the annoying problem! Now I can play Solitaire in peace lol. :D Thanks for that null.byte :D. Also, check out [this page](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=The+Different+Unichrome+family+display+drivers). It basically says that you are either down to using the VIA proprietary drivers, which are prone to malicious attacks, or use one of the stable ones with limited features. :| Either way, my IGP is not listed in the official VIA 3D driver support so I'll have to wait for until someone works on openchrome 3D support. :(

---

### Post by null.byte on 2009-04-05
It's just me, or the link is dead?

Where are the proprietary drivers?

---

### Post by Agent.Logic_ on 2009-04-05
The OpenChrome wiki link works. The proprietary drivers can be found [here](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=185).

Also, try this dude's xorg configuration settings: [https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807) (scroll down to the last post, too bad there are no permanent links for posts there). He apparently made compiz work, but note the side effect he posted. I'm going to try it now. :D

**EDIT**: Did not work for me.

---

