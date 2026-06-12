---
title: "Can't &quot;X&quot; out of Firefox"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-04-09
Based on a workaround suggestion in a launchpad, I deleted the "localstore.rdf files in my /home/ricardo/.mozilla/firefox/xxxdefault folders. This did indeed take care of the bug problem I was experiencing (and I should mention it did so without any consequence on my wife's account on the same machine, as well as on my work comp.)

However, I can no longer "X" out of Firefox; I can't just click on the "Close Window" X in the upper right-hand corner of FF. I can only select File >> Quit from the FF menu. This means that I also cannot close many of the popups that show up regularly, at least not without shutting down FF entirely, since most of these do not have a menu pallet, only the "X".

Any idea how to diagnose and fix this? Thanks.

---

### Post by Jakey_TheSnake on 2009-04-09
What happens when you do click on it? Nothing? Does the button do the standard things (graphically) as when you press it on any other windows? 

Anyways, as a temp. fix you can just press Ctrl + W ;) (or it may be ctrl + shift + W for you)

---

### Post by ricardisimo on 2009-04-09
It highlights when I mouseover, and darkens when I depress it, just like always. I ran FF from a terminal, to see if some input was getting through, but nothing.

Normally, of course, at the very least I would get some version of "This program is not responding... wait or force quit?" No longer. I have also tried a complete removal and re-installation via synaptic, to no avail.

---

### Post by hesjnet on 2009-04-09
It's not a solution but you can also use ALT + F4 to close windows

---

### Post by Jakey_TheSnake on 2009-04-09
Try uninstalling, deleting your ~/.mozilla/ folder, and then installing again using the terminal:

```
sudo apt-get install firefox
```

---

### Post by ricardisimo on 2009-04-09
I'd like to avoid losing all of my saved passwords, bookmarks, etc. Any other suggestions? I think it might be a moot point, if as I suspect I wind up doing a fresh install of jaunty in two weeks. We'll see.

---

### Post by ricardisimo on 2009-04-09
Has anyone else had this problem?

---

### Post by lisati on 2009-04-09
For saving bookmarks I'd suggest using the xmarks add-on (it used to be foxmarks). I think the latest version can save passwords too.

---

### Post by ricardisimo on 2009-04-09
So, you're saying there's no other way than to delete my Mozilla folder?

---

### Post by the.phantom on 2009-04-09
just for info

you can save the bookmarks by clicking the "bookmarks" in the top of ff
then "organize bookmarks
then "import or backup "

now on your saved passwords
go to 
edit ( in ff)
preferences


security
saved passwords
click "show passwords
make the screen full page

hit "print screen" and save the image to your desktop[ !
that way you have your bookmarks and passwords saved
and good insurance for any type of accident

---

### Post by HereInOz on 2009-04-09
Even if you upgrade to Jaunty, if you leave the /home directory intact, you will still have the problem.  The problem is not with the install of Firefox; rather it is in your profile, which is in /home/ricardo/.mozilla   

So, yes, I think you are going to have to delete that folder and start with a new profile.

---

### Post by ricardisimo on 2009-04-09
> **HereInOz said:**
> Even if you upgrade to Jaunty, if you leave the /home directory intact, you will still have the problem.  

Not if I do a fresh install, as usual. Thanks for the info, everyone.

---

### Post by myolbug on 2009-04-09
I have a twist to this problem yesterday my computer told me to install the latest drivers for my NVIDA gpu and so I did.  Now when I open Firefox, it is like it is in half of full screen.  The only way I can close it is to use File > Quit or F11 and put it to full screen then take it off of full screen.  This then brings up the bottom panel that shows the open/minimized windows and it then takes the top panel from being white and unresponsive to the normal FF color which then shows the minimize/maximize/x.

It may have something to do with Compiz Fusion as I have noticed that it doesn't happen with the visual effects turned off.

---

