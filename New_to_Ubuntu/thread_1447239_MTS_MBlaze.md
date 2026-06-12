---
title: "MTS MBlaze"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by ubun2warrior on 2010-04-05
I purchased a MTS Mblaze mobile broadband but it does not work in ubuntu. I tried a lot but i think ubuntu is not able to recognize the device (which is a ZTE modem).
The MTS details are as follows:
Username: [email]internet@internet.mtsindia.in[/email]
phone: #777
password: mts

I even tried creating a new connection with the above and also tried gnome ppp. But nothing works. I tried wvdial also.

Looking forward for replies..

---

### Post by ramakant2k on 2010-08-19
1. Double click on the CrossPlatformUI-V1.0.27-SSTL-i386-ubuntu.deb file in the USB drive.

 2. Eject the ZTE CD rom[it appears in the drive list screen when the usb device is inserted for the for the first time] by right clicking and clicking on eject.
3. Restart the computer.
4.start the crossplatform UI from the internet menu.
5. Browse after making sure Firefox is in online mode.

It worked on intrepid[8.10] as well as lucid lynx[10.04] for me, so it should probably work on 9.04 as well.

---

### Post by ubun2warrior on 2010-09-15
hi 

thanks a lot for ur help.. i got the device working by using usbmodeswitch. its available in the repositories. i just installed it and the device started working...

regards
ubun2warrior

---

### Post by ashik on 2010-09-17
There seems to be no binaries provided by MTS MBlaze for Ubuntu 64-bit. Is the source code available? What is the purpose of this CrossPlatformUI by the way? I am able to connect to the internet without it.

---

### Post by ubun2warrior on 2010-09-18
hi

MTS Mblaze is a win modem. It does not support linux... So what happens is that linux assumes it to be a storage device and treats it as a ZeroCD and not as a serial modem through which we connect to the internet.
usbmodeswitch solves this problem.. and when you go to network connection and try to set up a mobile broadband connection u will find that it shows a ZTE modem, which earlier was not shown...

Regards

ubun2warrior

---

### Post by kinshukt on 2010-10-02
Hi,

MTS use ZTS modem as a backend device , it worked for me but not in the way mentioned in the forum , steps which I followed are -

1. After attaching the MTS blaze go to /media/ZTE.. (directory name )
2. install the package with sudo dpkg -i CrossPlatformUI-V1.0.27-SSTL-i386-ubuntu.deb
3. step 2 will return some errors please ignore them 
4. go to preferences ---> network connections --------> select mobile broadband , and create a new connection 

      Use details -

Username: [EMAIL="internet@internet.mtsindia.in"]internet@internet.mtsindia.in[/EMAIL]
phone: #777
password: mts

5 . for getting connected go to Applications ------- Internet - ZTMET U! and get connected 

its all done

---

### Post by sunsing2000@hotmail.com on 2010-10-15
well i got mine connected
i hav ubuntu 9.04

system>administrator>synaptic package manager
open it
setting>repositories
new window opens
click to open third party software from top menu

click add
copy and past this: 
deb http://[mirrors.kernel.org/ubuntu]("http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-modeswitch/usb-modeswitch_1.1.0-2_i386.deb") lucid main universe

click close
say yes to all
click reload
after loading from internet completes
click origis from left menu
look for 
[mirrors.kernel.org/ubuntu]("http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-modeswitch/usb-modeswitch_1.1.0-2_i386.deb") 
click it
find usb-modeswitch in left menu
add it by clicking to install
installation complete then ur ready t go

insert ur mblaze modem
open network connection
find in ur wireless device 
mobile cdma connection
edit it
put
no: #777
user name: internet@internet.mtsindia.in
password: mts
save it
n ur ready to go

---

### Post by srinistuff on 2010-12-13
> **ubun2warrior said:**
> I purchased a MTS Mblaze mobile broadband but it does not work in ubuntu. I tried a lot but i think ubuntu is not able to recognize the device (which is a ZTE modem).
The MTS details are as follows:
Username: [email]internet@internet.mtsindia.in[/email]
phone: #777
password: mts

I even tried creating a new connection with the above and also tried gnome ppp. But nothing works. I tried wvdial also.

Looking forward for replies..

Hey UbuntuWarrior...

Did you finally get a resolution?? I'm trying to install MTS Mblaze modem on my laptop too in Ubuntu 10.4... Tried all possible things in various forums...just doesn't seem to work. I even set up the connection etc, it gets connected too, but doesn't work.. i.e no internet.. Looking for a solution if it worked for you.

Srinistuff

---

### Post by ubun2warrior on 2010-12-19
> **srinistuff said:**
> Hey UbuntuWarrior...

Did you finally get a resolution?? I'm trying to install MTS Mblaze modem on my laptop too in Ubuntu 10.4... Tried all possible things in various forums...just doesn't seem to work. I even set up the connection etc, it gets connected too, but doesn't work.. i.e no internet.. Looking for a solution if it worked for you.

Srinistuff

Hi

i just downloaded usbmodeswitch from ubuntu repositories, then i restarted my ***puter, after that i created a new mobile broadband connection with the mts dongle connected to my laptop. then i edited the connection details of mts connection the no is #777, username is [email]mts@mtsindia.in[/email] and password is mts. 

you can try this !! hope it works..

regards

---

### Post by Somnathsaltlake on 2011-07-23
I could not install MTS MBlaze software in my UBUNTU 11.04 version?

---

### Post by ubun2warrior on 2011-07-28
hey, 
you don't install the mts software, the driver info is already there in ubuntu 11.04. just plugin the usb into ur comp's usb and .. wait for some time then click on the network icon the top right corner, click on new mobile broadband connection then just follow the steps.. its simple :)
you will also have to edit this connection after the final steps, the username would be: [email]internet@internet.mtsindia.in[/email] and the password: mts

cheerio

---

### Post by nagarjuna_redhat on 2011-11-04
hi frnd,

I am using ubuntu 10.10 version. here the problem is when i plug the device it is not showing the device. tell me is there any package that i need to install for that?

---

### Post by lavankohsa on 2011-12-15
i am able to connect using this method, but the problem is that i can't monitor my browsing data amount with this bcoz i don't have unlimited plan and also it takes time to connect to internet and sometime it doesn't even connect.mts software in windows is good for all this. if u can tell any similar s/w, it will be of great help

---

### Post by ubun2warrior on 2011-12-16
> **lavankohsa said:**
> i am able to connect using this method, but the problem is that i can't monitor my browsing data amount with this bcoz i don't have unlimited plan and also it takes time to connect to internet and sometime it doesn't even connect.mts software in windows is good for all this. if u can tell any similar s/w, it will be of great help


hi

you check ur internet usage for each session from the gnome-system-monitor > resources

i use it to view the session wise usage, generally i keep it connected to my system and hardly disconnect, so its like only once or twice a day.. 

u don't need any additional software

hope this helps

regards

---

### Post by nizamibilal1064 on 2012-04-27
Hi 
I also faced same problem while connecting MTS Mblaze to my ubuntu 11.10. This can be solved by using usb-modeswitch as suggested by many people here. Following is the steps to get it working.

1- download usb-modeswitch from [http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch) and install it by double clicking on it 

2- After you’ve installed usb-modeswitch and usb-modeswitch-data packages, reboot your computer.

3- Connect the Mblaze Modem and wait for some moments. check the status through the following command in terminal:

dmesg

4- You need  “wvdial” also. It may be pre installed on your system. You can check that by typing in terminal “wvdial”. If it is not installed then you’d have to install it. 

5- download following packaged 

a. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
b. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
c. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
d. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
e. [http://packages.ubuntu.com/jaunty/wvdial/download](http://packages.ubuntu.com/jaunty/wvdial/download)

6- Paste them to the pc having ubuntu 11.10 into /var/cache/apt/archives/ directory using sudo nautilus from terminal. Then install all packages by double clicking each icon (of .deb package) in above order (1,2,3,4 and finally 5). Finally  run wvdialconf, edit the /etc/wvdial.conf file and be connected with sudo wvdial. (you can download above packages from any other pc having different os and transfer it by usb drive)


7- Now edit the file /etc/wvdial.conf

[Dialer cdma]
02
Stupid Mode = 1
03
Inherits = Modem0
04
Password = mts
05
Username = [email]internet@internet.mtsindia.in[/email]
06
Phone = #777
07
 
08
[Modem0]
09
Init1 = ATZ
10
SetVolume = 0
11
Modem = /dev/ttyUSB0
12
Baud = 115200
13
FlowControl = Hardware (CRTSCTS)
14
Dial Command = ATDT


8- Run following command in terminal and dont close terminal

wvdial cdma

9- Connect your modem and enable mobile broadband from network icon in top panel and click on mts mblaze connection1 and enjoy the power of world wide web:D

I have made it worked in dell inspiron 14 R running on ubuntu 11.10 with dual booted with windows 7 home basic.

---

