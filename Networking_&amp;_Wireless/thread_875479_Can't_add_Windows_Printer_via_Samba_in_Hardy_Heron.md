---
title: "Can't add Windows Printer via Samba in Hardy Heron"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by bkuhns on 2008-07-30
I've been using Ubuntu since 6.06 and have never really had an issue with adding a network printer from a Windows box, so I find it odd that I'm completely stumped on this issue. Seems everything I've found points to just simply click the "New Printer" button and select "Windows Printer via Samba". On my laptop, this option simply isn't there. I VNC'ed into my desktop that's also running Hardy, and sure enough "Windows Printer via Samba" is there. Does anyone know why that entry happens to be missing on my laptop, and how I may go about getting it back? Thanks! :)

Attached is a screenshot just to prove I'm not crazy ;)

---

### Post by jso2897 on 2008-07-30
Um, is your laptop connected wirelessly, and your desktop on a wired network?

---

### Post by cariboo on 2008-07-31
What happens when you click Other?

Jim

---

### Post by bkuhns on 2008-08-01
> **jso2897 said:**
> Um, is your laptop connected wirelessly, and your desktop on a wired network?

Yes, my laptop is wireless and my desktop is wired. This was never a problem in the past though. All my network printers (when I'm using the laptop at work or at home) used to work fine and were all imported when I upgraded from Gutsy, but in the last two weeks or so none of them work anymore. I deleted one and tried to reinstall it, but that's where I'm having problems.

---

### Post by bkuhns on 2008-08-01
> **cariboo907 said:**
> What happens when you click Other?

Jim

If I click Other, all it asks for is the device URI. I've tried somewhat desperate things like "smb://desktop/printer_name", but to no avail.

---

### Post by superprash2003 on 2008-08-01
this might sound stupid but maybe trying to install smbclient may work..

---

### Post by bkuhns on 2008-08-01
Not stupid at all, in fact, quite on the spot! I did a search for "samba" in Synaptic and as far as I could tell everything looked alright. I completely forgot to check for "smb"... smbclientlib was installed, but not smbclient. Installed, and now I can add Windows networked printers again! Thanks a ton! :)

---

### Post by zebraneo on 2009-09-21
add smbclient it should work

---

### Post by franziski on 2010-06-20
I'm having the same problem (but on a Debian squeezy).

I have installed smbclient.

With smbclient -L hostname I see the shares (printer too).

Any hint?

Thanks in advance

[UPDATE] FIXED after a purge/new installation of cups:

apt-get purge cups
rm -rf /etc/cups
apt-get --purge autoremove
apt-get install cups

---

### Post by broomie on 2010-07-25
Same with Lucid after a cups update - did as above removed cups, purged re installed all happy

---

