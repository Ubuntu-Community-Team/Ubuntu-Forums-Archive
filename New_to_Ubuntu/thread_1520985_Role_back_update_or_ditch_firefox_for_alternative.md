---
title: "Role back update or ditch firefox for alternative?"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by antmenj on 2010-06-30
A new firefox came down as an update and now it seems very heavy, clunky and slow.  I did a 'top' and it was up to 43% cpu just siting there.
I'm typing this form a fresh install with no updates on another machine and this one uses about 8% cpu.

Can I get back the old one, lighten up the new one or alternatively do I look for something else?

I do like firefox's add ons and I normally change about:config as soon as I set up a machine so I'd like those features or similar.

I do not want chrome.

Still using hardy in the above cases.

---

### Post by bruno9779 on 2010-06-30
The last FF updates have borked it for me too.

Not really performance wise, but some php based webgames I play (eg. Cantr) have stopped working properly.

I use chrome from time to time, especially for html5 tests and flash content, but I am really expectant to hear some release news from Wildfox.

[http://wildfox.sourceforge.net/](http://wildfox.sourceforge.net/)

---

### Post by Noz3001 on 2010-06-30
I use Chromium nightly. Smooth, fast and more importantly, it works.

---

### Post by ankspo71 on 2010-06-30
> **antmenj said:**
> 
I do like firefox's add ons and I normally change about:config as soon as I set up a machine so I'd like those features or similar.
I do not want chrome.

I have been hearing good things about Swiftfox (current version is 3.6.3.) It is an optimized version of firefox.

Also, you should still have your older firefox package files located in /var/cache/apt/archives/*. Once you get the older firefox reinstalled you could "pin" it so it won't get future updates. I believe the command to pin the current version of a package is: ```
sudo -s
echo packagename hold | dpkg --set-selections
```
(replace packagename with firefox or firefox-3.5 etc)
More info on pinning packages:
[https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages](https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages)
Hope that helps.

---

### Post by lovinglinux on 2010-06-30
I not using Firefox from the repositories, but it seems this update is not working for some other users as well.

I would recommend creating a new user profile in Firefox. See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

### Post by Metrop021 on 2010-06-30
I'd recommend chromium, runs really well.

---

### Post by lovinglinux on 2010-06-30
Please read the OP post, it says "I do not want chrome."

BTW, it seems FF 3.6.6 from the repositories had a few issues this morning that have been fixed. So I would recommend updating again, to make sure you have the latest patch.

I also recommend reading my tutorials on Firefox performance and optimization. I have more than 50 extensions installed and it works like charm. Chrome?...no thanks.

---

### Post by antmenj on 2010-06-30
Yep a firefox update is there.  Updating now.  We will see if that fixes anything for a start.  I think I'll have a look at these firefox related browsers too.

> **lovinglinux said:**
> Please read the OP post, it says "I do not want chrome."

BTW, it seems FF 3.6.6 from the repositories had a few issues this morning that have been fixed. So I would recommend updating again, to make sure you have the latest patch.

[COLOR="Blue"]I also recommend reading my tutorials on Firefox performance and optimization.[/COLOR] I have more than 50 extensions installed and it works like charm. Chrome?...no thanks.

Will take a look at those too.

---

### Post by antmenj on 2010-06-30
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=162005&stc=1&d=1277940660[/IMG]

Oh now thats great :roll:

---

### Post by lovinglinux on 2010-06-30
> **antmenj said:**
> [IMG]http://ubuntuforums.org/attachment.php?attachmentid=162005&stc=1&d=1277940660[/IMG]

Oh now thats great :roll:

Just update the icon. /usr/share/pixmaps/firefox

---

### Post by antmenj on 2010-06-30
Or remove from panel then drag it from the applications internet menu:p

It seem this update now has it using between 2.5 - 4.5% CPU when at rest so I'll hope its fixed and will let the new install update on the other machine.

Fingers crossed:lolflag:

Thanks for the help BTW

---

### Post by antmenj on 2010-06-30
This fixed another distasteful feature in the update.  The spell check M$ looking squiggly line.

[http://support.mozilla.com/en-US/forum/1/631766]("http://support.mozilla.com/en-US/forum/1/631766"):guitar:

Restore the lost properties menu:

[https://addons.mozilla.org/en-US/firefox/addon/14228/]("https://addons.mozilla.org/en-US/firefox/addon/14228/")

---

