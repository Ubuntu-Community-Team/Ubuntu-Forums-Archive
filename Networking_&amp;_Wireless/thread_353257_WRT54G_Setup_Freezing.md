---
title: "WRT54G Setup Freezing"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by balls on 2007-02-04
Hello,

Whenever I try connecting to my router by entering the information in the network option and attempt to activate the connection, my desktop freezes, causing me to restart my computer.  Is there a way to get around this?  My windows partition works fine with the router.  Any help would be very much appreciated.  Let me know if you need any more info.

Thanks.

---

### Post by balls on 2007-02-04
Any information at all would be helpful.

Thanks.

---

### Post by jml on 2007-02-04
What type of wireless card are you using?  And can you tell us what chipset the card uses.  This may seem rather arcane, but certain chipsets are notorious (Broadcom comes to mind,) for not playing well with Linux.  Also, does your wireless network use encryption?  If yes, what type, WEP, WPA-PSK, WPA2?  Depending on your answers, the default network utility may not be the correct application to get you on line.  More information is needed.

Another suggestion.  From a terminal run the following commands and post the output to this forum.  

ifconfig

iwconfig

Finally, hang in there.  Getting wireless working in Linux is probably the most frustrating task to complete, and in my opinion, is one of the major reasons Linux in general, and Ubuntu in particular, does not become more popular.

Joe

---

### Post by jml on 2007-02-04
Forgot to mention, even if the default network utility does work, it works very slowly.  Literally can take a minute or more.  So one other suggestion is after you try to activate a connection, move away from your computer for several minutes, have a stretch, get a cup of coffee.  You get the idea.  Its just possible that you are not waiting long enough for the application to complete its work.  A long shot, I know, but worth a try.

Joe

---

### Post by balls on 2007-02-04
Thanks for the response,

The chipset is RT2500USB.  I've tried looking for how-to's in the forums, but no luck there.

My network is protected by WEP, and one of the things I was having trouble with was distinguishing between hexadecimal and Plain (ASCII).  I figured that hexadecimal was the encrypted one, and plain was the passphrase.

Thanks again.

---

### Post by balls on 2007-02-05
So I tried what you suggested, but had no luck.  I left the network tool on, and walked away for a bit less than 20 minutes.  But I noticed something.  I hit activate, and it takes me back to the original network window, but it says the connection is active.  Only then does it freeze.  Any help is welcome.

---

