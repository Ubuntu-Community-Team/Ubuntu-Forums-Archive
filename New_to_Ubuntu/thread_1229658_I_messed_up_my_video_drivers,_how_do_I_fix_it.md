---
title: "I messed up my video drivers, how do I fix it?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by BigWoop on 2009-08-02
I was trying to install the Proprietary ATI drivers on my system, I followed the intructions from the ubuntu wiki.

The progress window sat on 0% for a long time and then I got some error message about something to do do with jockey I think, I really can't remember what it said unfortunately. I could see that it had downloaded something through system monitor.

I closed the hardware drivers window and then reopened it and it said I should restart so I did. Now on startup I see the animated logo for a bit and then this strip at the top with weird red symbols, and the logo is off color, red and tiled across the screen at the top and just blackness from about halfway down. Nothing seems to work really either.

I tried starting in recovery mode and using the try to automatically fix graphics problems and that didn't help.

I think it's maybe just some settings, but Ihave no idea what to edit or how to do it from this point as it's totally unusable. I would like to install the proper driver but maybe I should just revert back to original one for now? (I don't know how to do that either).

What should I do?

BTW I'm using Ubuntu Studio 9.04

---

### Post by Primefalcon on 2009-08-02
what exact ATI card are you using per chance?

---

### Post by BigWoop on 2009-08-02
Sorry, it's HD 4670, is there a problem with these in Linux or something?

---

### Post by jacklinux on 2009-08-02
> **BigWoop said:**
> Sorry, it's HD 4670, is there a problem with these in Linux or something?
ATI do have trouble in Linux. But theres always a fix thats what these forums are for

---

### Post by gorgon on 2009-08-02
hi,

try the suggestion in this post and tell us how it goes:
[http://ubuntuforums.org/showpost.php?p=7722240&postcount=3](http://ubuntuforums.org/showpost.php?p=7722240&postcount=3)

---

### Post by BigWoop on 2009-08-03
I tried that, it didn't help unfortuneately.

Well, ctrl+alt+f1 does squat. So I tried recovery mode and chose the option for root shell and then tried the commands mentioned in that post.

Went through a few screens, first time I said yes to the option about the kernel driver handling video stuff and just left all the keyboard options as they were.

Second time I said no to the first option and changed a few of the keyboard related settings but I don't think any of those will affect my problem.

Anyway everything is still the same, I did notice that on startup when it looks weird I my screen turns off and back on three times, doubt that really helps though.

---

### Post by BigWoop on 2009-08-03
Maybe, if I knew what you were talking about.

---

### Post by gorgon on 2009-08-03
ok. this is a good page for troubleshooting graphical problems:
[https://wiki.ubuntu.com/X/Troubleshooting/](https://wiki.ubuntu.com/X/Troubleshooting/)

Since you can log on in recovery mode I would try using the vesa graphic driver (from the Troubleshooting Single Color Screen on Boot Issues page):

> 
Try using the vesa video driver by editing your /etc/X11/xorg.conf,

```
sudo nano /etc/X11/xorg.conf
```

and next change the Device section to look like this:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection
```

and then restart

as far as Ive understood, vesa is a quite basic driver that should 'just work' on most cards but cant do well the most advanced kind of stuff.

---

### Post by BigWoop on 2009-08-03
Didn't help, I can see a bit of a green strip as well now though.

That troubleshooting page gave me the impression that I should be looking elsewhere, it mentions something like if the screen is multicolored (mine is and was before the green strip developement, sorry that wasn't really clear in my first post) it may be a different bug.

["If you see multi-colored corruption you are seeing a different class of bug. Obtaining register dumps (see below) may still be of value however."]("https://wiki.ubuntu.com/X/Troubleshooting/SingleColorScreen")

I don't know that I can really do the register dumps thing, as it says I need it with a working driver and don't have that now. Will it be worthhile to re-install and get register dumps on the clean install and then again after I have broken it?

I'm thinking I should maybe just re-install from scratch and then try again to see if the same thing happens, but somehow I expect it will.

---

### Post by realzippy on 2009-08-03
..have a look:

[http://ubuntuforums.org/showthread.php?t=1229145](http://ubuntuforums.org/showthread.php?t=1229145)

the only way not to downgrade to 8.1 ?!

---

### Post by BigWoop on 2009-08-03
Thanks, I will try this, I will have to re-install first though so it might take a while to get round to, I'll let you know if it works, but I think it should.

---

### Post by BigWoop on 2009-08-05
I tried that but am having another problem with it [http://ubuntuforums.org/showpost.php?p=7737539&postcount=17](http://ubuntuforums.org/showpost.php?p=7737539&postcount=17), so I guess I'm kind of half way there.

---

