---
title: "Aircrack wepcrack"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-01-17
Hi,

I have just installed aircrack-ng and am trying to crack my own wep key, It works fine when I use Backtrack but I don't have that installed at the moment and I don't have the space to rearrange my partition so i'm using Ubuntu(much more familiar with it)

I launch my attack but can only get one arp request out of about 200 de-auth attacks, I have a sneaking suspicion that it could be the version of aircrack-ng or my driver

I use the wusb54g v4  is there a special driver or patches that need to be applied? or is there a special version of the aircrack suite that is patched that i need?

any help would be great;)

---

### Post by tturrisi on 2007-01-17
your wusb54g is described at this aircrack page:
[http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)

---

### Post by andytof47 on 2007-01-17
Yeah I have setup my driver according to the guide but it still only gives me 1 ARP packet on my network 

the guide doesn't mention un installing the old driver so i didn't - do i need to?

cheers for the link:mrgreen: 

any other ideas that might be specific to Ubuntu?

---

### Post by KuroYoma on 2008-06-30
Sorry to add another question but i keep getting this error with WEPCrack when i activate pcap-getIV.pl

root@kuro-laptop:/tools/wifi/WEPCrack# ./pcap-getIV.pl -b 13 -i eth1
Opening device eth1.....
DLT = 1: unsupported DLT type at ./pcap-getIV.pl line 189.

Any Ideas

---

