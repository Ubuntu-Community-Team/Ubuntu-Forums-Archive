---
title: "in the market forr a new wireless card."
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by dethdeks on 2007-11-26
so im kinda getting sick of not being able to do much with my broadcom card cause its not supported in linux all that well. it connects n gets me online but it doesnt allow me to do anything else really. so im in the market for an express card wifi card that will work with my system. iv narrowed it down to about 5 that i kinda like and would like some oppions on them as to how hard they would be to install and if they would work in Ubuntu 7.10 Gusty on an HP pavilion DV6000.

i guess first off i should give my pc specs

gig of ram
1.86ghz intel cpu
80 gig hdd
Ubuntu 7.10
1 express card slot

so now the cards that im looking at are the following

TRENDnet TEW-621PC Wireless PC Adapter - 300Mbps, 802.11n (Draft N)
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3172609&CatId=2703]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3172609&CatId=2703")

D-Link DWA-645 N 650 PCMCIA Wireless Network Adapter - 300Mbps, 802.11n (Draft-N) with RangeBooster
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2160985&CatId=2703]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2160985&CatId=2703")

Netgear WN511T PCMCIA Wireless Network Adapter - 300Mbps, 802.11n (Draft-N), RangeMax
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2175863&CatId=2703]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2175863&CatId=2703")

Linksys WPC300N PCMCIA Wireless Network Adapter - 300Mbps, 802.11n (Draft-N)
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2175855&CatId=2703]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2175855&CatId=2703")

Linksys WPC4400N PCMCIA Wireless Network Adapter - 300Mbps, 802.11n (Draft-N)
[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2274978&CatId=2703]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2274978&CatId=2703")

are the 5 cards i found that will fit in my system, but if any one would please let me know if they are running them or have tried them thanks.

---

### Post by wieman01 on 2007-11-26
All I know is that wireless-N adapters are not too well supported... But check this out for a list of compatible cards:

[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

---

### Post by cmas on 2008-06-30
I am really late to this thread, but since this thread ranks high in google among threads that covered the topic of installing the wpc4400N on Ubuntu, I thought I should update this thread:

a) I got the wpc4400N working with my t40 thinkpad laptop. 
b) I copied my 'Drivers' folder (inf and sys files) from the CD that came along with my card. 
c) I used ndisgtk (System > Administration > Windows Wireless Drivers), pointed it to my inf file to install and the card started to work !
d) I am running Hardy (8.0.4)

For detailed instructions please see:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

