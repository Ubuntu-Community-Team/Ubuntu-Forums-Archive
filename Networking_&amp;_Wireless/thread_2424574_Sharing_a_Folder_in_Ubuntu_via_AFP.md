---
title: "Sharing a Folder in Ubuntu via AFP"
date: 2019-08-10
forum: Networking &amp; Wireless
---

### Post by zergling on 2019-08-10
Hello Everyone,

Could someone please explain to me how to share a folder/file in Ubuntu using AFP?

In my Mac I did the following:

System Preferences -> Users & Groups -> I create a user zergling

System Preferences -> Sharing -> Enabled File Sharing -> Options -> Enabled Share files folders using AFP -> Add user zergling with read & write permission

Everything works wonderfully... I am able to access the Mac's files/folders from my Ubuntu machine, but how do I do the other way? How do I share a folder in Ubuntu and being able to see it from my Mac?

If possible I would rather not install samba.

Thank you in advance.

---

### Post by DuckHook on 2019-08-10
You need to install *something* on your Linux box to act as a file server. This can be Netatalk, NFS or Samba. Optionally, you can SSH into your Linux box from your Apple box and transfer files with SCP or SFTP/FTPS. Every solution requires the installation of some sort of server component because the default install of Ubuntu desktop is not designed to make files available to the big bad outside world (for security reasons).

If you want your Apple box to see files natively, then Netatalk is the FOSS implementation of AFP. [Instructions here]("https://mycyberuniverse.com/linux/afp-and-bonjour-under-linux.html"). Note that Avahi is already installed in Ubuntu by default, so you don't need to install it separately. Just make sure you follow the configuration instructions in the link.

**DISCLAIMER** I have no personal knowledge of using Netatalk or of Apple file structures in general. I do not use Apple products. Above instructions are nothing more than blindly relaying the result of web searches, so I cannot help you with details or problems, and unless someone familiar with Apple comes along, you are on your own as far as troubleshooting goes.

---

### Post by zergling on 2019-08-10
Thank you so much for the info but unfortunately, it did not work for me but I was able to solve my issue by doing the following


```
sudo apt-get install netatalk

sudo nano /etc/netatalk/afp.conf

[seagate_blue]
 path = /media/zergling/seagate_blue
 valid users = zergling

sudo /etc/init.d/avahi-daemon restart
```

I hope this will help someone in setting up their AFP network between a Linux box and a MacOS.

---

