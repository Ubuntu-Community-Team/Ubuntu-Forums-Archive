---
title: "Selecting Wi-Fi service"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-07-07
Computer info in signature. Upgraded to 10.04 and hadn't noticed before but the indicator of connecting to a Wi-Fi is not in the upper task bar like it was in 9.10.

Noticed that when I was visiting the kids and set up a Netgear Wi-Fi there. Wanted to connect to that but did not see the indicator, or the method of choosing what I connect to.

It does show the globe that provides the choices of connecting to a remote server or shared disc but that requires the "public shared ftp" etc, not the ability to see available Wi-Fi's so you can select there.

Right clicked and went into "Add to panel" but that choice is not in there. Indicator applet is on. Volume and Envelope showing.

Any directions on getting that choice available?

Thanks.

---

### Post by uRock on 2010-07-07
Go to "add to panel" again and add "Notification Area." That will show the Network Manager.

---

### Post by nick_goodfate on 2010-07-07
> **uRock said:**
> Go to "add to panel" again and add "Notification Area." That will show the Network Manager.

i think Notification Area , in 10.04 is called indicator applet and flyfishingphil said its on . i may be wrong , i have not seen any panel on my desktop lately ... :P

> Any directions on getting that choice available?

You may not have network card drivers installed ?

---

### Post by uRock on 2010-07-07
I am on 10.04. Notification area has a status for Network Manager in it. The one the OP is using is a bit different and only has the mail and volume indicators.

Edit: I even deleted it and re-added it to double check.

---

### Post by flyfishingphil on 2010-07-07
> **uRock said:**
> Go to "add to panel" again and add "Notification Area." That will show the Network Manager.
Forgot to mention that is already there. All that shows is the Skype connections and options for Skype. Don't see the option to view available Wi'Fi's.

Also, checked Network Manager in Synaptics and there are several checked there as installed but don't have the option to view "local" Wi-Fi's and sign into one.

---

### Post by flyfishingphil on 2010-07-07
> **nick_goodfate said:**
> i think Notification Area , in 10.04 is called indicator applet and flyfishingphil said its on . i may be wrong , i have not seen any panel on my desktop lately ... :P



You may not have network card drivers installed ?
It's not in the network card drivers. I am on the one at home right now and, when visiting the kids I get on one, but don't know which one it is. Do some business on the 'net and need the secure for that purpose.

---

### Post by uRock on 2010-07-07
Hmm. I have even tried it on my Netbook that has wireless. It does fall under the Notification Area. This means something is wrong with your set up and we need to figure out just what it is. 

I looked under installed programs in the Ubuntu Software Center and I have no special wireless stuff installed to make it show. There are a few apps in the USC that will show up on the panel and allow you to choose your connection, such as WiFi Radar. I have tried WiFi Radar on another machine before with no problems.

Did you do a clean install or do an actual upgrade?

---

### Post by flyfishingphil on 2010-07-08
> **uRock said:**
> Hmm. I have even tried it on my Netbook that has wireless. It does fall under the Notification Area. This means something is wrong with your set up and we need to figure out just what it is. 

I looked under installed programs in the Ubuntu Software Center and I have no special wireless stuff installed to make it show. There are a few apps in the USC that will show up on the panel and allow you to choose your connection, such as WiFi Radar. I have tried WiFi Radar on another machine before with no problems.

Did you do a clean install or do an actual upgrade?
Just went in to the software center and uninstalled the Network Manager then reinstalled it. It now shows next to the Skype indicator and allows me to see all of the other ones around the neighborhood. 

Guess that's what I needed to do.

Did the upgrade, not clean install, but everything else worked fine following the update I did following the upgrade.

Call it solved unless it happens again.

---

### Post by uRock on 2010-07-08
> **flyfishingphil said:**
> Just went in to the software center and uninstalled the Network Manager then reinstalled it. It now shows next to the Skype indicator and allows me to see all of the other ones around the neighborhood. 

Guess that's what I needed to do.

Did the upgrade, not clean install, but everything else worked fine following the update I did following the upgrade.

Call it solved unless it happens again.
It is odd how stuff like that gets messed up, but it does. I am glad the fix turned out to be easy.

---

