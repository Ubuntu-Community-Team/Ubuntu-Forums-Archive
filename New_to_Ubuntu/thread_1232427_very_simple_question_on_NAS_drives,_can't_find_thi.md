---
title: "very simple question on NAS drives, can't find this specific answer!"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by darrude on 2009-08-05
hi all,

I am thinking of buying a NAS drive to store all my important data as well as DVD backups and MP3's.  As I have a PS3 I am going to get one that also works as a media server.

Can I just by any, most say they are only window's / MAC compatible.  From what I have read I keep seeing samba for windows nfs for linux!  I have seen some posts with people complaining about connecting to them.  Is this a good idea with Linux.  I don't mind a bit of hassle to set it as long as i never have to worry about it again.

I'm hopeing i would just see it in /media/NAS and then I could write to that from linux or my windows xp laptop as something like a "D" drive.

Suggestions and advice welcome.

Thanks in advance.

Darren

---

### Post by BDNiner on 2009-08-05
I bought about a month ago a Buffalo Link Station Pro
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154](http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154)

It works great with Ubuntu. The shares that I created can be mounted and browsed from the places menu. I ended up mounting several shares using CIFS and fstab though. It is a bit of work to get everything setup correctly. I am now working on backing up to the device using rsync, don't quite have things working right.

fwbackups is a great program for backing up files in Linux. I spent some time working with the maintainer to get the program compiled and now it works pretty well.

---

### Post by darrude on 2009-08-05
> **BDNiner said:**
> I bought about a month ago a Buffalo Link Station Pro
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154](http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154)

It works great with Ubuntu. The shares that I created can be mounted and browsed from the places menu. I ended up mounting several shares using CIFS and fstab though. It is a bit of work to get everything setup correctly. I am now working on backing up to the device using rsync, don't quite have things working right.

fwbackups is a great program for backing up files in Linux. I spent some time working with the maintainer to get the program compiled and now it works pretty well.


thanks for the post, that's very similar to one i'm looking at.  I will ordered after pay day!

thanks for the quick response!

---

### Post by gn2 on 2009-08-05
I have a [Linksys NSLU2]("http://en.wikipedia.org/wiki/NSLU2") and it's excellent.
It's out of production now, but you can still find them available.
It was replaced by the NAS200.

[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)
There are a few other devices mentioned in the above link.

---

### Post by BDNiner on 2009-08-05
No problem, I am contemplating picking up one of the cheaper models and turning it into a full blown linux server. There is a full community of user that have done this on various forums.

---

### Post by Zeedok on 2009-09-22
Could someone explain to me the benefits of a NAS device over a USB hardrive??

I'm just thinking aloud about connecting some extra storage to my Mythbuntu box and was wondering what the best way forward was.  It seems that the NAS enclosures often offer two drive bays and some have "web interface" login etc.  Are these the only advantages?

---

### Post by 3rdalbum on 2009-09-22
> **Zeedok said:**
> Could someone explain to me the benefits of a NAS device over a USB hardrive??

I'm just thinking aloud about connecting some extra storage to my Mythbuntu box and was wondering what the best way forward was.  It seems that the NAS enclosures often offer two drive bays and some have "web interface" login etc.  Are these the only advantages?

Your whole network has access, and most NAS units can be used for other things too; most can have a Bittorrent client installed for low-power seeding :-)

---

### Post by Zeedok on 2009-09-22
> **3rdalbum said:**
> Your whole network has access, and most NAS units can be used for other things too; most can have a Bittorrent client installed for low-power seeding :-)

Ah, pardon the ignorance . . . you can't share a USB drive on the network??

---

### Post by halitech on 2009-09-22
NAS - [http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)

the benefit of a NAS is it plugs directly into your router so no specific computer needs to be turned on in order to access it. You can share a USB drive but it requires it to be plugged into a computer and that computer must be turned on in order for other computers to access it.

---

