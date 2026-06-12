---
title: "Is my modem working?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by ser_virtual on 2007-10-25
Hi, I'm a newbi to Ubuntu Linux and I'm trying to get online either through dial-up or wirelles but without success. I'm running Gutsy on a Dell 1501 which has a so called softmodem  Conexant D110 chipset. I aparently installed the driver by Dell for Fi eisty and when I look at the Restricted Driver Manager it has marked the corresponding box. But really dont know if it is properly working and then how to activate the dial-up.
When I set the device properties the password seems to duplicate and I have no idea to which port the modem is connected (Under windows is COM3). Also the network monitor doesnot seem to recognize dial-up connecction. Thanks

---

### Post by mikeymouse on 2007-10-25
If you can get online here is one way to get dialup online.
 go to  [http://packages.ubuntu.com/dapper/net/gnome-ppp](http://packages.ubuntu.com/dapper/net/gnome-ppp)
download the  the correct package for your system (i-386,powrpc etc)
 Transfer gnome-ppp to your desktop and double click on it..
 you will notice when you go to the package page there are tabs for your version of Ubuntu.
 Hope this helps..
  If you cannot download gnome-ppp there is another way using  
 sudo pppconfig.. fill out the info and then go online  : to connect  sudo pon providers name and download what you require.. to disconect sudo poff.
 I will drop in later to see if your succesfull.
 good luck, hope i got everthing..:)
 mikeymouse

---

### Post by rundee_f on 2007-10-25
if u want to dial up u can easily use wvdialer but the problems here (i guess) is the modem.. i also use conexant chipset modem and base on linuxant.com, conexant doesnt have a 56 kbps driver for free!! aaarghh.. so i cant go dial up coz the max speed is only 14.4 kbps.. :(

---

### Post by mikeymouse on 2007-10-26
You could try Xandros , it worked quite well with my winmodem. I just cannot remember if it was the same modem you have or not..
Good Luck
mikeymouse

---

### Post by mikeymouse on 2007-10-26
Yep my modem in my dell 930 was a conexant, Xandros found it just fine and i had no problem getting online. 
 mikeymouse

---

### Post by ser_virtual on 2007-10-29
I'll try your tips today and see what happens. Thanks

---

