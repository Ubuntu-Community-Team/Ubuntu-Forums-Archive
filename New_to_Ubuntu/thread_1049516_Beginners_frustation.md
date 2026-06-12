---
title: "Beginners frustation"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by vjp38 on 2009-01-24
First let me start by saying I am not even a novice in the Linux environment.  I have been a brain dead MS Windows for years. I know absolutely nothing about Linux or Ubuntu.  For me its like living in another country without knowing the language.

I downloaded Ubunto 8.10 without any problems.  Played around working off the CD.  My current OS is Windows XP (SP3).  Quite honestly its running fine, but I was looking for a challenge and possibly a more secure environment.

Everything during installation went fine. I like the look and feel of the desktop.  I think I can figure out most of the applications I need to use in the short term. My problem or challenge is connecting to my windows network.  Again, remember I am a novice at best.  I am not a network guru.  My current set up is via Verizon FIOS.  I have one other computer that connects via a wireless router.  My desktop is the base and the one ubuntu (and MS WinXP) is installed on.  My security suite is McAfee total protection, virus, firewall, etc. I have not turned off anything.

I think I have all the settings I need from windows.  I ran ifconfig in windows and it gave me my network settings. I just can figure out where they go or if they are the ones needed.  

When Ubuntu boots up and the desktop appears the network icon initiates and looks for a network to connect to.  Each time it fails.  I check the connection box, but I am not able to edit the MAC address.  Sometimes its there sometimes its blank.  Regardless, I am not able to connect no matter what edits I try.

I really want to give this a go but without being able to connect to the network and internet really restricts my evaluation.  I know the internet is the internet, but bouncing back and forth between OS is counterproductive.

So can anyone walk me through this and get me connected? Remember I am less than a novice so you have to type real slow.

Appreciate any assistance.

Cheers,
Jim
Northern VA

---

### Post by MikeBrown on 2009-01-24
Jim, it's been my experience that you cannot change certain settings in the live cd, since it doesn't install anything on your computer (but allows you to use USB or removable media to move files). Because of this, you aren't able to configure your wireless settings. 
If you wanted to try out Ubuntu linux but don't want to take the chance of erasing or over-writing your previous install of windows, try installing Ubuntu within windows. 
To do this, you need to boot up your computer in windows like normal, then insert your live cd. It will give you the option to install within Windows (which gives you the ability to boot into ubuntu from start, but it will install like a program in windows).

This is what I did to 'get my toes wet' as a linux n00b. 

Hope This Helps!

---

### Post by Michael.Godawski on 2009-01-24
heya,

welcome and keep up the spirit.

We need some info about your network situation, especially what Ubuntu thinks about your network.

Boot into Ubuntu, open the [Terminal]("http://ubunturesources.ub.ohost.de/terminal.html") and run these commands one after the other:

```
iwconfig
ifconfig
sudo iwlist scan
sudo lshw -C network
```Linux is case-sensitive so the capital C is a capital C.

After the [sudo commands]("http://ubunturesources.ub.ohost.de/rootsudo.html") you will have to type in your login password. It won't be displayed; just type it in blindly and hit enter.

Post the output here on the forums. Might be some text, so you can save it to a usb stick if you have one in a txt file.

---

### Post by iaskedalice09 on 2009-01-24
That's interesting since I was able to connect from my first Live CD. To the OP: Did you click the two monitors icon on the top bar? If you do that, a drop down menu should show where you can create a new wireless network.

---

### Post by Bölvaður on 2009-01-24
*deleted*

---

### Post by handydan918 on 2009-01-24
First, have you in fact installed Ubu to the hard drive?

If so, how? Conventional install or Wubi?

Are you trying to connect wirelessly?

Please open a terminal and post the output of ```
lspci | grep -i net
```

This should be easy once we have the correct info. Usually. Linux is very good at "just working" where it comes to networking.

---

### Post by boof1988 on 2009-01-24
EDIT: I removed my post after I reread the thread.

---

### Post by theozzlives on 2009-01-24
If it's not a network card problem, then you need samba to connect to windows. Go to applications > accessories > terminal and type:
```
sudo apt-get install samba
```
then type:
```
gksudo gedit /etc/samba/smb.conf
```
you want to find the line under global that says "workgroup=WORKGROUP". Change the one in caps to the name of your Windows workgroup, save and exit. You then want to type:
```
sudo /etc/init.d/samba restart
```
If their are no hardware issues you should be able to connect to your Windows shares.

---

### Post by vjp38 on 2009-01-24
My mistake>  I did install it on my hard drive vice using a live CD.

---

### Post by kansasnoob on 2009-01-24
> **vjp38 said:**
> My mistake>  I did install it on my hard drive vice using a live CD.

So you do have a dual boot and you can still boot either Windows or Ubuntu?

---

### Post by vjp38 on 2009-01-24
> **kansasnoob said:**
> So you do have a dual boot and you can still boot either Windows or Ubuntu?
That is correct.  No impact on windows......yet.

---

### Post by SunnyRabbiera on 2009-01-24
This issue might be your device, can you give us info on your wireless device?
Its a good thing windows still works as you can use it as a gateway to fix ubuntus connection

---

### Post by vjp38 on 2009-01-25
That is correct.  I have installed it on my hard drive and I am able to dual boot without any problems.

I can open up terminal, but when I type the commands that some have suggested I try, nothing happens.  My command line has my login name @ ubuntu.  Remember when I said I was a novice? How do I get it to the root?

---

### Post by vjp38 on 2009-01-25
> **Michael.Godawski said:**
> heya,

welcome and keep up the spirit.

We need some info about your network situation, especially what Ubuntu thinks about your network.

Boot into Ubuntu, open the [Terminal]("http://ubunturesources.ub.ohost.de/terminal.html") and run these commands one after the other:

```
iwconfig
ifconfig
sudo iwlist scan
sudo lshw -C network
```Linux is case-sensitive so the capital C is a capital C.

After the [sudo commands]("http://ubunturesources.ub.ohost.de/rootsudo.html") you will have to type in your login password. It won't be displayed; just type it in blindly and hit enter.

Post the output here on the forums. Might be some text, so you can save it to a usb stick if you have one in a txt file.
OK, here is what I got.  Hope it makes sence.

jimp@ubuntu:~$ -C
bash: -C: command not found
jimp@ubuntu:~$ c
bash: c: command not found
jimp@ubuntu:~$ cd\
> iwconfig
bash: cdiwconfig: command not found
jimp@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

jimp@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:33:e3:f6  
          inet6 addr: fe80::20e:a6ff:fe33:e3f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

jimp@ubuntu:~$ sudo iwlist scan
[sudo] password for jimp: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

jimp@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:02:0f.0
       logical name: eth0
       version: 10
       serial: 00:0e:a6:33:e3:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:af:a5:24:5d:5f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jimp@ubuntu:~$

---

### Post by vjp38 on 2009-01-25
> **handydan918 said:**
> First, have you in fact installed Ubu to the hard drive?

If so, how? Conventional install or Wubi?

Are you trying to connect wirelessly?

Please open a terminal and post the output of ```
lspci | grep -i net
```

This should be easy once we have the correct info. Usually. Linux is very good at "just working" where it comes to networking.
Ok here is what I got:  
jimp@ubuntu:~$ lspci | grep -i net
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
jimp@ubuntu:~$

---

### Post by vjp38 on 2009-01-25
> **theozzlives said:**
> If it's not a network card problem, then you need samba to connect to windows. Go to applications > accessories > terminal and type:
```
sudo apt-get install samba
```
then type:
```
gksudo gedit /etc/samba/smb.conf
```
you want to find the line under global that says "workgroup=WORKGROUP". Change the one in caps to the name of your Windows workgroup, save and exit. You then want to type:
```
sudo /etc/init.d/samba restart
```
If their are no hardware issues you should be able to connect to your Windows shares.
Not sure this is what you were looking for:

jimp@ubuntu:~$ sudo apt-get install samba
[sudo] password for jimp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

---

### Post by llamakc on 2009-01-25
> **vjp38 said:**
> Not sure this is what you were looking for:

jimp@ubuntu:~$ sudo apt-get install samba
[sudo] password for jimp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate

You may install the smbclient package.

```

sudo aptitude install smbclient

```

In GNOME, you may use the GUI network-manager applet. Right-click on the network icon on your panel and choose "edit connections".

Mine has one entry, and says "Auto eth0". What does yours say? 

You are trying to connect to the router, correct? Is the cat5 cable in place & correctly inserted? Sometimes problems can be traced to simpler issues.

---

### Post by kestrel1 on 2009-01-25
You only need samba installed if you want to transfer files between Ubuntu & a separate windows machine.
I would imagine you are more interested in getting the internet working first.

---

### Post by vjp38 on 2009-01-25
Yes, mine says Auto eth0

---

### Post by llamakc on 2009-01-25
> **vjp38 said:**
> Yes, mine says Auto eth0

And do you have a CAT5 cable going from your ethernet card to your router?

---

### Post by russu52 on 2009-01-25
right-click on network icon
select edit connections
in the new window, click on DSL
click ADD
type in username and password 
check "connect automatically"
give your administration password and add permanently to keyring
close
click on network icon, you should have a new option other than eth0

select
bingo

hope this works for you

---

### Post by vjp38 on 2009-01-25
yes

---

### Post by vjp38 on 2009-01-25
OK remember when I said I was a novice?  Well I reboot my router and restarted ubuntu and everything works fine.  Thanks for everyone's help and sugestions

---

### Post by vjp38 on 2009-01-26
Well that only worked once.  Back to the same problem.

---

### Post by albinootje on 2009-01-26
> **vjp38 said:**
> Well that only worked once.  Back to the same problem.

How long did that work ?
Are you in the same situation after a reboot perhaps ?

---

### Post by vjp38 on 2009-01-27
I had connectivity for awhile.  Surfed around a bit, sent a email or two.  After rebooting it all went away.  I am sure it something very simple to folks use to this environment.

---

### Post by klein de usa on 2009-01-27
hi 
#1 if i'm understanding your problem correctly, if you left click on the network icon do you see your network name?

#2 you should not have to change the mac address the ubuntu os should of done that for you.

#3 if you left click on the network icon, and your network is recognised but will not connect, right click on the net work icon and click on edit connection, that should open network connections, the second tab from the left is wireless click on that, now if ubuntu is seeing your wireless network it should be listed by name there, if it is highlight your connection and click on edit, at the very top it should have the connection name mine is Auto libby yours should be what ever your network is with auto in front of it, 

ok click on wireless security, there you will have to know what your wireless security is set that and then type in your wireless network password, next go to the ipv4 settings and make sure the method is set to automatic (dhcp) this is assuming the router is running as a dhcp server. 

ubuntu 8.10 will not retain static ip addresses you set with network manager after a reboot there is a workaround for this though....... any further questions i will try to help the best i can

---

