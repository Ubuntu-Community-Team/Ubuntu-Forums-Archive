---
title: "cracking wep/wpa"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by markeee on 2007-11-23
Hi, whilst i know how to crack wireless networks - or at least I understand how having read copious amounts on it and such

I don't have a card which is of any use, my laptop has a card with a broadcom chipset-ugh i know, and the other is a centrino, which aren't great for it either-

I've been checking around and it seems Atheros would be the way to go, that or Prism2 based cards (which i can't seem to find any for sale at UK retailers!)

been looking at -> [http://www.ebuyer.com/cat/Wireless/subcat/Adapters---PC-Cards](http://www.ebuyer.com/cat/Wireless/subcat/Adapters---PC-Cards)

if anyone cares to have a look and help-id appreciate it, so far i think:

which card should i purchase:

Netgear WAG511
[http://www.linuxquestions.org/hcl/showproduct.php?product=675&cat=myprod](http://www.linuxquestions.org/hcl/showproduct.php?product=675&cat=myprod)
appears to have an atheros chipset

D-Link DWL-650


only 2 which seem like possibles, as the DLINK DWL-G630 depends on version number etc

---

### Post by jrusso2 on 2007-11-23
I use the netgear make sure it is the exact model that has the atheros chips cause some of the revisions don't.

---

### Post by markeee on 2007-11-24
hey jrusso, thats what im worried about-the site doesn't list the version!

you use the WAG511 not the WAG511T? I keep reading different comments when searching, 

btw what versions work if you know, ta

---

### Post by markeee on 2007-11-24
according to

[http://atheros.rapla.net/](http://atheros.rapla.net/)

the WG511T/WAG511 are both fine? it doesn't mention version numbers..and i cant seem to find much else:(

---

### Post by markeee on 2007-11-24
if anyone could confirm either the

Netgear WG511T / WG511/WAG511 will be what i need thatd be wicked


just searched a bit more - [http://lists.redbrick.dcu.ie/pipermail/bugi/2005-January.txt](http://lists.redbrick.dcu.ie/pipermail/bugi/2005-January.txt) seems WG511T is 'always' atheros-and the list at [http://atheros.rapla.net/](http://atheros.rapla.net/) says same

still, im not 100% sure, as some of the info is outdated, so could have changed

---

### Post by jml on 2007-11-24
I assume what you are looking for is a wireless card that can be put into monitor mode.  The reason you cannot find many prism 2 cards is the fact that it is an older chip set which supports 802.11B standard.  Not G.  It also does not support WPA encryption protocols.  Your best bet to find on if you still want one is to go on eBay and look for a "Cassic" Orinoco Gold 802.11B wireless card.  Its the one with a connecter for an external antenna.

The NetGear WG511T does have an Atheros chip set and supports Monitor mode.  Another card I had good luck with is the Cisco Aironet 802.11A/B/G card.  Its is also based on the Atheros chip set and supports monitor mode.  Its a bit pricy, but a good card.

Joe

---

### Post by markeee on 2007-11-24
hej jml,

thanks for replying:)

mmh about The NetGear WG511T , is it all versions are atheros? As i read some versions of cards have diffeent chipset depending on version -and ebuyer does not specify what version of the 511T they have.

The list i checked, shows WG511T as supporting wireless (with no *) the * meaning the chipset may vary depending on the version of the card

so all 511T are atheros? if so i am going to order in a minute

thank you mate

Mark,

---

### Post by markeee on 2007-11-27
hej jml have time to help??

The list i checked, shows WG511T as supporting wireless (with no *) the * meaning the chipset may vary depending on the version of the card

so all 511T are atheros? if so i am going to order in a minute

my list says all are atheros, unlike some cards which use diff chipset dependong on version of card-but i am also not 100% sure, i have read some people having trouble with the card 

not sure how to know for sure, before i buy and ebuuer doesnt say what vers iot is even

---

### Post by Tavorisch on 2007-11-28
What luck!, I have an atheros WG511t, i dont have my laptop with me but i will look up the revision and what not so you can make sure.. but.. all you have to do honestly is the madwifi-ng website..  search madwifi-ng in google. madwifi-ng.org  or madwifi-ng.org.trac    in the top right you can download the.tar.gz file..  you might wanna make sure you have fesity fully updated with all the repositories in synaptic checked... (works in gutsy too) running the -16 kernel cause i always did that before i installed this driver.... but yes.
just extract that folder.. go into it via terminal..  sudo make  then sudo make install...  hit R to remove the old modules.... run sudo modprobe ath_pci... or maybe ath0 instead of ath_pci   then edit.. i think sudo gedit /etc/modules         
and ath_pci   the newest madwifi-ng comes with the tools and everything..  putting into monitor mode is just
sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
and install aircrack-ng  from their site.. (search google)  extract the tar go into its directory via terminal then [sudo make]  next sudo [make install]
from there you should be ready for injection while in monitor mode.. works beautifully. umm if you get this card send me a pm or check my posts because i plan on making a how to that makes a lot more sense than this.. haha probably a lot of typos and what not cause im tired.

---

