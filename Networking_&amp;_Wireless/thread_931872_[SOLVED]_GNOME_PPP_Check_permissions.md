---
title: "[SOLVED] GNOME PPP Check permissions"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by MacDuff on 2008-09-27
Trying to set up a laptop to use a USRobotics Model 5637 USB modem so a friend can use a dial-up Internet connection.

This person needs a graphical user interface so I thought that GNOME PPP would be good.  However I have been trying to get it to work on my laptop and when it tries to connect I get the following error:

   Carrier detected. Starting PPP immediately
   Unable to run /usr/sbin/pppd
   Check permissions, or specify a "PPPD Path" option in wvdial.conf

Below is the content of wvdial.conf
  [Dialer Defaults]
  New PPPD = yes
  Stupid Mode = yes
  Modem Thpe = Analog Modem
  ISDN = 0
  Auto DNS = 1
  Auto Reconnect = 0
  Modem = /dev/ttyACM0
  Baud = 230400
  Initl = ATZ4

  Phone = 250 388 5747
  Username = {name}
  Password = {password}

Here is what the specs on on /usr/sbin/pppd :
Type is:          executable, 
permissions are: -rwxrwxr-- 
Owner:Group is:   root:30   That looks odd to me but I am still pretty green with Ubuntu.

Can anyone suggest what I must change, and how to get this machine to connect to the Internet via dial-up using GNOME PPP or other graphical interface?

---

### Post by pacz999 on 2008-10-22
Hi,
I was facing the same problem. Here is the solution (at least it solved the problem for me):
Open a terminal window and enter the following commands:
sudo chown root:dip /usr/sbin/pppd
sudo chmod 4754 /usr/sbin/pppd
sudo chmod 777 /etc/ppp/pap-secrets 
sudo chmod 777 /etc/ppp/peers

That should grant the required permissions and enable the connection to the internet.

Hope it helps.

---

### Post by MacDuff on 2008-10-22
For the benefit of those who were following this thread and providing help, I have returned from my sojourn to install an Ubuntu system for an old friend who lives 1000 miles away and who only has access to a dial-up Internet connection.

The installation went beautifully! thanks to your help.  I was able to install the Gnome-PPP dialer but I had to change some settings in "wvdial.conf as well as incorporate other suggestions before it would work.

My friend is happy and I am back home and can provide support to him while he learns the finer points of using Ubuntu.  The emails from him are a little odd because he has never ever used even a typewriter, but he is enjoying the experience and is really learning fast.  Before I left, he had mastered sending and receiving emails, browsing the Internet and had even made a purchase off the Internet. 

His family and neighbors are astounded, particularly one academic neighbor who warned him NOT to install Linux because "nobody around will be able to help you when you have trouble".  I wonder what she is thinking now?  
My friend's daughters-in-law have even become curious about Linux and I left a desktop CD with them to try.

A big "Thank You!" to travm, ModelM, and _duncan for the help you provided in making Ubuntu available to an ordinary person.

Mac

---

### Post by jabastija on 2008-12-23
Thanks for the post pacz!  I've been trying to figure this out for quite some time.  It works great and it seems as though it sped up my connection too!

---

### Post by undoIT on 2009-01-20
Thanks for the fix pacz999!

I only needed the first two lines to get my Samsung M610 cell phone tethered through gnome-ppp as a normal user:

```
sudo chown root:dip /usr/sbin/pppd
sudo chmod 4754 /usr/sbin/pppd
```

---

### Post by bth73 on 2009-01-31
didn't work for me
Why doesn't basic stuff just work and why is it not in the basic install?
Ubuntu is the best os I've ever used but, why does it have to be so incomplete and unfinished? I've been experimenting with a lot of different distributions, and they all have problems. Too techi, most people know nothing about boot loaders and grubs and networking ISP's, DNS, Mac addresses - where is that? -Appleville? Some won't load at all.
These dialer issues really are a turn-off for an average rural user that has no access to high speed internet. How can you download gnome ppp dialer if you have no dialer to get on the internet in the first place?
Smart people are really dumb sometimes.
And wireless, what a pain, I guess you have to be a computer engineer to figure that out. So far every computer I try sees the wireless network but will not conect to it.

---

### Post by undoIT on 2009-01-31
> **bth73 said:**
> didn't work for me
Why doesn't basic stuff just work and why is it not in the basic install?
Ubuntu is the best os I've ever used but, why does it have to be so incomplete and unfinished? I've been experimenting with a lot of different distributions, and they all have problems. Too techi, most people know nothing about boot loaders and grubs and networking ISP's, DNS, Mac addresses - where is that? -Appleville? Some won't load at all.
These dialer issues really are a turn-off for an average rural user that has no access to high speed internet. How can you download gnome ppp dialer if you have no dialer to get on the internet in the first place?
Smart people are really dumb sometimes.
And wireless, what a pain, I guess you have to be a computer engineer to figure that out. So far every computer I try sees the wireless network but will not conect to it.

Probably, if you were actually writing the code for Gnome PPP / networking and trying to get it to work with all the different modems (dial-up, cell phone modems etc) out there, you'd find out it is not so simple.

Rather than complaining, why not just state the modem you are using, what you did to try and get it working, and what the error message is. Somebody might be able to help you in that case.

In my experience, wireless has in most cases just worked out of the box on Ubuntu and several other distros, even with new wireless cards like the Intel 5300 and also cards from manufacturers that don't provide open source drivers like Broadcom.

---

### Post by Eric.brackenbury on 2009-11-17
> **undoIT said:**
> Probably, if you were actually writing the code for Gnome PPP / networking and trying to get it to work with all the different modems (dial-up, cell phone modems etc) out there, you'd find out it is not so simple.

Rather than complaining, why not just state the modem you are using, what you did to try and get it working, and what the error message is. Somebody might be able to help you in that case.

In my experience, wireless has in most cases just worked out of the box on Ubuntu and several other distros, even with new wireless cards like the Intel 5300 and also cards from manufacturers that don't provide open source drivers like Broadcom.

Hi There

I am trying to setup a Trendnet TFM-560X external dial up modem for a friend and have enjoyed your back and forth.

After sudo chown root:dip /usr/sbin/pppd
-Ubuntu:~$ sudo chmod 4754 /usr/sbin/pppd
-Ubuntu:~$ sudo chmod 777 /etc/ppp/pap-secrets
-Ubuntu:~$ sudo chmod 777/etc/ppp/peers
I got this
chmod: missing operand after `777/etc/ppp/peers'

Any help would be welcome and if you need more info let me what and how to obtain it, at my age (yes I am getting a pension) I need all I can get.
Thanks in advance
Eric B

---

### Post by Eric.brackenbury on 2009-11-18
OK so with some help I came across this answer that definitely works :-))

[https://answers.launchpad.net/ubuntu/+source/gnome-ppp/+question/56076](https://answers.launchpad.net/ubuntu/+source/gnome-ppp/+question/56076)

So go to System administration then users & groups, click on Unlock and authenticate with your password.
Select the user Account and hit the properties button after that select the user privileges tab and check the correct box for "connect to the Internet using a modem".
REBOOT the computer and it will take effect enabling dial up to work.

Thanks to Yuriy on that group for this and my wife for putting up with me on the computer for two night solving the problem.

Eric

---

### Post by kent2 on 2009-12-23
This is my first post here. I have a USRobotics Model 5637 USB modem that worked pretty much out of the box. I downloaded wvdial and gnome-ppp over a wired network through another computer that runs XP. I got dialup to work in a terminal window but not graphical. I've been fighting this for days. It's been driving me nuts. Reading this post worked like a champ. Thank you so much for asking and answering. By the way I'm running Jaunty 9.04. Thanks

---

### Post by hst19 on 2010-02-20
> **MacDuff said:**
> Trying to set up a laptop to use a USRobotics Model 5637 USB modem so a friend can use a dial-up Internet connection.

This person needs a graphical user interface so I thought that GNOME PPP would be good.  However I have been trying to get it to work on my laptop and when it tries to connect I get the following error:

   Carrier detected. Starting PPP immediately
   Unable to run /usr/sbin/pppd
   Check permissions, or specify a "PPPD Path" option in wvdial.conf

Below is the content of wvdial.conf
  [Dialer Defaults]
  New PPPD = yes
  Stupid Mode = yes
  Modem Thpe = Analog Modem
  ISDN = 0
  Auto DNS = 1
  Auto Reconnect = 0
  Modem = /dev/ttyACM0
  Baud = 230400
  Initl = ATZ4

  Phone = 250 388 5747
  Username = {name}
  Password = {password}

Here is what the specs on on /usr/sbin/pppd :
Type is:          executable, 
permissions are: -rwxrwxr-- 
Owner:Group is:   root:30   That looks odd to me but I am still pretty green with Ubuntu.

Can anyone suggest what I must change, and how to get this machine to connect to the Internet via dial-up using GNOME PPP or other graphical interface?

Just in case anyone else is browsing this thread, there's another way to solve this problem. I tried granting permission using the terminal but it didn't work, so here's how I did it:

Open terminal.
Open nautilus by typing "sudo nautilus".
Enter password when prompted.
When the file browser opens, go to the folder usr, then to folder sbin,where you will find the executable program pppd.
Right click on ppd, go to properties, then go to permissions tab under properties.
There, you will find an option for allowing the program to be run as an executable (I've forgotten the exact words). There's a check box adjacent to it. If there is a minus (-) sign in this box, click it to change it to a tick sign. Now permissions are ok and you should be able to use gnomeppp which executes pppd without a problem.

---

### Post by tboy5732 on 2011-03-30
I just installed Ubuntu 10.04.  I got KPPP working with my modem and I can connect and stay connected.  My issue is I cant get network manager to use the dialup connection bcause there is no tab for modem in the new GNOME Network Manager.  Can anyone tell me what to try next?

---

