---
title: "Screen resolution set at max..  Oops!.."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-03-08
A new install of Ubuntu..  

Silly me..  I was showing how large the screens could be made for an old lady's bad eyes.. and I made it so large that the buttons are way below the bottom of the screen.. and haven't found the restore-solution in the forum's archives...

What is the code to make screen resolution default at minimum screen resolution..?

---

### Post by DGortze380 on 2009-03-08
> **DonaldJ said:**
> A new install of Ubuntu..  

Silly me..  I was showing how large the screens could be made for an old lady's bad eyes.. and I made it so large that the buttons are way below the bottom of the screen.. and haven't found the restore-solution in the forum's archives...

What is the code to make screen resolution default at minimum screen resolution..?

Have you tried to reboot??

You may have to edit /etc/X11/xorg.conf

---

### Post by lindsay7 on 2009-03-09
this might work

sudo dpkg-reconfigure ubuntu-desktop

---

### Post by DonaldJ on 2009-03-09
Reboots did nothing to fix it...

I'll try that code...  I must pull this hd, and install the one with the screen problem...

This 37-gig hd needed a W98-format & Ubuntu reinstall, after it got hit a bit, and the nudie pix assortment got changed to flowers...  From then-on it wouldn't load new pix to the desktop-changer...  I suppose someone was telling me that, "in their world it's bad to gaze upon bare naked ladies, and that I should lust over flowers instead"...  Probably an extremely aggressive parental-figure, who figures the world should live by his or her extreme "morals", violently applied...
Oh well, this too shall pass...  In using Windows, no one ever applied their morals to my screen before, they just destroyed the OS's, "Bang!"..
I wonder if that was the selection of flowers they normally run on their desktop as background..?  Gotta admit, they were pretty flowers, but not my idea of xxx, gazing at the ripe reproductive organs of plants.. "WhooH!"...   Maybe if I was a plant it would...  Their choice of pix, replaced and filled the desktop background options..  and after I deleted them, some of the OS went with them..?  Then when new pix loaded to the hd, a few would load, then the PC would lock-up...  It gave me the feel I was living part of their extreme moral life...  Not my idea of living life though...  Not my idea of pleasing the senses neither...  They would sure make for a wicked government censor person...  I bet that person believed they were doing "good"...
I bet even kissing and smiling would be deemed illegal in their view of things...  Flowers..  Funny, hah hah!..  I was surprised it wasn't "religious iconic-pix"...  "Flowers".. lol...
I can almost imagine how their kids feel living under that almighty biblical-thumb's Crush... Poor kids!..  I suppose it a clear example of the abused becoming the abuser...
Maybe that PC-attacker :twisted: should read all of what's in this link:  [http://www.ubuntu.upc.edu/](http://www.ubuntu.upc.edu/)


OK!  Shut 'er down.. pull the hd.. install the troubled hd.. and try your suggestions...   I be Back...

---

### Post by DonaldJ on 2009-03-09
Your suggestions didn't work..  and the other maybe solutions I found in other forums didn't work neither...

It became a toss-up whether to reinstall, given that I hadn't done the 260 updates yet... It's reinstalling...  

**The obvious solution for this silly little glitch never happening to anyone again, is to give the background changer a minimizer button, and/or place the buttons in the middle of the window...**

A thought on the little close X-button's placement...  The close button is always at the top of the window.. but the user is generally at the bottom of the window when it's time to close the window...


Thanks for your suggestions...

---

### Post by cowboy7305 on 2009-03-09
If you used System -> Preferences -> Screen resolution:
Press Alt+F2
Enter: gnome-display-properties
You can use Alt+Left click to move the window around

If you used randr:
Press Alt+F2
Enter: gnome-terminal
You can use Alt+Left click to move the window around
Enter: sudo xrandr -s 1280x800
Enter: your_password
 i was given this 2 days ago 
and it worked for me  i did same thing

---

### Post by kansasnoob on 2009-03-09
You should also be able to reboot in recovery mode. 

If you have a single-boot (Ubuntu is the only operating system on your computer), you may have to press the Escape key during bootup in order to see the boot menu.

Then select recovery mode and wait for all the boot-up processes to finish, then you'll be presented with a few options. Choose the option "X-fix   Try to fix X-server".

That should auto detect your display just like if you were able to run in terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

