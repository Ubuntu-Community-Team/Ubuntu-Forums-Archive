---
title: "need to open an uif file"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-13
any recommendations?

---

### Post by sisco311 on 2009-09-13
convert it to .iso with uif2iso.

if you are using karmik:
```
sudo apt-get install uif2iso

uif2iso myfile.uif output.iso
```

if you are using an older versions of ubuntu, then you have to compile it from source:
```
sudo apt-get install build-essential zlib1g-dev libssl-dev unzip
mkdir /tmp/uif2iso
cd /tmp/uif2iso/
wget http://aluigi.altervista.org/mytoolz/uif2iso.zip
unzip uif2iso.zip
sudo make -C src PREFIX=/usr/local all install
cd

uif2iso myfile.uif output.iso
```

---

### Post by Insperatus on 2009-12-09
Worked for me! \\:D/

Thanks sisco =D>

---

### Post by VeterinaryPathologist on 2010-07-13
You can burn a disk from a .UIF file with NeroLinux 4 ([http://www.nero.com](http://www.nero.com))

---

### Post by LinuxHelper on 2010-08-26
I was stuck and couldn't find a way to convert an iso to an uif, until I found this article which breaks down the commands and gives good details.

There is also some screenshots for windows users who need an [uif to iso converter]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

