---
title: "Belcan F5D6001 wireless card does not work in Feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Aathos on 2007-04-21
My wireless card stopped working when I installed Feisty Faun.  It worked fine out of the box in Edgy, and now it doesn't.  The card shows up in the Device Manager, but Network Settings doesn't show anything.  I found [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2385104&postcount=19") post that says that Fiesty does not have drivers for this card, but it was still in beta at the time.  It doesn't make sense to me that they would stop supporting a piece of hardware that already have working :( .

The card is a Belcan F5D6001.  

It is in a desktop and I would have to move the whole thing to another room to connect to a wired network, and I would rather not have to do that.  Is there a way that I can get it to work without internet access?

---

### Post by Samma3l on 2007-04-24
I had this problem also, with the same card, though it didnt work for me out of the box last time (edgy).

To get it working this time, you will need the latest version of ndiswrapper (1.14 i think is what I used) and the card drivers Bel6001.sys and Bel6001.inf . I found the easiest way was to boot into an OS that could connect (in my case, it was windows) download ndiswrapper and copy the drivers and then move them into a shared area. 

Next step was to boot into Ubuntu and move those articles to the desktop (for ease of locating). Then extract & install ndiswrapper and then the driver.

I found the detailed instructions on ndiswrapper to be very helpful. They explained everything I had to do from start to end to get my card working. It can be found in one of the stickied threads I think.

I'm very new to Ubuntu so I can't help you much more than that

---

### Post by Aathos on 2007-04-24
Thanks.  

I got it working with ndiswrapper.  I had some trouble finding the drivers.  I am not sure which one I eventually used; I tried the one on the cd and one from  [here]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D6001_ver_3_wireless_pci_adapter_using_ndiswrapper_for_Slackware_10_0").

---

### Post by maestrobwh1 on 2007-05-21
Um, my F5D6001 worked out of the box in edgy, but druign my Feisty upgrade and reboot, the card does not even show up in Network Settings as a device.  If I go to KinfoCenter or Type lspci -v... the card is there.  Help?

---

