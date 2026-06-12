---
title: "Internet Connection Problem... Please help."
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by linuxquest on 2006-11-20
I have installed Ubuntu 6.06 using VMWare on top of my Windows Server 2003. I am using ADSL 512KB broadband modem and I am having problems connecting to the Internet. My broadband ISP provider is streamyx.

This is what I did on my Ubuntu desktop...

1.	Press Alt+F2 and type 'gnome-terminal' (without the quotes)
2.	In the gnome terminal, I typed 'sudo pppoeconf' (without the quotes, of 	course)
3.	All I have to do is follow the instructions and click Forward and then 	finally restart the Ubuntu OS. (I also did configured my ISP's username and 	password).


After I get to my Ubuntu desktop, this is what I did

1.	I left-clicked on System --> Administration --> Networking and I tried to configure my IP address (I believe I have no problem configuring my IP address because I just chose DHCP).

Then, I try to browse the Internet by using Firefox in Ubuntu, but, there are still no internet connection.

Later, I open the gnome-terminal again and I typed 

alex@alex-desktop:~$ sudo apt-get install build-essential'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential 
alex@alex-desktop:~$

So what should I do? I really need to connect to the Internet. Please help.

:confused:

---

