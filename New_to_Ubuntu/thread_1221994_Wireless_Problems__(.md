---
title: "Wireless Problems : ("
date: 2009-07-24
forum: New to Ubuntu
---

### Post by unclepauly14 on 2009-07-24
Hey everyone!!

So I just recently started using Ubuntu on my laptop. i have a HP Dv6 and i cannot connect to any wireless AP's. I searched all over the web and on the forums and have trie dout things people have mentioned and still turned up nothing. 

My wireless card from what i learned is this:

08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) 

Now with windows running i can access networks and my computer recongnizes that there are more then one to connect to.  In Ubuntu i get notihng for my wireless connections.

So i am assuming that i need to install a driver for my network card, or that it is not supported with Ubuntu : (

Well any kind of something would be nice because i cant figure it out out on my own there is just to much info pulling in to many dirrections and i dont know what to do :(

---

### Post by philcamlin on 2009-07-24
sudo apt-get install linux-backports-modules-jaunty

try that reboot after

---

### Post by superprash2003 on 2009-07-24
does your **lshw -C network** output show as UNCLAIMED? could you post the output

---

### Post by unclepauly14 on 2009-07-24
First thing i hate to say is that i am not good with the terminal so when it asks me for my password and i try to type it in it does not let me that one is directed toward Phil so i couldnt try out your method yet.

Super here is the info i got back:

  *-network [COLOR=Red]**UNCLAIMED**[/COLOR]!!! 
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:23:8b:b1:fa:6c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.103 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:3b:6c:11:d2:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=ye

---

### Post by philcamlin on 2009-07-24
when you type your password in terminal it wont show up :P

its to keep it secure! type it in and press enter :)

---

### Post by unclepauly14 on 2009-07-24
Ha! well look at that it worked. This is what it is telling me after I entered the command

paul@ubuntu:~$ sudo apt-get install linux-backports-modules-jaunty
[sudo] password for paul: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
paul@ubuntu:~$

---

### Post by philcamlin on 2009-07-24
do you have anything else thats running root?

or another terminbal window?

if you cant find anything just reboot and try it again :)

---

### Post by mud420 on 2009-07-24
If you have any problem with your computer ( Hardware or Software )
So do not waste your money on its repairation 
Just visit the site and learn solve of any problem!
 
[http://www.tectips.co.cc](http://www.tectips.co.cc)
 
Thanks

---

### Post by unclepauly14 on 2009-07-24
Ok i rebooted and tried again and this time it worked and I am installing the package, I will see if that works but for now time to go to work. Thank you for the help and I will post back later with the results!! Thanks you again!!:P

---

### Post by philcamlin on 2009-07-24
ahah no problem :)

im looking forward to your response :D

---

### Post by scrooge_74 on 2009-07-24
> **unclepauly14 said:**
> First thing i hate to say is that i am not good with the terminal so when it asks me for my password and i try to type it in it does not let me that one is directed toward Phil so i couldnt try out your method yet.


What so hard about opening a terminal (the terminal is your friend) copy and past that in it give enter, when prompted for your passsword give it and give enter.

Did it gave you some kind of error?

The only reason that aint working would be that you dont have the backports repositories enable.

Go to System>Admin>Software sources find the backports line click it update and try again ;)

Don't mind me, I got side tracked and posted after the fact :p

---

### Post by philcamlin on 2009-07-24
> **scrooge_74 said:**
> What so hard about opening a terminal (the terminal is your friend) copy and past that in it give enter, when prompted for your passsword give it and give enter.

Did it gave you some kind of error?

The only reason that aint working would be that you dont have the backports repositories enable.

Go to System>Admin>Software sources find the backports line click it update and try again ;)

he was running another process under root but i told him to reboot and now its installing :)

i like terminal too :)

---

### Post by unclepauly14 on 2009-07-24
Ok so I did the linux backports jaunty thing haha, and my wireless indicator is saying it is on, but now i accidentally removed the launcher from my panel showing my internet status, and i cant figure out how to get that to show back up, so right now i dont know if it is detecting any wireless netoworks or not

---

### Post by philcamlin on 2009-07-24
ah so it did work while it wasnt messed 

I've had this happen before and what I think I did to fix it was add the "Notification Area" back to my panel. Right-click, select 'Add to panel' and add the Notification Area one and see if that works.

---

### Post by LookTJ on 2009-07-24
> **unclepauly14 said:**
> Ha! well look at that it worked. This is what it is telling me after I entered the command

paul@ubuntu:~$ sudo apt-get install linux-backports-modules-jaunty
[sudo] password for paul: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
paul@ubuntu:~$
when this error occurs, you might have had synaptics open or another apt-get process running(or anything related to dpkg) :)

Hope this gives you insight

---

### Post by LookTJ on 2009-07-24
> **unclepauly14 said:**
> Ok so I did the linux backports jaunty thing haha, and my wireless indicator is saying it is on, but now i accidentally removed the launcher from my panel showing my internet status, and i cant figure out how to get that to show back up, so right now i dont know if it is detecting any wireless netoworks or not
Right click on the panel and click add to panel, then look for notification area. 

:)

---

### Post by philcamlin on 2009-07-24
> **LookTJ said:**
> Right click on the panel and click add to panel, then look for notification area. 

:)

thtas just what i said :P

---

### Post by unclepauly14 on 2009-07-25
Ok sorry its been taking me a while to get back, I have been on like a 23 day in a row working streak :( so I'ma busy guy!! But just wanted to say thank you for you help Philcamlin because after I installed whatever it was that you had me install and after I remembered my login for my network everything is working great!!! So thank you for all the advice it was greatly appreciated!!! :D

:popcorn:

---

### Post by philcamlin on 2009-07-25
> **unclepauly14 said:**
> Ok sorry its been taking me a while to get back, I have been on like a 23 day in a row working streak :( so I'ma busy guy!! But just wanted to say thank you for you help Philcamlin because after I installed whatever it was that you had me install and after I remembered my login for my network everything is working great!!! So thank you for all the advice it was greatly appreciated!!! :D

:popcorn:

no problem :) any time :popcorn:

---

