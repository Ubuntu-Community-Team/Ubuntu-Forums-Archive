---
title: "No Option for WPA in Feisty"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Ameeya on 2007-04-25
Hello

I just finished installing Ubuntu Feisty Fawn, and everything except for Wireless Networking works great.  I have a D-Link DWL-G650+ wireless card, and according to Ubuntu, the card is supported. Everything seems to work fine in Network Manager, as clicking on it gives me the drop-down menu with my router available for selection.  However, when I choose Connect, then under wireless security, I only have the various WEP encryptions available for selection in the drop-down menu.  I was under the impression that WPA is available by default in Ubuntu?  Is there something I am doing wrong.  How come I am not even seeing an option for WPA?  

I would really appreceate any help that anyone could provide me with.  I love Ubuntu, and don't want to not be able to use it just because I can't have WPA encryption.  

Thanks in advance!

---

### Post by Ardee83 on 2007-04-25
Well during my travels I found this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager)

which also has numerous ways of applying WPA w/o using the network manager. Hope that helps!

---

### Post by Ameeya on 2007-04-25
Thanks for your reply. :)  I will try that out and keep scanning this forum.

---

### Post by Catsworth on 2007-04-25
Do a search of the Forum for WICD.  I'm not sure how it works with Fiesty but I'm running it quite nicely with WPA in Edgy.

---

### Post by Lord Illidan on 2007-04-25
Wicd in feisty works with the edgy deb..

---

### Post by olizilla on 2007-04-28
> [http://ubuntuguide.org/wiki/Ubuntu:F...etwork-Manager](http://ubuntuguide.org/wiki/Ubuntu:F...etwork-Manager)

is useful for getting started with all things ubuntu, but that specific part is not relevent to Fiesty which comes with network-manager installed by default.

> Do a search of the Forum for WICD

I have exactly the same problem with the DWL-G650+ wireless card, so I tried out WICD as suggested. It seems like a nifty network switcher, but It does not solve this problem on its own.

After much googlising, I think the problem is that the generic driver for this card does not support WPA, only WEP, and so no network selection interface is going to be able to provide it.  [http://doc.gwos.org/index.php/ACXDriver#EDGY_EFT_6.10]("http://doc.gwos.org/index.php/ACXDriver#EDGY_EFT_6.10")
The solution seems to be to use ndiswrapper with the original windows driver in place of the generic one, with the usual warning that you should only use ndiswrapper if you are desperate, as it means the allowing evil binary MS code into your magical ubuntu paradise blah blah blah yawn.

So, wizard, we have the problem, we have something like a solution, so, why am i here? Well, I cant for all of google find a source for the DWL-G650+ driver that contains the hallowed GPLUS.inf file that i am supposed to use with ndiswrapper. The latest driver does not contain it, and i have no idea what i should use in its place? anyone got any clues?

Cheers.

---

### Post by Craigus on 2007-05-01
[ftp://ftp.dlink.co.uk/wireless/dwl-g650+_rev_Bx/DWL-G650+_rev_Bx_Drv_v202.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g650+_rev_Bx/DWL-G650+_rev_Bx_Drv_v202.zip)

I have managed to get my dwl-g650+ working in Feisty using this driver under ndiswrapper with WPA, but only once :) . Manual setup was needed as network manager won't connect.

---

### Post by scales on 2007-05-01
interesting, my issue is that network manager works alright and i see wpa and wpa2, but when i turn off roaming mode and try to manually connect, my only options are wep ascii and wep hex.  i do like wicd, but it doesnt have the nice vpn support that network manager does.  i just want to be able to see all networks and pick when and which i am connecting to.  auto connect isnt really important to me.  any suggestions?  i dont mind another client i just need vpn.

---

### Post by Craigus on 2007-05-01
Not an answer to your question, scales (or perhaps it is relevant), but I should add that the other thing I had to do to make WPA available was to remove the acx module by:

> sudo rmmod acx

I tried blacklisting acx, but for some reason it keeps loading anyway.

---

