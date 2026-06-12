---
title: "how to get wifi internet in ubuntu 12.04"
date: 2015-10-02
forum: Networking &amp; Wireless
---

### Post by anand_kumar_shukla on 2015-10-02
I just got my dell 9020 sff with ubuntu 12.04 and i want to connect  to Internet through my wifi. How should i do it ? It doesn't shows any  available connection. I Ran a system test and got these two relevant  results :-


Network/internet section says :- Error could not find  def gateway info in  /proc 

Networking/detect section says :- Intel corporation device 153a (rev 04)

I tried executing command lshw -c network and it shows intel every where with driver=e1000e
Output for lspci -knn | grep net -A2 is  just nothing
Please help me out brothers. i need an internet connection on this machine badly. I am building a website on some Classified Army document Leaks....

---

### Post by slickymaster on 2015-10-02
Hi anand_kumar_shukla, welcome to the forums.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by anand_kumar_shukla on 2015-10-03
I am having trouble in understanding that once i get this file to my machine (via usb) i have to simply save it as a text file orwhat do i have to do ???n  Finally i managed to run the shell script by providing sufficient permissions and got RESULTS (attaching the text file)[ATTACH]264799[/ATTACH]    Please Help Anybody....

---

### Post by praseodym on 2015-10-03
Obviously, the wifi card is not showing up. Check  the BIOS if you can activate it there. If it is a real BIOS (not an UEFI!!!) reset it to default

---

