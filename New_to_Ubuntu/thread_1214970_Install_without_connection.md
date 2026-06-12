---
title: "Install without connection"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Moh'd32 on 2009-07-16
Peace,

Firstly I wanna thank you for this great community,
I believed in all what Eric Raymond said in his article, so I am going to ask my question politely, that I have to work hard then I ask, so let's start

I have downloaded UBUNTU on the main page 9.04 and installed it on my laptop,
the bad thing is I don't use broadband, router or something alike, what I use is USB wireless device so I have to run the exe file, I read somewhere that I have to run the inf file in the same directory but it does not work,

so search for how to run an exe file on ubuntu, I found a file called wine it is not an Emulator like what the main website says, but it runs an exe file,

the bad thing is I have to install it in the terminal that requires a connection.

the good thing is I found it with a file called key, but could not install it I believe the format is not supported so I googled again to find out how to install programs without connection

I found a way by clicking on add/remove under applications by following this guide

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

but either I have to have a connection or the wine is not listed

please help me and any question you wanna ask I will answer so you get the clear picture, I really worked hard and it's enough to use vista that does not respond all the time, and sorry for my bad English.

by the way, I am using now vista business on another laptop that makes it harder to contact you whenever I can !!

---

### Post by Terry of Astoria on 2009-07-16
The Windows drivers will not work for Ubuntu (except for using NDISWrapper). I suggest connecting via a network cable if possible first, and sorting out a proper driver for your USB wireless. You may want to be a bit more specific with your questions. What, for example, is your USB wireless card's brand name, and model? Either there is or isn't a proper driver for it. If not, just buy a new wireless card, making sure it's compatible with linux.

---

### Post by t4thfavor on 2009-07-16
There may already be a proper driver installed for your usb card, is it a modem (like a verizon aircard) or is it a wifi card. Both tend to have adequate support under Ubuntu. You will definately not have good luck with the Windows driver. 

As a side note you will not need an internet connection to install, just for updates, and browsing.

---

### Post by Moh'd32 on 2009-07-17
That's what I read under the usb wireless device:

Huawei
Model: E220
HSDPA USB MODEM

so does it work ?

I'm not sure if I can buy a new one

so any suggestion on how to install wine ?

---

### Post by Arup on 2009-07-17
Follow the instructions on the attached pdf, should work out. [http://sharebee.com/028beaad](http://sharebee.com/028beaad)

---

### Post by darolu on 2009-07-17
> **Moh'd32 said:**
> That's what I read under the usb wireless device:

Huawei
Model: E220
HSDPA USB MODEM

so does it work ?

I'm not sure if I can buy a new one

so any suggestion on how to install wine ?

Following this instructions may work:
[http://ubuntuforums.org/showthread.php?t=595064](http://ubuntuforums.org/showthread.php?t=595064)

You can install wine with sudo apt-get install wine, but that won't solve your problem, windows drivers do not work with linux kernels.

Editing: I found out Linux kernel has the drivers for your usb modem since version 2.6.20; so you should already have what you need to make it work: [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)

---

### Post by Moh'd32 on 2009-07-18
About this link
 [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)
 
 looks like it will work but some problems
 
 but I'll say what I did, firstly Ubuntu 9.04 does not show the huawei icon on the desktop
 so I ignored this thing then went to the terminal and typed : tar xjvf huawei.tar.bz2
 looks like it worked it showed me some files
 then typed cd huawei and now I am in huawei
 
 BUT

after I type su

it requires me a password that I can't even type anything !!

I thought the reason is I disabled the PIN code of the huawei so I enabled it under Vista
again it requires me password, even if we considered the password is the same as the password of the administrator, I can't type nothing, neither letters nor numbers

if the reason is that ubuntu does not show the icon of huawei, then i followed the same
steps under UBUNTU live v7.10 and still requires password that I can't type anything

thank you and sorry for the bad English

any help ?

---

### Post by robert shearer on 2009-07-18
STOP. STOP  EDIT.   I reread that site, their instructions are for an older version of Ubuntu.

Ignore the instructions below unless using a version of Ubuntu with Kernel 2.6.20 less.(Ubuntu 7.04 down.)



 run the commands from [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)
Only when you get to $ su  use this command instead 

```
sudo make info
```

it will ask for a password. The password is your user password you created when you installed Ubuntu.

Type that,(it **will not show** any letters or other output.**This is normal**) you will be typing blind :D .

 After you have typed your password hit enter and the driver should compile.

Wait until it finishes, carry out any other instructions it asks for and you may need to reboot when it has finished.

---

### Post by Moh'd32 on 2009-07-18
thank you

I firstly did what that site said

> administrator@ubuntu:~$ tar xjvf huawei.tar.bz2
huawei/
huawei/conf/
huawei/conf/huawei-e220
huawei/conf/wvdial-huawei.conf
huawei/conf/huawei-e220.chat
huawei/Makefile
huawei/files/
huawei/files/huawei-mobile.sh
huawei/files/99-huawei.rules
huawei/PROVIDERS
huawei/README
huawei/VERSION
administrator@ubuntu:~$ cd huawei
administrator@ubuntu:~/huawei$ su
Password: 
su: Authentication failure
administrator@ubuntu:~/huawei$ 



then I did  what you said

> administrator@ubuntu:~$ tar xjvf huawei.tar.bz2

huawei/

huawei/conf/

huawei/conf/
huawei-e220
huawei/conf/wvdial-huawei.conf
huawei/conf/huawei-e220.chat
huawei/Makefile
huawei/files/
huawei/files/huawei-mobile.sh
huawei/files/99-huawei
.rules
huawei/PROVIDERS
huawei/README
huawei/VERSION
administrator@ubuntu:~$ cd 




huawei




administrator@ubuntu:~/huawei$ sudo make info

[sudo] password for administrator:
HUAWEI E220 Linux help   by OOZIE

 ================================= 

 
Usage: 

 make install_suse / make uninstall_suse (to remove)

 - tested on openSUSE 10.2, SUSE 10.1

 

make install_fedora / make uninstall_fedora 
 
- tested on Fedora Core 5 with 2.6.15 kernel



 make install_ubuntu / make uninstall_ubuntu 
 
- tested on Ubuntu 6.06, Ubuntu 7.04 

 

make install_mandriva / make uninstall_mandriva 
 
- tested on Mandriva Free2007Spring kernel 2.6.17 


 

make config / make remove_config 
 
- this will only copy/remove the configuration files



 make generic_install / make generic_uninstall
 
- If your system is not listed above try the generic option.

  
 In fact, it's what the other options do more or less :)

Linux / kernel 2.6.28-11-generic



administrator@ubuntu:~/huawei$ make generic_install

cp files/99-huawei.rules /etc/udev/rules.d/
cp: cannot create regular file `/etc/udev/rules.d/99-huawei.rules': 
Permission denied
make: *** [generic_install] Error 1

administrator@ubuntu:~/huawei$ 


Actually I did not only use generic, I used them all but no luck

---

### Post by robert shearer on 2009-07-18
with Ubuntu you need to invoke superuser permissions to make administrative changes, 
so where Linux tutorials usually instruct you to become the superuser by typing ```
su
``` and then your password

for Ubuntu you need to preface the command with ```
sudo
```.

So try..
```
sudo make install_ubuntu
```



again, I do not think this tutorial applies to current versions of Ubuntu but is for older versions.

Someone more conversant with HUAWEI will no doubt help here :D if we wait a while.

---

### Post by Moh'd32 on 2009-07-18
I hope I can say it worked but Unfortunately No !!

I told you in my previous comment that I did not only use generic but I tried them all including ubuntu

I am so sorry

---

