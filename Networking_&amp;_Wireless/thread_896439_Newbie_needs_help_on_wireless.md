---
title: "Newbie needs help on wireless"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by jacksparrow1 on 2008-08-21
Hi everyone,

I've been using Windows all my life and yesterday I decided to try and explore other operatubg systems and just get a feel to them and if I do like them then I would dump windows.

Now the first and most obvious O.S I would try would be Ubuntu and I'm a bit confused after installation so I was hoping someone could help me out please.

I have Ubuntu installed, I was browsing the web and saw that the first thing after installing Ubuntu is to install Automatix (so I can play Mp3's etc), I saw this forum and saw a thread where it asked me to 'Get automatix' using the website address, however the biggest problem is I have no Internet access on the Ubuntu machine. I do have a wireless router and a I tried connecting to it using Ubuntu but I can't for some reason I do have a PCI wireless card installed in the PCI slot in the motherboard. I dont want to move my pc to where my router is and take the ethernet cable and do a direct connection as the wire is too far.

Please help me as I do like Ubuntu but I just dont know what to do to install automatix and my wireless internet connection. (I think I have to install the wireless first and then use Ubuntu to install the Automataix)

One more thing is it possible to install automatix without the internet? So I download it now in Mozilla, put it on usb and install the usb in Ubuntu and copy the files ovre and then use terminal?

If not then its ok.

Thanks everyone

---

### Post by tuxxy on 2008-08-21
Did you read the wireless how to?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by jacksparrow1 on 2008-08-21
Thanks I will give that a try, just fyi I have a buffalo pci card and will update more information later on the card.

I just read somewhere that Automatix is not supported on this forum, is there a particular reason?  I just thought a ubuntu forum would offer help on all aspects of ubuntu, and requiring codecs is essential imo.

thanks

---

### Post by pro003 on 2008-08-21
what kind of connection do you use, pppoe? how do you connect to internet on windows? what kind of pci card you have and did you checked out network manager systray icon in upper right side of the desktop?

---

### Post by jacksparrow1 on 2008-08-21
Sorry what do you mean type of connection?  I have a modem connected to a router, windows works fine it connects to the wireless connection (under xp and vista) as on my pc I have tripple boot (ubuntu, xp and vista).  I will add more inforation on the car im using in about 15 minutes.  I will check the network manager try aswell in 15 minutes.

What I did try today was click on the network in the top right hand corner and it asked for the wireless connection name, and the type of password (which is wep) and for the key, I inserted all of these but it still didnt connect.

THanks

---

### Post by jacksparrow1 on 2008-08-21
Hi I have a buffalo wireless g 125 high speed pci card.  When I click on the network manager top right hand corner it says 

Wired network (disabled)
wireless network (enabled)
connect to other wireless network
create new wireless network and
manual configuration.

Thanks

---

### Post by jacksparrow1 on 2008-08-21
> **tuxxy said:**
> Did you read the wireless how to?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I looked at that link and tried some od the coding that was shown on that site but everything I try is not working on my terminal.

So far I tried the following:

```

ubuntu@UBUNTU-PC:~$ ishw 
bash: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sude pccardct1 ident 
bash: sude: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
[sudo] password for ubuntu:  
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo ishw 
sudo: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v 
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value] 
            {-i | -s | <command>} 
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ... 
ubuntu@UBUNTU-PC:~$ sudo ishw -businfo 
sudo: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardcti ident 
sudo: pccardcti: command not found 
ubuntu@UBUNTU-PC:~$ gksudo gedit /etc/pcmcia/config.opts 
ubuntu@UBUNTU-PC:~$ 1spci -v 
bash: 1spci: command not found 
ubuntu@UBUNTU-PC:~$  

```

As you can see for some reason its not working, am I doing this wrong>  I dont know what to do :confused:

thsnks

EDIT** What I have gathered is before I can install codecs/updates I HAVE to get my internet to work so I guess I have to fix my wireless before I can do anything so I have put automatix on hold.

---

### Post by jacksparrow1 on 2008-08-21
Anyone :mad:

---

### Post by pro003 on 2008-08-21
post the output of the command:

```
# ifconfig
```

---

### Post by Ayuthia on 2008-08-21
> **jacksparrow1 said:**
> I looked at that link and tried some od the coding that was shown on that site but everything I try is not working on my terminal.

So far I tried the following:

```

ubuntu@UBUNTU-PC:~$ ishw 
bash: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sude pccardct1 ident 
bash: sude: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
[sudo] password for ubuntu:  
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo ishw 
sudo: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v 
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value] 
            {-i | -s | <command>} 
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ... 
ubuntu@UBUNTU-PC:~$ sudo ishw -businfo 
sudo: ishw: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardct1 ident 
sudo: pccardct1: command not found 
ubuntu@UBUNTU-PC:~$ sudo pccardcti ident 
sudo: pccardcti: command not found 
ubuntu@UBUNTU-PC:~$ gksudo gedit /etc/pcmcia/config.opts 
ubuntu@UBUNTU-PC:~$ 1spci -v 
bash: 1spci: command not found 
ubuntu@UBUNTU-PC:~$  

```

As you can see for some reason its not working, am I doing this wrong>  I dont know what to do :confused:

thsnks

EDIT** What I have gathered is before I can install codecs/updates I HAVE to get my internet to work so I guess I have to fix my wireless before I can do anything so I have put automatix on hold.

The commands that you are looking far are lshw -C network.  The first letter is a lower-case L.  The Terminal is case-sensitve so make sure that you use a capital C.  The other command is lspci -nn.  The first letter is also a lower-case L.

---

### Post by jacksparrow1 on 2008-08-22
> **pro003 said:**
> post the output of the command:

```
# ifconfig
```

Will do in about half an hour,


Thanks both of you for helping me out, much appreciate it

---

### Post by jacksparrow1 on 2008-08-22
Hi pro003,  

As requested:

```

ubuntu@UBUNTU-PC:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1c:25:36:69:92  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:19 Base address:0x6000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1148 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1148 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:58360 (56.9 KB)  TX bytes:58360 (56.9 KB)

ubuntu@UBUNTU-PC:~$ 


```

By the way if it helps you in anyway I ran the following coding to make ndiswrapper install, don't know if it has installed though.

```

ubuntu@UBUNTU-PC:~$ sudo apt-get install ndiswrapper-utils-1.9

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following extra packages will be installed:

  ndiswrapper-common

Suggested packages:

  ndiswrapper-source

The following NEW packages will be installed

  ndiswrapper-common ndiswrapper-utils-1.9

0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.

Need to get 0B/30.4kB of archives.

After this operation, 213kB of additional disk space will be used.

Do you want to continue [Y/n]? y

Selecting previously deselected package ndiswrapper-common.

(Reading database ... 95844 files and directories currently installed.)

Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...

Selecting previously deselected package ndiswrapper-utils-1.9.

Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...

Setting up ndiswrapper-common (1.50-1ubuntu1) ...

Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...

ubuntu@UBUNTU-PC:~$ 


```

If my drivers arent installed, what do I do to make them install?  I have my wireless card driver on the cd that came with the wireless card.  Thanks

---

### Post by jacksparrow1 on 2008-08-22
Anyone help me out please?

---

