---
title: "Problem connecting to wired internet in China/ new to Ubuntu"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by bmold on 2008-12-02
Hi everyone, 

I suppose this is probably a dumb question, I am very new to Unix/ Ubuntu in general and am recently trying to make the switch (from windows). I am located in China right now, and in order to access the wired network at my school we have to install a program called "racer" (see link: [http://218.29.0.252/kuandai/self.jsp](http://218.29.0.252/kuandai/self.jsp)), the first link under the linux section, that allows us to connect to the internet provider. I downloaded and decompressed the tar/gz file but I'm not exactly sure what to do after that.. 

Basically my questions are

I understand how to install and do stuff as the root user. I am not exactly sure the parts about confirming the dhcp module or setting up the network interface, or the C share lib being more than 2.3.

Also, where should I extract the file to? Wherever I want? Is $dest_path just short for "put this file wherever you want and remember its location so you don't mess anything up later"?

How do I add it to the root user/ PATH environment?

Hope my questions aren't too stupid.

Here are the instructions for installing the program (they came with the file as a readme file:

1. It is necessary to have root privileges in order to use this client to access the network. Confirm the dhcp module (dhcpcd) have been installed on your Linux OS and the network interface have been set up to "use dynamic IP config". The version of C share lib in system is more than 2.3.

2. Install: Extract the installing file to the path denoted by $dest_path. $dest_path should be used below, and should be changed to the actual value when you use it. Then it is OK.

3. Environment setting: Environment variable RACERC=$dest_path should be added to the root user, and $dest_path should be added to PATH environment variable of root user.

4. Config: Edit the racer.ini to modify the value of server 1 and server 2. Server 1 and server 2 mean IP address of the server. Server 1 and server 2 should be set to one single IP if there is only one single IP address.

5. User's guide: 

Logon: $dest_path/racer/econ.sh start
check status: $dest_path/racer/econ.sh status
logoff: $dest_path/racer/econ.sh stop

---

### Post by philetus on 2008-12-02
What exactly is "Racer" supposed to do?

---

### Post by bmold on 2008-12-02
"Racer" is a program that allows us to connect to the network. It is a program from China unicom that stores a password and other user/ networking info. and allows us to connect to the internet. Without it the only website we can visit is the china unicom website that you can download the "racer" file from ( [http://218.29.0.252/kuandai/self.jsp](http://218.29.0.252/kuandai/self.jsp) ) i think it also provides some sorts of security features.

---

