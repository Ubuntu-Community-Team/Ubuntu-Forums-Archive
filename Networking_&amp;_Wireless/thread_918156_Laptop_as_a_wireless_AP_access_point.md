---
title: "Laptop as a wireless AP access point"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by Washington Irving on 2008-09-12
I'm going to be buying a laptop and one of the things that I'd like if it could do would be to act as a wireless AP, access point. I have been looking at Acer Aspire laptops and the inbuilt wireless cards they use are, I believe,the "Pro/Wireless 3945 ABG (Centrino)" ipw3945 (but they might be the iwl3945 
actually, how can I find out?). Anyway does anybody know if it will be possible with this card. Or have any recommendations of any sort. Also, am I right in thinking that if a laptop can be set up to be an AP then I could say extend the range of my wireless network? Also I don't want to be using ethernet cables. I already have a wireless router.

---

### Post by pytheas22 on 2008-09-12
ipw3945 and iwl3945 are just two different drivers (legacy and next-generation).  There's only one Intel 3945 wireless chipset, and you can use either driver to run it, although by default Ubuntu Hardy uses iwl3945.

I don't think that iwl3945 supports master (aka "access-point") mode yet, which is the mode that your card needs to function in if you want it to act as an AP.  I think it's a goal of the developers to get it working eventually, but as far as I know (could be wrong, of course), it's not yet implemented.

ipw3945, an older driver, is supposed to support master mode.  However, I've never been able to get ipw3945 to install on Hardy (there are some changes to the kernel that make it difficult), so you may have to use an outdated version of Ubuntu if you want to get ipw3945 running.

Most other Linux wireless drivers don't support master mode, although in principle many will some day (it's a goal of the new [mac80211]("http://linuxwireless.org/") wireless project, which covers many types of chipsets).  Some of the legacy drivers (like ipw3945) may (if you don't know the difference between legacy and mac80211 drivers, see the link in my signature about wireless drivers).

So the bottom line is that in principle, it would be possible to get a 3945 card to work in master mode using the ipw3945 driver, but it probably won't be easy (beyond driver issues, you're going to have to deal with setting up a dhcp server and bridging your network connections).  But it's definitely possible if you're willing to put the time into it.

Also, [this page]("https://help.ubuntu.com/community/WifiDocs/MasterMode") will probably be quite useful for you.

EDIT: as the poster below usefully mentions, creating an ad-hoc network with your laptop as the gateway is another option.  Just keep in mind that, again, not all Linux drivers support ad-hoc mode (most do, but not all), so make sure that yours will--not just for the laptop, but for all computers that need to connect to it as well, since they will all need to operate in ad-hoc mode.

---

### Post by superprash2003 on 2008-09-13
try this [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)

---

