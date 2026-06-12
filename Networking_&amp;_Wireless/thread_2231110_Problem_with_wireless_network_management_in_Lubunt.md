---
title: "Problem with wireless network management in Lubuntu 14.04 LTS"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2014-06-23
I recently upgraded from Lubuntu 13.10 to 14.04 on my laptop.

Sometimes it is convenient for me to connect to my Vodafone mobile network via my mobile phone ("Internet sharing").

With Lubuntu 13.10 the fan shaped network indicator doubled as status monitor and network manager. It would automatically "see" all available wireless connections (I can't remember whether on right or left click). Sometimes my mobile network would not be listed even though activated, but it could easily be brought up be clicking on "More wireless networks". Connection was no problem.

With 14.04 all this has changed. (Why change things if they work???!!!) Now there is a "Network Status Monitor" (the fan shaped icon), which only tells you if you are connected or not, and there is a "Manage Networks" icon, which in theory should do what it says. Just to complicate matters further the developers have decided that if there is no ethernet connection but there are available wireless networks, this icon should become two icons, one with a red cross through it (the ethernet one).

The other Manage Network icon should display the available wireless networks. It does so extremely erratically, most often saying there are no available wireless networks even though I know there are plenty of protected ones all around. There is no "More wireless networks" or "Show hidden networks" option, as there were on the previous version. It almost never shows my mobile network. When it does and I click on it, chances are nothing happens. If I am lucky enough for something to happen, I am asked for the security key, even though this should be memorised (I have configured this wireless network through Preferences -> Network Connections). Even then sometimes no connection is forthcoming, other times yes.

For me this is a big fail. My questions are:

(1) Am I missing something?

(2) Can I get the old network manager back again?

Many thanks.

---

### Post by Dennis N on 2014-06-23
You can get back the regular network manager icon you are used to which does the things you want. You can first remove the "network status monitor" and "manage networks" panel applets and then follow the steps here:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by Dennis N on 2014-06-23
There is also a video (Lubuntu screencast) on fixing this problem available here:

[http://www.youtube.com/watch?v=4ElJVE2oW18](http://www.youtube.com/watch?v=4ElJVE2oW18)

---

### Post by rdh61 on 2014-06-26
Thank you for that effective solution.

---

