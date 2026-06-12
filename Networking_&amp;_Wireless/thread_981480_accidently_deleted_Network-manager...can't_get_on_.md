---
title: "accidently deleted Network-manager...can't get on internet"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by nias9527 on 2008-11-13
I don't know how i delete it 
now i can't get on internet..
how to reinstall network-manager???

---

### Post by ciscosurfer on 2008-11-13
> **nias9527 said:**
> I don't know how i delete it 
now i can't get on internet..
how to reinstall network-manager???Are you sure you've actually deleted it?  In any event, you can get them installed again by typing this into a terminal```
sudo apt-get update && sudo apt-get install network-manager
```If the you want the nifty applet for GNOME, install```
sudo apt-get install network-manager-gnome
```For KDE, install```
sudo apt-get install network-manager-kde
```

---

### Post by nias9527 on 2008-11-13
thz
i'am going to try it....

---

### Post by ericesque on 2008-11-13
umm... cisco, he said he doesn't have internet.

nias, you may want to pop in your Ubuntu cd and
go to Software Sources to make sure you have
the Ubuntu cd checked as a source.  Then you should
be able to use one of the first two commands Cisco
recommended.

---

### Post by ciscosurfer on 2008-11-14
Now where does it say...oh. Yes.  Yes, I suppose he did. :oops: 
Sometimes you just have to ignore the painfully obvious and submit answers like no one's watching. 8-[ 

Good catch, ericesque.

---

### Post by Zhukov on 2008-11-14
Do you have a cable connection (network cable, with a router and such), you can easily get a connection with this:

sudo dhclient eth0

were you have to replace (or not =D ) eth0 with your device name.

You can list your devices with iwconfig (less information than ifconfig...)

Best regards!

---

### Post by ericesque on 2008-11-14
I thought iwconfig only listed wireless devices... quick google search... yup.  Give us your ifconfig.

---

### Post by ericesque on 2008-11-14
> **ciscosurfer said:**
> Now where does it say...oh. Yes.  Yes, I suppose he did. :oops: 
Sometimes you just have to ignore the painfully obvious and submit answers like no one's watching. 8-[ 

Good catch, ericesque.

Hey, no biggie. I'm no expert, so I half expected you to correct me. :)

---

### Post by nias9527 on 2008-11-15
when i type
sudo apt-get update && sudo apt-get install network-manager
yea, it said that i don't  have internet connection...
probably the CD one will work for me..i'm going to give it a try
thank u you guys!!

---

### Post by ericesque on 2008-11-16
any luck?

---

### Post by Zhukov on 2008-11-16
> **ericesque said:**
> I thought iwconfig only listed wireless devices... quick google search... yup.  Give us your ifconfig.

Nop.

In fact ifconfig may not show you all your devices.

ifdown eth0 and ifoconfig wont show it.

iwconfig lists *all* the devices.

It would have faster for you to check on your console instead of google...

Best regards!

---

### Post by ciscosurfer on 2008-11-16
@nias9527, 

How's it coming along?

@Zhukov,

> It would have faster for you to check on your console instead of google...Indeed.  A quick **man iwconfig** gives me the following:

```
NAME
       iwconfig - configure a wireless network interface

DESCRIPTION
       Iwconfig  is similar to ifconfig(8), but is dedicated to the wireless interfaces. It is
       used to set the parameters of the network interface which are specific to the  wireless
       operation  (for  example  : the frequency).  Iwconfig may also be used to display those
       parameters, and the wireless statistics (extracted from /proc/net/wireless).

       All these parameters and statistics are device dependent. Each driver will provide only
       some  of them depending on hardware support, and the range of values may change. Please
       refer to the man page of each device for details.

``````
whatis iwconfig
iwconfig (8)         - configure a wireless network interface

whatis ifconfig
ifconfig (8)         - configure a network interface

[B]
Useful Alternatives
[/B]ip link show - list network interfaces
ip addr show - list addresses for interfaces
``````
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"fancyid"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 1A:2B:3C:4D:4E:5F   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=23/100  Signal level:46/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Incidentally, I don't recall the OP ever mentioning anything about wireless connectivity.
OT: The "[projects]("http://www.jpoa.info/projects/%22")" link on [your website]("http://www.jpoa.info/index.html") is broken; you need to remove the quotation mark at the end if you want people to see the "[Oops, not yet!]("http://www.jpoa.info/projects/")" page.

---

### Post by Zhukov on 2008-11-18
Lol, congratulations, loved your remarks =) (honestly!)

I still think you missed the point. He may had some interfaces down, I just wanted to list the interfaces (get the names) on the machine, so iwconfig is the way I do it, at least that way they are all there.

But I guess I'll have to start using "ip link show" as the man pages suggest :D

The point I wanted to state:

ifconfig - some devices may not appear
iwconfig - all devices appear
ip link show - right way to do it

Oh, and I fixed the link, although all my projects are still offline (gotta get some time).

So thanks ciscosurfer =)

Best regards!

---

### Post by ciscosurfer on 2008-11-19
@Zhukov,

Nah, I didn't miss it...but it doesn't really matter anyway; there's always lots of ways of doing things :-D

In fact (here I go again =D), you *should* be able to display all interfaces which are currently available (plugged in), even if they are "down" by using the -a flag/switch```
ifconfig -a
```OT: Gosto de layout e as cores que você utilizou no site. Agora, você só tem a acrescentar alguns projetos ;-) Em outras notícias, esperemos que o nosso amigo tem o seu Internet trabalhar novamente :-D I'm sure I totally butchered that, but thank you Google Translate all the same. (PS Is that your flying cat!?)

---

### Post by nias9527 on 2008-11-20
damn..
it didn't work...  
What should i do,,,,:confused:

---

### Post by ciscosurfer on 2008-11-21
What exactly didn't work?  Did you get network-manager reinstalled but you still couldn't get online?  Did you try installing network-manager off of the CD?  What procedure did you use? Did you try the other suggestions that we presented, like```
sudo dhclient eth0
```Replacing eth0 with the appropriate interface name (e.g., eth0, eth1).

---

### Post by philetus on 2008-11-21
I had the same problem because I installed Wicd and (DUH)clicked "disconnect".
I was able to figure out how to fix everything except the "you're connected" message, from the taskbar icon, when I boot up.
Is there a way to fix it?

---

### Post by nias9527 on 2008-11-21
yeah..  i just do it like u said..
i made the CD as source
sudo apt-get update && sudo apt-get install network-manager
and it didn't work.. it still try to download it from internet
is it i do it in a wrong way or ...... ???
can u show the the exact way to disable it downloading from internet...

---

### Post by philetus on 2008-11-21
Did you go to "system,administration,software sources and checkmark the CD source?

---

### Post by buster2209 on 2008-11-21
My network manager manager has crashed before so I keep the deb package kicking around and have attached it

It's for ubuntu 8.04 and 32 bit architecture

Hope it helps!

---

### Post by ciscosurfer on 2008-11-21
> **buster2209 said:**
> My network manager manager has crashed before so I keep the deb package kicking around and have attached it

It's for ubuntu 8.04 and 32 bit architecture

Hope it helps!Unless you've cleaned it, all downloaded debian packages via apt are stored in the **/var/cache/apt/archives **directory.

---

### Post by nias9527 on 2008-11-21
what should i do exactly in the software sources?
can you show me the picture ....
by the way, I'm using Ubuntu 8.10 version

---

### Post by manuelg on 2008-11-21
One way to fix it is to

1. Open up a terminal window
2. Type "gksudo nautilus" (w/o quote marks)
3. Enter your password and a root nautilus window will come up
4. Navigate to /var/cache/apt/archives
5. Look for a file named "network-manager-gnome_0.7~~svn20081020t000444-0ubuntu1_i386.deb" or something really similar.
6. Double click on it.
7. A window will come up asking what to do, press "install"
8. Reboot and network manager should be back on your system.

Hope that helps

---

### Post by ciscosurfer on 2008-11-21
> **nias9527 said:**
> what should i do exactly in the software sources?
can you show me the picture ....
by the way, I'm using Ubuntu 8.10 version[https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD)

[https://help.ubuntu.com/8.10/add-applications/C/offline.html#repository-cds](https://help.ubuntu.com/8.10/add-applications/C/offline.html#repository-cds)

---

### Post by kevdog on 2008-11-21
This thread is a classic example that if you are seriously going to use Linux or Ubuntu for that matter, you should learn at least a method to use the wireless tools package to connect wirelessly from the command line.  Once you are connected, redownload whatever package you want and you are good to go.  Heck Network Manager and WICD are just fancy front end GUI's to the wireless tools package in the first place.

---

### Post by lswb on 2008-11-21
> **kevdog said:**
>  Heck Network Manager and WICD are just fancy front end GUI's to the wireless tools package in the first place.

I don't think that is really true about Network Manager. If NM did use wireless tools perhaps it wouldn't behave so erratically. :)

---

### Post by kevdog on 2008-11-21
Try removing network tools then and see if NM still runs!

---

### Post by ciscosurfer on 2008-11-21
> **kevdog said:**
> This thread is a classic example that if you are seriously going to use Linux or Ubuntu for that matter, you should learn at least a method to use the wireless tools package to connect wirelessly from the command line.  Once you are connected, redownload whatever package you want and you are good to go.  Heck Network Manager and WICD are just fancy front end GUI's to the wireless tools package in the first place.Part of the problem is we didn't (and still don't) know what type of connection the OP has and his answers have all been vague.  This is partially our fault for not asking more pointed questions (wired, wireless, access to another computer, iso close by, etc.).  He'll be able to use the CD or his cache to get going.  And while I agree with you that users should (eventually) know how to get out of sticky situations, that's not an entirely realistic expectation for a newcomer. In any event, it's a learning process for the OP as well as anyone else who stumbles onto this thread. You were once a beginner, too. ;-)

@lswb,

It's my understanding that the front-end network config apps use both the wired and wireless extensions built into the back-end by way of various libraries and daemons.  You can either confirm or deny this by checking out the packages and their features, libraries, dependencies, et cetera, on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by lswb on 2008-11-21
> **kevdog said:**
> Try removing network tools then and see if NM still runs!

I don't know about "network tools" but it will run without "wireless tools"

---

### Post by kevdog on 2008-11-21
Yes I was a beginner too (and still am in many Ubuntu areas :) ).  If you are having a problem with wireless however, stepping through a manual configuration which verifies each step along the way, and actually imparts ***Knowledge*** is the best way to advance past the beginner stage.  There are far too many "cookbook" tutorials, and not enough threads that show how to analyze and troubleshoot.  Stepping through a manual configuration imparts knowledge and gives you a set of basic tools that can be used to troubleshoot any wireless chipset.  

That of course if my opinion.  Knowledge is learning by making mistakes, but always analyzing the results.  Critical analysis is far too often ignored on these forums!

---

### Post by kevdog on 2008-11-21
> **lswb said:**
> I don't know about "network tools" but it will run without "wireless tools"

Technically you are correct however just a clarification:

network-manager uses libiw (Wireless Tools libs) for functionality. Iwconfig is part of Wireless Tools (wireless-tools package).

So hence although one uses a binary package, and the other a library, they both call the same functions.

---

### Post by nias9527 on 2008-11-22
wow...
you guys are experts!!
thz for the links...
i'm reading it !!

---

### Post by nias9527 on 2008-11-23
Okay...
i can't find it in Synaptic Origin 
It's like my CD dosen't include network-manger..
:(

but... if it doesn't included .. how can i deleted it???

---

### Post by ramblin' wreck on 2008-11-23
I lost network manager right when I upgraded to 8.10, or at least lost it in the system tray so it never showed up. I checked etc/network/interfaces to make sure it was setting up eth0 correctly by referencing
> man 5 interfaces

I had to make one change to eth0 (the manual has a good example).

Then I used 'ifdown' and 'ifup' to bring up eth0. Afterwards, I ran 'apt-get' for network-manager and all was well.

The code to reboot eth0 I used:
>sudo ifdown eth0 

#after it finishes
>sudo ifup eth0

#if all goes well, the last line should say it is reconnecting.

If that doesn't work, sorry-

---

### Post by Murflaw on 2008-11-24
Ok so I am running Ubuntu 8.04 on a Sony Vaio FZ-140E.

Today I was browsing my internet on my computer when the web browser stopped loading properly.  Then I removed Firefox and reinstalled it and the network manager completely disappeared from the tool bar.  

iwconfig shows no wireless connections 
lshw -C network shows that my networks are disable.

I am on another computer telling you all this, so I can't paste the output.

I tried loading network-manager from the DVD it doesn't work.

There is no network-manager in the deb archives folder.

I am a total newb at UBUNTU, and have been messing around with it for a couple weeks, so if anyone could help me resolve this w/o a full system reinstall that would be great.

Until then I'll be scratching my head :popcorn: scowering forums for some fix....lol

---

