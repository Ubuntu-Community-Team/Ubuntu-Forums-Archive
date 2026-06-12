---
title: "Appearance has changed overnight"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Bruv on 2009-07-17
After starting up to night my desktop is oversize and Thunderbird shortcut had disappeared from view, all the other desktop icons are larger too.
I have tried to change screen resolution but it only gives me two options 800 x600 and 640 x 480, when I changed it to 800 x 600 the 'apply' button was off screen and un-resizeable, until I moved the task bar to the side.
I have changed font size but FF remains chunky.
I apply all updates when they crop up.
Any clues what I should do.

---

### Post by Bruv on 2009-07-17
Solved it myself.
I rebooted and went to recovery mode, then repair packages or whatever it says.
It all seems back to how it was previously.

Should have done that before asking sorry.
Might help somebody else I suppose.
Bruv

---

### Post by Bruv on 2009-07-18
Despite my previous post saying everything has been resolved I am still having problems.

My desktop icons are larger than they were,too big to look good.
Firefox seems to be different too, the navigation,bookmark area seems to have enlarged, so that I have a smaller visible browser window and I am having to scroll sideways on some sites.
I have adjusted font size via system, preferences, etc.
Am I looking in the wrong place to sort this out ?

---

### Post by RomeReactor on 2009-07-18
Hi. Have you installed any new kernels (as part of an update maybe)? What video card do you have? If your video card is either ATI or nVidia, have you installed any proprietary drivers for it, downloaded from their website?

---

### Post by Bruv on 2009-07-18
I am almost a total novice, I accept all updates as a matter of course. So my my system is up to date.
I did update prior to this behaviour started.
I do not know what Video card I have installed but I have not installed any drivers for it.

---

### Post by Bruv on 2009-07-18
My screen resolution was fixed at 800x600 with the option to change it to 640x480 with all other options unavailable.

For some inexplicable reason it has now reverted to the full options, and I have changed it to 1024x768 as it should be.....so problem solved.

I have been tinkering around to find why my settings had altered, but as far as I know I had not changed anything until I logged on tonight to post this, and found my screen resolution settings were now fully available again. I went to screen resolution to remind myself what the options were, only to find ALL were there.

So a happy resolution mysteriously occurs.....If only I knew what I had done....I could tell everybody else.
Thanks for all the help.

---

### Post by Bruv on 2009-07-19
OK I give up........

The screen resolution appears to be the same as before everything altered.
But when viewing web pages many are too small.
The choices when changing screen resolution are now limited again, despite my 'seeing a wider choice before. Whatever I set the resolution to, the fonts are too small using firefox.
Seamonkey, Konqueror and Epiphany the fonts are correct,only Firefox is playing silly buggers.

---

### Post by manilaph on 2009-07-19
Hi,

I used to have a problem like that with my Nvidia desktop.

If you have the Nvidia drivers installed... you cannot save the settings unless you are root.

So you should open the terminal:
gksudo nvidia-settings 

and then adjust the settings and save them.

this should make your "adjusted changes" permanent.

---

### Post by Bruv on 2009-07-19
I don't know if it is my screen resolution or something else now.
I have played around with the resolution and font sizes.
I am posting screenshots of the member list bottom of Forum Opening page to show the difference between Konqueror and Firefox.[IMG]http://i2.photobucket.com/albums/y45/abbies/Screenshot-UbuntuForums-MozillaFire.png[/IMG]
[IMG]http://i2.photobucket.com/albums/y45/abbies/Screenshot-UbuntuForums-Konqueror.png[/IMG]

And I have lost the @ from its correct place, it is now reversed with the " speech marks.......what has happened to my PC ?

---

### Post by mgmiller on 2009-07-19
In Firefox, while displaying the page, hold down the ctrl key and move the scroll wheel on your mouse.  It may take a major fraction of a second or so to react depending on your video card, so go slowly one click at a time to start.  Scroll up makes the font larger and scroll down makes it smaller.  Firefox should remember your preferences on a site by site basis, so the next time you go to that site, it should look ok.

---

