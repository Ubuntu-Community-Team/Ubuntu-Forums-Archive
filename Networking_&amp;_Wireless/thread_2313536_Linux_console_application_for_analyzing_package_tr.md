---
title: "Linux console application for analyzing package traffic (in C)"
date: 2016-02-13
forum: Networking &amp; Wireless
---

### Post by artss2 on 2016-02-13
First of all I need to know how much place take ubuntu 10.4 .iso when installed on disk (how many gbs)? If I put ubuntu os on virtual machine can I use networkings (using and counting packages and adresses on MAC, IP, ports)? At first -- [COLOR=#ff0000]TCPDUMP/LIBPCAP [/COLOR], are there any C language editor such like Codelite? And the second question is could I use this functions of networking analysis on Ubuntu live cd, especially C language editor and [COLOR=#ff0000]LIBPCAP[/COLOR], if no -- is it possible to install? Which live cd is most relevant for 10.4, fully-functional for this task, and minimal in size?

---

### Post by SeijiSensei on 2016-02-13
First, you should be installing [14.04]("http://cdimage.ubuntu.com/releases/14.04.3/release/"), the current long-term release.  10.04 is already beyond its end-of-life, and 12.04 will be getting there soon.  If you don't need a GUI and can work with a text-mode console, you might find [Ubuntu Server]("http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/current/") a better choice.

I have a copy of Kubuntu 14.04 running in a VirtualBox VM.  It's currently using about 6 GB, but I don't have much in my home directory on the VM. (I have a server where I store most of my documents and such.)  I usually set aside at least 20 GB for an Ubuntu installation, though because VirtualBox allocates space dynamically, it won't all be used right away.

You have a variety of networking options if you use VB, but the most common are NAT, where the VM hides behind the host machine, and "bridged" where the VM connects directly to the network to which the host is attached.  I suggest you read this: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

Things like tcpdump and libpcap are available for pretty much any Linux distribution.

---

### Post by artss2 on 2016-02-14
1. If to use virtual one - i have parallels - so I am interested could ubuntu 10(12).4, as that one is required, take just 1.5-2 gb in basic installation on disk? 2. But I tried demo of ubuntu 10.4 and it has tcpdump and libpcap 1.0 preinstalled and even codeblocks could be installed for one session every time so i thought maybe just demo without full install could be used? As I think anothed livecd is not better then demo launch of full OS iso? But I cannot probably install internet connection for demo and codeblock is too large for my slow internet (codelite is not available for  my 32bit pc). So I tried debian package of codeblock 8.5. But there is about 6 packages with libs and I do not know which to install or in what order another with sudo dpkg -i c...deb? After trying each with errors I got some bad dependency error when launching CB. As far as I understood if CB is in ubuntu software center I need to install from there just with interned connection, it is absent in iso of ubuntu? When I use apt-get for install I got error: E: could not find package -- should it be due absent internet, due to demo mode, or absence in iso. The last error is very frequent.

Of course I need visual IDE. So I understood that key for C app is using libpcap headers whose functions could used in code the functionality of tcpdump and ifconfigure. The main - do they have functions to handle mac and ip adresses, ports, packages counting, and binding to NI. And if use demo I got such message about absent ports, should I use real network devices? Despite i need just app to work on any pc.

I tried to install this group of packages in the whole: sudo dpkg -i *.deb but gradually was getting the dependency problem. And final one: Errors were encountered while processing: AND NAMES OF 7 PACKAGES? When launching CD : error while loading shared libraries:.. cannot open shared object file: no such file or directory. Why I got it? Is it due I use demo mode? Should I install in the whole? Can I install through apt-get but offline package as I have no internet connection on this ubuntu.

---

### Post by ian-weisser on 2016-02-14
SeijiSensei's advice is sound and wise. Pay attention to it.

Consider using the apt-zip package to make installing to your offline system much easier.

dpkg -i works...but is complex and confusing and was superseded in general use by the much easier apt system over a decade ago. Until you understand how Debian package management works, I think you will find dpkg very frustrating. It is NOT like .msi files, the entire philosophy is different.

The error 'E: could not find package' means that the desired package is not on your system, and could not be located in any known online sources.

Ubuntu .iso images are intended for general use, not developers. None include an IDE...IDEs are not general use. Adding an IDE after install is very easy...if you use apt or apt-zip. Since you claim 32-bit and rather low-end hardware, I suggest Xubuntu or Lubuntu 14.04.

---

### Post by steeldriver on 2016-02-14
If you are trying to use 10.04 then errors about not finding packages are to be expected since the release is beyond end-of-life

---

### Post by artss2 on 2016-02-15
In dependency error I see I need such packages as libwqgtk.2.8.0, libwxbase.2.8.0 - that is probably in wxwidget. So maybe after installing it I will be able to use debian, so I did not understand what difficulties are with debian ones? And how can I install with apt-get the offline packages? And what about packages absent in my system? Is it due to absence in iso so maybe after full install it can appear, despite I would not do it as I probably have no place for it on disk despite I did not know how many mb/gb I need for it?

---

### Post by ian-weisser on 2016-02-15
> **artss2 said:**
> And how can I install with apt-get the offline packages? And what about packages absent in my system? Is it due to absence in iso
All of those questions are answered in Post #4.

---

### Post by artss2 on 2016-02-16
I have downloaded wxwidgets2.8_2.8.12.1+dfsg.orig and unpacked to "E:\33\wxwidgets2.8-2.8.12.1.orig", but I did not found no libwxbase, nor libwxgtk. So how I can instlall this packages if they are absent there, or maybe they are hided there? But when searched for this packages I was diected to  wxwidgets for download, so what I should to do?

---

### Post by ian-weisser on 2016-02-16
You should download libwxbase and libwxgtk from packages.ubuntu.com.
They are not hidden files. Those are separate packages, and may in turn have their own dependencies.

You can continue doing this the hard way if you wish, but apt (apt-zip for offline systems) calculates all the dependencies for you and presents you a single list.

---

### Post by artss2 on 2016-02-16
Yes, they are separate packages, about 200-500 kb, but final link when searching on  packages.ubuntu.com lead to wxwidgets2.8-2.8.12.1.orig about 16 mb tar archive, as well as 250 kb archive of wxwidgets. I would be happy to download just  libwxbase and libwxgtk but I have no such download link. Any way how to install the whole wxwidgets tar archive? I think this 2 packages will be available there. I also downloaded apt-zip package from there but I do not know how to install as it probably have no debian extension so I do not know how to install it. // Anyway what is the minimum of Ubuntu 10.4 on disk after installation? Maybe after it, it should be sinplier to handle all of it, and I should not install everything every session.

Really after serching up here [http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=wily&section=all](http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=wily&section=all) I go there [http://packages.ubuntu.com/wily/libwxbase2.8-0](http://packages.ubuntu.com/wily/libwxbase2.8-0) and really at right side is whole package but on the left side is just the one packege despite it is recomended to use just aptitude or sinaptic - I looked for right side as I firstly downloaded the apt-zip, also from wright side, so maybe at left part there is also the debian package of apt-zip as I know the procedure of offline installation of debian ones, at least. So what is the way to use sinaptic or aptitude offline?

---

### Post by ian-weisser on 2016-02-16
Do not install Ubuntu 10.04. See Post #2.

---

### Post by artss2 on 2016-02-16
I am instructed to use 10th or 12th version. So It is possibel to use it. But I try to use archives from there [http://packages.ubuntu.com/wily/i386/libwxgtk-media2.8-0/download](http://packages.ubuntu.com/wily/i386/libwxgtk-media2.8-0/download) (or libwxbase) but they failed everytime, as interrupted at 60 %, 80 % during download on Mozilla, Opera. I see it is permanent, so maybe it is impossible to download by package.

Could anybody providea this 2 packages (with private message or on another url ouside ubuntu.org ) as I would not download it probably in the nearest time from this mirrors.

Now I tried do install deb (with the help of *sudo dpkg -i *.deb*_)_ offline but every with error for Ubuntu 10.4 demo.
Apt-zip 0.18  return the -- short read on buffer-copy (lacked dpkg-deb during /usr/share/doc/apt-zip/changelog.gz) - it maybwe due demo version as /usr/share..such directories is the of full installed version?
The next -- libwxgtk2.8.0 returns - that multiarc support not installed -- so I do not know is it separate package for multiplatform? or multiarc version of libwxgtk2.8.0?
The[COLOR=#000000] [/COLOR]_[[COLOR=#000000]libwxbase2.8-0[/COLOR]]("http://packages.ubuntu.com/wily/libwxbase2.8-0") -_-is containing ununderstood data member data.xz .. giving up -- so also is not clear what is the reason.

10.4 has a problem with installation of extension of xz. That is why i want to ask what in command "dpkg-deb -z" add option of 6 or  &#1093;y -> -z# , -z 6 , -z xy?

Maybe such question I will  have answered. I use Parallels 2.2 on Windows XP. But when starting 12.04 virtual machine i got such error: graphics initializiction failed  Error setting up gfxboot. But I do not know what mode of videocard I should use? md5sum check is correct as well as 512 mb requirement comply with by pc capabilities of 512 mb.

Are there nobody to tell the reason of this error? Should I not use ubuntu 12.04 with Parallels 2.2? As after this error i type help and it returns that I need not use this VM with this kernel. So maybe kernel 3.2/ubuntu 12.04 due to this is not supported as there is option of linux 2.4/2.6 but not 3.2 so using 'other linux' after two these options is not appropriate for later kernel such as 3.2?

When I can got answer here. The main issue is that my intel windows xp probably do not support PAE. So i have such error about 13.04 and 12.04 in Paralels. The same  idling screen is in Virtual PC, and Virtualbox despite have the checker for pae/nx do not allow to install such ubuntu more than about 25%.  So I probably need Xubuntu or Lubuntu 12.04. As c   environment, tcpdump, libcaps is present on ubuntu 10.04 so is it on ubuntu, lub, xub 12.04? I would use 10.04 but it do not support xz packages installing so I cannot use codeblocks or so to install offline. The 12.04 should support. So I also interested can I use miniiso 12.04 for developing c/c   applications? Is there gcc, make, appropriate environment?

I put xubuntu non-pae 12.04 iso in parallels 2.2. But when starting install I got cycle of lines:1. Stack 2. Call trace 3.Code. Alot of double numbers sequence 4. Process swapper/0. What i can to do here to install nonpae iso in virtual machine in nonpae pc?

i would like to return to the very topic as xubuntu 10.4 with codeblocks 10.5 works. If i want to define the mac/ip adresses of packet should I use header structures and their properties with type casting or   I could use filter expressions in such functions like pc§Ñp_compil§Ö() for filtering and defining packets by means of tcpdump? If use the first one with headers I do know how use frame headers for defining frame d/s mac-adr. But what about sourc§Ö/d§Öst. ip adress of packet? To use pcap_loop? If use just eth0 in virtual machine without internet connection should I have just one? Mac adress of eth0 int.? And should it have the whole spectrum of port for such one interface as well if to use ppp0, then there will be another set of such post number?

It happened to have a more big problem. I need probaly use root for packet sniffing but without success. I use simple code with  pcap_lookupdev(errbuf) but it results in errbuf --  not suitable device found -- despite ifconfig shows eth0 ( &#1077;th3 here) and lo. I used  seteuid(0) but with the same error. As well when created handles by  pcap_create("eth3", errbuf). Maybe there is some other way f.e. with using sudo for whole file system? When taking into account - [http://ubuntuforums.org/archive/index.php/t-1526065.html](http://ubuntuforums.org/archive/index.php/t-1526065.html) maybe the last option with capabilities was not used.

---

