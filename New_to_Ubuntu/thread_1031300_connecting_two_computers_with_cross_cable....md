---
title: "connecting two computers with cross cable..."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by realmoonstruck on 2009-01-05
I am very inexperienced about networks. I have no idea how things work. So here I am Stuck in the attempt to connect my **HP 530 notebook running Ubuntu 8.1with my pc running UbuntuStudio 8.1.**
I have a **LAN port on both the computers**. I connect to the Internet wirelessly with the help of my **Nokia SL2_141** modem. I actually had Ubuntu 8.04 on my notebook when I configured the wireless connection. Then I updated to 8.1. I didn't understand the interface of the 8.1's updated version of the network tools :confused:. So if in any way it blows up I can't set it up again.
Coming to the present problem- **I have connected the LAN ports of my pc and my notebook with a cross cable. But I'm pretty mych stuck there only.** I have no idea how to proceed.
And please give specific step by step information if possible. Cause as I said before I'm a complete novice. And please keep in mind that I can't set up the wireless connection again anything happens to it (unless you guys help me of course...)

---

### Post by cmnorton on 2009-01-05
I'd try to straighten out why you cannot set up your network. 

The Ubuntu network config would have to list its gateway as the PC's address at the other end of the cross cable. That address would ideally be static. 

To do all that, you'll have to get into your network configuration, and from there, you could probably get to the reason you cannot set up your network.

---

### Post by realmoonstruck on 2009-01-05
But I have no idea how to do that.

Please tell me if you'd require some additional information.

---

### Post by cmnorton on 2009-01-05
Here are a couple of links:

[https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html)
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

These will describe things better than I can. I would start solving your problems off with configuring your network, and then you might not need the cross cable.

---

### Post by realmoonstruck on 2009-01-05
do i need to go through them before i can get started in configuring?
i mean is it necessary to know the details in this present scenario?

However i had configured my notebook previously in 8.04
I can't understand which options to use in this new interface in 8.1.
I actually don't know what to do with all the new option fields like:
[B]SSID
Mode
BSSID
MAC address
MTU[/B]
etc...
previously I didn't have to set all these in 8.04

I also don't know which security option to choose.
I use a 128 bit ascii key for security.
but if i select the 128 bit pass-phrase,
what to do with the **WEP index** & A**uthentication**?

---

### Post by realmoonstruck on 2009-01-05
and [SIZE=3]**please**[/SIZE] bear with me.

---

### Post by cmnorton on 2009-01-05
> **realmoonstruck said:**
> do i need to go through them before i can get started in configuring?
i mean is it necessary to know the details in this present scenario?

However i had configured my notebook previously in 8.04
I can't understand which options to use in this new interface in 8.1.
I actually don't know what to do with all the new option fields like:
[B]SSID
Mode
BSSID
MAC address
MTU[/B]
etc...
previously I didn't have to set all these in 8.04

I also don't know which security option to choose.
I use a 128 bit ascii key for security.
but if i select the 128 bit pass-phrase,
what to do with the **WEP index** & A**uthentication**?

All you need is how to setup Network Manager. As to WEP, I use the hex key option, because my wireless router has the capacity to let me enter in an ascii key and then translates it to hex. If you do use the ascii passphrase, make sure it's what got generated to hex in the wireless router.

---

### Post by realmoonstruck on 2009-01-05
the router is properly configured ant the wireless connection is also up and running properly.
actually i'm using it right now. Though somehow no wireless connections are listed under network connections.

do i need to add a new connection then?

---

### Post by cmnorton on 2009-01-05
I'm confused. To which computer are you referring? Network Connections sounds like Windows. Network Manager is Ubuntu.

---

### Post by realmoonstruck on 2009-01-05
Don't know what it is known as.
But the title shows "Network Connections"

I remember that 8.04 used to have "Network Manager"
which could be accessed as Administration->Network
but 8.1 doesn't have any such option, only Network Tools.

I access the Network Connections from the Panel.

---

### Post by bradthewanderer on 2009-01-05
If you have a wireless router and you are connecting through it for your notebook and you have a hard wired desktop, why even use a cross cable between the two? I am just saying you can hard wire the desktop and use wireless to connect with the laptop, so why do you need to use a cross cable in that configuration.

---

### Post by realmoonstruck on 2009-01-05
my modem is single user configured so i can't use the net on both computers at once.
maybe it's possible but I don't know to do it.

I basically need to connect the two computers to facilitate direct data exchange.
presently i have to manually use a pendrive to transfer data from one comp to the other.

---

### Post by bradthewanderer on 2009-01-05
On the back of the router there is a connection for the modem, this is where you put your modem in and then hook in your Ethernet cord from your desktop to one of the open ports in the back (i.e. port 1,2,3,4) and then you can get on the net via hard wired and wireless, that is the point of the router. As for transferring data between computers you should be able to via the router as well. I am not as competent in this realm so someone else might be able to help you on her with that.

---

### Post by uBeer on 2009-01-05
I don't know how to work with cross-cables, but I do know how you can share the internet connection of your laptop with a normal LAN cable.

My setup right now is a desktop connected to the internet (via pppoe) and my laptop wired with a normal LAN cable into the desktop pc.

This way I can share folders and files and transfer them between the computers. It's kind of hard to setup at first, but if you want this solution I can probably help you out.

This solution has a drawback because every time one of the computers disconnects and then reconnects the internet sharing has to be re-enabled.

I'll post a follow-up post explaining my solution.

---

### Post by lkraemer on 2009-01-05
I have just done this so I could transfer large (10 Gig) Virtual
Disk Images (VDI's) from my Desktop to my Laptop.  Here is what I did.

I made a 8" crossover cable, purchased a Coupler, and attached it to
the 8" cable.  Now I can use any length Ethernet patch cable to connect
my Computers.

REF:
keystonepos.tripod.com/sitebuildercontent/sitebuilderfiles/ethernetcablecolorcodingstandard.pdf
also.........
[http://www.perfectdrivers.com/images/regular.JPG](http://www.perfectdrivers.com/images/regular.JPG)

[http://www.perfectdrivers.com/images/crossover.JPG](http://www.perfectdrivers.com/images/crossover.JPG)

On my Desktop I installed vsftpd via Wired Ethernet connection.
One computer must have an FTP server running.  Doesn't matter which.
The other one will run Filezilla.

On my Laptop I installed Filezilla via Wireless connection.  (I used 
Filezilla to xfer my files.  Either machine to the other, but the machine
with Filezilla is used to select the files for the xfers.)

I needed the login and password for both computers.....I was good there.

I unhooked my Ethernet cable from the Desktop, and turned off the Wifi 
connection of the Laptop.  Hooked up the Crossover cable and a patch cable.

SYSTEM -> ADMINISTRATION -> NETWORK      8.04LTS
I assigned my Desktop a static IP address of 192.168.1.100
I assigned my Laptop a static IP address of 192.168.1.110

vsftpd (FTP server) was running on my Desktop.  I started Filezilla on
my laptop, told Filezilla to connect to 192.168.1.100 and inserted the Desktop's login and password.

Then it was just a matter of tagging the files and folders to move, from
Laptop to Desktop and vice versa.

I have a few notes on my other computer about vsftp, and will adjust this message accordingly,
next time I am on the other machine.  It was easy and nothing gets messed up.  Just set both Computers
back to roaming and you're back in business.  A folder FTP is created on HOME along with Larry.

[http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml](http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml)
[http://intrik.wordpress.com/2007/10/25/how-to-download-and-install-vsftpd/](http://intrik.wordpress.com/2007/10/25/how-to-download-and-install-vsftpd/)
[http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd](http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd)

vsftpd has some configuration that has to be setup, and that follows:

In a Linux Terminal Window:  (Change the ftp folder permissions)
  cd ~
  cd ..
  chmod 777 ftp

  cd /
  sudo gedit /etc/vsftpd.conf
     # Allow anonymous FTP? (Beware - allowed by default if you comment this out).
     anonymous_enable=NO
     #
     # Uncomment this to allow local users to log in.
     local_enable=YES
     #
     # Uncomment this to enable any form of FTP write command.
     write_enable=YES 

SAVE the file........

Start the FTP Server on one machine:
     sudo /etc/init.d/vsftpd start

Other commands that can be used to stop, restart, start the vsftpd

      sudo /etc/init.d/vsftpd restart
      sudo /etc/init.d/vsftpd stop
      sudo /etc/init.d/vsftpd start

(You should LIMIT access to one specific folder just in case, so others
won't have full access, if you somehow mess up the setup.)

Good Luck.

lkraemer

---

### Post by realmoonstruck on 2009-01-06
**@ uBeer**
Well the problem is that the wireless isn't detected if the pc is hardwired at that time.
To make the wireless work I have to remove the jack physically from the modem.
So both won't be on the net at the same time. Can this problem be overcome?

And will these transfers be over the net or LAN? Cause otherwise it'll then eat into my download capacity of my broadband connection.

---

### Post by realmoonstruck on 2009-01-06
> **lkraemer said:**
> 
SYSTEM -> ADMINISTRATION -> NETWORK      8.04LTS
I assigned my Desktop a static IP address of 192.168.1.100
I assigned my Laptop a static IP address of 192.168.1.110


could you please tell me which options to set in 8.1 :confused:
*I can't set up my wireless again if i mess it up!!!!!!*
(I had set it when I was 8.04 and its still working in 8.1)
and I also can't find the roaming mode under 8.1

Check out the screen-shot I've posted earlier.
its **network connections** not **network manager**
which can be accessed from the top panel.
and I have not found any documentation regarding that!

*am I supposed to have a network manager in 8.1 at all?*
if yes how do I get to it?

---

### Post by lkraemer on 2009-01-06
Left Click on.....

SYSTEM -> ADMINISTRATION -> NETWORK

This will bring up a window titled Network settings, and in it there will be:
WIRED CONNECTION
POINT TO POINT CONNECTION
WIFI CONNECTION

You will be changing wired.
Left Click on UNLOCK
and type your password.
Then Left Click on WIRED CONNECTION to highlight it, then click on PROPERTIES.
You will see it is set for ROAMING with the check mark
ticked in the box.  If you uncheck the box, you can set the IP
address that you want.  (Must do this on both computers so you get
the proper IP address for the xfers.)

You will be changing both machines WIRED CONNECTION so no other settings
should get changed.  Jut don't mess with any Wifi settings.

When you are done with Filezilla and vsftpd just go back, and check the
ENABLE ROAMING BOX in the WIRED CONNECTION on both computers.  It is that easy.
Of course you will unplug the crossover cable and then replug in
your LAN wired cable.........as it is now.

Just be sure that is all you change.  There shouldn't be any problems.

And I am also running 8.04.1 LTS.

lkraemer

---

### Post by realmoonstruck on 2009-01-07
for the love of god I dont have the "**Network**" under Admistration...

if i'm supposed to have it then tell me ho to get it first plzzzzzzzzzzz

It was there in 8.04, bot it's not there in 8.1

maybe that is some different error. but can it still be set up properly?

---

### Post by lkraemer on 2009-01-07
Well, since I haven't run Version 8.10 yet, I am at a loss.
I'll have to download 8.10, and boot the LiveCD to have a look.
There has to be a window that opens under some pulldown menu to allow 
you to access the Network settings.

I'll try and look tonight.

lkraemer

---

### Post by cmnorton on 2009-01-07
> **realmoonstruck said:**
> for the love of god I dont have the "**Network**" under Admistration...

if i'm supposed to have it then tell me ho to get it first plzzzzzzzzzzz

It was there in 8.04, bot it's not there in 8.1

maybe that is some different error. but can it still be set up properly?

I use Kubuntu, so things are a little different. Under Administration is there Preferences and System? Network settings would be under System, as I remember it.

---

### Post by realmoonstruck on 2009-01-07
there is no **Network Settings** option
i have a **Network Tools** option though.

and the **Network Connections** (in screenshot)
comes up from the Network icon on the top panel...

do none of you use Ubuntu 8.1 ????????

---

### Post by mapes12 on 2009-01-07
> I have connected the LAN ports of my pc and my notebook with a cross cable. But I'm pretty mych stuck there only. I have no idea how to proceed.
I guess what you want is file sharing between linux boxes - there is NO WINDOWS involved. This works for me:

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig
```

this should give you an output just like this one

> eth0 Link encap:Ethernet Hardware Adresse 00:13:77:04:cd:26
UP BROADCAST MULTICAST MTU:1500 Metrik:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Basisadresse:0x6000 Speicher:d2800000-d2820000

lo Link encap:Lokale Schleife
inet Adresse:127.0.0.1 Maske:255.0.0.0
inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
UP LOOPBACK RUNNING MTU:16436 Metrik:1
RX packets:992 errors:0 dropped:0 overruns:0 frame:0
TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:0
RX bytes:30392 (29.6 KB) TX bytes:30392 (29.6 KB)

wlan0 Link encap:Ethernet Hardware Adresse 00:13:02:0f:83:56
**inet Adresse:192.168.18.143** Bcast:192.168.18.255 Maske:255.255.255.0
inet6-Adresse: fe80::213:2ff:fe0f:8356/64 Gültigkeitsbereich:Verbindung
UP BROADCAST RUNNING MULTICAST MTU:1500 Metrik:1
RX packets:237037 errors:0 dropped:0 overruns:0 frame:0
TX packets:200628 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:208782489 (199.1 MB) TX bytes:22525126 (21.4 MB)
your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine so, in my case the address would be 192.168.18.143.

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine and away you go!

With regard to your wifi issue then why not go back to 8.04 if it worked OK with that version _and_ you get longer support.

---

### Post by achase79 on 2009-01-07
it is under System -> Administration -> Network

---

### Post by lkraemer on 2009-01-07
Look under 
SYSTEM -> PREFERENCES -> NETWORK SETTINGS.

You will see five tabs in that Network Configuration Window.
You will be setting a STATIC IP Address, but exactly how to do
that in version 8.10 isn't an area I've done.  Sorry.
You should be able to figure it out easily.

Maybe this will help.
[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)
[http://ubuntuforums.org/showthread.php?t=1034235](http://ubuntuforums.org/showthread.php?t=1034235)

lkraemer

---

### Post by realmoonstruck on 2009-01-08
> **mapes12 said:**
> I guess what you want is file sharing between linux boxes - there is NO WINDOWS involved. This works for me:

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig
```

this should give you an output just like this one


3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine and away you go!

With regard to your wifi issue then why not go back to 8.04 if it worked OK with that version _and_ you get longer support.

**Thanks u saved my LIFE** :P

by the is it possible to go back to 8.04 without reinstalling?

---

