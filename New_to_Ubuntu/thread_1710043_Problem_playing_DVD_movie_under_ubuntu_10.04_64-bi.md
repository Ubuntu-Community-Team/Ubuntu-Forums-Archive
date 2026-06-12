---
title: "Problem playing DVD movie under ubuntu 10.04 64-bit machine"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-03-19
Hi, 

I'm following a link as below to get my DVD playing under ubuntu 10.04 64-bit machine. I hope to play any DVD like finding nemo on my machine. Another laptop has successfully done, but this one is really strange :-(. The problem is simply it cannot be played/read.. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10")


Thanks in advance..

-alfa-

---

### Post by grahammechanical on 2011-03-19
You posted the link as code. You can use the icon that looks like the planet Earth with a single link from a chain, then you will create a link that can be clicked.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10")

You do not say what is going wrong or how you need help.

Regards.

---

### Post by alfa_80 on 2011-03-19
> **grahammechanical said:**
> You posted the link as code. You can use the icon that looks like the planet Earth with a single link from a chain, then you will create a link that can be clicked.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10,%2010.04%20%28i386,%20amd64%29%20and%2010.10)

You do not say what is going wrong or how you need help.

Regards.

Thanks. I've improved it..

---

### Post by uRock on 2011-03-19
You will need to run these two commands from [this link]("https://help.ubuntu.com/community/Medibuntu") to install the 64bit package needed for DVD decryption. ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb 
``````
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by alfa_80 on 2011-03-19
> **uRock said:**
> You will need to run these two commands from [this link]("https://help.ubuntu.com/community/Medibuntu") to install the 64bit package needed for DVD decryption. ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb 
``````
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

I've already run those two codes about 4 times but when I tried to play with VLC media player, it is just not reading from it. What should I do?

---

### Post by uRock on 2011-03-19
> **alfa_80 said:**
> I've already run those two codes about 4 times but when I tried to play with VLC media player, it is just not reading from it. What should I do?

Have your tried any other DVDs or just the one? 

Did the installs return any errors?

Is the DVD you are using very new? I ask because I have had some newer DVDs that had encryption couldn't be read.

---

### Post by alfa_80 on 2011-03-19
> **uRock said:**
> Have your tried any other DVDs or just the one? 

Did the installs return any errors?

Is the DVD you are using very new? I ask because I have had some newer DVDs that had encryption couldn't be read.

Yes, I've tried with 2 DVDs..

No error returned.

The DVDs are not really new. Also, both of them can be played in another 32-bit machine ubuntu 10.04 out of the box. It's nothing to do with the DVDs actually, but my machine configuration is not right, i guess.

Any ideas?

---

