---
title: "How to change wireless card driver in 7.04"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by skain on 2007-10-10
Hello all, I'm new to Ubuntu 7.04 Feisty and installed it on an HP XT595 (ze5200) P4 laptop..

So far it's great, runs much better than Windows, except for one thing, the wireless doesn't work.  At least, it probably works but with WEP only.

Unfortuately all the networks I use are WPA-TKIP encrypted, so as of now I have no wireless connection.

The card uses the Prism 2.5 Wavelan chipset, which I know 7.04 has issues with unless one does a little tweaking.

I had it running WPA under OpenSuSe 10.2 using the hostap_pci driver and it worked fine.

However, Ubuntu didn't give me the option of choosing which driver to use during install process like SuSe did, and SuSe, well... ran slow and had issues so that's why I'm on Ubuntu.

I did the lsmod command and it listed many different modules for my wireless card, hostap_pci, orinoco_pci, prism2_pci, etc.  But I know it's not using the hostap_pci driver since I don't have WPA listed in the network manager, only WEP.

I also did the lshw -C network command and the driver=hostap... but not hostap_pci.  If it were using the hostap_pci driver I should have WPA option just like in SuSe, right?:confused:

Is there any "Device Manager" equivalent or shell command I can invoke to knock out the other drivers and leave the hostap_pci running my wireless?

I've been searching for about a week now and tried various things to no avail... I really need your help guys,  I refuse to go back to Windows and SuSe is slowww as all heck.

Any suggestions guys?

---

### Post by kevdog on 2007-10-10
Did you install wpasupplicant??

---

### Post by skain on 2007-10-10
Thanks for the QUICK (5 mins.) reply, kevdog!  Now that's what I call dedication. :)

I just figured out the problem after a week of trying, the solution was in a post regarding NDISWRAPPER, which I don't use but was willing to try anything to keep my Ubuntu.

In my case, the problem was that in my /etc/iftab configuration file, it had my wlan0 interface as having a MAC of 00:00:00:00:00:00

I manually keyed in the MAC, rebooted and was immediately prompted for a network key, with WPA listed right along with WEP.  Success! :guitar:

Credit for the fix goes out to--get this--you, kevdog.  I just took a look at the post and it was your NDISWRAPPER guide that finally got me up and running.  I seriously cannot thank you enough, this was the last obstacle to a fully functional Ubuntu laptop.

I work IT for my University and will be spreading the word about the Ubuntu community at every opportunity.

Thanks again for the help from the guide and being willing to help again when needed.  If you're ever in Chicago drinks are on me buddy!!

---

### Post by kevdog on 2007-10-10
Hmm, cant say that my ndiswrapper post has helped anyone like you stated -- Im glad -- Im always trying to add more sections to the troubleshooting guides based on what Ive seen with others.

I am in Chicago :)

---

