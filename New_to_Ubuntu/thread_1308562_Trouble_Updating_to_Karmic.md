---
title: "Trouble Updating to Karmic"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2009-10-31
I'm trying to upgrade my distribution from Jaunty to Karmic, but when it gets to the last package, I get this message.

>  Failed to fetch [http://nl3.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build1_i386.deb](http://nl3.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2build1_i386.deb) Size mismatch

Does anyone know what's going on with this? I could use the help. Thanks!

---

### Post by s.dalas on 2009-10-31
A lot of users have reported that couldn't upgrade cause of failed fetching files. I am one of these users... It is an upgrade problem. If you can go for a clean install, otherwise wait a few days to fix the problem

---

### Post by GonzalitoUY on 2009-11-02
Got the same problem, trying to update using alternate CD.I'll try the internet update (damn, I've already downloaded i386,amd64, and alternate i386, and now I've must download 500-600MB AGAIN???. Is not as if i got lousy bandwith ,1024k/128k)

---

### Post by defishguy on 2009-11-02
I discovered that I had the same problem today at work upgrading a computer lab.  It turns out that the http content filter in my school district was objecting to "sexy" in libsexy2.

---

### Post by ranch hand on 2009-11-02
If you are updating from Jaunty you should first make sure that Jaunty is plumb up to date.

Remove all but the generic video drivers.

Remove or rename your /etc/X11/xorg.conf file.

If you plan to use grub2 in Karmic you should in Jaunty;
A> remove, through synaptic, grub and grub-common
B>install grub-pc and grub-common
C>run;
```

update-grub

```
and
```

grub-install /dev/sda

```
or what ever is your case instead of sda.

Run;
```

gksudo gedit /etc/apt/sources.list

```
Change all the places that refer to jaunty to read karmic

Run;
```

sudo apt-get update

```
AND
```

sudo apt-get dist-upgrade

```
this should do it.

If at the end of the ordeal there is a warning having to do with dpkg, run;
```

dpkg --configure -a

```
do this until you no longer get that message.

Go to synaptic and click on "status" and see if you have "broken packages".  If so correct them.

Then and only then you can reboot into your nice new 9.10.

This is the safest way I have found in about 15 upgrades during testing.

---

### Post by lilredcougar07 on 2009-11-03
So, I'm pretty sure the content filter at my accommodations was not letting me download it because the filter was blocking the site since it had the word "sexy" in it. I went to my school and did the upgrade. Thanks anyways!

---

### Post by ranch hand on 2009-11-03
That is just sick.

---

