---
title: "Accessing Vista files"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by spons8808 on 2008-12-15
Hi there everyone, first of all, I am COMPLETELY New to Linux, but I think this'll be a big experience for me. I've been a windows user for over 10 years, and it's hard to overstate that I'm sick of it. Now, I'm having problems with my wireless internet. I searched the internet and people with the same laptop as mine (Acer Aspire 7520) have a fix for it. I downloaded MadWifi, along with the instructions how to use it. Now the problem is, I can't access the file in linux.. Well, I just can't find out how to access my vista partition. Maybe it's because it's NTFS, idk. Can anyone help me fix my Wifi problem? After I have wifi I'll be überhappy, and then I can download stuff directly to Xubuntu.
Thanks in advance

---

### Post by earthpigg on 2008-12-15
soooo is the problem your wifi or your ntfs partition?

---

### Post by spons8808 on 2008-12-15
> **earthpigg said:**
> soooo is the problem your wifi or your ntfs partition?

Well, the problem is that the wifi fix is on the NTFS partition, and that I need a way to transfer it to my linux partition

---

### Post by kansasnoob on 2008-12-15
As far as WiFi I can only point you here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

As far as accessing your NTFS files I'd install ntfsprogs. It's in synaptic! An alternative is ntfs-config.

I like ntfsprogs, but it does give you the power to destroy NTFS files, even program files, so be sure what you're doing!

---

### Post by spons8808 on 2008-12-15
> **kansasnoob said:**
> As far as WiFi I can only point you here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

As far as accessing your NTFS files I'd install ntfsprogs. It's in synaptic! An alternative is ntfs-config.

I like ntfsprogs, but it does give you the power to destroy NTFS files, even program files, so be sure what you're doing!

Thanks man, I'll try these in an hour. I have an exam first :p

---

### Post by kansasnoob on 2008-12-15
> **spons8808 said:**
> Well, the problem is that the wifi fix is on the NTFS partition, and that I need a way to transfer it to my linux partition

OK, ntfsprogs will let you access anything on a NTFS partition!

[ATTACH]96449[/ATTACH]

Just be aware that if you break it, you own it!

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by spons8808 on 2008-12-15
Ok, I got the file from a seperate FAT32 partition (the ntfs tool didn't show up in the synaptics list). But now I have another problem..
All wireless networks that usualy show up, do show up in the list (all protected) Exept for mine >_> Mine doesn't show up at all, while I'm sitting next to the router with my laptop. I tried configuring it manually but that still doesn't allow me to connect to it. Can anyone help me out here? The network is protected by a 64bits WEP key..

---

### Post by handydan918 on 2008-12-15
Yeah, if you own the router, turn of WEP. At least for purposes of initial configuration. Get the thing working and THEN fiddle with WEP. (Which is nearly useless anyway...crackable in seconds.)

---

### Post by spons8808 on 2008-12-15
> **handydan918 said:**
> Yeah, if you own the router, turn of WEP. At least for purposes of initial configuration. Get the thing working and THEN fiddle with WEP. (Which is nearly useless anyway...crackable in seconds.)

Ok I'll try that :p. People around here are not cleaver with pc's at all so I doubt they'll ever try to crack the key..

---

### Post by spons8808 on 2008-12-15
This is Spons8808 reporting in from Xubuntu. Thanks man, disabling the encryption did the job

---

### Post by handydan918 on 2008-12-16
> **spons8808 said:**
> This is Spons8808 reporting in from Xubuntu. Thanks man, disabling the encryption did the job

Roger that. It often does.

---

