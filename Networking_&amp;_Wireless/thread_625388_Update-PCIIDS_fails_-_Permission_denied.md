---
title: "Update-PCIIDS fails - Permission denied"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by TMarvelous on 2007-11-27
I am trying to get my 7.10 install to see my wireless card.  I ran the following and it failed:

lauren@LK-Laptop:~$ update-pciids
/usr/share/misc/pci.ids.gz.new: Permission denied
update-pciids: download failed
lauren@LK-Laptop:~$ 

My card is a : SMCWCB-G

I appreciate any help you can offer.

---

### Post by burnttoast11 on 2007-11-28
You could try
sudo update-pciids

---

### Post by TMarvelous on 2007-11-28
Okay, that worked, thanks.  My wireless card still isn't being recognized but I suppose that's a separate issue.

---

### Post by burnttoast11 on 2007-11-29
Sorry, can't help you there.  I had a very tough time getting my wireless card to work on my laptop.  I found this thread about the same wireless card:
[http://ubuntuforums.org/showthread.php?t=242195&highlight=SMCWCB-G]("http://ubuntuforums.org/showthread.php?t=242195&highlight=SMCWCB-G")
Looks like you might have to use ndiswrapper.
Good luck!

---

### Post by devgon on 2007-11-29
try again..........

---

