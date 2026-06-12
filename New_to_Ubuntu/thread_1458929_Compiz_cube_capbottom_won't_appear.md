---
title: "Compiz cube cap/bottom won't appear"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by ed-koala on 2010-04-20
I'm trying to get custom pictures on my Compiz cube, but they are not showing up.  I'm seeing the default top/bottom even after changing the picture files in Cube reflection/deformation cube caps area.

I've followed the directions I found on the web, but no luck getting the pics to change.  What might I be doing wrong?

---

### Post by yetiman64 on 2010-04-20
With the settings in place you have made, try going to the "desktop cube" settings > appearance > cube caps, then highlight and delete the gdm themes human cap images (can be reset easily with the "broom" on the right of the settings if needed).

This should let your changes in "cube reflection and deformation" settings to show up. Worth a try, good luck.

---

### Post by ed-koala on 2010-04-20
I cleared the image there, as well as the othr check boxes, still no top or bottom pics showing.  I'm going to try moving my pics to another directory. Will see if that has any effect.

Very strange. I think I found the problem, but no idea how to fix it.

When I use the broom to clear my picture listed, it defaults to the default picture, which the broom will not clear.  I highlight the default, click delete, and it vanishes from the box, but if I click the broom it reappears (the default pic).

How can I permanently clear the default file?  It won't go away.

---

### Post by ed-koala on 2010-04-20
Fixed it.  I think I may have found a bug in Lucid also.

I had to log out and log back in for my changes to take effect. I didn't have to in 9.10, is there something about 10.04 I don't know?

---

### Post by yetiman64 on 2010-04-20
> **ed-koala said:**
> I cleared the image there, as well as the othr check boxes, still no top or bottom pics showing.  I'm going to try moving my pics to another directory. Will see if that has any effect.


Provided your pics are corectly pointed to in the "cube reflection and deformation" settings, it shouldn't matter where they are stored. 


> **ed-koala said:**
> Very strange. I think I found the problem, but no idea how to fix it.

When I use the broom to clear my picture listed, it defaults to the default picture, which the broom will not clear.  I highlight the default, click delete, and it vanishes from the box, but if I click the broom it reappears (the default pic).

How can I permanently clear the default file?  It won't go away.

What you're describing there sounds like the correct default behaviour, at least as I've always noted it in the past and your pics should have worked when the box was "cleared" -hmmmm. Must be another setting somewhere "blocking".

Maybe with your pictures set - just double check you've moved them to the TOP of the list where they're setup, and aren't below the compiz cap or fusion cap images - the top entry is only used, even with multiple entries in the list.

Compiz generally takes a bit of exploring and experimenting to get working, but is fantastic on the effects when setup works.


Edit: only just noted you've fixed it -- congrats.

---

### Post by ed-koala on 2010-04-20
I checked bugs and this seems to be a known problem with Lucid now.  Guess I'll have to log out if I decide to make changes to the pics until its fixed.

---

### Post by yetiman64 on 2010-04-20
> **ed-koala said:**
> I checked bugs and this seems to be a known problem with Lucid now.  Guess I'll have to log out if I decide to make changes to the pics until its fixed.

Good to hear, as I will be moving to Lucid very soon and definitely enjoy my Cube effects - will keep an eye on that - thanks.

Bye.

---

### Post by Compizshell on 2011-03-11
Do u want a sphere with no top or bottom ?  (the sphere but with transparent top and bottom or u can make it look like a fishbowl etc.) , i was trying to delete the default images too but to no avail.

solution   :     in "Enable cube reflection and deformation "  under   "appearance"  click the "New " button then click "close"      this will give you an empty picture so move it to the top of the list to make it default .       Now still in "Enable cube reflection and deformation "   Appearance change the opacity to  "  0  "    



Ty Yetiman "just double check you've moved them to the TOP of the list where they're setup" (thats what helped me  :D)   this has been bothering me for hrs too , sighned onto forum just to share this simple fix, seems a few ppl have had this problem of getting rid of default images , i had the semitransparent square on top of fishbowl problem :  [http://ubuntuforums.org/archive/index.php/t-1685702.html](http://ubuntuforums.org/archive/index.php/t-1685702.html)

this was already marked as solved nearly a year ago but i couldnt find a solution anywhere.

---

### Post by realzippy on 2011-03-11
..you notice you are necroposting?

---

### Post by Compizshell on 2011-03-11
im such a noob im not sure what that is but can take an educated guess  (posting to a dead thread )

should i delete it ?        

this is literally the 1st time ive ever bothered posting on a forum in my life  :D

---

### Post by realzippy on 2011-03-11
...no,don't get me wrong,just wanted to say:
"do not expect to get an answer!"

---

