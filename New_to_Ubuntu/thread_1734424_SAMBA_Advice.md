---
title: "SAMBA Advice"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Buckie_Bhoy on 2011-04-20
Greetings all.

I have installed 10.10 (64 bit) on my desktop pc to completely replace windows :D and have to say it is absolutely flying, and install was a doddle with no issues at all.

The intention for this machine is that it will eventually become a fileserver on my home network, with all the laptops and notebooks using it for music, video, document storing/sharing etc.

My hard disks have been partitioned for the various shares, and are mounted automatically at /mnt/Music, /mnt/Images etc.  The /home is on a seperate partition but has been left relatively small as I will be storing everything on the shares (I will point /home/user/documents etc. to the appropriate shares also).

Obviously I am looking at SAMBA to take care of the sharing etc., and am working my way through various documentation found online.  However, as others may use my network when they visit, I would like for them to have read only access to certain shares, but have read/write/delete access for designated accounts.  Is this acheiveable with SAMBA?  Also, are there any particular things to be aware of when setting things up?

Cheers

BB

---

### Post by CharlesA on 2011-04-20
Yes it's achievable.

You can take a look at the samba howto I wrote up [here]("http://charlesa.net/tutorials/debian/debiansamba.php").

---

### Post by jquis8411 on 2011-04-20
I have used CharlesA's guide too and it's very good. Another guide which has helped me learn more about Samba is__[]("http://samba.netfirms.com/sambconf.htm")  [http://samba.netfirms.com/sambconf.htm](http://samba.netfirms.com/sambconf.htm) I found it very useful when I decided I wanted to learn more.  also [http://oreilly.com/catalog/samba/chapter/book/index.html](http://oreilly.com/catalog/samba/chapter/book/index.html) I wish I had found these both months ago.[ ]("http://samba.netfirms.com/sambconf.htm")

---

### Post by Choragos on 2011-04-20
My only advice is to allocate more time than you think you need...took me forever to get mine running.  But now, I am delighted.

As a side note, I've been mapping the Samba area as a network drive on my windows machines and running automatic backups that way.  Saved my **** when I killed my wife's computer last night trying to install a new video card.

---

### Post by CharlesA on 2011-04-20
> **Choragos said:**
> My only advice is to allocate more time than you think you need...took me forever to get mine running.  But now, I am delighted.

As a side note, I've been mapping the Samba area as a network drive on my windows machines and running automatic backups that way.  Saved my **** when I killed my wife's computer last night trying to install a new video card.

+1. I do the same thing on my windows boxes at home.

Also, even if it takes a while to get is set up, it'll be running smoothly once you do.

---

### Post by Buckie_Bhoy on 2011-04-21
Thanks guys, will let you know how I get on.

---

