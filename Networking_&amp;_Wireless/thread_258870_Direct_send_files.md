---
title: "Direct send files"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Yayzik on 2006-09-16
Hi, I wanted to know if there was a way for me to send files directly from my Ubuntu laptop to my Windows PC, which are connected through an ethernet cable.

If not, could I do this on my Windows partition that I have on the same laptop?

Thanks a bunch!

---

### Post by lcg on 2006-09-16
> **Yayzik said:**
> Hi, I wanted to know if there was a way for me to send files directly from my Ubuntu laptop to my Windows PC, which are connected through an ethernet cable.
Try samba, which is an implementation of Windows' file and printer sharing. You can access a Windows share from Nautilus via smb://user@computername/sharename/ (<- press CTRL-L to enter this address into a Nautilus window).
I am also successfully using unison to sync files between several computers.

HTH,
Lars

---

### Post by threethirty on 2006-09-16
for lars' post to work, you must run the network wizzard on the windows box to create a workgroup, I dont remeber where to find that, does anyone else?

---

### Post by lcg on 2006-09-16
> **threethirty said:**
> for lars' post to work, you must run the network wizzard on the windows box to create a workgroup, I dont remeber where to find that, does anyone else?
Actually, Windows XP Pro asks for a workgroup name when installing, XP Home sets it automatically as "Workgroup", IIRC.
However, you need to define a network share, which you can do via the context menu of a folder. I don't know the English term to do this, though, as I'm not using an English Windows.

HTH,
Lars

---

