---
title: "Really need wireless help Belkin 75d7000 ver4"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by nal on 2005-10-15
Ok Sadly I am asking this on windows since i cant get any internet on ubuntu.

I just installed Ubuntu breezy  and used the cd to install ndiswrapper

I put the inf file and stuff in a folder went to that folder and did ndiswrapper -i and the name of the inf file  (worked fine)
I did ndiswrapper -l and it showed driver present.
so i do ndiswrapper -m
then modprobe ndiswrapper
after that i go into the admin networking and its not there
so i go back to terminal and do ifwconfig and it just shows lo no wireless eth0 no wirless.   Please some one help me.  I im REALLY impressed on the look and feel of this ubuntu release and really really want to be on it only but i must have the wireless card working cus i cant conntect to the net anyother way.

---

### Post by breakthestate on 2005-10-15
what is the exact readout when you type ndiswrapper -l ?

---

### Post by nal on 2005-10-15
when i do ndiswrapper -l it shows
bcmwl5a driver present

thats all it shows, I tried it in suse 10 and shows the same thing.  i have no clue what to do now and i really want to get straight Ubuntu  I hate having to go to windows for the net.

I have tried the bcmwl5 that came with it but that said invalid driver or something,  I checked alot of help files and they all say the inf file i have is the right one, but it dosent say hardware present just driver present, i know the hardware works cus im on windows using it right now(only i can use net is this card)  If you can help please do i really really need this working. oh cought something its not 75d7000 its f5d7000 ver 4 im sorry i put 75d hit wrong key

---

### Post by nal on 2005-10-15
Ok got it working

I did have a bad driver, I searched and searched and finaly got it all is well now.

---

