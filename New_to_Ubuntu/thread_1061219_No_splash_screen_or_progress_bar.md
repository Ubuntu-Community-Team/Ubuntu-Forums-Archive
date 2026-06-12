---
title: "No splash screen or progress bar"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Don1500 on 2009-02-05
This is just something I am curious about, not a real problem. 
I have Ubuntu 8.04 installed (Dual Boot) on my desk top PC and on my laptop. 

On the laptop everything works fine, boot goes to menu.lst and selection works, then the Black screen with UBUNTU and the progress bar. On the desk top everything works except I don't get the black screen with Ubuntu and progress bar. 

In both systems Ubuntu works fine, no problems, solid as a rock.

I'm wondering if there is a set up option that I didn't enable for that screen.

---

### Post by gettinoriginal on 2009-02-05
What do you get on the desktop?  Is it a text boot?

---

### Post by sdennie on 2009-02-05
With Hardy, using a kernel later than 2.6.26 (or maybe 2.6.27, I can't remember), makes the usplash program segfault no matter what I've tried.  If you are using the stock kernel, have you re-partitioned since installation?  A change in the UUID of the swap partition can cause this problem.  This post describes how to fix that problem: [http://ubuntuforums.org/showpost.php?p=4891382&postcount=11](http://ubuntuforums.org/showpost.php?p=4891382&postcount=11)

---

### Post by Don1500 on 2009-02-06
first I get a blank screen, in fact it has no output from the computer to the monitor because the "No Signal" notice is displayed. Then I get a blank screen with the default background color and the "loading cursor" (the mouse cursor with a little circle going around). I can tell that the screen resolution is incorrect because the cursor is an oval, not round. Then the welcome sound, then the normal back ground.

I do not get a text opening. Well, except for every 35 loads, then it does it's disk check thing. (Any way to stop that?)

---

### Post by Don1500 on 2009-02-07
OK, so, in MENU.LST I had "Quiet Splash" on the loader. But now all get is a text boot. Oh, well, step 2.

---

