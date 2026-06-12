---
title: "encryption v access lists for wireless"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by yetanothername on 2007-04-22
First I should say that I'm very impressed with the fiesty release, not only did it recognise my viewsonic 20 inch out of the box (no more messing with xorg.conf), but my wireless was detected without any problems at all (before I could not even use wireless for some reason). A job very well done.

I know little of wireless setups and when I set up the wireless I decided to forgo encryption and use an access list instead as this is a home network and we know the PCs that can have access. This seems like a decent option to me as I have the access security as well as no overhead for encryption.

What are the downsides to using an access list over encryption?
I assume my network data can be read as it's not encrypted - is this a big issue, or am I setting my self up for some bigger issues down the road?

---

### Post by Catsworth on 2007-04-22
1.  Your data (anything sent over the network, bank details, logins for sites, emails, files) is all available  to anybody that is able to wirelessly 'sniff' your network.

2.  Anybody sniffing your network traffic can find out what IP addresses and MAC addresses are in use, if an IP address or MAC address is in use then it stands to reason it is on your access list.  Changing (or spoofing) the IP address or MAC address of a network adaptor is simplicity itself, all I do is change the address of my adaptor to match that of a valid on on your network and I have complete access to your network, your internet connection, and all of your files.

The 'overhead' for encryption is so little when compared to the risk of your personal data being hijacked that there really isn't any sense in *not* implementing it in your situation.  Implement encryption (preferably WPA, not WEP) now please :)

---

### Post by yetanothername on 2007-04-23
"Implement encryption (preferably WPA, not WEP) now please"

Will do!

Thanks for the info, I suspected as much.....

---

### Post by wieman01 on 2007-04-23
Even WEP is not secure. Disabling ESSID broadcast and maintaining an access list based on MAC addresses are false friends as highlighted above. WPA2 with a "good" password is the way to go.

_**EDIT:**_
Even WEP can be compromised in less than an hour. Just FYI.

---

