---
title: "Weird font problem in Firefox"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by JoeBrooks on 2011-06-13
Sorry if this has been addressed before--I wasn't sure what to search for.

It looks like I installed a font in Ubuntu and now Firefox is using it on certain sites, even though I never changed any font settings in Firefox.  How do I fix this?

---

### Post by jtarin on 2011-06-13
Firefox>Options>Content>Fonts&Colors>Advanced(button)

---

### Post by JoeBrooks on 2011-06-14
Those are all still set to the defaults, which is why it's weird.

---

### Post by jtarin on 2011-06-14
Post a pic showing what you mean.

---

### Post by JoeBrooks on 2011-06-14
Here's a Community Docs page displaying the wrong font (it's this ultra-thin Helvetica-style font):

[[IMG]http://i.imgur.com/49Dqjm.png[/IMG]]("http://i.imgur.com/49Dqj.png")

And a shot of these forums displaying a normal font for comparison:

[[img]http://i.imgur.com/tpqIMm.png[/img]](http://i.imgur.com/tpqIM.png)

And my font preferences:

[[img]http://i.imgur.com/ZQ7jBm.png[/img]](http://i.imgur.com/ZQ7jB.png)

I don't understand how this happened.

---

### Post by jtarin on 2011-06-14
Do you have the MSttf installed? Does unchecking the box "Allow pages to choose their own fonts........." do anything?

---

### Post by papibe on 2011-06-14
I have a similar problem. It started after today's updates:
```
Upgraded the following packages:

apt (0.7.25.3ubuntu9.4) to 0.7.25.3ubuntu9.5
apt-transport-https (0.7.25.3ubuntu9.4) to 0.7.25.3ubuntu9.5
apt-utils (0.7.25.3ubuntu9.4) to 0.7.25.3ubuntu9.5
gimp (2.6.8-2ubuntu1.2) to 2.6.8-2ubuntu1.3
gimp-data (2.6.8-2ubuntu1.2) to 2.6.8-2ubuntu1.3
google-talkplugin (2.0.6.0-1) to 2.1.6.0-1
libgimp2.0 (2.6.8-2ubuntu1.2) to 2.6.8-2ubuntu1.3
libmodplug0c2 (1:0.8.7-1build1) to 1:0.8.7-1ubuntu0.2
```
If I disable the "Allow pages..." check box it gets worst (more ugly, far different rendering than FF in Windows).

Any idea?

Thanks in advance.

---

### Post by jtarin on 2011-06-14
Here's a [link]("https://wiki.ubuntu.com/Fonts") on fonts in Ubuntu. Skip down past installing fonts to configuring after installation. There might be something there that would be helpful. 
Do you have more than one user on your computer....one with a different Firefox profile? If yes check that one and see if it is having the same problems....[if not maybe create a new profile to test Firefox.]("http://kb.mozillazine.org/Profile_manager") If you decide to delete an old profile backup your bookmarks.

---

### Post by JoeBrooks on 2011-06-17
Thanks jtarin, but nothing in that link pertains to the problem.  I checked and found the msttfcorefonts is installed, and unchecking "Allow pages to choose their own fonts" just makes every page use the default font.  I also only have one user on my computer.

I'm not even sure what this font in question is called, and I'd rather not go through and un-install a bunch of my best guesses to find out.  How did this even happen?

---

### Post by jtarin on 2011-06-17
> **JoeBrooks said:**
> Thanks jtarin, but nothing in that link pertains to the problem.  I checked and found the msttfcorefonts is installed, and unchecking "Allow pages to choose their own fonts" just makes every page use the default font.  I also only have one user on my computer.

I'm not even sure what this font in question is called, and I'd rather not go through and un-install a bunch of my best guesses to find out.  How did this even happen?Don't delete anything, just create a new Firefox profile and see if it is your existing profile in Firefox causing the problems.[Go here and scroll down for Linux directions. ]("http://improvefirefox.com/multiple-firefox-profiles/")

---

