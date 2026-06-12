---
title: "how to put the icons on the right"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-04-29
so, I just upgraded, Its annoying, how do I fix it....

---

### Post by ubunterooster on 2010-04-29
Change the theme.
System>preferences>appearance.
You really could have just done a search on this.

Other ways are described [here]("http://ubuntuforums.org/showthread.php?t=1464127")

---

### Post by LunaticHiatus on 2010-04-29
ah, I switched the theme a couple times and ironically all the ones I picked also put them on the left... so... yeah... I'm an idiot.

---

### Post by Geoff918 on 2010-04-29
You can easily move the buttons to the left:

1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

menu:minimize,maximize,close

There, you're back to the "old, familiar style"

---

### Post by Brandel Valico on 2010-04-29
If your talking about the buttons Well go here.

[http://ubuntuforums.org/showthread.php?t=1430585&page=3](http://ubuntuforums.org/showthread.php?t=1430585&page=3)

If something else sorry it's not more help

---

### Post by UnknownFear on 2010-04-29
> **Geoff918 said:**
> You can easily move the buttons to the left:

1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

menu:minimize,maximize,close

Ah, that did it for me. Thanks :)

---

### Post by djchandler on 2010-04-29
> **Geoff918 said:**
> You can easily move the buttons to the left:

1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

menu:minimize,maximize,close

There, you're back to the "old, familiar style"
Until the user switches the theme back to Ambiance or Radiance meta-theme again--then they are frustratingly back to the left. The button placement key is overridden by the theme's description currently.

To avoid frustration, use System>Appearance>Themes>Customize after selecting a them with buttons on the right. Make sure you save your meta-theme with a unique name.

There will be a sticky on this soon. The  System>Appearance>Themes>Customize method is what is being advocated from the top.

---

### Post by docshawnc on 2010-05-02
Thank you - I just installed lucid and thought I was going crazy:)

---

### Post by freesitebuilder on 2010-05-02
I did read that they've been moved to make room for something else in a future release ... if I could only remember where I read it ...

---

### Post by freesitebuilder on 2010-05-05
Some of the pre-installed themes still have the icons on the right. Now that *is* confusing!

---

### Post by ubunterooster on 2010-05-05
I think "clearlooks" (default for 9.10) is still oriented to the right.

It is to prepare for "the radical changes in 10.10." Is there a name yet or shall I continue to call it "Mad Man"?

---

### Post by philinux on 2010-05-05
See the sticky in General Help forum re lucid.

---

### Post by ubunterooster on 2010-05-05
Ah, this one:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by howefield on 2010-05-05
> **freesitebuilder said:**
> I did read that they've been moved to make room for something else in a future release ... if I could only remember where I read it ...

Some ideas being described here..

[http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

---

