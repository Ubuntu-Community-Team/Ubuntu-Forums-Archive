---
title: "Wireless almost working?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Beware The Birchmen on 2009-07-01
HI
First off I've been through multiple installs today and had various issues I've been trying to sort out. Right now I'm trying to get my wireless card to work.

The strange thing is it worked during my first install to download(or attempt to download the updates, I didn't leave enough space :( ). Now that I've got it reinstalled the wireless card can see my access point but every time it'll sit at one green dot then shoot back to the wep/encryption screen. Once I got two green dots but it quickly shot back again.

I'm on an Acer Aspire 4530 if that helps. I've tried pushing the wireless button on and off but it didn't seem to do anything.

Thanks for any help you can provide.
:guitar:

---

### Post by PureLoneWolf on 2009-07-02
Hi

We need to establish what wireless card you have first.

Can you run a terminal and type 

lspci

Post the output in here.  Also, what version of Ubuntu are you running?

---

### Post by Beware The Birchmen on 2009-07-02
Hi!
Thanks for the reply this is the output(I'm running Ubuntu 9.04)

08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

This was at the bottom when I ran lspci, if you need the full stats I'll post it but looked mostly like nvidia related video stuff?

---

### Post by Beware The Birchmen on 2009-07-02
I'm not sure if it matters but that ethernet adaptor is working/regular LAN/CAT5 cable works fine.

---

### Post by austinpsycho on 2009-07-02
hmm..  if you open a terminal and type *wicd-client -n* what kind of errors does it give?

---

### Post by zwdev on 2009-07-02
Hi there,

Check if your wireless toggle switch or button is set to ON ?

---

### Post by austinpsycho on 2009-07-02
> **zwdev said:**
> Hi there,

Check if your wireless toggle switch or button is set to ON ?
He did infact say he had done that.

---

### Post by Beware The Birchmen on 2009-07-02
Hi guys

Thanks for the replies.

austinpsycho:
I noticed you mention wicd-client which was recommend by another user(pytheas22).
So I installed it and it connected the first try:p

Couple of questions about Wicd manager:
it is now in the taskbar...can I close that window and have some sort of relevant information popup where the gnome network manager was?(near the logout button/volume control)?

is there anything I need to know about Wicd besides?

Thanks a lot for the help, I'm rather new to Ubuntu but everything is coming together thanks to this community 8-).

---

