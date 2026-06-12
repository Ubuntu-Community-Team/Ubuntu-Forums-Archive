---
title: "[SOLVED] Firefox all of a sudden started opening strange"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-12-03
Hey everyone,

About a week ago I went to open up Firefox, and this is how it looked when it opened:

[http://bitimage.co.uk/images/lnf4mdwafvgokvjsbypn.png](http://bitimage.co.uk/images/lnf4mdwafvgokvjsbypn.png)

As you can see, there is no title bar for Firefox. So there is no way that I can minimize or close by clicking the boxes in the upper right hand corner. Plus...the browser totally covers up the Ubuntu bar at top(the one with Applications, Places, System, etc.).

So, the only way I can make the browser look like how it's suppose to, is by hitting F11 twice. The first click of F11 will make it in full screen mode, then the secret click will make the browser into normal mode.

Now, I"m getting really sick of hitting F11 twice *every single time* I open FF. So what can I do to fix this, so FF open normal again, without have to do a totally new install. Because, when I installed Ubuntu, I imported all of my parents settings from IE from Windows, into FF. And I have no idea how I'd do that again if I uninstalled FF, and reinstalled. Plus I don't really want to do that. I'm hoping there's a way to fix this without having to do a full install.

Any help will be greatly appreciated. Thank you.

---

### Post by HittingSmoke on 2008-12-03
> **h8uthemost said:**
> Hey everyone,

About a week ago I went to open up Firefox, and this is how it looked when it opened:

[http://bitimage.co.uk/images/lnf4mdwafvgokvjsbypn.png](http://bitimage.co.uk/images/lnf4mdwafvgokvjsbypn.png)

As you can see, there is no title bar for Firefox. So there is no way that I can minimize or close by clicking the boxes in the upper right hand corner. Plus...the browser totally covers up the Ubuntu bar at top(the one with Applications, Places, System, etc.).

So, the only way I can make the browser look like how it's suppose to, is by hitting F11 twice. The first click of F11 will make it in full screen mode, then the secret click will make the browser into normal mode.

Now, I"m getting really sick of hitting F11 twice *every single time* I open FF. So what can I do to fix this, so FF open normal again, without have to do a totally new install. Because, when I installed Ubuntu, I imported all of my parents settings from IE from Windows, into FF. And I have no idea how I'd do that again if I uninstalled FF, and reinstalled. Plus I don't really want to do that. I'm hoping there's a way to fix this without having to do a full install.

Any help will be greatly appreciated. Thank you.

Do you have the AutoHide extention installed?

---

### Post by h8uthemost on 2008-12-03
Nope, I sure don't. These are my list of extensions:

Adblock Plus
All in One Sidebar
Custom Buttons
DownThemAll
FireGestures
FireTray
FlashGot
Greasemonkey
Paste Email Plus
Quick Restart
Speed Dial
Tab Mix Plus

I *think*, I didn't install any new extensions when this started happening. But i could be wrong.

---

### Post by HDave on 2008-12-03
I have the exact same problem and it really is annoying.  From your list of add-ons, here are the ones I am using:

Adblock Plus
Tab Mix Plus

Perhaps the problem is with one of these two....

---

### Post by nhasian on 2008-12-03
yeah your right on the money.  you have to press F11 to get the title bar to return.  its a bug in the nvidia graphics driver.  as a workaround you can install the latest beta nvidia driver if you dont want to wait for a new one to become available in the repos.

---

### Post by h8uthemost on 2008-12-03
Nah...I tried uninstalling these two and the problem still happens.

Wow, this really sucks. Didn't know there were others with this problem.

EDIT: Thank you for the info nhasian. If the update isn't in the repos, where is the best place to get it?

---

### Post by xjcannonx on 2008-12-03
I had this problem and i had to uninstall the ubuntu firefox modifications add-in.
tools --> Add-ons --> Extensions

---

### Post by h8uthemost on 2008-12-03
I don't have a ubuntu firefox modification in my add ons.

---

### Post by xjcannonx on 2008-12-03
Maybe I can help if I know a little more about your setup. Does your gnome-panel autohide at all, do you use compiz-fusion or have any other specialty things set up?

---

### Post by h8uthemost on 2008-12-03
That's ok xjcannonx. I really appreciate you taking the time to try and help me. But I did a little searching and found the solution. I would have done this in the first place, but I didn't know this was an actual bug with 8.10. I thought it was just a problem I was having.

So, I found the solution here:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740)

The actual solution from that page is:

**Workaround : Install compizconfig-settings-manager , start ccsm, click on "Workarounds" plugin in the "Utility" section and uncheck "Legacy Fullscreen Support".

So that's what I did. I installed compizconfig-settings-manager from Synaptics. Then I started compizcofig by going to System>Preferences>CimpizConfig Settings Manager. Then I just went to Utility>Workaround, and un-ticked the Legacy Fullscreen Support box.

After doing this, I've closed and opened FF numerous times so far, and the browser is now opening like it's supposed to. So for the ones that are having the same problem, just follow this and it should fix it for you.

A big thanks to everyone that tried to help me. I appreciate it.

---

### Post by alienexplorers on 2008-12-03
If you use a nvidia card and compiz then make sure you have the line > Option         "AddARGBGLXVisuals" "True".
Also did you by chance change desktop themes?

---

### Post by h8uthemost on 2008-12-03
I'm not sure if compiz is enabled. When I looked in synaptics to install compizconfig-settings-manager, there was a bunch of compiz stuff installed i saw. But I haven't used any of the compiz desktop effects.

And no, I'm positive I didn't change a desktop theme when this started. Right when I updated to 8.10, I changed my theme. Then...a couple weeks after FF started behaving like this.

---

### Post by nhasian on 2008-12-03
if your still interested in installing the latest nvidia driver:

[http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html](http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html)



> **h8uthemost said:**
> Nah...I tried uninstalling these two and the problem still happens.

Wow, this really sucks. Didn't know there were others with this problem.

EDIT: Thank you for the info nhasian. If the update isn't in the repos, where is the best place to get it?

---

### Post by madverb on 2008-12-03
[http://ubuntuforums.org/showthread.php?t=992666](http://ubuntuforums.org/showthread.php?t=992666)

Do people even search the forum before asking questions?

---

### Post by h8uthemost on 2008-12-03
Thank you nhasian. And madverb, I already stated I didn't search first. But if you would have bothered to read the whole thread first, you would have found that out. Smart ***..

---

### Post by madverb on 2008-12-03
No need to be abusive.
> And madverb, I already stated I didn't search first. But if you would have bothered to read the whole thread first, you would have found that out. Smart ***..
If you had bothered to search the forums before posting pointless threads, this could have all been avoided.
Peace

---

### Post by HDave on 2008-12-03
I am running v180...the latest nVidia driver and it still happens to me.

---

### Post by loomsen on 2008-12-03
[www.opera.com](www.opera.com)

---

