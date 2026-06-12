---
title: "Unable to update or install new programs (10.04)"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Whamola on 2011-01-05
Hey everyone, so I just did a fresh install of Ubuntu 10.04 on a Dell laptop and the first thing I did was run the updater, while that was running I changed the name of my computer from "localhost" to something else.  Upon rebooting the computer after installing over 600MB of updates, I can't install any programs downloaded from firefox (tried skype and chrome), synaptic doesn't launch, and the update manager sits at a greyed out window and refuses to close.

This computer gave me some trouble installing Ubuntu on to it. Ended up using the text only install to get it on the machine.  I would really like to not have to reinstall the OS again, but if that's my only option, I guess I'll deal with it.

Thanks

---

### Post by scheuri on 2011-01-05
> **Whamola said:**
> Hey everyone, so I just did a fresh install of Ubuntu 10.04 on a Dell laptop and the first thing I did was run the updater, while that was running I changed the name of my computer from "localhost" to something else.  Upon rebooting the computer after installing over 600MB of updates, I can't install any programs downloaded from firefox (tried skype and chrome), synaptic doesn't launch, and the update manager sits at a greyed out window and refuses to close.

This computer gave me some trouble installing Ubuntu on to it. Ended up using the text only install to get it on the machine.  I would really like to not have to reinstall the OS again, but if that's my only option, I guess I'll deal with it.

Thanks

may I ask WHERE you changed that localhost name? Which part of the GUI? Which file?

cheers
scheuri

---

### Post by Whamola on 2011-01-05
I hit alt+f2 and ran (gksudo gedit /etc/hostname) and changed the name in the document, then hit save.

Now I can't even get into that.  Every time I ask an administrative process to run, I get the notification in my task bar, then it goes away and nothing happens.

---

### Post by scheuri on 2011-01-06
Was probably a bad idea doing this during an update :)
Well, I am sorry...I am not much of help. I thought I had a similar problem once (not the same though) and I searched google about the problem and found a terminal command that should have solved that issue....but sorry, can not really remember (was with the 6.06 Ubuntu version, if I recall correctly).

Maybe you are just better off installing it again (timewise at least).
Dont forget to make a backup!

Edit: Try downloading the new CD with 10.04.1 which includes many updates already. maybe then you have to download less patches afterwards

cheers
scheuri

---

