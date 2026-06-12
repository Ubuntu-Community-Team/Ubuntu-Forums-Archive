---
title: "how to install wireless drivers offline?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by pedrorrf on 2010-02-06
I have ubuntu 9.10 on a netbook, and I'd like to install the drivers for the wireless card. I found instructions for my specific model, which involve using apt-get. But I have no internet on the netbook until I get the wireless to work... Is there any way of getting the files under windows and tell apt-get to use those files instead of connecting to the internet?  Thanks.

---

### Post by bkratz on 2010-02-06
What is your specific wireless model?  If not known you can find out with lspci (LSPCI in lowercase) in the terminal.

---

### Post by pedrorrf on 2010-02-06
> **bkratz said:**
> What is your specific wireless model?  If not known you can find out with lspci (LSPCI in lowercase) in the terminal.

 # lspci | grep Network 
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by airtonix on 2010-02-06
I hate it when people don't answer the original question.

Original Posters question is : 
How to make APT use local debs to install stuff that was obtained from another computer.

Answer : 

dpkg -i debfilename.


my netbook (hp mini 311-1018tu) also has a broadcom 4312 wireless chip, I managed to get bluetooth and wifi working with ndiswrapper (i assume ndiswrapper is what you need apt-get for ).

Show me the guide you talk about, maybe i can offer some observations.

also helps if you describe the netbook manufacturer, make & model.

---

### Post by bkratz on 2010-02-06
> **airtonix said:**
> I hate it when people don't answer the original question.

Original Posters question is : 
How to make APT use local debs to install stuff that was obtained from another computer.

Answer : 

dpkg -i debfilename.



Well that could be because there is a better way. In his case the files he needs are available on the installation disk!


To the OP see this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by sandyd on 2010-02-06
you dont need to use ndiswrapper.
The broadcom STA site says that that chipset is supported by the (wl) drivers.

Download these on a windows machine
[http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu5_i386.deb)

and transfer it to your netbook (assuming netbook is 32 bit...)
install them in order (from first link to last)

---

### Post by pedrorrf on 2010-02-06
> **airtonix said:**
>  
dpkg -i debfilename.


my netbook (hp mini 311-1018tu) also has a broadcom 4312 wireless chip, I managed to get bluetooth and wifi working with ndiswrapper (i assume ndiswrapper is what you need apt-get for ).

Show me the guide you talk about, maybe i can offer some observations.

also helps if you describe the netbook manufacturer, make & model.

 Thanks! Mine is a compaq mini 311, it's the very same hardware as the hp. Actually I wanted apt-get to install bcmwl-kernel-source, as I read somewhere that would do the trick. I'll try Carlee's suggestion.

---

### Post by bkratz on 2010-02-06
bcml-kernel-source is on the installation cd. Carlee's suggestion is really the best way to accomplish your goal.

---

### Post by sandyd on 2010-02-06
> **bkratz said:**
> bcml-kernel-source is on the installation cd. Carlee's suggestion is really the best way to accomplish your goal.
i didnt think dkms was tho.

---

### Post by bkratz on 2010-02-06
> **carlee said:**
> i didnt think dkms was tho.




You are right, that is one of the reasons I think your solution is the best.

---

### Post by pedrorrf on 2010-02-06
> **carlee said:**
> you dont need to use ndiswrapper.
The broadcom STA site says that that chipset is supported by the (wl) drivers.

Download these on a windows machine
[http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu5_i386.deb)

and transfer it to your netbook (assuming netbook is 32 bit...)
install them in order (from first link to last)

 For future reference, that did work, but patch must be installed before. Or at least I think it worked. iwconfig now shows eth1 IEEE 802.11 Nickname: "" Access Point: Not-Associated, which wasn't showing before.

---

### Post by lfabresm on 2010-05-23
I tried to do the Carlee's solution, but didn't work for me, the GDebi Package Installer says "Dependency is not satisfiable" for both.
I installed Ubuntu 10.04 on a HP Mini 311 mentioned before.
And I just have a wireless network available, no hardwired internet connection :(, but I'm still without the wireless adapter working.
 
Thanks.
 
PD: I'm totally newbie on Ubuntu :)

---

### Post by lfabresm on 2010-05-27
Finally I found a hardwire connection and all problems are solved, very easy

---

