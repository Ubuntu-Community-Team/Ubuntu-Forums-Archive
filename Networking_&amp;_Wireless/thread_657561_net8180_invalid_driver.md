---
title: "net8180 invalid driver"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by kanh on 2008-01-03
I've been trying to configure my linksys wpc11 v4 for a secure network on 7.10 but am not having much luck.  I've been using ndisgtk to install the net8180/rtl8180 and I'm told it's an invalid driver.  This driver was OK up until about a week ago and all of a sudden ndisgtk didn't seem to like it.  Any ideas?

Thank you.

---

### Post by joe_newbie on 2008-01-06
I also am having problems with this chipset and ndisgtk. This card worked previously under Mandriva (with ndiswrapper) with the lsrtnds.inf that came with the card (which I have attached). Probably something I am doing wrong but.. any suggestions are greatly appreciated.

---

### Post by joe_newbie on 2008-01-07
problem solved (for me)

ran: sudo ndiswrapper -i /home/joe/Desktop/LSRTNDS.inf

command line told me that I was missing files. Figured out I had copied the .inf to my desktop instead of pointing ndisgtk towards the folder on the disk. Removed the first attempt in ndisgtk, then tried again (from command line)

Problem solved :)

---

### Post by kanh on 2008-01-07
Thanks for the idea, I tried but it didn't work for me.  Last week I went back to Feisty for a bit and couldn't get that to work with wireless either so now I'm on a fresh install of Gutsy.

---

### Post by 1r0nman on 2008-05-06
i have the same problem...any ideas,it was good for about a week and now it says invalid driver...

it was working until today when i put a WEP encryption on my wireless router...any help would be much appreciated

---

