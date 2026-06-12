---
title: "Firefox corrupt"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by myolbug on 2009-05-14
Jaunty 64bit:  
I don't know what happened, but Firefox has gone south on me.  I even tried to uninstall in Synaptic and rebooted.  It is still there.  Is there a log I can access and post to show what happened?

---

### Post by Bios Element on 2009-05-14
Try this in console. Note: You will lose all your settings.

```

sudo apt-get purge firefox
sudo apt-get install firefox

```

---

### Post by whoop on 2009-05-14
(re)move ~/.mozilla

---

### Post by hyperdude111 on 2009-05-14
Go to your home directory
Press ctrl-H
Delete the folder named ".mozilla"
It should work

---

### Post by HittingSmoke on 2009-05-14
I had a friend who had this happen as well on the Jaunty upgrade. Just remove .mozilla from your home directory after enabling viewing of hidden files in Nautilus.

It will delete all your settings and such so make sure you know what plugins/themes and such you have. Also, not sure if this wipes bookmarks so you may want to back them up.

---

### Post by myolbug on 2009-05-14
I have actually have tried all of the above, but is still persists.

I do the above purge script and the terminal says that it isn't found and yet it is still in the applications menu.  When I open it, I get a blank browser with basically just an address bar.  The forward/back/home etc buttons are blanked out.

How do I make it go away?

---

