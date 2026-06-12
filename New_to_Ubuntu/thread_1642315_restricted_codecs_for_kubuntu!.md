---
title: "restricted codecs for kubuntu!"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-12-10
I am using Kubuntu 10.04 and i do not have an internet connection! could any pls give the link for downloading the restricted codes for playing mp3,acc, and opening rar files,etc

---

### Post by cptrohn on 2010-12-10
1 Make sure you go to Medibuntu.org and open a terminal and copy and paste this ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then after that process has finished use ```
sudo apt-get install kubuntu-restricted-extras
```

If you want to play DVDs then use ```
sudo apt-get install libdvdcss2
```

Then if you REALLY want to get a bunch of great codecs use this command ```
sudo apt-get install ffmpeg
```

That should get you a great start for Multi-media in kubuntu.

---

### Post by 1991sudarshan on 2010-12-10
> **cptrohn said:**
> 1 Make sure you go to Medibuntu.org and open a terminal and copy and paste this ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then after that process has finished use ```
sudo apt-get install kubuntu-restricted-extras
```

If you want to play DVDs then use ```
sudo apt-get install libdvdcss2
```

Then if you REALLY want to get a bunch of great codecs use this command ```
sudo apt-get install ffmpeg
```

That should get you a great start for Multi-media in kubuntu.

i do not have an internet connection to install form the shell. i just want the repository links for that!!

---

### Post by cptrohn on 2010-12-10
Oh sorry. There is a way you can put all of it on a flash drive or a CD posted here in a few places.  I have never had to do it that way though.  If you search the forums it should come up though... or maybe go to kubuntuforums.net and ask there,  I use KDE as well and find that site very helpful for KDE specific information.

---

### Post by 1991sudarshan on 2010-12-10
thank you! any way i found them after a long google search!

---

### Post by cchhrriiss121212 on 2010-12-10
For future reference you could try using Linux Mint, it is basically Ubuntu but includes all of these codecs on a fresh install.

---

### Post by desnaike on 2010-12-10
You have a great option here [http://www.linuxcd.org/view_distro.php?id_distro=452](http://www.linuxcd.org/view_distro.php?id_distro=452) it's the entire canonical repositories on dvd's and the price is great 20.00 if u think it's a good investment. or just stop at starbucks once or twice a month and use the free wifi

Good Luck

---

### Post by 1991sudarshan on 2010-12-11
the problem is the codec debian packages are creating non ending dependencies!!!:(

---

### Post by 1991sudarshan on 2010-12-11
> **desnaike said:**
> You have a great option here [http://www.linuxcd.org/view_distro.php?id_distro=452](http://www.linuxcd.org/view_distro.php?id_distro=452) it's the entire canonical repositories on dvd's and the price is great 20.00 if u think it's a good investment. or just stop at starbucks once or twice a month and use the free wifi

Good Luck

I am using a desktop and it's not possible to carry my system to a wifi zone;)

---

### Post by 1991sudarshan on 2010-12-11
it was very easy to install the necessary plugins in ubuntu! it just show the extra codes to be downloaded.

---

