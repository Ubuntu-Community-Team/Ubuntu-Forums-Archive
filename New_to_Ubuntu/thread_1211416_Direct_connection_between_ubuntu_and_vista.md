---
title: "Direct connection between ubuntu and vista"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by .:PiXi²:. on 2009-07-12
Hi

I need to set up a direct connection between my ubuntu machine and a machine running vista to transfer a large file. Since I'm new to ubuntu, I don't know how to do this with ubuntu. I assume it can be done as easy as connecting two WinXP machines with a crossover cable.
The difficult fact about this situation is that I don't have a crossover cable with me at this moment, but I assume there must be a way to solve this within the software.

Thanks in advance and sorry for my bad English.

---

### Post by JohnnySage50307 on 2009-07-13
Unfortunately, there is no such thing as a cross-connect cable solution to go between any Windows machine and Linux--the issue stems from how the OSs differ!

My best solution, set up an FTP server on your Ubuntu machine.  You can install one by typing:
sudo apt-get ftpserver
 
This will automatically run an FTP server program on your Ubuntu machine.  All that's left is for you to configure your router so that your Ubuntu machine can listen to Port 21 (TCP).  As a note, write down the IP address of your machine on the local network.

From your windows machine, you can open an FTP client and use your local network IP for the Ubuntu machine.  Log in as root, and you'll be able to transfer files to anywhere between your machines.  Best of all, should you ever need to transfer again, future runs only involve opening the FTP client on your windows machine!

---

### Post by nhasian on 2009-07-13
fortunately, there is an easier way then what JohnnySage50307 is suggesting.  you are right.  its as easy as connecting to windows computers via a crossover cable.  

simply connect your ubuntu and windows computer via an ethernet crossover cable and share a folder on your windows computer.  then right click on a folder and enable sharing on your ubuntu computer.  (You may have to reboot if it asks you to install samba).  then thats it.  both shares will appear on your network and you can access them from Places->network

easy.

if you dont have a crossover cable, only ethernet cables, you will need a switch or hub or router to plug both machines into.

alternatively if both of your computers have gigabit ethernet adaptors they will autosense wether your using a crossover cable or not and adjust itself to work properly.

---

