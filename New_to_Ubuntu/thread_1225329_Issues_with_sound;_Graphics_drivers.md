---
title: "Issues with sound; Graphics drivers"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by MoonlitFate on 2009-07-28
First off, if this is in the wrong section I apologize.  I thought it's be good to post it here, since I'm a beginner to Ubuntu. :P

Anyway, I just switched over from Windows XP to Ubuntu 9.04, and I'm encountering some issues.  I'd appreciate it if I could get some help with them. :D

[LIST]
[*]First is a **sound issue**.  My main volume on the taskbar doesn't seem to be working.  Basically, nothing happens when I try raise / lower / mute the sound with one of the buttons on my keyboard and nothing happens.  Could this just be a driver issue or something?  I'm entirely lost, to be honest.
[/LIST]

[LIST]
[*]The second is related to **graphics drivers**.  Would I need to install the drivers for my graphics card (if I can even find them)?  I have an ATI FireGL 8800 and on the ATI website the I've tried to look for the graphics drivers for Linux, only to receive a 404 error when trying to get on the page with the drivers. ._.; Also is there a way to set your default graphics card (seeing as I have 3 in this computer. ><; The 8800, an old RageXL card, and my MB's Intel 865 chipset)?
[/LIST]
Thank you for taking the time to read this, and I'd appreciate any help that I get with these issues.

---

### Post by tacantara on 2009-07-28
Here's a link to a Forum post that covers many of the most common sound problems.  I have used this before and found it quite helpful:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

As for the graphics card question, Linux distributions (such as Ubuntu) include hardware driver info in the kernel.  If you're not experiencing any problems with graphics, then you probably don't need to do anything further.  Have you tried enabling any features that would require advanced graphics (i.e Compiz Fusion for advanced desktop features, i.e. wobbly windows and desktop cube)?

---

### Post by MoonlitFate on 2009-07-28
Thanks for the reply, and the post to that thread.  Though, I'm still having the same issue, but it could the fact that I'm using headphones.  I'm not really sure, but I'll continue looking into it. Hopefully I won't need to install the driver or anything, since it's finding my sound card. 

As far as the graphics card thing goes, I don't think so.  Some webpages (Myspace) aren't smooth when scrolling for some reason, but is that a graphics problem, or more of a web browser issue?  I'm kind of confused, heh.  And I haven't tried to do anything that would require advanced graphics. :x I'm kind of afraid to, but would there be anything that I could use to test them out to see if I have any issues? :/ A game or something perhaps?

---

### Post by tacantara on 2009-07-28
> **MoonlitFate said:**
>  As far as the graphics card thing goes, I don't think so.  Some webpages (Myspace) aren't smooth when scrolling for some reason, but is that a graphics problem, or more of a web browser issue?  I'm kind of confused, heh.  And I haven't tried to do anything that would require advanced graphics. :x I'm kind of afraid to, but would there be anything that I could use to test them out to see if I have any issues? :/ A game or something perhaps?

I also see a bit of a lag on websites when I scroll, but it's not anything extreme.  Enabling Compiz Fusion and the advanced desktop settings will certainly put your graphics card to the test, but I suppose you could also try some of the games that come stock with Ubuntu (Applications > Games).

---

### Post by sandeepraj on 2009-07-28
try installing ati driver from add/remove.. there is a driver there

---

### Post by MoonlitFate on 2009-07-28
> **tacantara said:**
> I also see a bit of a lag on websites when I scroll, but it's not anything extreme.  Enabling Compiz Fusion and the advanced desktop settings will certainly put your graphics card to the test, but I suppose you could also try some of the games that come stock with Ubuntu (Applications > Games).

I'll have no idea how to enable Compiz Fusion, and I'm afraid of messing something else up. ><;  If you can offer a link to thread on how to enable Compiz, then I don't think I'd have that big of an issue with trying to get that to work. :3

> **sandeepraj said:**
> try installing ati driver from add/remove.. there is a driver there

Thank you, I'll try that. :D  EDIT: Those graphics drivers killed Ubuntu. ;.;  I can't even log-in, or see the log-in screen for that matter.  It's just a jumbled mess of colors and other weird things and it's just frozen there.  I'm on the Live USB (SD Card) that I made last night.  So, I guess I'm re-installing Ubuntu, since I have no idea how to fix all of this. :( 


And now, I have a new issue-- It seems I've murdered my sound entirely. :/  I made the mistake of downloading the Realtek drivers for my soundcard and have no sound at all, and very annoying beeps that don't end (unless I close the sound window) when I go to test my sound. ><; :confused:

---

### Post by halitech on 2009-07-28
first off, power down and remove the Rage card, its old enough there is no support for it at all and you will get at best 2d and probably 800x600 resolution.

Try booting up and when you get to GRUB, press ESC and select Single User mode, that will allow you to hopefully fix the video by running
```
xfix
```

---

### Post by Mark Phelps on 2009-07-28
> **sandeepraj said:**
> try installing ati driver from add/remove.. there is a driver there

Wow -- Way to tell someone to install a driver that will trash their system!!

There are NO ATI drivers that work with Ubuntu 9.04 for the op's card.  Best bet is the open source drivers -- which are installed by default.

---

### Post by halitech on 2009-07-28
> **Mark Phelps said:**
> Wow -- Way to tell someone to install a driver that will trash their system!!

There are NO ATI drivers that work with Ubuntu 9.04 for the op's card.  Best bet is the open source drivers -- which are installed by default.

hopefully they will learn by someone else's pain and not suggest something like that again.

OP: forget about Compiz as well, you need a card with 3D performance to make it worthwile

---

### Post by MoonlitFate on 2009-07-29
> **Mark Phelps said:**
> Wow -- Way to tell someone to install a driver that will trash their system!!

There are NO ATI drivers that work with Ubuntu 9.04 for the op's card.  Best bet is the open source drivers -- which are installed by default.

Oh, okay. I didn't seem to think that the drivers were installed by default.  At least I know that now, so I won't be making the same mistake twice.  But, thanks for letting me know. :D

> **halitech said:**
> 
OP: forget about Compiz as well, you need a card with 3D performance to make it worthwile

I'm pretty sure my graphics can handle 3D performance, maybe not as awesomely as the new cards that come out now, but it's something.   [http://ati.amd.com/products/firegl8800/index.html](http://ati.amd.com/products/firegl8800/index.html)

---

### Post by CatKiller on 2009-07-29
> **MoonlitFate said:**
> First is a **sound issue**.  My main volume on the taskbar doesn't seem to be working.  Basically, nothing happens when I try raise / lower / mute the sound with one of the buttons on my keyboard and nothing happens.

The channel that gets affected with the keys on the keyboard is defined by the setting at the bottom of the Preferences &#8594; Sound window; the Default Mixer Tracks section. You'll want to set it to something that's outputting sound. Something like "Playback: ... (PulseAudio Mixer)" if you're using PulseAudio or "... (ALSA mixer)" if you're using ALSA.

You'll probably also want to check that the buttons are the correct ones (Volume mute, Volume down, Volume up) for the shortcuts in System &#8594; Preferences &#8594; Keyboard Shortcuts. Just click in the box next to the shortcut and press the appropriate media key on your keyboard.

The channel that gets affected with the volume control applet on the panel is defined in the applet itself. Right-click on it and select Preferences. At the top of the window that opens you'll see a drop-down box which defines which device it should control. The rest of the window lets you select which track of that device to control.

---

### Post by halitech on 2009-07-29
> **MoonlitFate said:**
> Oh, okay. I didn't seem to think that the drivers were installed by default.  At least I know that now, so I won't be making the same mistake twice.  But, thanks for letting me know. :D



I'm pretty sure my graphics can handle 3D performance, maybe not as awesomely as the new cards that come out now, but it's something.   [http://ati.amd.com/products/firegl8800/index.html](http://ati.amd.com/products/firegl8800/index.html)

the card might be able to handle it but its going to be a matter of if the drivers have support for it in Ubuntu.

---

### Post by MoonlitFate on 2009-07-29
**CatKiller**,

Wow, thank you!~ :D  Though, I'm sure I may have to tweak a few things volume-wise (maybe just raising on volume track with the keyboard as opposed to two), but for the most part this solution works.  Thanks again, for giving me a rather quick and easy solution to my problem!

---

