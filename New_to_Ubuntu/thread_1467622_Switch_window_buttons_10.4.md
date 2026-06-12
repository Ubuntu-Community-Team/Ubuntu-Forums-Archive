---
title: "Switch window buttons 10.4"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by JigglyWiggly_ on 2010-04-30
How do I switch the buttons to the right again? I have used gnome for like forever, and now they switch them for no reason.

Any ideas how to get the proper way back?
(To the right, and in the right order?)

---

### Post by nhasian on 2010-04-30
alt-F2 and enter the command gconf-editor

then in apps-> metacity-> general set the button_layout to say
menu:minimize,maximize,close

---

### Post by wojox on 2010-04-30
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

Or just change themes.

---

### Post by The Thunder Chimp on 2010-04-30
Changing themes doesn't work all the time, the first way is not much harder, but really more efficient.

---

### Post by JigglyWiggly_ on 2010-04-30
Thanks bros, worked like a charm.

Easy fix, but I would assume there should just be a button for:

"FIX THIS ****" in the appearance tab.

---

### Post by Sealbhach on 2010-04-30
> **JigglyWiggly_ said:**
> Thanks bros, worked like a charm.

Easy fix, but I would assume there should just be a button for:

"FIX THIS ****" in the appearance tab.

It's not something that's broken, it was a design decision.

.

---

### Post by JigglyWiggly_ on 2010-04-30
I realize it's not broken, I am saying it's the stupidest design choice ever.

---

### Post by The Thunder Chimp on 2010-04-30
> **JigglyWiggly_ said:**
> I realize it's not broken, I am saying it's the stupidest design choice ever.

Hahaha, word.

It's true they should have the option though. I really easy option, these is so common in these forums. I remember posting the same question about 2 months ago in the Beta 1 release :lolflag:

---

### Post by nhasian on 2010-05-01
i think its a poor choice as well.  the (x) button to close is always on the right side.  in programs, firefox tabs, even pop-up advertisements.  now i have to go against my first instict and move the mouse cursor all the way to the top left to close a window.  :confused:

skip that.  the first thing i do is move it back to the right with the instructions from my previous post.  i've done it so many times now i know it by memory.

I understand that possibly as early as Ubuntu 10.10 they will use the top-right window area for something new and intuitive.  if that is the case, couldnt they have just added this new feature the to the top-left of a window and left our widgets alone?

---

### Post by JRHA on 2010-05-01
Absolutely terrible terrible awful decision, if you're going to move something to make it more intuitive, you better put that new shiny better thing in. Now we're left with something completely unintuitive which forces all loyal users to either un-learn years and years of muscle memory or fight with the completely user-unfriendly gconf editors.

This is probably the first thing Ubuntu has done that's given me the same rising anger and frustration I usually associate with trying to anything productive with Windows.

Forcing users to edit gconf to fix this is like expecting Windows users to edit the registry without a) breaking everything in sight or b) snapping and killing themselves or everyone around them.

I had naively thought that an option would be provided in the "Appearance" or "Windows" configuration dialogues to put the buttons back, but I should have learnt from the xsplash/gdm mess in 9.04 that "Canonical knows better/doesn't care". Obviously user-friendly customisation isn't a priority.

These releases are starting to feel increasingly rushed and rough around the edges.

I am definitely Mr Grumpy Face today.

---

### Post by RyanBFS on 2010-05-01
My first instinct upon logging into 10.4 was right in line with you guys.  But I've changed my mind a bit.  Firstly it's way worth the trouble if it will help entice some of the "windows alternative" crowd over from Apple, it's good for the community, and gives push to the "make it work on linux" chant that gets ignored so often.  Secondly adding an option for everything sounds like a good idea, but remember why many of us went to linux in the first place... Bloat.  Maybe somebody could work something into the repos for synaptic as a fix.  That way first timers are getting an idea of the integration power available in software packages, and were not adding yet another core button.  

But I feel ya, it's taken me all day to get used to it.  Maybe whatever is going on the right will be something that they don't want overlooked.  I can honestly say that I had a theme that gave me an option on the left and I didn't notice it for over a week.

---

### Post by Sealbhach on 2010-05-01
I never use the default themes anyway, so it doesn't affect me.

.

---

### Post by smartroad on 2010-05-09
Thanks for that. Its funny how such a little thing almost turned me off of using Ubuntu. I don't WANT to have to re-learn how to use such a simple thing that I have been doing for the last 20 years! Especially when there is not logical or apparent reason for doing so (rumours of a magical 'intuitive' new thing notwithstanding). And then not to have the easy option to put it back reeks of the Apple "we know what is best for you" rubbish.

Sorry rant over LOL

---

### Post by r-senior on 2010-05-09
Nobody is forced to use gconf-editor, in fact this is not the recommended solution:

From [http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")

> Minimize, Maximize and Close button placement.
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
[[Update ]http://www.markshuttleworth.com/archives/333

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.

1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.

[COLOR="Red"]Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders. Unfortunately, if the wrong approach spreads, they won't be able to do that[/COLOR].

---

