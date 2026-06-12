---
title: "Reinstall Ubuntu with data intact?"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by garrison0fmars on 2010-12-23
Not sure if this is the appropriate area, and if not please move to the appropriate section.

Is there anyway to reinstall Ubuntu (10.4 LTS) while keeping your usernames and data intact? The installation on my hard drive broke for some reason, and the only way I can get an OS working is to (re)install one. So I'm wondering is there anyway I can do this without losing my user settings and data on the hard drive?

---

### Post by ibe2fly4chu on 2010-12-23
Well from what i can remember i did recall a friend telling me he was able to move ONLY the the necessary files and just swap them out with the existing one without looseing/formatting his hdd. So to answer your question yes i think it is possible but i cannot recall how to do it at this time. 


From what i have experienced with ubuntu however a fresh install always is better than just about any other options.

---

### Post by sikander3786 on 2010-12-23
The only way you can preserve your settings is to use a separate /home partition. That way, whenever you re-install, just define your /home partition from manual partitioning and choose not to format it. So you basically need 3 partition then. '/', /home and Swap.

As your install is broken at the moment, it might be a pain to move your /home to a separate partition that would otherwise have been easier if you were booted in Ubuntu.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

You'll need to chroot your install and do the steps mentioned in above post. Not even sure that would be successful.

Post back if you decide to go that way, or wait for some other replies as there might be some other solution that I am missing here.

---

### Post by bodhi.zazen on 2010-12-23
> **sikander3786 said:**
> The only way you can preserve your settings is to use a separate /home partition. That way, whenever you re-install, just define your /home partition from manual partitioning and choose not to format it. So you basically need 3 partition then. '/', /home and Swap.

As your install is broken at the moment, it might be a pain to move your /home to a separate partition that would otherwise have been easier if you were booted in Ubuntu.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

You'll need to chroot your install and do the steps mentioned in above post. Not even sure that would be successful.

Post back if you decide to go that way, or wait for some other replies as there might be some other solution that I am missing here.

While that will work for data in /home, it will not work for system information such as /etc/passwd and /etc/groups or any other system wide customizations.

You can try moving /home to a separate partition and making a back up of /etc/passwd and /etc/group, but

You should, IMO, keep any data you want to keep separate from your OS including backups of any system files you make.

---

### Post by amjjawad on 2010-12-23
> **garrison0fmars said:**
> Not sure if this is the appropriate area, and if not please move to the appropriate section.

Is there anyway to reinstall Ubuntu (10.4 LTS) while keeping your usernames and data intact? The installation on my hard drive broke for some reason, and the only way I can get an OS working is to (re)install one. So I'm wondering is there anyway I can do this without losing my user settings and data on the hard drive?

What kind of problems do you have on your current installation so that you want to re-install?

---

### Post by garrison0fmars on 2010-12-23
> **amjjawad said:**
> What kind of problems do you have on your current installation so that you want to re-install?

Well, the problem originally was the update manager would consistency crash, but now the entire OS doesn't work upon loading...

---

### Post by amjjawad on 2010-12-23
> **garrison0fmars said:**
> Well, the problem originally was the update manager would consistency crash, but now the entire OS doesn't work upon loading...

Update Manager is a different case than the entire OS doesn't work upon booting.
What kind of errors/problems do you have upon booting?

---

