---
title: "Netgear MA311 Disappeared"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Episcopus on 2007-03-04
I installed Edgy yesterday.  My Netgear MA311 PCI card worked.  I downloaded and installed system updates, about 138 of them.  I went to bed while they were installing.  There were no error messages this morning, but now my wireless card does not work.  iwconfig shows no wireless connections.  dmesg shows that the prism2 card is found.  The device manager shows the card, but no details about it.  The card is supposed to work out of the box, at least according to this page: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear).  

I have searched the forums and can't find anything addressing this specific issue.  Any help fixing this would be greatly appreciated.  My student budget can't afford a new wireless card right now, and I really want to give Ubuntu a fair shake.  My last XP install on that machine became infected, and I am tired of that.

Thank you

---

### Post by Episcopus on 2007-03-05
The solution was to delete kernel 2.6.17-11-generic. See this thread: [http://ubuntuforums.org/showthread.php?p=2250027#post2250027](http://ubuntuforums.org/showthread.php?p=2250027#post2250027)

---

