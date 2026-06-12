---
title: "PXE DHCP Server"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by D8TA on 2008-01-26
I have an old notebook, IBM 390 which is a PII 400 with 128MB of RAM. The sole purpose of this book was to provide PXE and DHCP services. It currently is in our lab and is the primary DHCP server but it wasn't handing out any IP addresses so I did a reboot. When the notebook came back up I noticed that the pcmcia_core had failed which then the DHCP failed also. This notebook was running an old Debian 3. something. No GUI just command line. I tried pulling out the card and reseating it but nothing. I typed dmesg and noticed the card but still it is not doing anything. Any suggestions?

 I am fairly new to Linux and only have used OpenSuse but wanted to try out Ubuntu or Xbuntu, something small that would work. I even thought about Server but what would work in terms of my hardware mentioned above. The hard drive is about 5GB. I searched for a LiveCD solution but then figured that would take forever to boot. What we have now is decent and works except the pcmcia_core keeps failing which makes the book dead in my opinion. 

Thanks in advanced!

---

### Post by D8TA on 2008-01-28
What about if I complete overhaul the notebook and use Xubuntu. What steps do I need to do in order to setup a PXE server to boot my machines from the network?

---

### Post by D8TA on 2008-01-28
Could someone maybe point me in the right direction for a "how-to" so I can setup a PXE boot Xubuntu box?

---

### Post by D8TA on 2008-01-30
Thanks for all the replies. :lolflag:

I have got everything working but now am wondering can I PXE boot ISO files?

---

