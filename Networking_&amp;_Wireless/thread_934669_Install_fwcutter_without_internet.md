---
title: "Install fwcutter without internet?"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by PFSpectrum on 2008-09-30
Ok, i downloaded the tar.gz file for fwcutter off of the website on my windows partition because i don't have internet access on my Ubuntu partition. so now i have the tar.gz file on my desktop but i have no idea how to install it now. I cannot get a wired connection either because my whole house is wireless. I already have the drivers and i have ndiswrapper installed fine. I just have to install the fwcutter. Someone help me do an offline install?

---

### Post by minigeek on 2008-09-30
Login to Ubuntu.

Open a terminal session and su to root

cd to the windows partition . Locate the fwcutter.tar.gz

Copy tar to your home directory
cp -v fwcutter.tar.gz /home/<username>

Change to the home directory
cd /home/<username>

Untar the fwcutter
tar zxf fwcutter.tar.gz

cd in to fwcutter directory
cd fwcutter

Run the following commands to install
./configure&&make&&make install

---

