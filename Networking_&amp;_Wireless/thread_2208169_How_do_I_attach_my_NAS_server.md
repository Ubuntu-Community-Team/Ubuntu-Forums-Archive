---
title: "How do I attach my NAS server?"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by philromford-q on 2014-02-26
Firstly, when I installed Ubuntu 12.04 LTS, my two NAS servers were available in File Manager where I could access and open all my files. This had been fine.  Then I decided to install the KDE desktop environment, I then found that although the NAS server names appeared in Dolphin (i.e. dlink-F95B64), it wasn't possible to access them as I had previously.

I have tried booting with the Ubuntu environment but the result is the same.

I have tried for rather a long time to get them back by setting up shares in SAMBA. However, I have not succeeded; indeed I don't really know what I'm doing with this. Could someone please advise on what to do. I am considering a re-install of Ubuntu, but I'm not sure if this work.

Thank you.

---

### Post by bab1 on 2014-02-26
> **philromford-q said:**
> Firstly, when I installed Ubuntu 12.04 LTS, my two NAS servers were available in File Manager where I could access and open all my files. This had been fine.  Then I decided to install the KDE desktop environment, I then found that although the NAS server names appeared in Dolphin (i.e. dlink-F95B64), it wasn't possible to access them as I had previously.

I have tried booting with the Ubuntu environment but the result is the same.

I have tried for rather a long time to get them back by setting up shares in SAMBA. However, I have not succeeded; indeed I don't really know what I'm doing with this. Could someone please advise on what to do. I am considering a re-install of Ubuntu, but I'm not sure if this work.

Thank you.

Install ***Gigolo*** This allows you to browse the network for Samba shares using the Gnome Virtual File System (gvfs) without installing all of the  Gnome desktop environment.

It's in the Software Center or you can use Synaptic or from the CLI you can use this```

sudo apt-get update

sudo apt-get install gigolo
```

---

### Post by philromford-q on 2014-02-27
I have now got Gigolo, however, being totally pathetic I don't know how to set up a connection; which protocol and how to find out the path, port etc. I am at a loss with this.

---

### Post by bab1 on 2014-02-27
> **philromford-q said:**
> I have now got Gigolo, however, being totally pathetic I don't know how to set up a connection; which protocol and how to find out the path, port etc. I am at a loss with this.

Service type = Windows Share

Server = (whatever your NAS name is)

Share = (whatever your share name is)

---

### Post by philromford-q on 2014-02-27
Thank you, I have it sorted out now.

Thank you all for your assistance.

---

