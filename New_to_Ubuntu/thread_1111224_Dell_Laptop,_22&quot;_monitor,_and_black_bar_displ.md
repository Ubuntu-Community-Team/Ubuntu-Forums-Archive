---
title: "Dell Laptop, 22&quot; monitor, and black bar display areas"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Surly1 on 2009-03-30
New to Linux as of last week when I installed Ibex in place of XP on my Dell D610 Latitude Laptop with Hanns-G Hi221D 22" monitor.

Using "Configure Display Settings" I was able to turn off the laptop screen, uncheck the mirror display and change the resolution to what I ran before using XP:  1680 x 1050.  Unfortunately my preferred setting gives me the black bar along the bottom and right side of the display.  The display is cut off but the mouse cursor will still track on the black areas.

Changing the resolution to 1440 x 900 fills the entire monitor display but the quality of the display is not satisfactory.  1680 x 1050 is what I should be able to run as it worked fine with XP.

I spent some time searching the forums but was unable to unearth the solution to my particular problem.  If someone can find it in the forums, please fling me the link.  If anyone has a (useful) suggestion with this fun problem, please do not hesitate to suggest away!

Thank-you in advance for your help.

Cheers!
Surly1

---

### Post by Surly1 on 2009-03-30
Is there a moderator that can point me in the right direction?

Cheers!
Surly1

---

### Post by Mark Phelps on 2009-03-30
> **Surly1 said:**
>  1680 x 1050 is what I should be able to run as it worked fine with XP.

The two (MS Windows and Linux) use totally different drivers; so, to presume just because it worked in XP it will work in Linux is a bad presumption.

Check your Screen Resolution applet and see what it says.  It probably says something like "generic monitor" instead of the correct make or model.  If that's the case, it didn't correctly detect your monitor.

Click the button to detect the display to see if it does better.

My guess is that the default it picked is not correct for your monitor. If it does not correctly detect your monitor, you will need to experiment with different makes and models to find a resolution and frequency combination that works.

---

### Post by Surly1 on 2009-03-30
Thanks, Mark.

Under system>preferences>screen resolution, I see both my laptop screen and my 22" monitor screen.  Ubuntu identifies the 22" screen as "HSD 22"".  I don't see where I have any choices in this particular applet to choose from different makes or models.  I clicked on the button to Detect Displays and nothing changed (that I noticed.)

My monitor is a Hanns-G Hi221D.

Is there a different screen resolution applet that I should be using?

Thanks again.


Cheers!
Surly1

---

### Post by Mark Phelps on 2009-03-31
OK, so it DID detect your monitor correctly.

At this point, I think your only recourse is to fiddle with the xorg.conf file.

Since others have already discussed doing this, let me refer you to the following link -- it's not for your monitor, but the actions (editing xorg.conf, adding modeline) are essentially the same.  Ignore the stuff about installing Nvidia drivers and scroll down to the posts on viewing your Xorg.o.log file and adding a modeline:

[http://ubuntuforums.org/showthread.php?t=1104935&highlight=dpkg-reconfigure]("http://ubuntuforums.org/showthread.php?t=1104935&highlight=dpkg-reconfigure")

---

### Post by Surly1 on 2009-03-31
Thank-you for the help, Mark, and for pointing me in (what I hope is) the right direction!

Cheers!
Surly1

---

