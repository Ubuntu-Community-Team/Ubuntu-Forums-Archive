---
title: "how to install to a specified location"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by adasti on 2010-10-06
scenario: i am booting from ubuntu 7.10 cd and want to install slackware linux. the iso image is mounted at /mnt/dvd and the target HDD at /mnt/hdd. what i cant figure out is which command and how to use. i read the man pages for apt-get, aptitude and dpkg and still couldnt find the solution. the guide im using tells me to use this command-line script

   # for i in a ap d e f k kde l n t tcl x xap y
    > do
    > installpkg -root /mnt/sda3 $i/*.tgz
    > done

(mnt/sda3 is /mnt/hdd in my case)
but it seems installpkg does not exist in ubuntu and i do not know how to replace it with one of the aforementioned commands.

---

### Post by k33bz on 2010-10-06
Can you post the link to the guide you are referring to?

---

### Post by adasti on 2010-10-06
> **k33bz said:**
> Can you post the link to the guide you are referring to?

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_Slackware_12_or_another_version_with_the_ISO_images_but_without_burning_them](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_Slackware_12_or_another_version_with_the_ISO_images_but_without_burning_them)

the second post, starting with ` You can also do this without USB and without copying iso files to another directory. `

---

### Post by k33bz on 2010-10-06
ok another question I noticed you stated this

iso image is mounted at /mnt/dvd

do you have the image burned to a dvd?

If so you dont need the command line for it, just boot from the dvd and it will start.

---

### Post by adasti on 2010-10-06
> **k33bz said:**
> ok another question I noticed you stated this

iso image is mounted at /mnt/dvd

do you have the image burned to a dvd?

If so you dont need the command line for it, just boot from the dvd and it will start.

no, the iso image is located on my main HDD. having a DVD-ROM device at hand would make things a lot easier, true that, but aint got one available.

---

### Post by k33bz on 2010-10-06
this might be of help to you

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")

[http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948")

---

