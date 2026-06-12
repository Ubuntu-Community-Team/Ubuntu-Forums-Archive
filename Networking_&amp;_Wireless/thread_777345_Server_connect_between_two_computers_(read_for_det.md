---
title: "Server connect between two computers (read for details)"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by iamthebest22 on 2008-05-01
I hope this belongs in here. I recently bought a mac mini, with 2GB of RAM, and I'm using a network switcher to connect it with my old laptop, an AMD 2000+ with 1 GB of RAM, to have those two run as a server. What I"m wondering is, now that I have two computers, what should I type in to have linux recognize both as one server? DO I still follow the same steps as in the online documentation? Or do I have to do something different? Also does the same also apply for the Apache program that I'm soon hoping to download to help manage my servers? Thank you for taking your time to answer this!

---

### Post by warp99 on 2008-05-01
> **iamthebest22 said:**
> I hope this belongs in here. I recently bought a mac mini, with 2GB of RAM, and I'm using a network switcher to connect it with my old laptop, an AMD 2000+ with 1 GB of RAM, to have those two run as a server. What I"m wondering is, now that I have two computers, what should I type in to have linux recognize both as one server? DO I still follow the same steps as in the online documentation? Or do I have to do something different? Also does the same also apply for the Apache program that I'm soon hoping to download to help manage my servers? Thank you for taking your time to answer this!

You want both computers to be seen as one server like a cluster, correct?

---

### Post by iamthebest22 on 2008-05-01
Yes, correct, sorry if I wasn't clear enough, this is my first time user server edition (i used the desktop edition)

---

### Post by iamthebest22 on 2008-05-01
BUmp, so yes, any help? I really need to run this server for my manga forum. Basically, as warp99 mentioned, I want to know, that in order for linux to recognize both laptops as one cluster server, is there anything different that I should do?

---

### Post by warp99 on 2008-05-01
> **iamthebest22 said:**
> BUmp, so yes, any help? I really need to run this server for my manga forum. Basically, as warp99 mentioned, I want to know, that in order for linux to recognize both laptops as one cluster server, is there anything different that I should do?

If you want a clustering file system you can use something like lustre:

[http://wiki.lustre.org/index.php?title=Main_Page#What_is_Lustre.3F](http://wiki.lustre.org/index.php?title=Main_Page#What_is_Lustre.3F)

or GPFS:

[https://help.ubuntu.com/community/SettingUpGPFSHowTo?highlight=%28cluster%29](https://help.ubuntu.com/community/SettingUpGPFSHowTo?highlight=%28cluster%29)

both of these are clustering file system usually for high performance computing, so this solution is most likely overkill. I think what your looking for is can I use the directories on both computers to be seen as one and the answer is of course using either NFS, SSHFS, or even Samba since you can access Linux, Windows, and OSX shares equally. More info can be obtained here:

[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29](https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29)

[https://help.ubuntu.com/community/SSHFS?highlight=%28sshfs%29](https://help.ubuntu.com/community/SSHFS?highlight=%28sshfs%29)

[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

Edit:

To answer you original questions you don't have to do anything different with the server version versus the desktop version. Linux is a module component OS so you just add or remove components for your particular application. 

The difference between the server version and the desktop version is that the server has a different kernel and no GUI plus some server applications, everything else is the same. 

If you like you can even use the desktop version and install all of the server applications and that will also work, but I would not advise using a GUI when the server is live because that's a security risk. 

Remember Linux is **NOT** Microsoft where you have twenty different versions and have to pay twenty different prices while most of the component applications are not interchangeable.

---

### Post by iamthebest22 on 2008-05-01
So basically, I won't be able to see the GUI, unless I install a desktop edition on it, which can cause security issues. That being said, I'm using the two computers (mac mini and pc laptop) to host a website, so anything else I also need to do?

---

### Post by warp99 on 2008-05-01
> **iamthebest22 said:**
> So basically, I won't be able to see the GUI, unless I install a desktop edition on it, which can cause security issues. That being said, I'm using the two computers (mac mini and pc laptop) to host a website, so anything else I also need to do?

I assume the Mac Mini will host Apache2 so you can use NFS to share the directories with the laptop. Don't install a GUI since it's not needed. If you need a graphical interface there are plenty of web based tools such as phpmyadmin for your database. You can just set up a LAMP stack.

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

There are millions of them out in the wild. What do you think runs the internet?

---

