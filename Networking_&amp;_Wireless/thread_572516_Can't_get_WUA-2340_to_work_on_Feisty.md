---
title: "Can't get WUA-2340 to work on Feisty"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2007-10-10
Firstly, yes I have searched these forums and found no solution yet.  And this would be the reason you are reading this thread, because I have found no solution published, and am looking for one.

I just installed Ubuntu Feisty.  The computer it is on is rather old, and lacks an ethernet port.  So because of this I have chosen a wireless usb adapter(WUA-2340).

I tried an installation guide that has worked flawlessly for me in the past(ubuntu, kubuntu and xubuntu dapper versions).
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux")

But for some reason I am unable to get it to work now.  I used the 1.01 version of the driver from dlink's site.  by using 'sudo ndiswrapper -l' I can see "Installed ndis drivers:  neta5agu   driver present, hardware present".

But the interface is not yet recognized by ubuntu, therefore I can not use it.

the step that fails for me is 'sudo ifup wlan0'.  This step gives me a vey long and drawn out message about how it can't bring up the device, so it doesn't work.

There is no LED activity.  Also(and maybe this will be where the fix is), my ubuntu 7.04 cd seems to lack an ndiswrapper package, so I used my ubuntu 6.10 cd to get the ndiswrapper-utils package installed.  So it is possible a newer version of ndiswrapper might do the trick, but of course, why did this work for me with dapper and not feisty?  I used the same ndiswrapper version for both, but feisty is not recognizing my device still...


[EDIT]
  I reinstalled ndiswrapper, but I need to uninstall the driver to install it with the update ndiswrapper.  it tells me to use the -e command, but when i type 'sudo ndiswrapper -e neta5agu' it fails, as well as 'neta5agu.inf' and other version where I capitalized the letters(as in the original filename of the driver).  How are you supposed to uninstall a driver?

---

### Post by Sup3rkirby on 2007-10-10
I hate to do this, but it seems like my only solution right now.

I could just install Ubuntu 6.10, then from there upgrade my installation with the Ubuntu 7.04 disc, correct?  And in doing so, migrate my settings, assuming I can get the adapter installed under 6.10.

I'll just have to get started on this, unless I get a reply soon.

[EDIT]
not that it matters I think, but I meant Ubuntu 6.10 and not Ubuntu 6.06.  All references have been edited.


Well, I'm getting very frustraighted right now.  6.10 is doing the same thing.  "sudo ndiswrapper -l" shows me the driver is not only installed, but the usb adapter is detected as it says 'hardware present'.  But yet for some reason "sudo ifup wlan0" is giving me an error that basically says there is no device detected for wlan0.  Someone please help me here.  I would hate to have to give up on Ubuntu because I couldn't get any help to get my PC online.

---

### Post by Sup3rkirby on 2007-10-11
^^ Bump ^^

---

### Post by Sup3rkirby on 2007-10-12
^^ Bump ^^

---

### Post by Sup3rkirby on 2007-10-15
^^^ BUMP ^^^

I'm very frustraighted right now. I have 3 usb adapters. I have successfully used 2 of them with Linux in the past. Now I'm trying to use Ubuntu 7.04 and none of them work, therefore, no internet/network. And in my case this renders that PC completely useless.

Since no one seems to know how to get the WUA-2340 working, I'll ask if anyone might now about microsoft's usb adapter(mn510)? I supposedly installed it and it shows up on my list of network adapters, but it detects NO wireless networks, and if I add a new one(or connect to one not listed really), i can put the exact name of my network but still get no connection(there is no pass).  Why isn't anything working?  I have installed and reinstalled Ubuntu about 5 or 6 times now.

---

### Post by leegweaver on 2007-10-28
I am having the exact same issue with the mn-510 and Xubuntu 7.10 as above.

---

