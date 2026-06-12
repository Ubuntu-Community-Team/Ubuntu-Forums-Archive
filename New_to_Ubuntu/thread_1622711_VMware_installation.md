---
title: "VMware installation"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Rakeshvijayan on 2010-11-15
Hi friends 


 I am was usual windows user .i change my win7 and install ubuntu . i want install vmware in ubuntu 
i tried but i get  errors ,that may my lack of my knowledge or package problem .
I write this letter for help me some one 
1)where should  i get good vmware installation package 
2)what should i do

I followed this instruction 
--------VMware Workstation 7.0.1-227600 x86_64 Linux

* How To Install

   -Open a terminal and 'cd' to the directory containing the .bundle file
   -Run: sudo chmod +x VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
   -Run: sudo ./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
   -Follow the onscreen instructions to install

* How To Use Keygen
-Open a terminal and 'cd' to the directory containing the keygen
-Run: sudo chmod +x vmware-keygen_x86_64
-Run: ./vmware-keygen_x86_64-------------------

---

### Post by adwhitenc on 2010-11-15
The best plan would be to install directly from the website and make sure to download the Linux version of vmware player. 

Could you possibly share what the errors were?

---

### Post by fatharraxman on 2010-11-15
did you tried > sudo apt-get install vmware ?

---

### Post by Rakeshvijayan on 2010-11-15
This is the package that  i  use to install VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle. i copy that it my Desktop iI tried to install by terminal 
message was 
(

rakesh@rakesh-desktop:~$ '/home/rakesh/Desktop/VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle' 
bash: /home/rakesh/Desktop/VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle: cannot execute binary file
rakesh@rakesh-desktop:~$ cd Desktop/
rakesh@rakesh-desktop:~/Desktop$ ls
VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
rakesh@rakesh-desktop:~/Desktop$ ls -l
total 111120
-rwxrwxrwx 1 rakesh rakesh 113783072 2010-11-14 07:24 VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
rakesh@rakesh-desktop:~/Desktop$ ./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle 
bash: ./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle: cannot execute binary file
rakesh@rakesh-desktop:~/Desktop$ sudo ./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle 
[sudo] password for rakesh: 
./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle: 1: Syntax error: Unterminated quoted string
rakesh@rakesh-desktop:~/Desktop$ sudo ./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle 
[sudo] password for rakesh: 
./VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle: 1: Syntax error: Unterminated quoted string
rakesh@rakesh-desktop:~/Desktop$ 
)
 I am using athlon processor and 4 gb ram



















9

---

### Post by Rakeshvijayan on 2010-11-15
h

---

### Post by Rakeshvijayan on 2010-11-15
> **fatharraxman said:**
> did you tried  ?
  yes i tried 
rakesh@rakesh-desktop:~$ cd Desktop/
rakesh@rakesh-desktop:~/Desktop$ ls
new file
TS_WinServer2008_Applications_Infrastructure_70-643_with_Bon-{370fb236-9b79-4654-944f-aac3ffeac366}.dtapart
VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
rakesh@rakesh-desktop:~/Desktop$ sudo apt-get install VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle
rakesh@rakesh-desktop:~/Desktop

---

### Post by fatharraxman on 2010-11-15
I searched your problem in google using the words > VMware-Workstation-7.0.1-227600.x86_64.NoTools.bundle: cannot execute binary file
many of the answers advice you to download again from
 [http://www.vmware.com/downloads/login.do](http://www.vmware.com/downloads/login.do)

---

