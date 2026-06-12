---
title: "ubuntu dlna question help"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-10-30
I just purchased the iomega home media network hard drive (Nas).  It is set up as a DLNA media server. I can watch videos from it on my ps3, xbox and windows 7. I am looking for a program on ubuntu 10.10 so i can watch content from my nas.  Can someone recommend a program?. Thanks

---

### Post by P4man on 2010-10-30
xbmc
Be aware there is no maverick ppa for it yet (that I know off), but you can install the lucid version it works fine here on maverick. Awesome app.

---

### Post by hunter99507 on 2010-10-30
i tried to install xbmc and boxee but it doesnt work.  any other programs?

---

### Post by P4man on 2010-10-30
Try again. Try harder. Be more verbose :)
Seriously xbmc is the app you want.

Open a terminal and type

```
sudo add-apt-repository ppa:team-xbmc
```
```
sudo apt-get update
```

Then open the software center, go edit/software sources/other software. You should find 2 entries for team-xbmc. Edit them both and replace "maverick" with "lucid" (since the ppa doesnt provide packages for maverick yet, but the ones for lucid work fine).

Let it reload and then just install xbmc from the software center.

---

### Post by hunter99507 on 2010-10-30
[SIZE=2]Perfect that worked for me, thanks.

I did have one more question. Its a hard one so im not sure if you will be able to answer it. Like i said before i have the 
[/SIZE]**[SIZE=2]Iomega  Home Media 1 TB Network Attached Storage 34337[/SIZE]**

On windows 7 i can connect to it real easy under network. I cant figure out how to connect to it or even see it through ubuntu. I know that iomega doesnt provide software to connect to it for ubuntu, but there has to be a work around. Any ideas? Thanks

---

### Post by P4man on 2010-10-30
I strongly suspect you can just connect to it through places | network |
If it doesnt show up there automatically, try entering the IP

smb://192.168.0.3/

(replace with appropriate IP address).

---

### Post by hunter99507 on 2010-10-30
That worked. Thanks for your help.

---

### Post by srlake314 on 2011-04-04
None of those steps worked for me and xbmc isnt listed in software center :(.

---

### Post by srlake314 on 2011-04-04
s@blahblah:~$ sudo add-apt-repository ppa:team-xbmc
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
s@blahblah:~$

---

### Post by srlake314 on 2011-04-04
s@blahblah:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

