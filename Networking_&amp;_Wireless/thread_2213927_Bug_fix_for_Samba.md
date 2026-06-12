---
title: "Bug fix for Samba"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by Wtdtexas on 2014-03-29
Quick background on me, Linux hobbyist, burned out programmer, Novell guy that, 10 years ago got sick for a year, lost my company, and now work as the on-site guy for a national Geek company. not "squad" :mad:

 I get customer getting systems upgrades or Dead HDD&#8217;s that they want me to haul off their old equipment. So I play with Linux on the old systems, as hobby not for a living. Doing this for 10 years or so.
 
 At the start of 2014, I stated getting a lot of old xp system, and down loaded my favorite Linux distro's and started installing...... Could not see Shared xp, win 7 systems. Thought it was just a bug with that release and tried another distro. Same problem, one after another, same problem. Would check boards and try lots of things and get it to work. But over and over on a fresh install, it would not see windows shares. Never had this problem before.:mad:

 Remember this is a hobby, but after 2 months I discovered the problem :p, small changes to smb.conf where made in the last 6 to 12 months that made it so you can't see XP, win 7 Shares &#8220;out of the box&#8221;.

 I think this was deliberate by &#8220;they who can not be named&#8221; that is if you don't want to get sued.

 This was done in prep for the upcoming deadline. So that first time Linux installers would install a Linux, not see other systems at home and give up on Linux.

 Please change the Samba Default to see win shares.
 
Netbios section  
 
 Dns proxy = yes;
 
 Set the &#8220;name resolve order&#8221; remove &#8220;;&#8221; by default and set order, I believe is &#8220;bcast host lmhost wins&#8221;.

Any other changes please make as needed.

---

### Post by Lars Noodén on 2014-03-29
Welcome.

It looks like that file belongs to the package samba-common.  So to get a bug reported run in the terminal:

```

ubuntu-bug samba-common

```

You'll need to sign up for a [Launchpad](https://launchpad.net/ubuntu) account for that.  Launchpad is where all the bugs need to get reported to be seen.  If you post the bug number here, maybe others can help add information.

---

### Post by bab1 on 2014-03-29
> **Wtdtexas said:**
> ...

 Remember this is a hobby, but after 2 months I discovered the problem :p, small changes to smb.conf where made in the last 6 to 12 months that made it so you can't see XP, win 7 Shares “out of the box”.  

I think this was deliberate by “they who can not be named” that is if you don't want to get sued.

This was done in prep for the upcoming deadline. So that first time Linux installers would install a Linux, not see other systems at home and give up on Linux.
I just set one up this morning. With no changes to the smb.conf file I can see the server when browsing. > 

Please change the Samba Default to see win shares.
Netbios section  
 
Dns proxy = yes;

This is only needed if you are running a multi-segment network (subnets) and nmbd is also the WINS server.  You do not need WINS in a simple single subnet LAN.  From the smb.conf man page```
 dns proxy (G)

           Specifies that nmbd(8) **[COLOR="#FF0000"]when acting as a WINS server[/COLOR]** and finding that a NetBIOS name
           has not been registered, should treat the NetBIOS name word-for-word as a DNS name and
           do a lookup with the DNS server for that name on behalf of the name-querying client.
```
> 
Set the “name resolve order” remove “;” by default and set order, I believe is “bcast host lmhost wins”.

The default order (whether commented out or not) is: name resolve order = lmhosts host wins bcast

The defaults do not need to be declared to function.  To see all the parameters in use use this command ```
testparm -v
```

---

### Post by Wtdtexas on 2014-03-30
"I just set one up this morning. With no changes to the smb.conf file I can see the server when browsing."

Which one? all the installs i tried have been download in the last month or so.

The problem is not seeing severs or nas but windows shared folders. 

My network hads 3 XP systems 3 windows 7 with shared folders.

Netgear Cable modem/router. one segment.

I downloaded all the below and tried most the below on virtualbox or a test system  same results every time :

archlinux-2014.03.01-dual.iso
boss-5.0-i386-DVD-23-Dec-2013.iso
crunchbang-11-20130506-amd64.iso
debian-7.4.0-amd64-DVD-1.iso
debian-7.4.0-amd64-DVD-2.iso
debian-7.4.0-amd64-DVD-3.iso
deepin_2013_en_amd64.iso
Fedora-Live-Desktop-x86_64-20-1.iso
kubuntu-12.04.4-desktop-amd64.iso
linuxmint-13-mate-dvd-nocodecs-64bit.i
linuxmint-16-cinnamon-dvd-oem-64bit.is
linuxmint-16-kde-dvd-64bit.iso
linuxmint-16-mate-dvd-64bit.iso
linuxmint-201303-mate-dvd-64bit.iso
lubuntu-13.10-desktop-amd64.iso
LuninuXOS-13.00-Desktop-amd64-Beta-1.i
lxle-12.04.3-64.iso
lxle64.iso
lxle64.iso.md5
pclinuxos-kde-minime-2013.12.iso
pclinuxos-lxde-2013.12.iso
pclinuxos-mate-2013.12
pclinuxos-mate-2013.12.iso
pclinuxos64-kde-2013.12.iso
pclinuxos64-kde-fullmonty-2013.12.iso
pclinuxos64-mate-2013.12
Peppermint-4-20131113-amd64.iso
progress-linux-2.1-base-system_amd64.i
Sabayon_Linux_13.08_amd64_MATE.iso
Sabayon_Linux_14.01_amd64_KDE.iso
snowlinux-4-cinnamon-amd64.iso
snowlinux-4-e17-amd64.iso
solydx64_201401.iso
ubuntu-12.04.4-desktop-amd64.iso
ubuntu-13.04-desktop-amd64.iso
ubuntu-13.10-desktop-amd64(1).iso
ubuntu-13.10-desktop-amd64.iso
zorin-os-8.1-core-32.iso
zorin-os-8.1-core-64.iso

---

### Post by Wtdtexas on 2014-03-30
The only changes i have to make for the linux installs to see the shared folders are :

Set the workgroup name, set the netbios name( for those that require that), 

Set Dns proxy = yes;
 
 Set the &#8220;name resolve order&#8221; remove &#8220;;&#8221; , set order &#8220;bcast host lmhost wins&#8221;.

restart.

Then most of the installs see windows shared folders fine after that.

1 or 2 I had to do more(change 1,2 more lines), but after so many installs, lost track of them sorry.

---

### Post by bab1 on 2014-03-30
> **Wtdtexas said:**
> Which one? all the installs i tried have been download in the last month or so.

This one: ubuntu-12.04.4-desktop-amd64.iso.  All the distro packages will work.  In the past I have used CentOS and Debian.  Your problem is not the distro or the packaging of Samba.  I'm assuming we are talking about Samba v3.  FYI -- Ubuntu 14.04 will have Samba v4 only 
> 
The problem is not seeing severs or nas but windows shared folders.
My network hads 3 XP systems 3 windows 7 with shared folders.

Netgear Cable modem/router. one segment.

I downloaded all the below and tried most the below on virtualbox or a test system  same results every time :

archlinux-2014.03.01-dual.iso
...
zorin-os-8.1-core-64.iso
That should tell you something in itself.  My guess is that you have something misconfigured somewhere else.

---

### Post by bab1 on 2014-03-30
> **Wtdtexas said:**
> The only changes i have to make for the linux installs to see the shared folders are :

Set the workgroup name, set the netbios name( for those that require that), 

Set Dns proxy = yes;
 
 Set the “name resolve order” remove “;” , set order “bcast host lmhost wins”.

restart.

Then most of the installs see windows shared folders fine after that.

1 or 2 I had to do more(change 1,2 more lines), but after so many installs, lost track of them sorry.
This most likely means you don't have local network DNS (hosts) set up correctly.  

Samba by default converts the hostname to a netbios name internally.  If it can't correctly do that it will fail.  Providing the netbios name is one way of correcting the conversion manually.  The name resolve order most of the time uses host (DNS) and then bcast.  You have to declare a WINS server for that to work.  LMHOSTS is not used very often anymore.

---

### Post by Wtdtexas on 2014-03-30
> **bab1 said:**
> This most likely means you don't have local network DNS (hosts) set up correctly.  

Samba by default converts the hostname to a netbios name internally.  If  it can't correctly do that it will fail.  Providing the netbios name is  one way of correcting the conversion manually.  The name resolve order  most of the time uses host (DNS) and then bcast.  You have to declare a  WINS server for that to work.  LMHOSTS is not used very often anymore.

In the past I have used CentOS and Debian.  Your problem is not the distro or the packaging of Samba.

  

Used the Netgear software to configure the rounter.

Just switched from Uverse to TWC during the middle of all this, same problem with my ATT Uverse.

A few of the installs left the Netbios names blank, Not Ubuntu.

I got that order off of the boards, after a week of looking.

I have never had this problem before the last 3 months.

The simple changes to the smb.conf file above fixes the problems.

---

### Post by bab1 on 2014-03-30
> **Wtdtexas said:**
> Used the Netgear software to configure the rounter.

Most home networks do not have LOCAL DNS resolution  You would have to set that up yourself outside of the router.
> 
Just switched from Uverse to TWC during the middle of all this, same problem with my ATT Uverse.

Not an ISP problem.
> 
A few of the installs left the Netbios names blank, Not Ubuntu.

By *default* no netbios name is configured.  You always have to add it to the smb.conf
> 
I got that order off of the boards, after weeks of looking.

It's all stated in the documentation.  Check ```
man smb.cof
```...available at the command line.
> 
I have never had this problem before the last 3 months.
I don't know what to say about that.  I don't even think of it as a problem.  Samba is used in many different configurations.  It's acceptable to change the configuration file.  The package maintainer has no idea how you want to use the application.  A large enterprise won't use or configure Samba like you would.

---

### Post by Wtdtexas on 2014-03-30
What is the problem. 

I got these solutions off the boards from other people having the same problem.

2 small changes to the Samba default config file would solve the problems for everyone who is having this problem.

---

### Post by bab1 on 2014-03-30
> **Wtdtexas said:**
> What is the problem. 

I got these solutions off the boards from other people having the same problem.

2 small changes to the Samba default config file would solve the problems for everyone who is having this problem.

I think the default config file is fine.  The vast majority of the Samba installs work correctly.  if you need to edit the config file then so be it.  The folks that have a issue just need the *correct* answers.

In this case I would say learn how Samba really works.  Read the documentation.

---

