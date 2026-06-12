---
title: "Can't restore a software source"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-27
On upgrading to karmic, a lot of my software sources were disabled, as expected. It's been pretty easy to re-enable most of them, but I'm struggling with one last little bu**er.

I'm getting the following message when I try to reload my package list:
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 106A92EF1E5F9737
```

Does anyone have any ideas as to what I should do to restore that source?

---

### Post by lykwydchykyn on 2009-11-27
That error doesn't mean the software source is disabled, it just means the signing key hasn't been added, so you'll get an error about unverified packages if you try to install anything from that source.

It will still work though.

If you go to the web page for that ppa, it should have instructions for adding the key to your apt keys.  Which ppa is it?

EDIT: nm, check out these instructions: [http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

---

### Post by Roger Allott on 2009-11-27
> **lykwydchykyn said:**
> That error doesn't mean the software source is disabled, it just means the signing key hasn't been added, so you'll get an error about unverified packages if you try to install anything from that source.

It will still work though.

If you go to the web page for that ppa, it should have instructions for adding the key to your apt keys.  Which ppa is it?

EDIT: nm, check out these instructions: [http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

It's this one: [http://ppa.launchpad.net/sargentd/ppa/ubuntu]("http://ppa.launchpad.net/sargentd/ppa/ubuntu")

FWIW, I haven't got the foggiest recollection of why I added it in the first place!

---

### Post by Roger Allott on 2009-11-27
> **lykwydchykyn said:**
> 
EDIT: nm, check out these instructions: [http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

That little tutorial seems to have done the trick. Cheers.

---

