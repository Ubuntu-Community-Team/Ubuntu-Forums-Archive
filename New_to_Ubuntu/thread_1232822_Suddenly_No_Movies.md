---
title: "Suddenly No Movies?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Grrruff on 2009-08-05
Hi everyone,

I've been pestered by the upgrade utility lately.

I was in the middle of watching a stargate movie on Hulu.com.
After the upgrade I could not get Hulu to play movies period.

I can get to other sites and view the pages on Hulu, but I cannot play the flicks.

Is there someway to undo the last upgrade?  I've been looking for some sort of tool that offers that option without much luck.

Thanks,

~Gruffster

---

### Post by jmszr on 2009-08-06
Grrruff,

Someone on the forums today was having the same sort of trouble. He finally figured out that Adblock Plus had started blocking Hulu.

I'll see if I can find it. I don't know if he had updated or not.

Edit: Here it is: [http://ubuntuforums.org/showthread.php?t=1229313&highlight=hulu](http://ubuntuforums.org/showthread.php?t=1229313&highlight=hulu)

---

### Post by Grrruff on 2009-08-06
All fine I suppose however it does not tell me what to do.

I cannot stress just how new I am to ubuntu and linux.

I rooted around and found Addons for Mozilla.
1) uninstalled AdBlock.  No change
2) Removed Flash.  No change
3) Reinstalled Flash No change.

Hulu now says I need Flash 9.n or better.
Installed Flash 10.n  No change.

---

### Post by bryncoles on 2009-08-06
is firefox using the correct version of flash?

look for a 'lego-brick' icon on the bottom right of the firefox window when you're on hulu. click it, and you'll get a nice pop-up where you can change from what its using (probably gnome swfdec player) to adobe flash player (installer). 

does that help?

---

### Post by Katalog on 2009-08-06
> **bryncoles said:**
> is firefox using the correct version of flash?

look for a 'lego-brick' icon on the bottom right of the firefox window when you're on hulu. click it, and you'll get a nice pop-up where you can change from what its using (probably gnome swfdec player) to adobe flash player (installer). 

does that help?

True that. You most definitely need to purge swfdec or you'll continue to run into issues like this. One of the first things I would do is open the terminal and run the following:

```
sudo apt-get --purge remove swfdec*; sudo apt-get --purge autoremove; sudo apt-get autoclean; sudo apt-get install flashplugin-installer
```

---

