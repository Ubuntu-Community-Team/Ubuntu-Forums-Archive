---
title: "Firefox Image Link Underlines"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by nmcgrew on 2010-01-17
Just recently and I don't know why, but my Firefox is underlining random image links.  It's not consistent in that one linked image may show underlines and the one next to it might not.  Some text links are also being underlined but I haven't noticed it quite as much as in the image links.  And that too isn't consistent.  A text link may show an underline and then two links beneath it, another is not.  It's very obnoxious and unsightly and annoying.  I've tried uninstalling FF and reinstalling and that did nothing.  I've doublechecked my FF preferences to be sure the option for underline links is off.  And again, it just started happening.  I think when my system prompted me to upgrade from jaunty to karmic actually is when it started happening.  Is that possible?  Brand new to Ubuntu.  Any ideas how to fix this issue?  Thanks!

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20100106 Ubuntu/9.10 (karmic) Firefox/3.5.7

---

### Post by JackRock on 2010-01-17
Can you link to an example where you see this? Some sites code it so that certain links are not underlined.

---

### Post by nmcgrew on 2010-01-17
> **JackRock said:**
> Can you link to an example where you see this? Some sites code it so that certain links are not underlined.


I could but you won't see the lines.  I have windows xp on my laptop using ff there as well and the websites [which btw are my own :) ] do not have any issues with links or underlining.  I also installed a different browser [seamonkey ... i never heard of that!] on my desktop running Ubuntu to be sure before I started posting for help and it showed the websites fine too.  I wanted to know if it was my computer or the browser.  So by process of elimination, I am certain it is FF and given that it's fine on the laptop, it's either a Ubuntu conflict or the Linux version of FF that I'm using.  Worth noting though maybe is that this problem is new and only started after my system updates prompted me to upgrade to karmic.

---

### Post by lidex on 2010-01-17
Try starting Firefox with a new profile. If it works OK then you can import what you need from your old profile.

Close all instances of firefox
Alt+F2 run dialog 
Enter code:
```
firefox -profilemanager
```

---

### Post by lidex on 2010-01-17
Firefox help:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

Profiles:
[http://kb.mozillazine.org/Profile_Manager]("http://kb.mozillazine.org/Profile_Manager")
and here:
[http://support.mozilla.com/en-US/kb/Profiles]("http://support.mozilla.com/en-US/kb/Profiles")

---

### Post by nmcgrew on 2010-01-17
> **lidex said:**
> Try starting Firefox with a new profile. If it works OK then you can import what you need from your old profile.

Close all instances of firefox
Alt+F2 run dialog 
Enter code:
```
firefox -profilemanager
```

Genius!  Thank you, it worked like a charm.  
And... thanks for the FF links.  Bookmarked!

---

### Post by nmcgrew on 2010-01-17
> **nmcgrew said:**
> Genius!  Thank you, it worked like a charm.  
And... thanks for the FF links.  Bookmarked!

Oh fudge.  I ONLY thought it worked.  And it did for one browsing session.  Then after starting a new firefox window, same old problem.  I think FF needs to update and since I'm using the Ubuntu version, I have to wait until the next upgrade release of Ubuntu to upgrade my FF don't I?  I'm not sure I like that very much.  Can I go back to an earlier version of FF somehow?

---

### Post by lidex on 2010-01-17
It must have restarted with the old profile. You'll need to move it and, to be safe, rename it. Then when you start firefox it will create a new profile. Use the links provided to import the data you need from the old profile and reinstall any extensions afresh, one at a time, in case they were causing the issue.

Your profile should be located here:
"/home/your_username/.mozilla/xxxxxxxx.default"
and it's a folder. Rename it by adding ".old" after ".default" and move it somewhere safe. Make sure Firefox is closed while you do this.

---

