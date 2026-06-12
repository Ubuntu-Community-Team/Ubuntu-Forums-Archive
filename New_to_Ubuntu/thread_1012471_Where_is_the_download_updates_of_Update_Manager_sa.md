---
title: "Where is the download updates of Update Manager saved? can copy? and install later?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by asaren on 2008-12-15
Hi All,

Where is the download updates of Update Manager saved?

Is it a files?

and Can i copy it and how to install later?

Thank you

---

### Post by Shhnap on 2008-12-15
The update manager get files from repositories, cache's them and then installs them. If you don't want to install them then just wait for later to install it when you're ready. Although i suppose there should be a way to just download and install later. Give me a moment, i'll check.


Solution:
Ok yes there is. Just run apt-get with the -d option. So:

sudo apt-get -d update
sudo apt-get -d upgrade

and then when you actually want to install:

sudo apt-get upgrade

just remove the -d

Hope that helps.

---

### Post by cdtech on 2008-12-15
This link will explain the Repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you go to the bottom of the page you'll see more links (ie..personal repository)

Hope this helps ya....

---

### Post by Ender41 on 2008-12-15
> **asaren said:**
> Hi All,

Where is the download updates of Update Manager saved?

Is it a files?

and Can i copy it and how to install later?

Thank you


 The files are downloaded to /var/cache/apt/archives
Others have given you the information about grabbing the files and installing later.
You can copy the whole lot of the files to say a cd and carry them to another machine and make use of them should you want to.

---

