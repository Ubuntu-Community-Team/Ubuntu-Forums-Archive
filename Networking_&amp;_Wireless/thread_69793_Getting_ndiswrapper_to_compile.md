---
title: "Getting ndiswrapper to compile"
date: 2005-09-27
forum: Networking &amp; Wireless
---

### Post by Comrade on 2005-09-27
So I installed Fedora Core 3, got ndiswrapper to work, etc. etc. 

I annihalated the FC3 partitions, put Ubuntu there, and tried to do the same thing for ndiswrapper. Granted, it did not work. 

What am I supposed to download - the [ndiswrapper-source.deb file]("http://ndiswrapper.sourceforge.net/debian/ndiswrapper-source_1.3rc1-1_i386.deb")? I have a tar.gz that I used for FC3 (not that I was expecting it to work). But I can't access the internet through my Linux partition (I'm on Windows right now), and so I need to download it onto Windows, put it onto a USB drive, and pull it back into Linux.(It would also be nice if someone could explain to me how to access my Windows partition's data on Ubuntu - this would speed things up a little.)

Ubuntu is based off of Debian, I assume, so I think I'm supposed to get the deb file. However, I am not sure, and so I decided to consult here first.

After I download the file, what am I supposed to do? On FC3 I did this:

make install
/usr/sbin/ndiswrapper -i <home>/whatever/.inf
/usr/sbin/ndiswrapper -l
modprobe ndiswrapper
dmesg
ndiswrapper -m

I have the .inf file and everything. I've gotten ndiswrapper to work before - I'm just not sure about Ubuntu. 

Thanks for the help guys and girls! :cool:

---

### Post by spd106 on 2005-09-28
First I suggest you try the ndiswrapper-utils package that is included on the install cd. You just then need to install the driver etc. I think the current version on hoary is ndiswrapper-utils_0.12+1.0rc2-1_i386.deb.
If this doesn't work or you want to compile from source may I recommend following the instructions on this wiki page [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Good luck

---

### Post by Comrade on 2005-09-28
I did not know that it was called ndiswrapper-utils. 

So I guess I'm supposed to apt-get install ndiswrapper-utils, with the cd in the drive?

I'll try to compile it from source. It should work, but if it doesn't, I will come back here and ask.

---

