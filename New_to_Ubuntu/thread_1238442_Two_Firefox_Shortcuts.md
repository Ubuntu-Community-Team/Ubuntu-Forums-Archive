---
title: "Two Firefox Shortcuts?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by AxelMan0 on 2009-08-12
I recently updated my system and there were several Firefox updates. It updated Firefox 3.0 and also installed Firefox 3.5. Now there are two shortcuts to Firefox in my applications>internet menu. One says "Firefox" and one says "Firefox 3.0". Which one can I get rid of? Can I actually uninstall one of these rather than just deleting the link to it? I'd hate to have extra programs lost in my system floating around.

On a related note, is there a terminal command like apt-cache search that will list only the packages installed on my system?


Edit: Both shortcuts appear to open Firefox 3.5.2 but I'm not sure how to be certain of this (I just clicked on help and it briefly displayed 3.5.something in the url before redirecting me)

---

### Post by alexlafreniere on 2009-08-12
Try going into synaptic and searching for "firefox" and see what packages show up. If there's an outdated one uninstall that. Worst case scenario just uninstall and reinstall Firefox if only one package shows up.

---

### Post by lovinglinux on 2009-08-12
> **AxelMan0 said:**
> I recently updated my system and there were several Firefox updates. It updated Firefox 3.0 and also installed Firefox 3.5. Now there are two shortcuts to Firefox in my applications>internet menu. One says "Firefox" and one says "Firefox 3.0". Which one can I get rid of? Can I actually uninstall one of these rather than just deleting the link to it? I'd hate to have extra programs lost in my system floating around.

On a related note, is there a terminal command like apt-cache search that will list only the packages installed on my system?


Edit: Both shortcuts appear to open Firefox 3.5.2 but I'm not sure how to be certain of this (I just clicked on help and it briefly displayed 3.5.something in the url before redirecting me)

Is not recommended to uninstall Firefox 3.0, since it is the official package. It won't hurt your system to leave it there.

Instead of deleting the launcher, go to "System >> Preferences >> Main Menu", select the Internet tab and then untick one of them. It won't show in your menu anymore, but will remain there if you need it. Which one you should disable depends on which version you want to use and which file they are launching. Right-click on them, select Properties and copy what is in the **Command** field. Paste it here so we can tell you which one to disable.

---

### Post by oldfred on 2009-08-12
To list your packages:
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Note the comment about exporting sources also for any PPA's that you have added.

I tried this for my many times updated 32bit Ubuntu to my clean install of 64 bit Ubuntu. Of course some applications are not correct for the 64 bit and I had tons of old stuff still installed like python 2.4 and 2.5 when 2.6 is all I wanted. So bottom line it should only be used for current version to current version and reviewed to make sure the apps are what you still want.

---

### Post by AxelMan0 on 2009-08-12
Firefox launcher: firefox %u
Firefox 3.0 launcher: firefox-3.0 %u

I suppose I'll just leave it there until the official firefox 3.5 package is released--I'd rather not forget that it's there and have it floating around my computer until my next clean install. I read something about a 'transition phase' and I think this may be part of it. If it's not gone in a couple weeks then I'll remove it.

---

### Post by lovinglinux on 2009-08-12
> **AxelMan0 said:**
> Firefox launcher: firefox %u
Firefox 3.0 launcher: firefox-3.0 %u

I suppose I'll just leave it there until the official firefox 3.5 package is released--I'd rather not forget that it's there and have it floating around my computer until my next clean install. I read something about a 'transition phase' and I think this may be part of it. If it's not gone in a couple weeks then I'll remove it.

What version of Firefox launches when you hit the first launcher?

---

### Post by AxelMan0 on 2009-08-12
They are listed in order, I'm assuming 3.5.2 since the other one launches 3.0. 3.5 was marked as 'initial install' in the update manager and it was only afterwards that I had two firefox icons. I have no idea how to check for sure though.

---

