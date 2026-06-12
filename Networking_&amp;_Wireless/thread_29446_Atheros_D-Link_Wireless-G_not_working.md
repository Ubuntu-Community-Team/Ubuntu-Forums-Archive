---
title: "Atheros D-Link Wireless-G not working"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by joudbren on 2005-04-24
Hi all.  Relative Linux Noob with a new D-Link DWL-G520 PCI wireless card in my system and no go.  Bought this one specifically as it is on the Ubuntu recommended hardware list and several posts on this site have indicated good luck with it.

I have confirmed that it is the Atheros chipset version AR5212 and specifically it is hardware version B3 and F/W version 4.10 on the card.  I have tried a clean install of Ubuntu and even though the card shows up in the list of PCI stuff at the command line it will not initialize with the included drivers.

I have searched every post I can find on this site including a wiki post entitled "WiFiWithSomeoneElsesRouter" that had some great stuff to try at the command line.  MadWiFi drivers are indeed showing as loaded but when I get to the point of "ifconfig ath0 up" then nada.  It's at this point the Wiki mentions if the card doesn't show up then "go find someone more experience than me" and so here I am looking for more experience!

I'm assuming the included MadWiFi drivers somehow don't work with the particular revision level of the card as I get "ath%d: unable to attach hardware; HAL status 13" which apparently means the drivers are incompatible with the hardware according to the MadWiFi website.

I can still take this card back so if anyone has a SOLID recommendation for a Wireless PCI G card that works OUT OF THE BOX with no issues, no hassles, i.e.: it might or might not have a different chipset, firmware, revision number, etc, etc.  

As mentioned before, the card I purchased IS on the recommended list so getting a little paranoid now in my old age....  (grin)

I am all ears and very appreciative for any info provided.   I am also willing to try updating any drivers that might be required to get this D-Link card going if anyone can point me in the direction of a fairly noob freindly set of instructions on how to do this.  I'm not totally helpless with Linux and I can certainly follow clear directions but I also have a minor gift for doing lots of damage pretty quickly if the instructions are vague enough. (grin)

Thanks again for any help that can be provided.  I did fire up a CD Live distro of a security Linux package called Auditor (ver 150405) based on Kanotix/Knoppix and it loaded drivers for this card on the exact same system with no issues and ran fine so I know this can be made to work somehow.  Cheers!

James   8-)

---

### Post by fizzatbeyond on 2005-04-24
[QUOTE=joudbren]Hi all.  Relative Linux Noob with a new D-Link DWL-G520 PCI wireless card in my system and no go.  Bought this one specifically as it is on the Ubuntu recommended hardware list and several posts on this site have indicated good luck with it.

I have confirmed that it is the Atheros chipset version AR5212 and specifically it is hardware version B3 and F/W version 4.10 on the card.  I have tried a clean install of Ubuntu and even though the card shows up in the list of PCI stuff at the command line it will not initialize with the included drivers.

I have searched every post I can find on this site including a wiki post entitled "WiFiWithSomeoneElsesRouter" that had some great stuff to try at the command line.  MadWiFi drivers are indeed showing as loaded but when I get to the point of "ifconfig ath0 up" then nada.  It's at this point the Wiki mentions if the card doesn't show up then "go find someone more experience than me" and so here I am looking for more experience!

I'm assuming the included MadWiFi drivers somehow don't work with the particular revision level of the card as I get "ath%d: unable to attach hardware; HAL status 13" which apparently means the drivers are incompatible with the hardware according to the MadWiFi website.

I can still take this card back so if anyone has a SOLID recommendation for a Wireless PCI G card that works OUT OF THE BOX with no issues, no hassles, i.e.: it might or might not have a different chipset, firmware, revision number, etc, etc.  

As mentioned before, the card I purchased IS on the recommended list so getting a little paranoid now in my old age....  (grin)

I am all ears and very appreciative for any info provided.   I am also willing to try updating any drivers that might be required to get this D-Link card going if anyone can point me in the direction of a fairly noob freindly set of instructions on how to do this.  I'm not totally helpless with Linux and I can certainly follow clear directions but I also have a minor gift for doing lots of damage pretty quickly if the instructions are vague enough. (grin)

Thanks again for any help that can be provided.  I did fire up a CD Live distro of a security Linux package called Auditor (ver 150405) based on Kanotix/Knoppix and it loaded drivers for this card on the exact same system with no issues and ran fine so I know this can be made to work somehow.  Cheers!

James   8-)[/QUOTE]
 I'm using a Dlink DWL-G650 (pcmcia) and have been using it for some time with little problem.  So hopefully I can help.

I can't say about that specific revision, but the card is listed on the madwifi site as working.  I do know some simple ways to check to see if the device is recognized though.

First, and most importantly does the module get inserted? (lsmod|grep ath)
  Mine gives me this - 
    mfilizzi@lappy:~$ lsmod|grep ath
    ath_pci                55584  0
    ath_rate_onoe           8840  1 ath_pci
    wlan                  106588  3 ath_pci,ath_rate_onoe
    ath_hal               133328  2 ath_pci

you might not have all those modules show up (not sure what the pci version needs)

If you do have modules listed then the card was automaticly detected so that's good.
Second is if you run iwconfig, does ath0 get listed there? 

If it's not then it didn't create the network device at all.  If it is then it should show you some info about the card and network.

If it is there then it seems like you just have the network misconfigured.  (but I'm guessing the problem was before here).

---

### Post by joudbren on 2005-04-24
Ok, lsmod | grep ath gives me this:

ath_pci                60608  0
ath_rate_onoe           8904  1 ath_pci
wlan                  118524  2 ath_pci,ath_rate_onoe
ath_hal               133232  1 ath_pci

When I type iwconfig I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

So looks like the ath0 is definitely not showing up.  Not sure how the network config is messed up as this is a brand new and unmodified install of Ubuntu with the exception of the 686 kernel (but problem was the same with the 386 kernel).  Any other suggestions to try?  Thanks!

James   8-)

---

### Post by fizzatbeyond on 2005-04-25
If it's not showing up in the iwlist then it seems like a problem in madwifi itself.  I would suggest emailing their list (I think they also spend time on IRC if you would rather that).  Either way you can get all their info from [http://madwifi.sf.net](http://madwifi.sf.net).  Or maybe someone else here would have a better idea.

---

### Post by joudbren on 2005-04-25
Thanks again for the info.  I'll check out the MadWiFi website as suggested.  I'm 100% certain it's a driver issue not recognizing the card for some reason.  Probably the new firmware in the D-Link card or something.

I ran the latest version of Auditor Linux and they specifically mentioned that they took the opportunity with this new release to update all of the WiFi drivers to the latest versions.  It has no problem with this latest D-Link G520 so I'm going to assume that the MadWiFi driver version installed in Hoary is just slightly old enough to not work with this card.   Guess I'll have to try manually updating the driver set and hopefully not blow up yet another distro! (grin)

Any easy way to determine a revision number of the MadWifi drivers in Linux to see what is working and what is not working?  I'm curious as to the difference between the Auditor set and the Ubuntu set of drivers.  Thanks!

James   8-)

---

### Post by malegria on 2005-04-25
Joudbren:  If you manage to get your card going in Hoary, please leave an explanation as to how you did it. I have the same card and am having the same issues. It is detected in Device Manager but I also get the "no wireless extensions" message. 

Thanks in advance.

---

### Post by malegria on 2005-04-26
I went to #madwifi @ irc.freenode.net and they told me what the issue is (if your card is rev. B).  It turns out the HAL part of driver (even the CVS one) is not up-to-date when it comes to this hardware upgrade that this card has undergone (namely the "rev. B"). 

So it seems that one will have to wait until the developers get-on-the-ball and get this part of the driver going. The "ath_pci" works, but the the "ath_hal" doesn't. 

Does anyone know if an attempt with ndiswrapper is worth trying?

---

### Post by copeja on 2005-04-27
The pcmcia card works perfectily with the ndiswrapper the pci cards do not work they disconnect every few seconds. I have set both up in Gentoo using the madwifi drivers 
0.1_pre20050420 it loads all rev B and I have rev B5. Can you build the modules for Ubuntu with out brakeing the other modules that are prebuilt in the kernel ? 
If you need more information check bug #6097

---

### Post by joudbren on 2005-04-27
So I was correct in my guess that it is apparently a driver issue.  Thanks everyone for your feedback, much appreciated.  I'll probably return the card while I still can and hang tight for eventual driver support.

In the meantime, I also have a new Asus PCI G card with a Ralink 2500 chipset that I'll try (cool card BTW with a stock external antenna on a 3 foot wire that can be positioned wherever for best connection!).  Need to compile drivers for it but pretty sure this one will have awesome support shortly seeing as how Ralink has GPL'd their drivers.  Hoping the Linux community will reward Ralink quickly with a major show of support for doing that.  Cheers!

James   8-)

---

