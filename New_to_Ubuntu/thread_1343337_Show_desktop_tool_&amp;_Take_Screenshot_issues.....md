---
title: "Show desktop tool &amp; Take Screenshot issues....."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-01
Ubunteros,

In the bottom left hand corner of the attached pic. is the so-called "Show Deskktop Button". The version I have is 2.22.2.

I was under the impression that this button would work like in Windows. Simply said, You click on it a "voila" Your desktop instantly appears.

However, when I click on it it shows hidden windows. It must be clicked on repeatedly to show the desktop.

What can be done to show the desktop instantly????

I also noticed that when using the "Take Screenshot" tool, a reflection of the "Take Screenshot" window appears in the pic. The attached pic shows this clearly. To get rid of it You must move it aside. Then take a pic. Is this feature really that cumbersome to use?

If You read and understand what I have said and can offer advice then You suggestions and advice is most welcomed.

Thank You!

---

### Post by plucky on 2009-12-01
> I also noticed that when using the "Take Screenshot" tool, a reflection of the "Take Screenshot" window appears in the pic. The attached pic shows this clearly. To get rid of it You must move it aside. Then take a pic. Is this feature really that cumbersome to use?

Try putting a delay into the screenshot window.


See attachment for a description of that button

---

### Post by mörgæs on 2009-12-01
Regarding the snapshot: Have you tried the delay option in the dialog box?

---

### Post by camaron1 on 2009-12-01
For screen shots install Shutter (repositories). For showing the desktop I I've got UbuntuTweak installed and I show my desktop with a mouse gesture (taking the mouse pointer to the lower left corner of the screen). You can do this directly with Compiz. Having said that I re-installed the Icon you use (just to check) and works OK for me.

---

### Post by suomalainen on 2009-12-01
Thanks Everyone on the advice regarding the delay feature. That solves the problem....

I deleted the "Show Desktop Icon" and re-installed it but now I need to figure out how to get it back into the left hand corner.....


Thanks again.

---

### Post by suomalainen on 2009-12-02
Unless I'm missing something, I still can't get the "Show Desktop tool" icon to IMMEADIATELY show the desk top when it is clicked.....

Is there something else I can do?

Thanks

---

### Post by mgmiller on 2009-12-02
I have found the easiest screen shot capture to be the PrtScrn button on my keyboard.  If you just want the active window, then use alt/prtscrn.

I can't duplicate your show desktop problem.  When I click on my show desktop button, any open windows drop down to the lower panel using whatever animation is set in compiz.  If it's the time it takes the animations to run that is bothering you, try turning off desktop effects:
System > Preferences > Appearance  and go to the Visual effects tab.  Select "None"  and see if the show desktop button works as expected. 
When I do this in my system, the show desktop button function becomes almost instantaneous.

If it fixes your problem, then you may want to try tweaking some of the settings in ccsm (compiz-config-settings-manager) to change the animations that are used to minimize windows, or you could just speed them up.

---

### Post by suomalainen on 2009-12-02
MGMiller,

Thanks for the suggestion, i.e..

> try turning off desktop effects:
System > Preferences > Appearance and go to the Visual effects tab. Select "None" and see if the show desktop button works as expected.
When I do this in my system, the show desktop button function becomes almost instantaneous.

Now it works instantly. But I would like to tweak things. How do I access the CCSM?

Thanks again for your help. Much appreciated!!!!

---

### Post by mgmiller on 2009-12-04
> How do I access the CCSM?Install the package:
```
sudo apt-get install simple-ccsm
```This will install 2 control guis in System > Preferences.
Compiz Config Settings Manager
&
Simple Compiz Config Settings Manager

The 2nd one is easier to use, but does not have as many options.

The first one is for full control of all things Compiz.  It can be daunting, but fun to play around in.

In the Simple CCSM, try going to the Animations tab and on the Minimize Window drop down, select "None".

See if that helps.  If not, in the full CCSM, Type into the Filters field:
```
animations
```On the right side, click on "Animations" and then the "Minimize Animation" tab.

Have at it. You can change the animations on a per application basis in here if you want, as well as their speed.  For example, I have the minimize animation for evolution set to airplane so the window folds into a paper plane and flies off the screen.

The default speed is 300, which means 300 milliseconds (about 1/3 sec).  If that's too slow and you still like the effect, just change the number to a smaller value like 100 and see how you like it.

 If things get totally screwed up, the little icon of a broom resets things to their default values.

Have fun.

---

### Post by suomalainen on 2009-12-06
I guess the command for "Compiz Config Settings Manager" is missing????

I tried with simple and had really strange results. 2 of my 4 desktops vanished. Then rotate cube disappeared.....


Maybe I should stick with what I have?????

---

