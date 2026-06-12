---
title: "Install NDISWRAPPER in Feisty Fawn"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by timorrill on 2007-05-10
I've just installed Feisty Fawn on my desktop, and would like to install ndiswrapper so that I can get my wireless card to work. The Ubuntu help files claim that ndiswrapper is on the CD, but I am having trouble finding it. I can't add an internet repository because I can't access the internet. Any suggestions? Can someone help me find ndiswrapper on the CD?

Thanks!

---

### Post by H.E. Pennypacker on 2007-05-13
If you are able to access the Internet for a short period of time, download ndiswrapper from:

[http://archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/)

You can also get NDISWRAPPER from the CD.  Insert the CD, and browse to /pool/main/n/ndiswrapper.  Once the CD has been inserted, you'll see the Pool folder.  Start there.

You could have also done a search to find the file.  Places > Search for files, but instead of searching your home folder, you should have searched the CD.

---

### Post by aysiu on 2007-05-13
Actually, I don't believe *ndiswrapper* is available on the CD any more. It was in Edgy and Dapper, but not for Feisty, for some reason.

---

### Post by king_arthur on 2007-05-13
Are you 100% sure you need ndiswrapper for your card to work?

Go checkout this link first [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You might be surprised..


/P

---

### Post by H.E. Pennypacker on 2007-05-13
> **aysiu said:**
> Actually, I don't believe *ndiswrapper* is available on the CD any more. It was in Edgy and Dapper, but not for Feisty, for some reason.

I used the Edgy Live CD.

---

### Post by aysiu on 2007-05-13
Cool. So the Edgy *ndiswrapper* works with Feisty, too?

---

### Post by H.E. Pennypacker on 2007-05-14
> **aysiu said:**
> Cool. So the Edgy *ndiswrapper* works with Feisty, too?

No, I am just saying I popped the Edgy CD in to see where ndiswrapper was located on the CD.  I installed the latest version of ndiswrapper from source (downloaded from its website).  Apparently, there's a bug in the ndiswrapper that is in the repos.

aysiu, your card does not need ndiswrapper, right?  I ask, because I remember you speaking highly of the card.

---

### Post by aysiu on 2007-05-14
Yeah. Before I bought my card, I tried to do some research/asking to find a good Ubuntu-compatible one. I was recommended the Intel Pro Wireless 2200, and it's been great.

---

### Post by Cenotaph on 2007-05-14
actually i think ndiswrapper comes with the Feisty CD. I would recommend installing the latest source from ndiswrapper.sourceforge.net though

---

### Post by aysiu on 2007-05-14
> **Cenotaph said:**
> actually i think ndiswrapper comes with the Feisty CD. I would recommend installing the latest source from ndiswrapper.sourceforge.net though
Not with the Feisty Desktop CD--I checked. I don't know if it's on the Feisty Alternate CD, though.

---

### Post by iAlta on 2007-05-14
> **Cenotaph said:**
> actually i think ndiswrapper comes with the Feisty CD. I would recommend installing the latest source from ndiswrapper.sourceforge.net though

What do I need, to compile it from source?

---

