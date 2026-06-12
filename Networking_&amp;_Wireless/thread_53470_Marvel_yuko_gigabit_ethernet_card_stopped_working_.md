---
title: "Marvel yuko gigabit ethernet card stopped working after upgrade"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by Nasir Amra on 2005-08-01
hello,
    I've installed ubuntu 5.04 and did an update ; upgrade as well as follow through most of the software install portions of the unofficial guide for ubuntu. Now , the marvel yuko gigabit ethernet on my gigabyte 848p motherboard has stopped working and I can't ping any machines on my network. The ifconfig shows no Rx or Tx packet counts ( both are zero). I've read somewhere ( I believe here) that there is a driver problem with the gigabit ethernet within the kernel ( I have 2 kernels installed 2.6.10 and 2.6.11, both don't have a working ethernet ). My problem is that although I can use a live kanotix cd and get the ethernet working, I don't know how to resolve this problem with the machine cut off from the internet ( my machines are in a lan and connect via a linksys router).  Any help , short of erasing the partition and reinstalling? I  have tried booting with acpi=off , but that does not work.  Is there a way to ftp a working linux kernel (i.e,, an ethernet working kernel -- what kernel does 5.04 come with? and from where can I get the binary .deb and install it. 
      Any help would be greatly appreciated.

---

### Post by kleeman on 2005-08-01
You are in luck  :)  :)  :razz:  :razz: I wrote a howto on this very subject:

[http://www.ubuntuforums.org/showthread.php?t=47615](http://www.ubuntuforums.org/showthread.php?t=47615)

I have this card (actually a Yukon 2) and am using hoary right now with it....

---

### Post by Nasir Amra on 2005-08-01
My problem is which comes first : the chicken or the egg  :) . The computer is disconnected from the internet and therefore I can't download anything. I tried following your post , but when I came to compile the linux source , I discovered that I didn't have a compiler installed !! In the end , it was simpler to get a $8 ethernet realtek pci card and get on line again ( and I can stop having my kids saying see I told you windows was better then linux  :) ).

---

### Post by kleeman on 2005-08-01
Yeah right know the problem! Actually now you have the internet you can install the compiler headers etc and get the other card working  :)  :)  :)  :)

---

