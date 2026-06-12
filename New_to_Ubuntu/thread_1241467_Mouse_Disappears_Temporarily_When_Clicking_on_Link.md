---
title: "Mouse Disappears Temporarily When Clicking on Links"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Joseph Schwenker on 2009-08-16
Hi everyone!  I have been following Ubuntu for about half a year, and finally decided to install it on my computer.  However, I have encountered a problem with Epiphany.  Whenever Epiphany loads a web page, or whenever I double click on a file, my mouse cursor disappears temporarily.  The only way for it to reappear is for me to move the mouse outside of the window, or wait until the page or file finishes loading.  I am using Epiphany 2.26.1 and Compiz.  Thanks in advance!

---

### Post by Joseph Schwenker on 2009-08-16
Update: My mouse cursor not only disappears in Epiphany, but also in Firefox, File Browser Metacity, and Compiz.  This happens whenever a page loads in Firefox or Epiphany, whenever I click on a folder in File Browser's sidebar, or double click on a file in File Browser.

---

### Post by Keith Hedger on 2009-08-16
Sounds like its the 'wait' cursor that is not being displayed, you may have a corrupt cursor theme try changing it and see what happens.

---

### Post by Joseph Schwenker on 2009-08-16
> **Keith Hedger said:**
> Sounds like its the 'wait' cursor that is not being displayed, you may have a corrupt cursor theme try changing it and see what happens.
Thanks for the reply.  I just tried changing the cursor from DMZ (White) to all of the others listed.  However, it only applied the cursor theme in applications, and not to Ubuntu.  Now, my cursor switches from white (when I am hovering over my desktop) to black (when I am hovering over an application).  When I press the refresh button in Epiphany and Firefox, then move my cursor to the application, the cursor still disappears.  Although, I haven't seen the wait cursor yet.

---

### Post by Keith Hedger on 2009-08-17
Maybe try re-installing them from synaptic and then logging out and back in (you shouldn't really need to do this but sometimes linux is just plain cantankerous)

---

### Post by Joseph Schwenker on 2009-08-17
> **Keith Hedger said:**
> Maybe try re-installing them from synaptic and then logging out and back in (you shouldn't really need to do this but sometimes linux is just plain cantankerous)
After restarting my computer, and fiddling around with the mouse theme in yesterday's session, the wait mouse cursor is now visible!  :D
I think that I accidentally solved the problem by setting the cursor theme to something else, then back to the default, then by turning off my computer for the day in frustration.  When I turned on my computer today, the wait mouse cursor was there!  Anyway, hopefully, it will not disappear again.  And if it does, I will try what you said.  Thanks a bunch!  :)

---

### Post by Joseph Schwenker on 2009-08-18
Oh dear, it is disappearing again.  I normally use compiz, but when I switch back to Metacity, I still have the problem.  I reinstalled the package, but that did not do any good.  When I first boot into Ubuntu, the mouse never disappears.  It starts disappearing later in the session, when I never see the wait cursor again.  Since the wait cursor is the only animated cursor, could it be a problem with animating cursors?

---

### Post by Joseph Schwenker on 2009-08-20
I have found that the cursor does not disappear if I use Metacity, but oddly enough, when the cursor disappears and I switch back to Metacity from Compiz, the cursor is still disappearing.  Also, it takes some amount of time while in Compiz for the cursor to start disappearing.  After it disappears, I will have to start a new session.

---

### Post by Joseph Schwenker on 2009-08-24
Edit: I have been able to solve the problem by not using Compiz EVER in a session.  If I do not use Compiz, the problem does not exist.

---

### Post by philcamlin on 2009-08-24
> **Joseph Schwenker said:**
> Edit: I have been able to solve the problem by not using Compiz EVER in a session.  If I do not use Compiz, the problem does not exist.
well thats not very good at all but you have to do what you have to do 

maybe there are some mouse settings in compiz that screw it up ??

---

### Post by Joseph Schwenker on 2009-08-24
> **philcamlin said:**
> well thats not very good at all but you have to do what you have to do 

maybe there are some mouse settings in compiz that screw it up ??

At first I thought this, but I couldn't find any settings that would have done it.  The only things I use in compiz are Expo, Desktop Wall, and Scale, Invert, and Zoom.  I just installed Ubuntu on my main hard drive, so *maybe* it will not have the same troubles that my last install had.  Of course, I really hate the slow windows resizing in compiz, and that's why I prefer Metacity.

---

### Post by Joseph Schwenker on 2009-08-26
Oh dear, it has the EXACT SAME PROBLEMS as in my last Ubuntu install.  UGH!!!

---

### Post by Joseph Schwenker on 2009-09-08
Anyone have any idea what settings could be making the mouse cursor disappear, then make the same problem carry over from Compiz to Metacity in the same session?

---

### Post by andreibranescu on 2009-10-22
I have the same problem..

I think it's the zoom option in Compiz that messes up the mouse. Apparently it has to do with the hide option in the Enhanced zoom feature. 

In a different thread some people said that turning off zooming in Compiz and restarting the X server does the trick.

I just turned off the zoom option and the same thing happens. I'll try shutting down X server.

---

### Post by andreibranescu on 2009-10-22
I've found the solution, here, on Ubuntu forum.

It's in this thread [http://ubuntuforums.org/showthread.php?t=469891&page=2]("http://ubuntuforums.org/showthread.php?t=469891&page=2")

> The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described here [beryl-project.org]. Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not. This is also why the bug appears so random. It only occurs after the first usage of the zoom function.

The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in. The size of the cursor will now always stay the same, but it will also not disappear anymore.

---

