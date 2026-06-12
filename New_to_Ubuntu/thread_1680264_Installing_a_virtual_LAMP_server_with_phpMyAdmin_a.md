---
title: "Installing a virtual LAMP server with phpMyAdmin and PEAR"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by nOxOq on 2011-02-02
Hy! I'm a beginner in Ubuntu, but lately I have to learn it. I'm using WinXP on my laptop, but now I will work on a PHP project that later will be moved to an Ubuntu Server machine. Because of that I want to make a virtual server for testing my code at our LAN. I downloaded and installed Oracle's VirtualBox. Set up an ubuntu virtual machine set the network to the laptops wireless card with bridge (I'm connecting an ADSL router via wireless card) and installed Ubuntu Server 10.10 on it. At installation i checked the option LAMP server, but I didnt realised that server have apache mysql and php installed on it so I installed all of them manually like written in the ubuntu help manuals. The virtual machine has the 192.168.1.7 IP address. When I type it in the browser in Win it says that It works!, so the apache server is running. I made a testphp.php file and tryed to access it and it works too. I installed SSH and I can access the virtual machine with WinSCP (I'm logging in withmy root user name and password, but I dont have the right to edit or copy files, I think its a permission problem, but its not my biggest problem). The point where I have stuck is the mysql and the phpmyadmin. I installed both of them, but when I try to access it in my browser it says that the requested URL /phpmyadmin was not found on this server.

So the question is that what I have to do above the default installation process to get phpMyAdmin to work on LAN?

---

