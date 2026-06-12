---
title: "[SOLVED] What happened to flash after Hardy upgrade"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Unstuck on 2008-12-18
I just upgraded a friend's Inspiron 1420 to Hardy and the only hiccup seems to be that Firefox doesn't recognize Flash is installed.  When we navigate to pages that use flash, a message pops up telling us to install missing plugins and gives us a few choices (nonfree, swfdec, gnash).  When I clicked to install flash, a message popped up saying it was already installed, but doesn't run flash like it's supposed to.

---

### Post by Therion on 2008-12-18
Open Synaptic.
In the "Search" box enter "Gnash".
Remove anything "Gnash" related, leaving ONLY the **Adobe** Flash player in place.

---

### Post by Unstuck on 2008-12-18
I removed all instances of Gnash with no luck.  Then I removed all installed instances of Adobe, too, with the same result.  Now, Adobe is the only one installed but I'm still getting the missing plug-in message.

---

### Post by Unstuck on 2008-12-19
bump

---

### Post by hotstovejer on 2008-12-19
What happens when you type in a terminal ```
sudo apt-get install flashplayer-nonfree
```

You could also try installing the restricted extras in Add/Remove.

Try that, and get back to us.

Thanks!

Jeremy

---

### Post by Unstuck on 2008-12-20
> **hotstovejer said:**
> What happens when you type in a terminal ```
sudo apt-get install flashplayer-nonfree
```

You could also try installing the restricted extras in Add/Remove.

Try that, and get back to us.

Thanks!

Jeremy

Response after I tried pasting the above code
> E: Couldn't find package flashplayer-nonfree

Enabling restricted extras didn't resolve issue.

---

### Post by Captain_tux on 2008-12-20
Your browser’s hopelessly optimistic claim that installation of Flash is only a few clicks away is a lie. You have to install Flash via **Synaptic** or **apt-get** using the CLI. Once you do that, you'll have to update (the red caution arrow will be displayed next to the clock). Update, re-start Firefox, and you *should* be good to go.

---

### Post by Unstuck on 2008-12-20
Solved.

After completely removing all instances of flash in Package Manager, I installed the Macromedia Flash Plugin through Add/Remove.  This seemed to install flashplugin-nonfree (again) and resolved the issue.  If someone suggested this and I didn't understand you're instructions, I apologize for complicating the issue and thank you--and everyone else--for your help.

---

### Post by anjilslaire on 2008-12-20
best bet is to get the .deb file from Adobe'a website, designed for Ubuntu 8.04+:

[http://get.adobe.com/flashplayer/?promoid=DXLUJ]("http://get.adobe.com/flashplayer/?promoid=DXLUJ")

This way, you can get Flash 10, vs 9 in the repositories.

---

