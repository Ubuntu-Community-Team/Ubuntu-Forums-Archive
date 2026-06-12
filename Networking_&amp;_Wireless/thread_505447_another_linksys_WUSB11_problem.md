---
title: "another linksys WUSB11 problem"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by pumpkinking11 on 2007-07-20
ok here's the lowdown...

after much time spent browsing the forums, i was able to install build-essentials and ndiswrapper.  i then proceeded to install the current driver for my adapter off the linksys website.  i accidentaly ndiswrappered (its a verb now :D) another file that wasnt a driver, so now 'ndiswrapper -l' shows the first non-driver file as 'invalid driver!' and 'driver installed' for the real file.  i tried to remove the first one using 'ndiswrapper -r Wlan.ini' (thats the name of the file) while in the directory of the file, but it wont work.  i think this is because its not an .INF file.

before i installed the driver after i just plugged in the network adapter, i was picking up my home network (which comes from a belkin router, ill get the model number if that helps; also, its upstairs and this computer is in the basement, this migh be too far, but my laptop works fine down there so i dont think thats the problem).  now, i dont even see it when i try to fool with the network settings under administration.  also, im using ubuntu 7.04 (i think).  

i spent half of yesterday trying to get this to work.... i hope someone can help me.  thanks in advance.  also for anyone else with similar overall problems, i used this tutorial to get the driver installed: [http://doc.gwos.org/index.php/HowToUbuntuWireless](http://doc.gwos.org/index.php/HowToUbuntuWireless)

---

### Post by pumpkinking11 on 2007-07-21
bump :(

---

### Post by kevdog on 2007-07-21
To remove the old driver -- (you can not have two drivers ndiswrappered at the same time), the syntax
sudo ndiswrapper -r ****  <--- do not include the .inf extension just the prefix

Another way to do it is the following (brute force method)
cd /etc/ndiswrapper
sudo rm -R *

Then do an ls to make sure no files or directories are listed inside the /etc/ndiswrapper directory.  You want it completely empty.

---

### Post by pumpkinking11 on 2007-07-21
ok i uninstalled the wrong driver and the real driver, and reinstalled the real one.  then i plugged in the adapter.  now i can see the belkin wireless network, and it has 0% next to it.  i also set it to DHCP auto detect for ip address.  but it still doesnt work.  also, when i type lsusb, it shows my mouse and its name, but for the adapter it only shows:

Bus 002 Device 003: ID 1915:2233

without saying what kind of device it is.  not sure where to go from here.  but i can see the network now, so thats a start, thanks.

---

