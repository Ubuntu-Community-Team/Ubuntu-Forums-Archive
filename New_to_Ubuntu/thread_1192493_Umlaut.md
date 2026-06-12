---
title: "Umlaut"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by demalan on 2009-06-20
How do I put two dots on an e? Or how do I put a ^ on an e or on an o? In any Windows application I have always typed alt-137 for two dots on an e, but in ubuntu it doesn't seem to work. Please help!

---

### Post by starcraft.man on 2009-06-20
Ah, you want language support. Go to System > Preferences > Keyboard then to the layouts tab. Once there you'll see the default language selected usually USA. Push add, then you can select language by country and national dialect. Once added, then you can go to layout options and pick a key combo to switch between them (it will highlight in bold in the menu). I usually use alt + caps.

That's it, enjoy. French Canada Legacy keyboard has all the accents you need I believe.

---

### Post by HotShotDJ on 2009-06-20
This is assuming a United States keyboard:

From the Gnome-Panel, go to System -> Preferences -> Keyboard.  Click on the Layouts tab.   Just below the "Selected Layouts" dialog, click on "Add."  Now, add the "USA International (with dead keys)" layout.  Verify that it has been added to the selected layouts dialog.  Go ahead and click "Close"

You'll want to add the keyboard indicator to your gnome-panel by right-clicking on the panel an selecting "add to panel."  Select "Keyboard Indicator."  You can now toggle between the two layouts.

To get an Umlaut (ä,ë,ï,ö,ü), toggle to the USA International keyboard.  Type Shift + " (double-quote key) and then the desired letter.  You can type Shift + ^ and then the desired letter to get, for example, ê.  Other options will give you é, è, ç, Ç, etc..

---

### Post by tea for one on 2009-06-20
> **demalan said:**
> How do I put two dots on an e? Or how do I put a ^ on an e or on an o? In any Windows application I have always typed alt-137 for two tots on an e, but in ubuntu it doesn't seem to work. Please help!
You may also wish to explore this utility:-

Applications > Accessories > Character Map

---

### Post by Veteropinguis on 2009-07-02
I'm using the US-International layout with dead keys, and I can't figure out how to get a lowercase letter with an umlaut.

My dead key is the Windows key.

Win+shift+"+e gets me Ë, but win+"+e gets me é. Win+;+e gets me &#281;. Win+ '+' +e gets me €. I can get just about every character I want except a lower-case 'e' with an umlaut.

What am I doing wrong?

---

### Post by Veteropinguis on 2009-07-04
Bump.

---

### Post by CatKiller on 2009-07-04
> **Veteropinguis said:**
> What am I doing wrong?

You're holding the Shift key too long. I suspect that what you're doing is holding Shift for the whole thing, meaning that you're actually doing

Shift-Compose, Shift-2, Shift-E, giving you a capital E.

What you want to do is

Compose, Shift-2, e, giving you a lower-case e.

EDIT: Just noticed you're using US keyboard layout, so switch Shift-2 for whatever combination gets you a " character.

---

### Post by HotShotDJ on 2009-07-04
> **Veteropinguis said:**
> I'm using the US-International layout with dead keys, and I can't figure out how to get a lowercase letter with an umlaut.

My dead key is the Windows key.


What am I doing wrong?No.. your dead key is not the Windows key.  I'm not quite certain what your talking about with that.  The "dead" keys are things like the ', `, ", ~. etc.  When you try to type those characters alone, you should get nothing.  However, if you press the "space" key after one of them, it will then appear.  If you type a " and then the lower case e, you will get ë.

Please see: [http://en.wikipedia.org/wiki/Dead_key](http://en.wikipedia.org/wiki/Dead_key)

EDIT:  Ok... Now I know you were talking about regarding using the Windows key as a "dead" key.  Using it that way is normally called a "Compose Key."  Sorry for my confusion.

---

### Post by Jonno303 on 2013-04-16
I'm having difficulty in using dead keys with different programs. For example, here using Chrome, I can use regular dead keys to create Ü = shift + " and then U. 

However using Everpad, my dead keys are jumbled and it doesn't seem to register the shift + function. The same formula to create Ü does not work, and results in:  ¨U. 

Does anyone have a fix for this?

---

### Post by overdrank on 2013-04-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

