---
title: "ATI drivers unable to install"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by crogo94 on 2009-08-06
I have just installed Ubuntu 8.04..3 and am trying to install my ATI Radeon 9250 graphics card drivers. At first I couldn't run the check.sh file from the ATI website to figure out which version of xFree 86 I was running. It would fail to run under sudo sh commands, giving me the error that it did not have permissions.

I have decided to go ahead and just install the drivers since there was only 1 version available from the ATI website anyway. I can't figure out how to run the file. I have tried running it through the terminal using sudo sh commands and no luck.

Everything is running sluggishly because of this problem. Any ideas?

---

### Post by Buuntu on 2009-08-06
Can't you just install them by activating them in System > administration > hardware drivers?

---

### Post by crogo94 on 2009-08-06
I think that only works for already installed drivers as my list is still empty.

---

### Post by mcduck on 2009-08-06
Radeon 9250 isn't supported by Ati's proprietary drivers any more. You'll pretty much have to stick with the open-source "radeon" driver (which you should have by default).

(and no, the Hardware Drivers tool isn't for showing already installed drivers, if there were any proprietary drivers available for your hardware they would show there and you would be able to install them with that tool)

edit: With Ubuntu 8.04 you should actually be able to use some older version of Ati's fglrx driver if you manage to find one old enough that it still supports your graphics card. It's just all the new driver versions that don't support older cards any more.

---

### Post by crogo94 on 2009-08-06
Where can I find an open source Radeon driver? I feel pretty confident that I do not have one currently installed or that I am missing something else important graphics related, as I can barely browse web pages such as these forums with out much stress and frustration do to slow loading.

---

### Post by mcduck on 2009-08-06
If you really don't have it already, you'll find it available through package manager.

---

### Post by Mark Phelps on 2009-08-08
> **mcduck said:**
> Radeon 9250 isn't supported by Ati's proprietary drivers any more. You'll pretty much have to stick with the open-source "radeon" driver (which you should have by default).

While the first part it true, the second isn't unless you're running 9.04.  You can still use ATI restricted drivers in 8.04 or 8.10.

You have to go to the AMD/ATI site and select the older versions of the drivers.  You can run anything up through Catalyst v9.3.  Starting with 9.4, they dropped support for "legacy" cards.

---

### Post by shae on 2009-08-09
I believe the last version that supported the 9250 was 0.9.28, which cannot be ran on any modern Ubuntu version I believe.

Check to see if you have Desktop Effects enabled.  If you do, turn them off.

---

