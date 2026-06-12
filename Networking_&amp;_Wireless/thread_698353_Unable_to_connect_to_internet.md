---
title: "Unable to connect to internet"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by choco_ram on 2008-02-16
I have the dell inspiron 1420 vista basic...i am running ubuntu with  the live cd...but iam not able to connect to internet...I have the reliance wimax connection...the antenna cable connects to the power adapter (PoE adapter)...and a LAN cable connects my pc to the adapter...I did ifup ifdown etc...but it cant connect...i did dhclient but it says no DHCPOFFERS received...i very badly want to use ubuntu..pls help...
do i need to install anything on top of the live cd components...internet works perfectly well with vista...
thx in advance...
my ethernet adapter is broadcom netlink fast ethernet...
i used the gui tools for networking..i enabled all options in it..no use...
i switched on the poer adapter after starting ubuntu and vice versa .....no luck...
im literally stuck up here.....

---

### Post by kagashe on 2008-02-16
> **choco_ram said:**
> I have the dell inspiron 1420 vista basic...i am running ubuntu with  the live cd...but iam not able to connect to internet...I have the reliance wimax connection...the antenna cable connects to the power adapter (PoE adapter)...and a LAN cable connects my pc to the adapter...I did ifup ifdown etc...but it cant connect...i did dhclient but it says no DHCPOFFERS received...i very badly want to use ubuntu..pls help...
do i need to install anything on top of the live cd components...internet works perfectly well with vista...
thx in advance...
my ethernet adapter is broadcom netlink fast ethernet...
i used the gui tools for networking..i enabled all options in it..no use...
i switched on the poer adapter after starting ubuntu and vice versa .....no luck...
im literally stuck up here.....How do you login to your ISP on Vista?
I mean there may be a userid and password.

kagashe

---

### Post by choco_ram on 2008-02-16
when i start vista..it takes about a couple of minutes to detect the lan...i dont do anything until it gets connected....the LAN symbol in the system tray shows as connected...then i open the service provider's website and there i enter my login id...but in ubuntu i cannot even open the ISP's website....

---

### Post by kagashe on 2008-02-16
I think your Ethernet card has some problem. See whether this [page]("http://www.cyberciti.biz/faq/linux-broadcom-ethernet-card-driver-installation/") helps.

This [thread]("http://ubuntuforums.org/showthread.php?t=534540") on Ubuntuforums may help.

kagashe

---

### Post by kagashe on 2008-02-16
By the way, which version of Ubuntu are you trying?

At the end of this [thread]("http://ubuntuforums.org/showthread.php?t=498746") DaveTRG (who is also using e1420 laptop) says that it is working on Ubuntu Gutsy.

kagashe

---

### Post by ramans_cse on 2008-02-21
Hi, 
I also face teh same problem, I am hainv Ubuntu Gutsy Gibbon, and the connection is very much fine in my office network. I am having Reliance Wimax internet connection, and the problems i have are:
either or this happens
1. It doesnt get an ip address assigned.
2. or , it gets an ip address after a long time since pluggin in the cable.

when i did strace over the dhcp process, i can see some ipaddress being returned, which is actually the ip address that the provider assigns. But that ip address is not accepted for unknown reasons, Sometimes after a long time, it accepts that ip address , sometimes it doesnt.

PS: The network connection is fine with a Windows machine i am using.
The network connection with ubuntu is fine with all other providers that i tried out. But this provider couldnt understand my problem, since basically all providers support only windows based systems, so i could nt draw any help from their end.

---

### Post by ramans_cse on 2008-02-21
The laptop i am having is HP Compaq nc6400.

---

### Post by kagashe on 2008-02-21
> **ramans_cse said:**
> Hi, 
I also face teh same problem, I am hainv Ubuntu Gutsy Gibbon, and the connection is very much fine in my office network. I am having Reliance Wimax internet connection, and the problems i have are:
either or this happens
1. It doesnt get an ip address assigned.
2. or , it gets an ip address after a long time since pluggin in the cable.

when i did strace over the dhcp process, i can see some ipaddress being returned, which is actually the ip address that the provider assigns. But that ip address is not accepted for unknown reasons, Sometimes after a long time, it accepts that ip address , sometimes it doesnt.

PS: The network connection is fine with a Windows machine i am using.
The network connection with ubuntu is fine with all other providers that i tried out. But this provider couldnt understand my problem, since basically all providers support only windows based systems, so i could nt draw any help from their end.
No. Your problem may not be same. He is having Broadcom Ethernet card which may not be correctly detected on Ubuntu Live CD.

You may seek help on this [forum.]("http://broadbandforum.in/reliance-broadband/")

There is a thread on using Reliance Wimax on Gusty Gibbon [here.]("http://broadbandforum.in/reliance-broadband/22473-reliance-wimax-ubuntu-7-10-a/")

kagashe

---

### Post by pk_rulz on 2008-02-25
Hi 

I am using Reliance wimax with Gutsy. Reliance uses a DHCP server. It works fine on Vista

With Ubuntu I have manged to get an IP address. Using dhcpcd shows me a IPv4 Address however 
ifconfig gives a IPv6 address.

And my avahi ie
eth0:avah also shows up in ifconfig

In Vista once i have acquired the IP all I have to do is open my ISP page and login but here my Firefox refuses to come up with the login page.

I am totally down ... tried all the gyan i could lay my hands on Google

Please help

---

### Post by kagashe on 2008-02-26
> **pk_rulz said:**
> Hi 
In Vista once i have acquired the IP all I have to do is open my ISP page and login but here my Firefox refuses to come up with the login page.

I am totally down ... tried all the gyan i could lay my hands on Google

Please helpTry Opera.

---

### Post by pk_rulz on 2008-02-26
Fixed the issue ... it was avahi that was not assiging a ipv4 add 2 my eth0 ... brought it down its fine now

---

