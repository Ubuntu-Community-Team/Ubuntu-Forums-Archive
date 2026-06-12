---
title: "ubuntu is falling apart...:S"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by grobar87 on 2010-04-09
Hi,
my ubuntu is falling apart....i install updates few minutes ago and i don't know what is happend:S My pidgin is gone,K3b is gone,Exaile crush on every start up,audacious cruches when adding songs,not sound in amarok and bunshee,limewire works only 5 min and then gone...and the sound of all system is very very bad.Cannot open firefox,got some message "is already running".....
What is happend with my system???? :S:S:S:S:S
I run ubuntu 9.10 for 5 mounths and never have problem like this.What should i do,is reinstalling will help?I have separate home parttition,so i'm not gonna lose my files..right?
anyone pls help...and sorry for my english.

---

### Post by moetunes on 2010-04-09
If you haven't changed the sources.list file then try in terminal
sudo apt-get update && sudo apt-get upgrade
it might pull in any missing files from previous updates tho if you hadn't edited anything I'm suprised it borked so bad.

---

### Post by 311005901 on 2010-04-09
I'm sorry you're having issues...
Did you restart your computer after you updated?

---

### Post by grobar87 on 2010-04-09
Yes i restart laptop after update...and try sudo apt-get update and upgrade,but still the same.

---

### Post by ubunterooster on 2010-04-09
You could try to reinstall, keeping the old home partition for the new install but DO NOT install Lucid while using the oldhome partition. But you are backed up, I assume, so not much is in risk of data loss. You can use [clonezilla]("http://www.clonezilla.org") to copy partitions for safety in the event you mess something up and remove the home partition

---

### Post by zeroseven0183 on 2010-04-09
Are there any error messages when those two commands were executed?

good to see you here, Ubunterooster

---

### Post by grobar87 on 2010-04-09
no error message..everything seems to be normal just my programs not work properly...i reinstall ubuntu now...tnx for help guys.

---

### Post by LowSky on 2010-04-09
Hmmm are you sure your not running 10.04, because I am having the same issue running the Beta. It keeps removing all apps that are not tied into gnome.

Your home folder will still have all your files don't worry, and if you reinstall the missing apps all your settings will still be there.

---

### Post by grobar87 on 2010-04-09
No it's not lucid,i use karmic.I fix this with reinstall.:) tnx to all

---

