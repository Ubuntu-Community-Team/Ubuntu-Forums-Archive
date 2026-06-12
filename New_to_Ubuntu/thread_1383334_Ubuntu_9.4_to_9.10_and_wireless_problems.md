---
title: "Ubuntu 9.4 to 9.10 and wireless problems"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by apaschou on 2010-01-17
Hi,

I installed some month ago the version 9.04 of Ubuntu on my Toshiba Satellite L-30. A that time, the wireless driver for my integrated Wireless card (AR5BMB5) was working. I remember that I had some stability problems on the connection and I remember having found some third-party drivers that worked better. I don't remember how I install them, but it was through some graphical interface.

I upgraded yesterday to Ubuntu 9.10. The upgrade went well, except for the wireless which is not seen any more by the system. So my options are the next: either I roll-back to 9.4 (I don't know how to do that without reinstalling everything to be honest), or I find a solution on 9.10. However, I am really disppointed to have such surprises when updgrading the system.

Let's speak about the second solution: Keeping 9.10 and solving the issue. I searched hours and find lots of discussion on this Wireless card. But everything was for earlier versions of Ubuntu, and nothing was working for me. Therefore, I don't know any more what to do. I can see my card using the command 'lspci -v'. I get:

[FONT=Courier New]09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/FONT]

So as some propriteray driver was existing with Ubuntu 9.4, I should be able to find them on Ubuntu 9.10. But I am unable to do that... I am browsing the web for hours.

Any ideas?

And just in case I don't find a solution, does someone has a link on a tutorial how to rollback to 9.4 ?

Thanks for any help.

Regards.

---

### Post by ikt on 2010-01-17
> **apaschou said:**
> And just in case I don't find a solution, does someone has a link on a tutorial how to rollback to 9.4 ?


As far as I'm aware there is no rollback, you would have to reinstall.

Here is a quick guide on separating the 'home' partition so if you do need to reinstall(again) you can keep all your files etc

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)

and here is some information that may help you:

[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)

---

### Post by fooman on 2010-01-17
should be easy to fix (at least it was for my atheros card)....open a terminal and type or copy/paste the following:

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```when it opens,  put a # in front of the last line (blacklist ath_pci),  so that it looks like this:

```
#blacklist ath_pci
```then save and close the file.  restart and see if it works.

hope that helps.

---

### Post by apaschou on 2010-01-18
Hi,

Yes, it helps :-). In the mentionned file:

/etc/modprobe.d/blacklist-ath_pci.conf
I found next line:

blacklist ath5k

As you mentionned, adding a # makes the trick. So it seems that for some reason, the first time the PC boot ater my update, there was a problem at Wireless card initalization. Strange, but at least I learned something: I wasn't aware about such "blacklist" files.

Thank you very much for the help you provided.

Regards.

---

