---
title: "[SOLVED] network manager wont detect wireless network"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by help_me_please on 2008-05-14
Hello every1.
Just installed hardy today and this is my my first linux install, so go easy on me with the technical stuff please.

i've been having trouble all day long with my wireless card and tried various fixes that were suggested all over the place:

at first ubuntu didnt recognize my card - iwconfig gave me "no wireless extensions" msgs.

i tried installing wcid, but that did nothing other that trash my wired connection as well.

then i found this: [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers]("http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers")

i downloaded and installed the file, and after a reboot, Network Manager recognizes my wireless, iwconfig recognizes my wireless as wlan0, but i can neither detect nor force-connect (through network manager) to my wireless network.

i tried [this]("http://http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html#") as well, but it didnt help at all.


this is the hardware im using: an LG E-500 series notebook. lspci tells me my wireless card is Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) (LG website tell me its an intel pro 3945ABG card).


my wireless network is NOT hidden.

i'll be more than happy to supply any additional data.

thanx in advance.

---

### Post by Rytron on 2008-05-14
Try NDISwrapper and WifiRadar.
I also tried wcid before and it messed up my wireless connection.
Get NDISwrapper to find a .inf file in your drivers folder. Keep trying differant inf files until NDISwrapper says Hardware Present: Yes.

My wireless connection is now perfect.

---

### Post by williamson389 on 2008-05-14
Rytron, could you be a little more specific?  i ask because i have the same exact problem as this.  I have an ACER aspire 5100 with an AR242x wirerless card that has never shown up.

I tried installing madwifi and ndiswrapper by reading help given in the forums.  i think they are install correctly, because i can now go to system-administration-windows wireless drivers and it shows net5211 and says hardware is present.

I am unsure about what madwifi did but either way my wireless connection is not appearing.  If you could go over what to do after installing madwifi it would be greatly appreciated.

---

### Post by nicedude on 2008-05-16
Try wicd it will manage your wifi network connections and store your keys for you to connect at the push of a button for as many networks as you want.

Its what I use everyday including to post this :-)

Just google "wicd ubuntu" for simple instructions on how to add it to your software sources.

---

### Post by help_me_please on 2008-05-17
problem solved!

i found the solution [here]("http://translate.google.co.il/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/160673/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://forum.ubuntuusers.de/topic/160673/%26hl%3Den%26sa%3DG") (page is originally in german. this link is translated by google).

to all of those who wish to use this solution:
* i made a clean ubuntu install b4 applying this solution. I chose not to try it on a system littered with failed previous solutions.

* i had 1 problem with this tutorial: when i tried to preform "sudo apt-get install - reinstall build-essential linux-headers-`uname-r`" i got an err msg stating that the system couldnt find 'reinstall' package. to solve this i just dropped '-reinstall' from the command.

i want to thank the creator of the above tutorial from the bottom of my heart. i've been struggling with this problem for days.


now.... how do i set thread status to solved?

---

### Post by help_me_please on 2008-05-17
quick update:

installing latest nvidia drivers with EnvyNG broke the solution. i will check if i can get things to work again and post an update.

Edit:
tried redoing the same steps in the tutorial, but when i get to "sudo modprobe ath_pci" i get an error:
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

i don't understand the error at all. ideas any1?

#2 Edit:
ok this is super wierd. i rebooted, and suddenly the wireless is working again. i have no idea how or why.

thank you every1 for your help.
i hope this post helps others with similar problems.

good night.

---

