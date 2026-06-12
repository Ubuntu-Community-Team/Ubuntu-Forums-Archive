---
title: "Internet Connection Doesn't Function"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by IdanH14 on 2008-01-28
Hi there,
About two months ago, I made a good deed and recommended a friend of mine to try Linux. Since I use Ubuntu, it naturally proposed he should try it.
On the first trial, he had some serious problem concerning the partitions which I was unable to solve. Needless to say, the system ran well, including the internet connection, except for the partitions problem.
On the second trial, he noticed a weird thing right from the start. Whereas his internet connection was working well on Ubuntu Feisty Fawn (both on live CD and after the installing process), it didn't work at all on Gutsy Ribbon (again, not in the Live CD and not after the installing process).
He is using a B-Focus 352 router, which is connected to his computer with a USB port, which is running well. He can't use a network card because there is none. The router worked well with the same configuration and the same connection cable on Feisty Fawn. Needless to say, the router works well on Windows XichsPee (XP).

In my opinion (and you should run your own tests. I'm not a expert when it comes to Linux in general or Ubuntu in particular), the router seems not to provide the computer with "external" IP address. Meaning, the computer is recognized by the router, and is a part of the network, but the router doesn't allow him to access the internet.

If you need any additional information, please ask.
Any help on this matter, which make me go crazy for a week now, would be appreciated!
Thank you all!

Ido

---

### Post by chewearn on 2008-01-28
1. What IP is assigned to the router?
2. Is DHCP enabled, or are you setting ubuntu by static IP?
3. Can you ping the router from ubuntu?
4. Can you ping and external IP?
5. Can you resolved a url to it's IP, i.e. is the DNS properly configured?

Based on what I know about LAN set-up, if you can answer positive to these questions, then it should work.   Go thru the questions one by one, and feedback at which point it is negative.

---

### Post by IdanH14 on 2008-01-28
> **AstalaVista said:**
> 1. What IP is assigned to the router?
2. Is DHCP enabled, or are you setting ubuntu by static IP?
3. Can you ping the router from ubuntu?
4. Can you ping and external IP?
5. Can you resolved a url to it's IP, i.e. is the DNS properly configured?

Based on what I know about LAN set-up, if you can answer positive to these questions, then it should work.   Go thru the questions one by one, and feedback at which point it is negative.

1. Are you sure you mean the IP of the router? Anyway, it's 10.0.0.138.
2. My friend claims that DHCP is enabled, but I don't have a clue what do you mean by static IP. Do you refer to the static IP which is assigned by the router? How can control the configuration?
3 + 4)
I don't know how to read these results, so I'll just hand it over to you:

```
 ping www.walla.com
PING en.walla.com (192.118.82.148) 56(84) bytes of data.
64 bytes from www.walla.com (192.118.82.148): icmp_seq=1 ttl=249 time=1162 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=2 ttl=249 time=1243 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=3 ttl=249 time=1236 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=4 ttl=249 time=1289 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=5 ttl=249 time=1347 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=6 ttl=249 time=1310 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=7 ttl=249 time=1339 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=8 ttl=249 time=1409 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=9 ttl=249 time=1352 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=10 ttl=249 time=1281 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=11 ttl=249 time=1011 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=12 ttl=249 time=768 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=13 ttl=249 time=778 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=14 ttl=249 time=823 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=15 ttl=249 time=858 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=16 ttl=249 time=921 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=17 ttl=249 time=973 ms
64 bytes from www.walla.com (192.118.82.148): icmp_seq=18 ttl=249 time=970 ms
.....


===================================================================================================
 ping 10.0.0.138
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
64 bytes from 10.0.0.138: icmp_seq=1 ttl=255 time=1.06 ms
64 bytes from 10.0.0.138: icmp_seq=2 ttl=255 time=0.838 ms
64 bytes from 10.0.0.138: icmp_seq=3 ttl=255 time=0.797 ms
64 bytes from 10.0.0.138: icmp_seq=4 ttl=255 time=0.836 ms
64 bytes from 10.0.0.138: icmp_seq=5 ttl=255 time=0.808 ms
64 bytes from 10.0.0.138: icmp_seq=6 ttl=255 time=0.789 ms
64 bytes from 10.0.0.138: icmp_seq=7 ttl=255 time=0.805 ms
64 bytes from 10.0.0.138: icmp_seq=8 ttl=255 time=0.802 ms
64 bytes from 10.0.0.138: icmp_seq=9 ttl=255 time=0.805 ms
64 bytes from 10.0.0.138: icmp_seq=10 ttl=255 time=0.789 ms
64 bytes from 10.0.0.138: icmp_seq=11 ttl=255 time=0.962 ms
64 bytes from 10.0.0.138: icmp_seq=12 ttl=255 time=0.915 ms
64 bytes from 10.0.0.138: icmp_seq=13 ttl=255 time=0.832 ms
64 bytes from 10.0.0.138: icmp_seq=14 ttl=255 time=0.839 ms
64 bytes from 10.0.0.138: icmp_seq=15 ttl=255 time=0.828 ms
64 bytes from 10.0.0.138: icmp_seq=16 ttl=255 time=0.836 ms
64 bytes from 10.0.0.138: icmp_seq=17 ttl=255 time=0.834 ms
64 bytes from 10.0.0.138: icmp_seq=18 ttl=255 time=0.804 ms
64 bytes from 10.0.0.138: icmp_seq=19 ttl=255 time=0.833 ms

......

```

Walla.com is external IP, it's a web page.  10.0.0.138 is the router.

5. How can I check that?

Thank you for you quick reply.

---

### Post by IdanH14 on 2008-01-28
Bump

---

### Post by etz on 2008-01-28
U should check with your ISP.
Has same problem and it was on there side

[ETZ]("http://www.allcanadamovers.com")

---

### Post by chewearn on 2008-01-28
Based on the ping results to [www.walla.com](www.walla.com), ubuntu is accessing internet; there is no problem there.

So then, could you explain a bit more about the problem.  Example, you enter a URL in Firefox and it came back with an error?

---

### Post by IdanH14 on 2008-01-28
The one who said it's the ISP's problem:
It's not. He called his ISP's tech support and were unable to help him.

> **AstalaVista said:**
> Based on the ping results to [www.walla.com](www.walla.com), ubuntu is accessing internet; there is no problem there.

So then, could you explain a bit more about the problem.  Example, you enter a URL in Firefox and it came back with an error?

My fried claims that Firefox can't surf at all, he can't use Pidgin and that's basically it.
I will ask him for snapshots of what he sees exactly once he will be online.

Thank you all again!

EDIT:
Here are two pictures:

[http://i25.tinypic.com/2vt2s7a.jpg](http://i25.tinypic.com/2vt2s7a.jpg)
[http://i26.tinypic.com/20at102.jpg](http://i26.tinypic.com/20at102.jpg)

---

### Post by IdanH14 on 2008-01-29
Bump
Plus, here are two snapshots (I noticed that editing didn't bumped the message):

[http://i25.tinypic.com/2vt2s7a.jpg](http://i25.tinypic.com/2vt2s7a.jpg)
[http://i26.tinypic.com/20at102.jpg](http://i26.tinypic.com/20at102.jpg)

---

### Post by IdanH14 on 2008-01-31
Bump, I guess. :(
Any thoughts?

---

### Post by lungdart on 2008-01-31
Odd that you can ping an external source through DNS and get a result, but neither pidgin or firefox will resolve a destination.

First off, im going to give you some commands and what to look for as your kind of glazed by the previously mention trouble shooting guides. Everything is to be typed in the terminal as the normal user. Give the entire output of the commands.

1. is the USB network dongle wireless or wired? If it is a wireless card, how was it configured? Did you need to use the restricted driver manager/ndiswrapper, or are you going from straight out of the box.

2. Are there any other networking interfaces? what are your interfaces locations and settings?
```
ifconfig -a
```

3. are your interfaces connected with static or DHCP?
```
cat /etc/network/interfaces
```
Also make sure in here that the gateway is set to the router IP of 10.0.0.138

4. Have you tried to power cycling the router? Turn the router off, and unplug it for 5 seconds. Plug it back in and turn it on. Once it is booted try connecting again

5. Do all other devices (wired and wireless) work on this router?

6. Ping the router again
```
ping 10.0.0.138
```

7. Ping another outside address
```
ping www.red.com
```

8. Test something other then firefox/pidgin, like apt.
```
sudo apt-get update
```

9. If that worked try installing Firestarter(firewall front end) if it is not allready
```
sudo apt-get install firestarter
```
Run this, configure it for the interface your using, and then disable it temporarly and see if that lets you through.


Let us know.

---

### Post by IdanH14 on 2008-02-02
> **lungdart said:**
> Odd that you can ping an external source through DNS and get a result, but neither pidgin or firefox will resolve a destination.

First off, im going to give you some commands and what to look for as your kind of glazed by the previously mention trouble shooting guides. Everything is to be typed in the terminal as the normal user. Give the entire output of the commands.

1. is the USB network dongle wireless or wired? If it is a wireless card, how was it configured? Did you need to use the restricted driver manager/ndiswrapper, or are you going from straight out of the box.

2. Are there any other networking interfaces? what are your interfaces locations and settings?
```
ifconfig -a
```

3. are your interfaces connected with static or DHCP?
```
cat /etc/network/interfaces
```
Also make sure in here that the gateway is set to the router IP of 10.0.0.138

4. Have you tried to power cycling the router? Turn the router off, and unplug it for 5 seconds. Plug it back in and turn it on. Once it is booted try connecting again

5. Do all other devices (wired and wireless) work on this router?

6. Ping the router again
```
ping 10.0.0.138
```

7. Ping another outside address
```
ping www.red.com
```

8. Test something other then firefox/pidgin, like apt.
```
sudo apt-get update
```

9. If that worked try installing Firestarter(firewall front end) if it is not allready
```
sudo apt-get install firestarter
```
Run this, configure it for the interface your using, and then disable it temporarly and see if that lets you through.


Let us know.

OK, I'm a little late, but here are the results. He and I both have no clue how to read those results, therefore here they are:
1. Wired. He didn't need any "restricted" drivers.
2.
```
eth0      Link encap:Ethernet  HWaddr 00:19:D1:12:35:FF  
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::219:d1ff:fe12:35ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:826168 (806.8 KB)  TX bytes:27648 (27.0 KB)
          Base address:0x30c0 Memory:52200000-52220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
```
3.
```
 cat /etc/network/interfaces
auto lo
iface lo inet loopback
dns-nameservers ip.address.of.nameserver
```
4. He was stupid enough not to tell me whether he tried this or not.
5. Yes. I can't tell whether they are wired on wireless, but I know he has a couple computers connected to the router.
6 + 7. I'm not sure whether this is related to  the previous instructions, but here's the output:
```
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
64 bytes from 10.0.0.138: icmp_seq=1 ttl=255 time=0.804 ms
64 bytes from 10.0.0.138: icmp_seq=2 ttl=255 time=0.817 ms
64 bytes from 10.0.0.138: icmp_seq=3 ttl=255 time=0.809 ms
64 bytes from 10.0.0.138: icmp_seq=4 ttl=255 time=0.798 ms
64 bytes from 10.0.0.138: icmp_seq=5 ttl=255 time=0.796 ms
```
```
PING red.com (72.32.210.6) 56(84) bytes of data.
64 bytes from www.red.com (72.32.210.6): icmp_seq=1 ttl=54 time=248 ms
64 bytes from www.red.com (72.32.210.6): icmp_seq=2 ttl=54 time=286 ms
64 bytes from www.red.com (72.32.210.6): icmp_seq=3 ttl=54 time=351 ms
64 bytes from www.red.com (72.32.210.6): icmp_seq=4 ttl=54 time=252 ms
64 bytes from www.red.com (72.32.210.6): icmp_seq=5 ttl=54 time=271 ms
```
8.
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-he
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-he
Reading package lists... Done
```
9. I'm assuming it didn't help by because of the following output:
```
sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firestarter
```

Thank you very much for your help!

---

### Post by IdanH14 on 2008-02-03
I guess I will...
Bump!

---

### Post by lungdart on 2008-02-05
The oddness continues.

if that machine is on the network pinging and outside source by its domain name, it is plain and simple reaching the internet.

Now, your apt-get update didnt do anything but ignore the CD's that arent in your tray. How is your repository list?

Open a terminal and tyoe:
```
sudo su -p
cd /etc/apt
cp ./sources.list ./sources.bak
gedit /etc/apt/sources.list&
```

This will make a backup of your repository list, and open a text editor to add more to it (The first sudo command allows you to change to root while keeping your user info like your home directory). Replace what ever is in that with this

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```

Save the file and exit the text editor. If at any point you want to undo this change:

```
sudo su -p
cd /etc/apt
rm ./sources.list
mv ./source.bak ./sources.list
```

But dont do that unless your apt goes wild on you, but it never should, as that is taken directly from ubuntuguide.org

Then try running (Use sudo unless your still root from the sudo su -p)
```
apt-get update
```

This should generate more information, and look something like this

```
root@lung-zilla:/etc/apt# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 http://ca.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://ca.archive.ubuntu.com gutsy/main Translation-en_CA                
Ign http://ca.archive.ubuntu.com gutsy/restricted Translation-en_CA  
Ign http://ca.archive.ubuntu.com gutsy/universe Translation-en_CA    
Ign http://ca.archive.ubuntu.com gutsy/multiverse Translation-en_CA  
Get:2 http://ca.archive.ubuntu.com gutsy-updates Release.gpg [191B]  
Ign http://ca.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Get:3 http://ca.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Get:4 http://archive.canonical.com gutsy Release.gpg [191B]          
Ign http://archive.canonical.com gutsy/partner Translation-en_CA     
Get:5 http://security.ubuntu.com gutsy-security Release.gpg [191B]   
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA 
Ign http://ca.archive.ubuntu.com gutsy-backports/main Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://archive.canonical.com gutsy Release                       
Hit http://security.ubuntu.com gutsy-security Release                
Hit http://archive.canonical.com gutsy/partner Packages              
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Ign http://ca.archive.ubuntu.com gutsy-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com gutsy Release
Hit http://ca.archive.ubuntu.com gutsy-updates Release
Hit http://ca.archive.ubuntu.com gutsy-backports Release
Hit http://ca.archive.ubuntu.com gutsy/main Packages
Hit http://ca.archive.ubuntu.com gutsy/restricted Packages
Hit http://ca.archive.ubuntu.com gutsy/main Sources
Hit http://ca.archive.ubuntu.com gutsy/restricted Sources
Hit http://ca.archive.ubuntu.com gutsy/universe Packages
Hit http://ca.archive.ubuntu.com gutsy/universe Sources
Hit http://ca.archive.ubuntu.com gutsy/multiverse Packages
Hit http://ca.archive.ubuntu.com gutsy/multiverse Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/main Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com gutsy-backports/main Packages
Hit http://ca.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://ca.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://ca.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com gutsy-backports/main Sources
Hit http://ca.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://ca.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://ca.archive.ubuntu.com gutsy-backports/multiverse Sources
Fetched 5B in 2s (2B/s)  
Reading package lists... Done
```

If it does, go ahead and do a (Again use sudo if you are not root)
```
apt-get upgrade
```

Then restart the system, power cycle the router, reboot the system and try again. That will let any restart necessary changes like kernel upgrades to take effect and also force you to close out of your browser :P

Again, is the USB dongle wired to the router? Or is wireless?

---

### Post by IdanH14 on 2008-02-07
UPDATE:
My friend called his ISP tech support, and they somehow managed to get his Firefox working.
For the time being, he can only surf with  Firefox.
The  tech supporter told him that the problem was the DNS configuration, which leads me to the question: How can he configure the DNS globally? Meaning, how can he change the DNS configuration so that every program (i.e. Pidgin) would be effected and not only Firefox?
I ask that because it seems like the DNS configuration was only applied to  Firefox.
Any other ideas would be appreciated.

lungdart:
Sorry that I ignore your suggestion, I only try to find another line of thought.
Anyway, my friend promised me he'd do what you suggested today.

---

### Post by lungdart on 2008-02-07
DNS shouldn't be the problem since he can ping out to an outside address. This obviously implied that DNS is working.

to set the DNS server globally, go to system->Administration->Network and click on the DNS tab. It will normally be pointed to your router as your router should get the DNS information from your ISP. you can enter it at the desktop side here though.

---

### Post by Arghesis on 2008-02-28
Unbelievably !

Finally found someone who has  the same problem I have.

I have a connection to my router from my laptop. I also have connected my regular PC to the router. Internet works fine on PC but doesn't work on Laptop. Connection is cable.
The lan card is broadcom, but the drivers are ok. They have to be, since I can also ping an outside address. I can, for example go to Konq and fish://pc_ip and get the files I need to work with 

BUT !!! I don't have internet on the laptop! Only on the PC .... can't acces any web page or use aptitude update or anything on the laptop!

I'm searching for a solution on the forums for 3 days now.

I edited sources.list and did sudo aptitude update but after waiting for some while (trying to connect) it says Ignoring [http://security.ubuntu](http://security.ubuntu) .... for each source.
Sometimes it shows:
1% [6 Release 0/65.9kB 0%] [Waiting for headers] [Waiting for headers]

THIS IS WEIRD !!!

Wlan is also broadcom. I have managed to install the restricted drivers, but haven't tested them. I will test it tomorrow. Anyway, wlan wouldn't be such a much problem.
 
THE PROBLEM is that i can't have internet at home. And it sux big time! Especially that I'm using a wired connection.

I also try connecting to the internet directly! Still no results. 

Router gives dhcp ip addresses. 

The output of $cat /etc/network/interfaces is :

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth0

That's it ...
If someone could help ...

I wanted to add one more thing ... I'm sure it's doable but I'm not sure how (if you have any answers to this)
 - I was thinking of making a bridge connection between the PC and the Laptop (since the connection between them 2 works fine) and get the internet through the PC.
(I'll google this up when I come home tonight)

PS: I have an Acer Extensa 5220 if this info is usefull.

---

### Post by Arghesis on 2008-03-01
Problem solved for me.

It was actually the router who had the problems ...

I connected directly and it works. I don't know why it didn't work the first time, but I'm happy that it works now.

I'll see about installing ndiswrapper for wlan.

---

### Post by Arghesis on 2008-03-01
Problem solved for me.

It was actually the router who had the problems ...

I connected directly and it works. I don't know why it didn't work the first time, but I'm happy that it works now.

I'll see about installing ndiswrapper for wlan.

---

