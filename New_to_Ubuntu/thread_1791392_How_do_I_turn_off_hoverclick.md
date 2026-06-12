---
title: "How do I turn off hoverclick?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by john wagner on 2011-06-26
At least that's I call it.  I just installed 7.10 on my laptop and the darn touchpad is activating windows all over the place.  I hate that!  How do I go into the terminal to shut that function off.  Any window that opens, I want to manually do it!
I tried the 7.10 help, went in to terminal and did what it claimed, but it didn't work.
Also, what's up with the repositories?  I cannot download/activate acess to ANY of them...

---

### Post by wolfen69 on 2011-06-26
Ubuntu 7.10 is 4 years old and no longer supported. That's why you're not getting updates. 7 versions of ubuntu have come out since then. Maybe you should try a newer version. 10.04 is good if you like the classic ubuntu look and feel, and supported for 2 more years.

---

### Post by nzjethro on 2011-06-26
Are you referring to the "tap-to-click" feature?

You could add
> Option	 "MaxTapMove"	"0"
to your xorg.conf.

Or else I've read that gsynaptics can resolve the issue. Not sure if these will work on Gutsy Gibbon though...

---

### Post by john wagner on 2011-06-26
> **wolfen69 said:**
> Ubuntu 7.10 is 4 years old and no longer supported. That's why you're not getting updates. 7 versions of ubuntu have come out since then. Maybe you should try a newer version. 10.04 is good if you like the classic ubuntu look and feel, and supported for 2 more years.

Yeah.  I went to 10.04 (dislike the look of 11.04).  Now I have repositories, but gsynaptic doesn't deactivate point to click.  More help please!

---

### Post by nzjethro on 2011-06-26
Is this Ubuntu rather than {X,K,Ed,etc}ubuntu? There should be an option in System > Preferences > Mouse > Touchpad to disable the touchpad when typing.

If that option isn't there on 10.04, or if it doesn't work, [this thread ]("http://ubuntuforums.org/showthread.php?t=1469754")has a user script that disables tap-to-click, which could be set to autorun at startup. The thread is for Xfce, but I imagine it would work on Ubuntu too.

---

### Post by john wagner on 2011-06-26
> **nzjethro said:**
> Is this Ubuntu rather than {X,K,Ed,etc}ubuntu? There should be an option in System > Preferences > Mouse > Touchpad to disable the touchpad when typing.

If that option isn't there on 10.04, or if it doesn't work, [this thread ]("http://ubuntuforums.org/showthread.php?t=1469754")has a user script that disables tap-to-click, which could be set to autorun at startup. The thread is for Xfce, but I imagine it would work on Ubuntu too.

Nope.  Not there in >mouse>touchpad.

What I'm trying to kill is the AUTOMATIC selection of whatever the pointer/cursor is on.  I want to manualy 'click' to open/activate any/all windows.  I hate the pointer doing it all by itself.
I installed gsynaptics, no control over this issue.  Anything to add to the terminal?

---

### Post by john wagner on 2011-06-26
Anyone?  Gotta kill the automatic pointer/cursor select.  Need to go manual only.  Do I go into the terminal?  what do I change?

---

### Post by nzjethro on 2011-06-26
Perhaps I misunderstood your problem. Is it that the cursor is automatically selecting things without any input from you (i.e. without brushing the touchpad), on is it that when you are, for example typing, you are accidentally brushing the touchpad and invoking the tap-to-click feature, which is selecting a different textbox or window?

---

### Post by Bizko1288 on 2011-06-26
on mine (11.04)  I click the top right button, system settings>hardware>mouse>touchpad

and i can toggle off touchpad clicking from there.

---

### Post by john wagner on 2011-06-26
> **Bizko1288 said:**
> on mine (11.04)  I click the top right button, system settings>hardware>mouse>touchpad

and i can toggle off touchpad clicking from there.

Thanks everyone, I guess I'm a tad slow today...  I went into synaptics>touchpad and was able to kill it.  Go to second tab, "tapping", and turn off "enable tapping".

I thought by turning it off it would kill my two buttons.  Nope, it just kills the automatic function.  Thank you everyone for trying to pound it into my thick skull!

---

### Post by nzjethro on 2011-06-26
Cool, glad you found a nice simple fix. :D

---

