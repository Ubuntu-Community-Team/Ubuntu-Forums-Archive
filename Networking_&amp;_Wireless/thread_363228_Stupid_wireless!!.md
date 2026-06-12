---
title: "Stupid wireless!!"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by FreshPrince on 2007-02-16
So, i installed Linux Ubuntu 6.10 again again. And this time i asked in another forum how to get connected to my wireless network. Well my answer was that i had to install network manager. So i followed the instructions, went into terminal and wrote **sudo apt-get install network manager**, but then it says this: "**E: Kunne ikke finde pakken network-manager-gnome**"

Then instead i tried to installe the program from Install/remove programs, but still it dont want to. This time linux says this: "**Network Manager cannot be installed on your computer type (i386)**
*Either the application requires special hardware features or the vendor decided to not support your computer type"*

My laptop is Hp Pavillion dv5000 and its (as said)ubuntu 6.10 edgy i have installed.
I have NO idea wat to do, and i have been strugeling with linux in two weeks now, and i really want it to work and get it over with. 

So PLEASE help me with my irritating problem!

---

### Post by H.E. Pennypacker on 2007-02-16
You must be doing something unusual, because downloading and installing Network Manager (a part of Gnome) should not be this difficult.  

Something could be wrong with your sources list (which is a list of places where you download software from).  Try searching Synpatic, and look for Network Manager there.  If you still can't find it, please post your sources list (/etc/apt/sources.list).

---

### Post by FreshPrince on 2007-02-16
Well...i couldt find network manager in synaptic.
And when i try to enter /etc/apt/sources.list in therminal it says: permisson denied, even though i am logged in as root

EDIT: well, i used: sudo gedit /etc/apt/sources.list and now i am in sources.list. and it looks like this:


deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Cobikegeek on 2007-02-16
You need to enter "gksudo gedit /ect/apt/sources.list" (without the quotes) in the terminal to edit your sources list.  If you just want to look at sources.list in read only mode so you can cut and paste the contents, just use the file manager to locate the file, right click on it and select open with text editor.

---

### Post by FreshPrince on 2007-02-17
well i copy pasted it here, so now wat?

---

### Post by FreshPrince on 2007-02-18
no help? :(

---

### Post by FreshPrince on 2007-02-19
BUMP!

not i installed network manager...and commented out my network connection in /etc/network/interfacec, but it still cannot find any network :(

help plz!

---

### Post by sdide on 2007-02-19
Please post ouput from the following executed as root

# iwconfig 
# cat /etc/network/interfaces
# iwlist scan
# ip link
# ip neigh

---

### Post by FreshPrince on 2007-02-21
[SIZE="4"]**# iwconfig **[/SIZE]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

[SIZE="4"]**# cat /etc/network/interfaces**[/SIZE]
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


auto eth0

iface eth1 inet dhcp
wireless-essid linksys

auto eth1
[SIZE="4"]

**# iwlist scan**[/SIZE]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

[SIZE="4"]
**# ip link**[/SIZE]
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:16:d4:30:c4:b6 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:14:a5:ac:39:c9 brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0


[SIZE="4"]**# ip neigh**[/SIZE]
couldnt find anything here

---

### Post by FreshPrince on 2007-02-22
sry for bumping all the time, i really need a solution :(

---

### Post by sdide on 2007-02-23
How is your AP set up? 
is it named (ESSID) "linksys"?
is it an encrypted connection? 

Try as root

# ip link set eth1 up

and then do a 

#iwlist eth1 scan

again.

---

### Post by FreshPrince on 2007-02-24
Its without any form of encryption.

I tried that...first it says permission denied and then no scan results

---

### Post by sdide on 2007-02-24
You need to do all these things as root.

That means either do: 

# sudo su -

and log in as root, 

or execute each command through sudo.

---

### Post by FreshPrince on 2007-02-24
> **sdide said:**
> You need to do all these things as root.

That means either do: 

# sudo su -

and log in as root, 

or execute each command through sudo.

so i did...it still says no suck directory to the first one.

the other one:

[I]lo   Interface dosen't support scanning.


eth0   Interface dosen't support scanning.


eth1   Interface dosen't support scanning : No such device


sit0   Interface dosen't support scanning.[/I]

---

### Post by sdide on 2007-02-25
Hmmm, 

Can you do (as root or with sudo)

# lshw -C network
# cat /etc/iftab
# which ip

---

### Post by rubykj on 2007-03-07
did you figure it out? I have the same problem

---

### Post by liljoe76 on 2007-03-07
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
to the OP!

---

### Post by rubykj on 2007-03-07
I dont need ndiswrapper my card is supported
I'm getting an error when I try and  configure network manager:
wireless-tools >= 28pre9 not installed or not funcitonal
what do I need to do?
can you help me step by step?

---

