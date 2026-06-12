---
title: "Canon printer driver problem"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by JohnnyBa on 2011-03-08
Have downloaded the driver from Canon and followed other posts but finish up with the following on the terminal.
  	 	 	 	p { margin-bottom: 0.08in; }   	 	 	 	p { margin-bottom: 0.08in; }  john@Bates:~/Downloads$ sudo dpkg -i cnijfilter-mx350series-3.30-1-i386-deb 
 dpkg-split: error reading cnijfilter-mx350series-3.30-1-i386-deb: Is a directory 
 dpkg: error processing cnijfilter-mx350series-3.30-1-i386-deb (--install): 
  subprocess dpkg-split returned error exit status 2 
 Errors were encountered while processing: 
  cnijfilter-mx350series-3.30-1-i386-deb 
 Anyone know where i stuffed it up?
As a brand new user I am sure running into lots of problems, but I need to get the printer going before I can advance much.
 Thanks, John Bates

---

### Post by JohnnyBa on 2011-03-09
Finally got it sorted. Tried to open the extracted .deb file by double clicking install.sh with no result. I then used the option of opening install.sh in a terminal and all went well.John):P

---

### Post by maqtanim on 2011-03-09
In most of the cases, installation archive files contains an install.sh inside them. By just double clicking that install.sh file, the driver can be install with a breeze. 

By the way, welcome to the community! :D

---

