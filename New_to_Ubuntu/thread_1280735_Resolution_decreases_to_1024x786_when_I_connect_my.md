---
title: "Resolution decreases to 1024x786 when I connect my HDTV to my laptop"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by diablo75 on 2009-10-02
I just got an HDTV from a buddy of mine and it is capable of 1080p resolution.  My laptop is only capable of 1280x800 resolution and all I want to do with this TV is mirror what I have on my desktop, though it would be cool if I could extend the TV as a second monitor to play videos while using the laptop for Internet related stuff... but it's not a priority.  Ultimately, I just want to watch videos from my laptop on TV.

Now when I attach the SVGA cable to the TV and the laptop and restart the laptop, Ubuntu boots up at 1024x768 and when I look in System>Preferences>Display Preferences, I can't select any higher resolution (though I know the TV is capable of FAR more).

The video card in my laptop is an ATI Radeon X1250 (and yes, it does suck).  I love nVidia cards because I get a detailed control panel seperate from the generic display properties panel mentioned above.  I don't know of any such detailed ATI control panel...

Anyway, all I want to do more than anything is force Ubuntu to stay in 1280x800, no matter what.  Anyone know how I can do this?

---

### Post by diablo75 on 2009-10-03
Bump.

---

### Post by DrMelon on 2009-10-03
Your TV probably isn't meant for 1280x800; TV's are meant for their own resolutions, and those resolutions only.
I suggest trying 1920x1080 (as that is the 1080p resolution).
Also, make sure that you set your Laptop screen to be off when setting this up, as it will not work since your laptop will force the resolution back down to keep it consistent between both screens.

EDIT: In short, you won't be able to mirror at 1280x800 since your TV will not support that. You will also not be able to mirror 1920x1080 since your laptop screen doesn't support that. One or the other, it's your choice.

---

### Post by diablo75 on 2009-10-03
> **DrMelon said:**
> Your TV probably isn't meant for 1280x800; TV's are meant for their own resolutions, and those resolutions only.
I suggest trying 1920x1080 (as that is the 1080p resolution).
Also, make sure that you set your Laptop screen to be off when setting this up, as it will not work since your laptop will force the resolution back down to keep it consistent between both screens.

EDIT: In short, you won't be able to mirror at 1280x800 since your TV will not support that. You will also not be able to mirror 1920x1080 since your laptop screen doesn't support that. One or the other, it's your choice.

Actually the TV will accept any resolution I throw at it, and I know this because I dual boot with Windows from this laptop and have tested it from that OS to see how the TV handles it.  The TV (just like ANY modern LCD monitor I've ever seen) will auto-scale the input feed to fit the screen.  For example, 1024x768 isn't the native resolution of the TV or even the screen that's on my laptop, but on both screens it "just works".  Sure, it's not perfect and doesn't match the native resolutions of either screen, but it doesn't harm either screen at all, so I'd be happy to set them to the native resolution of the laptop so they match (they already do mirror at 1024x768 ).

That being said, I still don't know how I to set a custom resolution with my ATI video card.  Even if I wanted to try to set the resolution at 1920x1080, I wouldn't know how to do this as it's not offered, nor is any other resolution above 1024x768.  Anyone know how this can be done?  Is there something I can add to my xorg.conf file to do the trick?

---

### Post by solitaire on 2009-10-03
> **diablo75 said:**
> I just got an HDTV from a buddy of mine and it is capable of 1080p resolution.  My laptop is only capable of 1280x800 resolution and all I want to do with this TV is mirror what I have on my desktop, though it would be cool if I could extend the TV as a second monitor to play videos while using the laptop for Internet related stuff... but it's not a priority.  Ultimately, I just want to watch videos from my laptop on TV.
...
...



 I've got the same setup as you. I have a full 1080p tv and a 1280x800 laptop. You *don't* want to mirror the screens, you want to 'extend' the desktop so you can drag movies over to your tv and watch at full res... I do that all the time both your laptop and tv will display at their highest res in that setup.

If you mirror the screens, then your card tries to output at the lowest common supported res, which looks terrible with most cards (well all the ones I've tried it does). Try it with mirroring off

---

### Post by diablo75 on 2009-10-03
Where do I go to change these settings?

---

### Post by solitaire on 2009-10-03
It should be under "system" / "preferences" / "display"
If you open that with the tv plugged in you should see 2 displays listed.
select the tv and then take the tick out of "mirror display" you might have to select "on" for the laptop to use the tv.

I'm running on a intel GM965 card in my laptop, so Im not sure if the ATI has its own program to handle displays. But the default one should do what you require.

---

### Post by raghavendraprakash on 2012-12-12
My analysis goes as below ...
SVGA resolution is 1024 X 786 and you have connected that to TV from your laptop. The resolution is downgraded.

---

