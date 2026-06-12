---
title: "No more &quot;add/remove&quot; on application menu? Rhytmbox now also won't play OGG stream?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-06-18
I'm back, just fixed octoshape thread after almost a full day and night, was really happy but....

I couldve sworn that my Applications Menu was longer. (I have, Accesories, Games, Graphics, Internet, Office, and Sound & Video) I thougth there was more like some separation bar and Add/Remove Programs How do I get it back?

Also Rhythmbox did play my stream almost fine (occasional choppiness I assume my connection) But totally fine for hours on end, and then....
I get this error:

A text/uri-list decoder plugin is required to play this stream, but not installed.

It was fine today then this error. I did do quite a bit of changes based on:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

So I am suspect, but don't know why it suddenly wont work. I think I did only a few other recent changes, 

but still... No Add/Remove??? No Rhythmbox because of  "text/uri-list decoder" ??

Yet again I say... Please help.

-Desi

---

### Post by DesiArnez6 on 2010-06-18
[http://ubuntuforums.org/showthread.php?t=375480](http://ubuntuforums.org/showthread.php?t=375480)
 p
^seems to adrees the basics, but no solution

I also checked System >> Preferences >> Main Menu and Add/Remove... IS checked, If I find more I'll post.

---

### Post by warfacegod on 2010-06-18
> I couldve sworn that my Applications Menu was longer. (I have, Accesories, Games, Graphics, Internet, Office, and Sound & Video) I thougth there was more like some separation bar and Add/Remove Programs How do I get it back?

Right click your Menu bar and select Edit Menus.

What OS are you using, by the way?

---

### Post by DesiArnez6 on 2010-06-18
After Edit Menus, It says I do have the right order, but it doesn't show up

I use Ubuntu Jaunty

Also, wasn't there two different options under System>>Administration that dealt with Synaptic? All I have now is Synaptic Package Manager, but I thought there was another option right above it that said Synaptic something. hmm.

---

### Post by DesiArnez6 on 2010-06-18
Update:
With Edit Menus, I realized it wasn't two Synaptics, just the same logo

it was "Software Sources" which the edit menus says is there, but thats missing too from the actual menus. I hope im not missing other things as well

---

### Post by warfacegod on 2010-06-18
Are there checks next to the missing items?

---

### Post by DesiArnez6 on 2010-06-18
Well a learned a few things

1. If youve done some changes to your system, sometimes you just need to reboot. I was definitely on Profile 2. Both are now normal, no more text/uri decoder error etc. Add/Remove and menus seem intact.

Interesting fact, when i open as a guest instead of a profile, i get all the same problems that somehow crossed over to my regular profile.

Also I did have to re-add rhythmbox stations that I have saved, but i am fortunate that in my case it was only one station :)

ok, i have been probably working for what...26 hours fixing things :) So that means sleep time soon.


I Hope that this post is helpful in some way. All seems well :)

---

### Post by DesiArnez6 on 2010-06-18
> **warfacegod said:**
> Are there checks next to the missing items?

Yep that was the odd part.

Interesting note: Just checked guest account, and while the same things are missing that were missing in my profiles, there are NO checks next to the missing item.  Strange.

---

### Post by warfacegod on 2010-06-18
Use Synaptic and select Edit on the top left and select "Fix Broken Packages".

Now search for gdm-guest-session and mark it for "Complete Removal". Click Apply. Now install it again if you want to use it, or don't if you have no need for it.

---

### Post by DesiArnez6 on 2010-06-19
As a side note to make my report more complete, I did have to reinstall Movie Player which remained missing and then uncheck and check it again in "Edit Menus" All seems fine on this issue

Thanks warfacegod, I didn't even know about the Synaptic "Fix Broken Packages" feature. I may just consider that.

---

