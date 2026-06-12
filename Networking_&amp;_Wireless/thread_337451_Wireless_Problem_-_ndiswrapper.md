---
title: "Wireless Problem - ndiswrapper"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Sierra_Dave on 2007-01-13
Hi,

I am trying to put ndiswrapper in and when I tried the command "Make inactive" or "make" I get invalid command.

Any help would be appreciated.

Thanks,
Dave](*,)

---

### Post by jhunholz on 2007-01-13
I'm not sure what you're trying to do.  Can you be a little more descriptive of the command you're using and what it's intended purpose is? Then I can help see what you're doing wrong.

---

### Post by Sierra_Dave on 2007-01-13
Hi,

This is how far I have been able to go with terminal so far:

carol@carol-laptop:~$ cd /home/carol/downloads/ndiswrapper-1.34
carol@carol-laptop:~/downloads/ndiswrapper-1.34$ cd
carol@carol-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname -r
carol@carol-laptop:~$ ln -s /usr/src/linux-2.6.15-26-386/lib/modules/VERSION/build
carol@carol-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname -r
carol@carol-laptop:~$

Thanks,
Dave



I

---

### Post by Sierra_Dave on 2007-01-14
Isn't there a package installer that I could use to install ndiswrapper that would be easier?  I am trying to get wireless card up and working on laptop.  

Thanks, Dave

---

### Post by chamberlain2006 on 2007-01-14
Just do "sudo apt-get install ndiswrapper-utils1.8 ndiswrapper-common".  That should install the necessary program.  Then do "ndiswrapper -i yourdriver.inf" to install the windows driver.

---

### Post by Sierra_Dave on 2007-01-14
Hi,

I tried that and the response was package not found.  I have downloaded, transferred and extracted the ndiswrapper files.  

I tried using terminal and those commands w/o success.  Using Synaptic Package Manager, I cant get it to add the downloaded package - ndiswrapper.

Another poster indicated that he was able to do this on Edgy and I am still on Dapper on the laptop.  It should load the same on dapper.

](*,) 

Dave

---

