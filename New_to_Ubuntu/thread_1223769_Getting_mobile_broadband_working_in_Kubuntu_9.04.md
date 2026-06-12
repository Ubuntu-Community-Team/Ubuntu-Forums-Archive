---
title: "Getting mobile broadband working in Kubuntu 9.04"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Ji Ruo on 2009-07-26
Hello All,

Mobile broadband does not work 'out of the box' in Kubuntu Jaunty. The problem seems to be the network manager plasmoid featured in the latest version of KDE. I first noticed when I installed 9.04 on my desktop a few weeks ago, and then installed 8.10 over it straight away -  at the time it was my only pc and it would have been too frustrating to try and get it working without an internet connection nearby (mobile broadband is my only option at home, no phone line). Since then I have a couple of other computers to play with, and I've put Kubuntu 9.04 on another desktop as a project to see if I could get it working (with some help).

Just to be clear, the mobile broadband dongle works fine with Kubuntu 8.10 on my primary desktop, and using Xubuntu 9.04 on my laptop. Searching the web has led me to believe that KDE is the problem, for example - [http://forum.kde.org/viewtopic.php?f=18&t=59914]("http://forum.kde.org/viewtopic.php?f=18&t=59914") (there is a link to a bug report for the plasmoid on this page also).

I think fixing the plasmoid might be a bit unrealistic, but would anyone be able to give me some advice on how to get mobile broadband working on a fresh install with no internet connection, say using the command line?

Thanks in advance

---

### Post by Ji Ruo on 2009-08-09
OK, I managed to solve this one. I'm posting the solution here in case anyone else is in the unusual position of using Kubuntu Jaunty and having only mobile broadband for their internet connection.

It is possible to use mobile broadband (and also dial-up) from the command line in linux, using the wvdial command. Unfortunately, wvdial is not included by default in Ubuntu, so I had to install it by downloading the packages from the internet, and transferring them to my computer by flash drive. I found what packages to use from installling wvdial on Ubuntu Jaunty. From [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , I downloaded the packages and installed them in this order (by clicking on them on the desktop):

libxplc0.3.13
libwvstreams4.4-base
libwvstreams4.4-extras
libuniconf4.4
wvdial

Now, using wvdial - the configuration file is at /etc/wvdial.conf  . I was lucky enough to find a blog from someone with the same modem and service provider (Huawei E160, 3 Prepaid Australia) so I used their settings. Other modems & providers should be very similar anyway. From [http://www.mig5.net/content/huawei-e160g-wireless-usb-three-debian-lenny](http://www.mig5.net/content/huawei-e160g-wireless-usb-three-debian-lenny)```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Modem = /dev/ttyUSB0
New PPPD = yes
Phone = *99#
ISDN = 0
Username = '
Password = '
Stupid Mode = yes
Carrier Check = no
Baud = 460800
Init5 = AT+CGDCONT=1,"IP","3services"
Auto Reconnect = no
```With this saved, I entered a terminal and entered this to start up my internet connection:```
sudo wvdial
```
An alternative method if I had an Ubuntu Jaunty CD, and the Kubuntu alternative CD, would be to install Ubuntu, then add the alternate cd as a source - ```
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
```And of course there is always the option to download kubuntu-desktop from the repositories using apt-get. Then I should be able to log into the kubuntu desktop, <Ctrl>+<F2> and```
nm-applet
```but I haven't had the opportunity to try this yet.

---

### Post by RabbitWho on 2009-08-21
I searched for these two files on the packages website and they and weren't there 

libwvstream4.4-base 
libwvstream4.4-extras

Will it work without them ? 

Any other ideas or new solution? If i'm going to download another CD i'll downgrade to 8.10 
I'd rather stick with what I've got!

---

### Post by Ji Ruo on 2009-08-22
Hmmm... I thought it was the search function playing up, but I've left the 's' off the end of those packages. Don't worry, they are there. Here are the links -

[http://packages.ubuntu.com/jaunty/libwvstreams4.4-base](http://packages.ubuntu.com/jaunty/libwvstreams4.4-base)
[http://packages.ubuntu.com/jaunty/libwvstreams4.4-extras](http://packages.ubuntu.com/jaunty/libwvstreams4.4-extras)

(They were listed in the depedencies section of wvdial). HTH, let me know if you get it working.

---

### Post by jhfry on 2009-11-11
Why bother with wvdial... just use KPPP... Included with Kubuntu and it works great!

Simply define the modem on the modems tab... mine was using /dev/ttyUSB0 as you described below.

Then create an account with PAP/CHAP and the phone number you used (I use #777 for sprint)... then connect with some nonsense in the username and password boxes (sprint doesn't require a UN/PW either).

---

### Post by Ji Ruo on 2009-11-11
Interesting. I wasn't aware of the existence of KPPP! It would have saved having to download the wvdial packages from another computer. I think I still have a Kubuntu 9.04 installation somewhere so I will have to try this out.

---

### Post by praveesh on 2009-11-11
There's an easy way to solve. Install nm-applet . Run nm-applet after closing knetworkmanager. An applet in Gnome will appear at the notification area

 To install nm-applet, open synaptic system->synaptic package manager->search . Type nm-applet press enter . Tick on nm-applet . Apply. 


To close knetworkmanager, open ksysguard  . It can be found at system tab of kmenu. Or hit alt+f2 and type ksysguard . In the window that opens, click on knetworkmanager and click on kill. 


To open nm-applet , hit alt+f2 and type nm-applet 
 

the command line way 
to install nm-applet , sudo apt-get install nm-applet 
to stop knetworkmanager,  killall knetworkmanager 
to launch nm-applet, nm-applet

---

### Post by Ji Ruo on 2009-11-11
> **praveesh said:**
> There's an easy way to solve. Install nm-applet . Run nm-applet after closing knetworkmanager. An applet in Gnome will appear at the notification area

That won't work Praveesh. Firstly it's KDE for Kubuntu, not GNOME. You would need to download the nm-applet files which depend on the GNOME environment, and my original question was for a pc with no internet connection available. Transferring all of the packages for GNOME from an internet connected PC would be much more complicated than just for wvdial. You could do this using a copy of the alternate install cd for Ubuntu as the source if you had this available. I wasn't able to run nm-applet in the KDE desktop (though that doesn't mean it's impossible), this meant for me that I would have to use the GNOME environment as my desktop to use the internet, and this would somewhat defeat the purpose of using Kubuntu in the first place.

---

### Post by praveesh on 2009-11-12
> **Ji Ruo said:**
> That won't work Praveesh. Firstly it's KDE for Kubuntu, not GNOME. You would need to download the nm-applet files which depend on the GNOME environment, and my original question was for a pc with no internet connection available. Transferring all of the packages for GNOME from an internet connected PC would be much more complicated than just for wvdial. You could do this using a copy of the alternate install cd for Ubuntu as the source if you had this available. I wasn't able to run nm-applet in the KDE desktop (though that doesn't mean it's impossible), this meant for me that I would have to use the GNOME environment as my desktop to use the internet, and this would somewhat defeat the purpose of using Kubuntu in the first place.

I did it and it's working . I don't know how much Gnome packages it requires. I have to mention that Iam having both kde and Gnome installed  . When I got errors with wvdial, I tried this method

---

### Post by Ji Ruo on 2009-11-12
> **praveesh said:**
> To install nm-applet, open synaptic system->synaptic package manager->search . Type nm-applet press enter . Tick on nm-applet . Apply. 


To close knetworkmanager, open ksysguard  . It can be found at system tab of kmenu. Or hit alt+f2 and type ksysguard . In the window that opens, click on knetworkmanager and click on kill. 


To open nm-applet , hit alt+f2 and type nm-applet 
 

the command line way 
to install nm-applet , sudo apt-get install nm-applet 
to stop knetworkmanager,  killall knetworkmanager 
to launch nm-applet, nm-applet

This may be useful for people who have a working internet connection (I didn't). 

I was under the impression that knetworkmanager was dropped in favour of the network plasmoid from 9.04 onwards... are you sure this advice posted is for Kubuntu 9.04 (Jaunty)? I had no problems using Knetworkmanager in 8.10 for mobile broadband (only with the broken plasmoid in 9.04).

Does anyone know if the network plasmoid has been fixed in the latest release (Kubuntu Karmic 9.10) ?

---

### Post by Ji Ruo on 2009-11-18
> **jhfry said:**
> Why bother with wvdial... just use KPPP... Included with Kubuntu and it works great!

Simply define the modem on the modems tab... mine was using /dev/ttyUSB0 as you described below.

Then create an account with PAP/CHAP and the phone number you used (I use #777 for sprint)... then connect with some nonsense in the username and password boxes (sprint doesn't require a UN/PW either).

Hi again jhfry

Looking at my old installation of Kubuntu 9.04 and the live CD, it appears that KPPP was not included with Kubuntu Jaunty. So I could have transferred the KPPP and dependency .deb files from another computer, as an alternative to wvdial (I'm not sure what dependencies would need to be downloaded).

I have the live CD of Kubuntu Karmic now, so I will try out KPPP for connecting soon. KDE4.3 still doesn't have intelligent connection for mobile broadband it seems (at least not for my modem).

---

