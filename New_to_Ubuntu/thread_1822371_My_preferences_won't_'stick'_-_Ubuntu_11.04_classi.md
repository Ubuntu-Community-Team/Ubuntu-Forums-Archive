---
title: "My preferences won't 'stick' - Ubuntu 11.04 classic dsktop"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by DrVladimirtzu on 2011-08-10
Various preferences I set will not stick.  The first one I noticed is my browser preference.  I have chrominium set as the default under Preferred Applications, but every time I open it, it prompts me to set it as the default.  I then proceed to do so from within chrominium, but its the same next time I open the browser.  Its only frustrating because if I click on a link from an instant message or something, and there's no browser open, it won't automatically open chrome.

The second thing I noticed was under keyboard shortcuts.  "Move Between Panels and the Desktop, using a popup window" which allows you to switch between windows in different workspaces was set to "ctrl alt tab."  I changed it to "ctrl tab"  But that won't take effect either.  Even more puzzling is that the original keyboard shortcut "ctrl alt tab" still works.  I double checked, and there are no shortcuts set for "ctrl alt tab" now that its been changed.

I also closed the keyboard shorcuts and reopened it to make sure the changes I made still showed, and they do.  They just will not take effect.

---

### Post by amjjawad on 2011-08-10
Hello and Welcome :)

I'm not exactly sure how to fix that but will do my best.

How did you install Ubuntu?

Do you still have Firefox? when you open any link, does Firefox ever start? or it's just Chromium?

What about themes, background, etc? can you change that without problems?

I'm trying to search for similar issues.

[www.googlubuntu.com](www.googlubuntu.com)

---

### Post by DrVladimirtzu on 2011-08-10
> **amjjawad said:**
> Hello and Welcome :)

I'm not exactly sure how to fix that but will do my best.

How did you install Ubuntu?

Do you still have Firefox? when you open any link, does Firefox ever start? or it's just Chromium?

What about themes, background, etc? can you change that without problems?

I'm trying to search for similar issues.

[www.googlubuntu.com](www.googlubuntu.com)

I sure do appreciate it.  I installed from a burnt disc, just recently.  Themes and background change just fine.  The only preference problems so far have been with chrome and that keyboard shortcut I wanted to set.

I actually uninstalled firefox to keep links from opening in it, so yes they were.  

And like I say, even after a restart, the changed preferences of mine do show up under the preferences.  They're just not 'in action' I guess. o.O

---

### Post by amjjawad on 2011-08-10
I'm searching for the browser issue and I found this:

[http://ubuntuforums.org/showthread.php?t=1793496](http://ubuntuforums.org/showthread.php?t=1793496)

---

### Post by amjjawad on 2011-08-10
Also found a bug report but the case is a bit different than yours.

I found this if the other link didn't work: [http://askubuntu.com/questions/16621/how-to-set-the-default-browser-from-the-command-line](http://askubuntu.com/questions/16621/how-to-set-the-default-browser-from-the-command-line)

---

### Post by DrVladimirtzu on 2011-08-10
Alright, this is bizarre.  I tried solution 1 to no avail.  I even uninstalled and reinstalled chrominium.  Then I tried solution 2, editing it from the command line.

I noticed that firefox had been reinstalled.  Maybe the Ubuntu software center automatically installs firefox if it notices you have no web browser?  At any rate, I set chrominium as the default browser from there...

Still no cookie.  So I close down chrome, and I try to open a link from an IM window again.  This time it opens up with firefox, and when I went to the preferences firefox NOW was listed as the default browser.  I switched it to chrominium, and now it works.

While I'm glad to have chrome working like I want it now, I can't help but suspect something very strange is going on with this install.  I may burn a disc for the last LTS and reinstall since I don't have much work on here to bother backing up yet.

---

### Post by DrVladimirtzu on 2011-08-10
Nevermind on this post.

---

### Post by amjjawad on 2011-08-10
> **DrVladimirtzu said:**
> I noticed that firefox had been reinstalled.
As if it has been already removed. Perhaps you didn't remove it completely.

> Maybe the Ubuntu software center automatically installs firefox if it  notices you have no web browser?
NO WAY.

> While I'm glad to have chrome working like I want it now, I can't help but suspect something very strange is going on with this install.  I may burn a disc for the last LTS and reinstall since I don't have much work on here to bother backing up yet.

Well, good to know it works the way you want but I suggest to wait for a while and keep checking. If the same issue will occur again, go ahead with formatting and re-installing.

Google Chrome/Chromium gave me HARD TIME months ago and I have did ALL the possible solutions then nothing happened. Problem Solved when Google updated and released version 11.

[http://ubuntuforums.org/showthread.php?t=1612922](http://ubuntuforums.org/showthread.php?t=1612922)

What version do you have by the way?


If you don't like Firefox, keep it as a backup browser, don't remove it. Just a suggestion.

---

### Post by DrVladimirtzu on 2011-08-10
> **amjjawad said:**
> As if it has been already removed. Perhaps you didn't remove it completely.


NO WAY.



Well, good to know it works the way you want but I suggest to wait for a while and keep checking. If the same issue will occur again, go ahead with formatting and re-installing.

Google Chrome/Chromium gave me HARD TIME months ago and I have did ALL the possible solutions then nothing happened. Problem Solved when Google updated and released version 11.

[http://ubuntuforums.org/showthread.php?t=1612922](http://ubuntuforums.org/showthread.php?t=1612922)

What version do you have by the way?


If you don't like Firefox, keep it as a backup browser, don't remove it. Just a suggestion.

Well, I know it was as uninstalled as uninstalling it from the software center uninstalls it. =P   I'm using 12.something on chrome, and Ubuntu 11.04.  If I can't get to the bottom of the keyboard shortcut problem, or if chrome gets un-defaulted again, yeah, I'm gonna go for a new install.

---

### Post by DrVladimirtzu on 2011-08-10
Oh, and thanks a lot for the help, man. ^.^

---

### Post by amjjawad on 2011-08-10
> **DrVladimirtzu said:**
> Well, I know it was as uninstalled as uninstalling it from the software center uninstalls it. =P   I'm using 12.something on chrome, and Ubuntu 11.04.  If I can't get to the bottom of the keyboard shortcut problem, or if chrome gets un-defaulted again, yeah, I'm gonna go for a new install.

I don't like the Software Center, I always use Synaptic or The Terminal. I prefer The Terminal to be honest. New Users don't like it because it's new to them but once they try it for few times, they will love it.

Version 12? I think the latest is 13.
Is it Chrome or Chromium?

As for the Keyboard Shortcuts, I need to search for that too but that might take some time as I'm a bit busy now :)

You most welcome :)
Glad to help you!

---

### Post by DrVladimirtzu on 2011-08-10
Chromium.  I like working from the terminal as well.  I just bought a new computer though after going 2 years without one, so I'm just focusing on the user experience at first while reading through Oreilly's book on Ubuntu. 

I'll get to playing around under the hood soon enough.

---

### Post by DrVladimirtzu on 2011-08-10
My younger brother's smart as a whip girlfriend asked if it was possible the automatic updates would reinstall firefox if there was an update to it.  Think that could've been what put firefox back on there?

---

