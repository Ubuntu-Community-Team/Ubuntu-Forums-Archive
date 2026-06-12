---
title: "need help with installing ppas (keeping chromium up to date)"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by djmh on 2009-05-28
well, first of all by adding these links to my repository what will happen?
i assumed it would provide me with updates when a new version is out, is that correct?

but second of all how do i add these to my repository, i have this link but i cant figure out what im supposed to do from there...i have read the provided documentation and i put the link into 
system>admin>software sources>third party
i really dont know which link needs to go into the sources, where it goes or anything
any help is appreciated
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
that is the link that i have for the ppa

---

### Post by Tibuda on 2009-05-28
What's your Ubuntu version? For jaunty, you have to add this line to your third party sources:
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

See also [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by djmh on 2009-05-28
oh, thats it?
well thanks man thats pretty easy !!
but what about the other link, the source one?
is that not needed?
and what will adding this to my repositorys do, will it give me updates of chromium or what?

---

### Post by Tibuda on 2009-05-28
> **djmh said:**
> oh, thats it?
well thanks man thats pretty easy !!
but what about the other link, the source one?
is that not needed?
You only need that line if you want to download the packages source codes. If you only want to run the application, you don't need it.

> and what will adding this to my repositorys do, will it give me updates of chromium or what?
Once you install the chromium-browser package from your package manager, you'll be able to update it using the update manager. The chromium PPA has an update almost every day.

---

### Post by kukibird1 on 2009-05-28
> **djmh said:**
> oh, thats it?
well thanks man thats pretty easy !!
but what about the other link, the source one?
is that not needed?
and what will adding this to my repositorys do, will it give me updates of chromium or what?

You can add it or leave it out useful if you want to build it yourself. 


You may want to add the security key for this ppa 

in a terminal type the following all on one line . 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5 

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index")

---

### Post by djmh on 2009-05-28
i put it in the apt line hit close, choose to reload and get this

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5



also do i need these two things that are unchecked in the third party software

one is
archive.canocal/ubuntu jaunty(source code)
the other is
aqrchive.canocal.com/ubuntu jaunty (partner)

can those be removed, or are they neccassary for something?

---

