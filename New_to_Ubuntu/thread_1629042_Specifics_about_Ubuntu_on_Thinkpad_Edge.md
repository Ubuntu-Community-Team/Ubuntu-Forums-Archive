---
title: "Specifics about Ubuntu on Thinkpad Edge"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by edzell on 2010-11-23
I'm considering the Thinkpad Edge, 15.6" with intention to install either Ubuntu or Linux Mint: hopefully Mint 10 "Julia." The Edge will be at the limit of my budget once I sell my present laptop. I'm looking for advice & experience with running Linux "on the edge."

Some features that appeal to me - compared with my current HP laptop - are:
- Simple keyboard layout with legible, "normal" key sizes & relationships (e.g. there are no tiny keys with microscopic icons and the left shift is BIGGER than the caps key)
- Hopefully, complete keyboard functionality under Linux
- Available Matt screen & non-gloss casing.

Things I'm unsure about:
- Hopefully, complete keyboard functionality under Linux :)
- The trackpoint system may be hard to get used to, and easy to engage accidentally while typing?
- Could I disable the touchpad & trackpoint at will?
- Will the touchpad reliably disengage when typing? (With a suitably long delay between keystrokes for this non-typist) ****

Any & all feedback/advice welcome. (Please distinguish between educated opinion and hands-on experience :)
I'm not very Linux-savvy and almost exclusively a GUI-GUY, so simpler explanations are better.

**** This is the most frustrating issue with my HP laptop. No matter how I try to disable or hobble the touchpad while typing, it always defeats me - shifts the cursor if ever I brush it with my wrist. That's even when I use the laptop's "touchpad off" switch or allegedly disable the pad using touchfreeze, installed from Synaptic. I HATE this machine! It was a present from someone who spent more than she could really afford :(

---

### Post by LowSky on 2010-11-23
I have used Thinkpads and older Dells that use the eraser style mouse pointer and have never had a accident when trying to type. It impossible they need a bit of pressure to work, a keypress wont effect them. Trackpads on the other hand I casually have issues with. Trackpads are not my favorite at all.

The keyboard will work just fine. On the 4 laptops I have installed numerous verisons of Linux all have worked fine. Some might have issues with media keys, but thinkpads are very well supported on Ubuntu.

---

### Post by edzell on 2010-11-23
> **LowSky said:**
>  ..... Trackpads on the other hand I casually have issues with. Trackpads are not my favorite at all.

The keyboard will work just fine. On the 4 laptops I have installed numerous verisons of Linux all have worked fine. Some might have issues with media keys, but thinkpads are very well supported on Ubuntu.

Thanks. Is Trackpad the same thing that I'm calling Touchpad? The little area where you can move & tap your finger instead of using a mouse. And are you saying it maybe can't be disabled using Ubuntu? I gather you're not talking specifically about the Thinkpad Edge though; the one I'm hoping to use?

---

### Post by rCXer on 2010-11-24
I own a Thinkpad Edge 14 (intel) with 10.04 and so far things have been working great.  I wrote about my experiences at [ThinkWiki](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Edge_14%22_%28Intel%29).  Make sure you look at [this thread](http://ubuntuforums.org/showthread.php?t=1412406) as well.

> 
- Simple keyboard layout with legible, "normal" key sizes & relationships (e.g.there are no tiny keys with microscopic icons and the left shift is BIGGER than the caps key)


The keyboard is comfortable and legible but the arrow keys are a bit small for my tastes.  A few people have complained about keyboard flex on 15-inch models but this may have been fixed by Lenovo.

> 
- Available Matt screen & non-gloss casing.

Get Matte!.  I got the glossy cover and it picks up alot of fingerprints.

> 
- Hopefully, complete keyboard functionality under Linux :)

All regular keys and **most** special keys (volume, mute, etc...) work.  See the ThinkWiki link above for more info.

> 
- The trackpoint system may be hard to get used to, and easy to engage accidentally while typing?

This hasn't been a problem for me but I'm a trackpoint person :P

> 
- Could I disable the touchpad & trackpoint at will?


Touchpad can be disabled using...
```

gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean false

```
...and enabled using...
```

gconftool-2 --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" --type boolean true

```

I don't know how to disable the trackpoint. The trackpoint and touchpad can be configured as described in the ThinkWiki article.

> 
- Will the touchpad reliably disengage when typing? (With a suitably long delay between keystrokes for this non-typist) ****

No and since the touchpad is really big this problem is unavoidable.  I don't think this is an Edge-Specific problem.

---

