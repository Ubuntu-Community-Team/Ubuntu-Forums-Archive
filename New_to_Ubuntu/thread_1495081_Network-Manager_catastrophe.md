---
title: "Network-Manager catastrophe"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Wyxr on 2010-05-27
I have a Dell netbook running the Hardy version of Ubuntu. Recently I tried to configure it to use a PPTP VPN. Synaptic required me to remove network-manager-gnome to do so. Well, the VPN didn't work and I was without a connection.  

Running Synaptic/apt-get to reinstall network-manager-gnome just returned lack-of-connection errors.  

SO I downloaded the packages to a thumb drive via my desktop, copied them over, and tried to install, but I get dependency errors: Libatk1.0-0.

I downloaded Libatk1.0-0's package, copied it over, and tried to install THAT.  I'm told it already exists, and when I try to reinstall it popped up an error that dependencies couldn't be installed (and to sudo apt-get install -f, which of course doesn't work due to no connection).  

It seems like I'm falling down a rabbit hole here, potentially seeking out and redownloading infinite packages to satisfy dependencies (all of which seem to already exist other than the original network-manager-gnome).

I've searched the forums and found similar questions, but no useful answers. In response to some of the common questions: yes, I'm sure network-manager-gnome is gone and it's not just the applet not showing up. Yes I've tried both apt-get and Synaptic--neither of them functions due to lack of connection.  

I DID try to just reinstall a fresh copy of Ubuntu. I used USB-creator and successfully made a bootable thumbdrive, but after booting through it and getting to the Ubuntu install menu and selecting install, it inevitably just goes to a perpetual black screen.

While I WOULD like to figure out why I can't reinstall this, I'd prefer to focus on the first problem--simply reinstalling network-manager-gnome so I can get online.

I would appreciate any tips--I'm pulling my hair out at this point. :/

Thanks so much.

---

### Post by -humanaut- on 2010-05-27
From the liveCD try downloading network manager onto a USB drive then install it to your system I use to have to do this on a Dell that was running Zenwalk (note, you'll have to download it from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) synaptic will just reinstall it to the LiveCD )

---

### Post by mikewhatever on 2010-05-27
Can you post the outputs of the following commands from Applications->Accessories->Terminal:

cat /etc/lsb-release

uname -r

Also, please post the links to the files you downloaded.

---

### Post by bodhi.zazen on 2010-05-27
You should probably bring up your network card manually.

Use ifconfig

```
sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0 broadcast 192.168.0.255 up
```Now edit /etc/resolv.conf and add your nameserver

```
sudo -e /etc/resolv.conf
```Add

> nameserver 192.168.0.1

You just need to change your ipaddres and nameserver to match your desired ip address network.

Once you have a connection, apt-get away.

---

### Post by -humanaut- on 2010-05-27
If nothing else works and network manager can't be restored you can retrieve it here in a .deb (Ubuntu Specific) Binary [http://packages.ubuntu.com/karmic/network-manager](http://packages.ubuntu.com/karmic/network-manager) scroll to the bottom download to a USB key or CD-R if you want and install with dpkg (Just double click should be a graphical installation).

---

### Post by mikewhatever on 2010-05-27
It's a Dell netbook + 8.04, so I suspect the OP has an LPIA version of Ubuntu.

---

### Post by -humanaut- on 2010-05-27
Here's the link for Hardy [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

---

### Post by mikewhatever on 2010-05-27
> **-humanaut- said:**
> Here's the link for Hardy [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

i386 and amd64 architectures, no lpia. Hope it helps the OP anyway.

---

### Post by -humanaut- on 2010-05-27
> **mikewhatever said:**
> i386 and amd64 architectures, no lpia. Hope it helps the OP anyway.

If it's a netbook it should be i386 I don't think they make a x64 bit netbook yet.

---

### Post by mikewhatever on 2010-05-27
> **-humanaut- said:**
> If it's a netbook it should be i386 I don't think they make a x64 bit netbook yet.

Dell/Canonical had a home made lpia (Low Power Intel Architecture) port, which Dell used for netbooks. It's neither i386 nor x64.

---

### Post by Wyxr on 2010-05-27
Thanks for all the replies.  One thing at a time: 

When I say I downloaded the packages to a thumb drive and tried to install them I'm referring to the i386 versions of network manager (and the other packages I mentioned in the original post).  

cat /etc/lsb-release returns:
ID=Ubuntu / RELEASE=8.04 / CODENAME=hardy / DESCRIPTION="Ubuntu 8.04.2"

uname -r returns:
2.6.24-24-lpia

Links to packages I tried to install:
[http://packages.ubuntu.com/hardy/gnome/network-manager-gnome](http://packages.ubuntu.com/hardy/gnome/network-manager-gnome) (i386 version)
[http://packages.ubuntu.com/hardy/libatk1.0-0](http://packages.ubuntu.com/hardy/libatk1.0-0) (i386 version)

Libark1.0-0 again was because I tried to install the former and it said this was required.

BODHI.ZAZEN : I typed your commands, but I think I'm supposed to know some IPs that I don't. Where would I find those? My router's IP address? Its DNS addresses?

---

### Post by bodhi.zazen on 2010-05-27
> **Wyxr said:**
> Thanks for all the replies.  One thing at a time: 

When I say I downloaded the packages to a thumb drive and tried to install them I'm referring to the i386 versions of network manager (and the other packages I mentioned in the original post).  

cat /etc/lsb-release returns:
ID=Ubuntu / RELEASE=8.04 / CODENAME=hardy / DESCRIPTION="Ubuntu 8.04.2"

uname -r returns:
2.6.24-24-lpia

Links to packages I tried to install:
[http://packages.ubuntu.com/hardy/gnome/network-manager-gnome](http://packages.ubuntu.com/hardy/gnome/network-manager-gnome) (i386 version)
[http://packages.ubuntu.com/hardy/libatk1.0-0](http://packages.ubuntu.com/hardy/libatk1.0-0) (i386 version)

Libark1.0-0 again was because I tried to install the former and it said this was required.

BODHI.ZAZEN : I typed your commands, but I think I'm supposed to know some IPs that I don't. Where would I find those? My router's IP address? Its DNS addresses?

If you can tell us your router's ip address, we can tell you how to modify the command I gave you.

---

### Post by -humanaut- on 2010-05-27
> **mikewhatever said:**
> Dell/Canonical had a home made lpia (Low Power Intel Architecture) port, which Dell used for netbooks. It's neither i386 nor x64.

Really? never heard of it are they still selling those? or did they die with mini 9 or whatever

---

### Post by Wyxr on 2010-05-27
> **bodhi.zazen said:**
> If you can tell us your router's ip address, we can tell you how to modify the command I gave you.

I'm not home right now, but for the sake of simplicity let's just say it's 100.200.300.400 ?

Thanks

---

### Post by bodhi.zazen on 2010-05-27
> **Wyxr said:**
> I'm not home right now, but for the sake of simplicity let's just say it's 100.200.300.400 ?

Thanks

That does not help. It is a private router, so I would assume it is an ip address of 192.168.0.1 . It may be 192.168.1.1 or some variant.

Set your ip as 192.168.0.10 netmask will be 255.255.255.0 and broadcast will be the first 3 numbers with a 255 on then end.

ifconfig eth0 ip_address_here ( ?192.168.1.10) netmask 255.255.255.0 broadcast ? 192.168.1.255 up

---

### Post by Wyxr on 2010-05-27
> **bodhi.zazen said:**
> That does not help. It is a private router, so I would assume it is an ip address of 192.168.0.1 . It may be 192.168.1.1 or some variant.

Set your ip as 192.168.0.10 netmask will be 255.255.255.0 and broadcast will be the first 3 numbers with a 255 on then end.

ifconfig eth0 ip_address_here ( ?192.168.1.10) netmask 255.255.255.0 broadcast ? 192.168.1.255 up

(I'm home now)
Aha! I thought you meant the IP range/address the Internet sees me with. Well the way I connect to the router through my browser to configure it is via 192.168.1.1, so I assume that's it.

So I did as you say (ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255 up) and added "nameserver 192.168.1.1" to that conf file.  I'm not connected, but then I haven't been given any way to enter the network password.  How would I even be able to tell I'm connected without any wireless applet or indicator of any kind?

---

### Post by bodhi.zazen on 2010-05-27
> **Wyxr said:**
> (I'm home now)
Aha! I thought you meant the IP range/address the Internet sees me with. Well the way I connect to the router through my browser to configure it is via 192.168.1.1, so I assume that's it.

So I did as you say (ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255 up) and added "nameserver 192.168.1.1" to that conf file.  I'm not connected, but then I haven't been given any way to enter the network password.  How would I even be able to tell I'm connected without any wireless applet or indicator of any kind?

If it is a wireless card, you need to use iwconfig.

You also need to use the ipaddress you wish to assign to your computer, not your router IP.

So use an ipaddress of 192.168.1.10

```
sudo ifdown eth0
sudo ifup eth0 192.168.1.10 netmask 255.255.255.0 boradscast 192.168.1.255 up
```See man iwconfig if it is wireless, similar command, and iwconfig allows you to assign your wireless access point, AKA ESSID.

Keep your nameserver as 192.168.1.1

---

### Post by Wyxr on 2010-05-27
> **bodhi.zazen said:**
> If it is a wireless card, you need to use iwconfig.

You also need to use the ipaddress you wish to assign to your computer, not your router IP.

So use an ipaddress of 192.168.1.10

```
sudo ifdown eth0
sudo ifup eth0 192.168.1.10 netmask 255.255.255.0 boradscast 192.168.1.255 up
```See man iwconfig if it is wireless, similar command, and iwconfig allows you to assign your wireless access point, AKA ESSID.

Keep your nameserver as 192.168.1.1

For "ifdown eth0" I get "interface eth0 not configured". For "ifup eth0..." I get 7 lines of "ignoring unknown interface..."

---

### Post by bodhi.zazen on 2010-05-28
> **Wyxr said:**
> For "ifdown eth0" I get "interface eth0 not configured". For "ifup eth0..." I get 7 lines of "ignoring unknown interface..."

Is your connection wired -> use ifconfig

Or wireless -> use iwconfig

---

### Post by Wyxr on 2010-05-28
> **bodhi.zazen said:**
> Is your connection wired -> use ifconfig

Or wireless -> use iwconfig

If I replace ifconfig with iwconfig I get the error: "iwconfig: unknown command '192.168.1.1'"

That's when "iwconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255 up"

Something I notice when just typing "iwconfig" is that eth1 looks like it's set up for wireless, but eth0 says "no wireless extensions." Though if I replace eth0 with eth1 above it still returns the same error. 

:(

---

### Post by bodhi.zazen on 2010-05-28
That is not how you use iwconfig

read the man page

man iwconfig

and see this blog

[http://www.everyjoe.com/newlinuxuser/howto-use-iwconfig/](http://www.everyjoe.com/newlinuxuser/howto-use-iwconfig/)

You will need to set your essid (you did not tell me your network name).

You do not need to set your channel or mode.

Turn off security (for the time being) or set your WEP.

Then use 

sudo iwconfig eth1 up

sudo dhclient eth1

---

### Post by mikewhatever on 2010-05-28
Try downloading and installing [-->this package<--]("http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/network-manager-gnome_0.6.6-0ubuntu3usg6_lpia.deb"). It's an lpia version of network-manager-gnome.
I suspect you'll also need [network-manager]("http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5_lpia.deb"), so here is the link just in case.

---

### Post by Wyxr on 2010-05-29
Ok, I just deleted a long psychological meltdown expressing my frustration with Linux.  

Suffice to say "Man iwconfig" -- and particularly how to apply it to my problem -- is unapproachable for me and I may be near the end of my rope on this problem, having spent far too much time already. Perhaps I should focus on successfully formatting with a fresh install....and then never ever open Terminal again.  

I understand the problem is me and not the OS; for me it's just leaps and bounds less intuitive than I was prepared for (i.e. "what do you mean the program I downloaded doesn't actually come with all the files it needs in order to run??")

---

### Post by Wyxr on 2010-05-29
> **mikewhatever said:**
> Try downloading and installing [-->this package<--]("http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/network-manager-gnome_0.6.6-0ubuntu3usg6_lpia.deb"). It's an lpia version of network-manager-gnome.
I suspect you'll also need [network-manager]("http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5_lpia.deb"), so here is the link just in case.

I downloaded these, copied them to the netbook, and figured out how to --force the install to get around broken dependencies (how do I get rid of those without an Internet connection, anyway?), but still didn't seem to do anything. Restarted, tried to run nm-applet. Nothing. :/

---

### Post by mikewhatever on 2010-05-29
You shouldn't have forced anything. These packages need their dependencies to work, so that whatever was removed needs to be reinstalled.

Is there a way you could connect the netbook to the router via an ethernet cable?

---

### Post by Wyxr on 2010-05-31
> **mikewhatever said:**
> You shouldn't have forced anything. These packages need their dependencies to work, so that whatever was removed needs to be reinstalled.

Is there a way you could connect the netbook to the router via an ethernet cable?

Yeah, there is (facepalm). Ouch what an oversight.

So I got the packages installed, fixed the broken dependencies, etc. Went to Terminal, launched nm-applet, but it gave me a bunch of errors. A little homework turns up that my Broadcom 4312 chipset needs a special driver. Had a tough time with another series of errors, but eventually......I have wireless again.

Yikes.  I can't believe I didn't just plug it in before.

Well thanks everyone for your help. I clearly have a long way to go figuring out how things work.  Much appreciated.  Sorry the fix came down tos omething pretty simple.

---

