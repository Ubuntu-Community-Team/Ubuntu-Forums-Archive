---
title: "Help! Beetel 220BX connectivity problems"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Games Goblin on 2007-05-29
HELP ME !!! I AM ONLY 1 STEP AWAY FROM INSTALLING UBUNTU!!

The problem is internet...I use a BEETEL 220BX ADSL modem connected via USB since the ethernet port wonked out! Ubuntu may have detected the thing because an icon for network sprang up in the top right corner of the screen.....

I set to configure the network connections and entered my IP adddress , DNS, Default getaway and stuff which i usually enter in windows but the i-net is still not working.... 

Many people, it seems have come across this problem... 

I have been googling about my modem with the keywords "Beetel 220BX" "Ubuntu" & "USB". The results i got are:

From [http://witopia.blogspot.com/2006/07/adsl-modem-in-ubuntu.html]("http://witopia.blogspot.com/2006/07/adsl-modem-in-ubuntu.html") :

> Ubuntu keeps on impressing. I have a Beetel 220BX ADSL2 Modem which came with my Airtel connection. It has has an ethernet connector as well as an USB connector. I had previously tried to get my Fedora Core 5 installation working with the USB connector but failed. I was anxious whether it would work in Ubuntu or not after I read the wiki which said that its best to use the Ethernet connection!

But then I read the Home Networking Wiki which had some more pointers. Finally it was as easy as running the live CD with the USB Modem connected. It generated the /etc/network/interfaces file which lists down the physical interfaces and the rules to bring them up. All I had to do was to copy the file to my hard drive installation and the modem was running on USB!

It was a breeze. The love increases.




From [http://www.thinkdigit.com/forum/showthread.php?t=57869]("http://www.thinkdigit.com/forum/showthread.php?t=57869") :

>  ^^ I am using ADSL with USB but in ubuntu from the last september. No problems till now.

@asdfgh2: Assuming that the basic linux are all same. Use this script:

Make a new file anywhere (on the desktop maybe)
[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

SAve the file and click on it.

Run: Applications -> Internet -> RP-PPPoE


THis worked fine in ubuntu 6.06. I cont guarantee that this will work fine in RH. Anyways Best Of Luck. 


From [http://vprajan.org/]("http://vprajan.org/")

Making Airtel USB Beetel 220bx Modem work with UbuntuOpen Source, Technology - No Comments » - Posted on April, 27 at 11:06 pm

   I have a airtel connection with Beetel 220bx ADSL Modem. As i was using Fedora for about a year and when i tried configuring airtel USB connection for it, i had no success. It was very difficult to make Fedora to recognize USB modem as a ethernet connection and map it with an IP address.

But now, i am getting more attraction towards Ubuntu. ;).. It is like a cake in pie when it comes to USB Modem. Just connect and you are in.

So, there is no work to be done. Just try connecting your USB modem and you can see the magic.

NOTE: I am using Ubuntu 6.10.



From [http://techstreak.blogspot.com/2007/05/ubuntu-experience.html]("http://techstreak.blogspot.com/2007/05/ubuntu-experience.html")

ubuntu experience 

Yesterday I installed ubuntu "breezy badger".....installation worked fine as it was installed on the separate partition....as its compulsory to create a separate partition for installing any Linux flavour be it Red Hat or Suse.I used partition magic for partitioning my drive.
I was not sure whether my internet will work on it, as I am using usb connection for connecting to internet . With ethernet card .....the internet is gauranteed to work.

After installing I straight away went to Network Settings and just entered the open DNS address :
4.2.2.1
4.2.2.2

then i opened the built in Firefox and jackpot it worked.....wow.
The one more thing that I like about ubuntu is that it automatically installs all the drivers for every possible device eg. usb, bluetooth, nvidia etc.

It also shows my windows partition on the desktop and i can easily access the files...afterall ubutu is windows friendly.


_______________________________________________________________________________________


Here are some photos:

[IMG]http://i7.photobucket.com/albums/y294/games_goblin/Ubuntu/Screenshot.png[/IMG]

[IMG]http://i7.photobucket.com/albums/y294/games_goblin/Ubuntu/Screenshot-2.png[/IMG]

[IMG]http://i7.photobucket.com/albums/y294/games_goblin/Ubuntu/Screenshot-1.png[/IMG]




You can see that ubuntu has detected my modem as a network icon appeared near the clock, just like windows.....but to check, i turned off the modem and it said that the network was disrupted....so it has been detected all right!

I entered all infos like DNS, IP and stuff like i do in windows but to no avail


HELP!!!!!

---

### Post by Sushubh on 2007-06-20
ubuntu works fine with ethernet on 220 bx... :)

---

### Post by Games Goblin on 2007-06-21
Sorry my internet is working .... i forgot to report back here! thanks!

---

### Post by Georgekutty007 on 2007-07-11
[B]Hi,

could you please tell me how to configure Beetel 220BX modem with an ethernet connection. If you could, please tell me how to do it step by step. I tried it several time and failed.. 

Please check the link below it contains the trouble i am facing and it contains a screenshot of the error message...

[http://ubuntuforums.org/showthread.php?t=489953&highlight=airtel](http://ubuntuforums.org/showthread.php?t=489953&highlight=airtel)

Thank you,

George... [/B]

---

