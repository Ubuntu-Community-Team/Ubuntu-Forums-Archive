---
title: "Vodem on 8.1"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ColormanNZ on 2009-02-10
Have installed Ubuntu 8.1 on my Toshiba laptop - love it. Need to install my Vodem E220. Have installed the deb but get error when starting "Vodafone mobile connect card for linux"

Comes up with

 Vodafone Mobile Connect Card driver for Linux needs the following files and dirs with some specific permissions in order to work properly: /etc/ppp/pap-secrets should have 0660 mode, found 0600 /etc/ppp/chap-secrets should have 0660 mode, found 0600

I figure I have to change permissions but says they dont belong to me! Thought I owned every thing on my computer! Bet its an easy fix. Please type answers slowly as I am a nebie to linux.

---

### Post by Temposs on 2009-02-10
Those files rightly belong to root. In order to change the permissions, you should in the terminal use something like:

```
sudo chmod 0660 /etc/ppp/pap-secrets
```

this should allow you to temporarily 'own' the file and change the permissions.

---

### Post by Temposs on 2009-02-10
In case you'd like to understand more completely how files on your Ubuntu system work in terms of permissions, take a look at this page: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ColormanNZ on 2009-02-12
Thanks  - worked a treat, now I can dump Vista.

---

### Post by ColormanNZ on 2009-04-23
Have loaded 9.4 and lost my vodem software. tried to reinstall but when running the deb the "Install Package" icon is grayed out. Any ideas.

---

### Post by Temposs on 2009-04-23
you need to check the permissions and the owner on the deb file.

example:
```
ls -l vodem-installer.deb
```

where "vodem-installer.deb" is the name of the actual file.

---

### Post by kiwimenace on 2009-07-06
hi colorman, i take it you are a kiwi like my self, im also having trouble getting my vodem to work in 9.04 ubuntu, just wondering how you got on so far. if youve got it working perhaps you could fill me in on the details.
kind regards

---

### Post by ColormanNZ on 2009-07-07
Its easier than you think 

Remove any vodafone connect card software you have installed

Right click on network icon top right
Select Edit connections
Choose mobile broadband
Select Vodafone Unrestricted
Save and thats all.

Loads automatically works a treat.

---

### Post by kiwimenace on 2009-07-08
Thanks for your reply colorman.
Yes it eventually worked me, just didnt want to do it right away for some reason, had tried what you said and didnt want to work initially but now it has, cool!
have a good one mate.

---

