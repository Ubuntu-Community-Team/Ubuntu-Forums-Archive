---
title: "ubuntu feisty on the eeepc 2g surf"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by heiowge on 2008-07-12
The only install I've managed to get onto my (4gb) SDHC card of my eeepc 2g surf is Ubuntu fiesty.

The only real issue is that there is no internet.  Any ideas how to reactivate the ethernet or wifi without an internet connection?

What about with one on another machine?

---

### Post by heiowge on 2008-07-12
bump

---

### Post by charliebrownau on 2008-07-12
Almost the same issue I have .

If you cant download Ubuntu EEE v8.04 
then I suggest ordering the free cd off
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
(hopefully they offer shipping Ubuntu EEE)

Maybe check out a Public LAN Party in your
local area and see if anyones got the 
Ubuntu EEE v8.04 ISO you can grab.

I have posted an issue in the Laptop Tech section
that the Wireless card works with Ubuntu EEE v8.04
but the LAN Ethernet card isnt working and I have
low bandwidth aswell. I am after a HTTP link for the
driver (NOT using apt-get) so I can install it 
off a USB stick for the laptop

A ultra quick Distro that ALMOST worked on the EEE
is TinyME ( [http://tinyme.mypclinuxos.com/wiki/doku.php](http://tinyme.mypclinuxos.com/wiki/doku.php) )
Installs on the EEE via a PATA USB Caddy with PATA DVD Burner
in about 6 mins and the ISO is like 200 meg 
It didnt work , bitched about the file system wasnt loading.

---

### Post by heiowge on 2008-07-13
Cheers, but I already have about a dozen original / mag supplied / downloaded ISOs of 8.04

8.04 crashes after the login screen on my eeepc.

The only distro to successfully go on was 7.04

I'm happy with this, if I can get Wifi or ethernet working.  Hence my post...

---

### Post by heiowge on 2008-07-14
bump

---

### Post by heiowge on 2008-07-14
double bump.  issue still not resolved.

Please help

---

### Post by snowpine on 2008-07-14
Ubuntu EEE is a special version just for the EEE PC as CharlieBrown mentioned. There's also a distro called eeexubuntu that has wireless working out of the box. Check out the awesome user group at forums.eeeuser.com.

---

### Post by heiowge on 2008-07-14
Cool, but I've had wireless and wired working before under feisty on the eeepc before, and I can't find the method.

I've uploaded more than a dozen different distros, including Mandriva 2008 spring one that is supposed to support the eeepc out of the box.  I like plain old ubuntu, and if hardy and gutsy won't go on, I'll take feisty.

My only problem is fixing the ethernet or wifi so I can get updates.

It took in excess of 16 hours to get even feisty on.

The problem is that I'm dual booting with XP.  The only way it wanted to go on is to change the boot disc between ssd and SDHC card in the BIOS.  But that's ok.  I can deal with that.  I'm not really interrested in reinstalling another OS, whether or not it is tailored to the eeepc.  I just want to fix the ethernet or wifi.

I have 3 other computers I can get the files with if necessary - 1 ubuntu, 1 XP and ubuntu and 1 Vista (yeuch! - the wife's!)  I just need to know how and where to get them.

So again...  please help.

---

### Post by heiowge on 2008-07-15
Sorry if I came across a bit ratty there.  Not feeling well atm.

---

### Post by SarahKH on 2008-07-15
I've a 4G 701 and wired Ethernet works out of the box in 8.04... I think it should work in 7.10.  Obviously some hardware differences between your 2G Surf and mine but even so...

Boot yon sucker up and open a terminal.  Go super user (sudo su - or if like me you set a root password just su) and lets see.

lspci on my 4G gives me:

```
<SNIP>
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
```

If you don't see two ethernet controllers listed you could have some really odd hardware or BIOS issue, it should show up even without a cable connected.  Next, plug a cable in.  
Then do dmesg 

You should see loads of text scroll up the screen, what we want will be the last few lines where the netdetect routine figures out a cable is plugged in.  Assuming you see that, do an ifconfig eth0

```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7b:1e:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 
```

This is my deactivated eth0 (I'm on wireless ATM), if something has appeared when you issued the command then good.  If you see it mention IP Address then even better.  Smack the network-manager around and see if it'll play ball; it should automagically start hunting around for a DHCP server to get an address from.

Issue the command: ping [www.google.com](www.google.com)  and see if you get a response (assuming you've got an IP).  It it fails to resolve, you get zero responses ever I'd be inclined to sniff at your network.

Wireless is fairly easy.  Easier than figuring out WTF is wrong with your wired ethernet :)

```
sudo apt-get update
sudo apt-get install -y -f build-essential module-assistant
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
make clean
make
sudo make install
sudo reboot
```

One deft reboot later and Network Manager should be able to control the Atheros card (it did on my 4G until I replaced it with wcid).

BTW doing an 8.04 install never crashed for me doing login, but I do have enough internal storage to have the whole distro on the SSD.  You might want to poke around the Ubuntu community resources and the eeeuser.com forums as I'm sure I remember something you had to do with the key manager if you were going totally from a SD card.

---

### Post by heiowge on 2008-07-15
I've got both ethernet and WIFI on XP on the ssd.  It's the feisty install that's missing bits.

I heard that the issue of crashing on the brown screen is common with 8.04, I looked it up when I started doing it.

I've had gutsy working on it before, but it wouldn't play ball this time.  I think I follow you, but am a little too much of a newbie to know where to get that info from.

Could you please resend the post, putting in exactly what I have to type in before I can do the apt-get.

lspci? eth0? etc.  you get what I mean.

Ta!

---

### Post by heiowge on 2008-07-16
bump

---

### Post by heiowge on 2008-07-16
double bump

---

### Post by snowpine on 2008-07-16
> **heiowge said:**
> double bump

You really need to check out eeeuser.com, they have an awesome forum for this kind of question (as much as I love ubuntuforums) since you are not getting the answers you want here.

Their wiki will acquaint you with many of the options: [http://wiki.eeeuser.com/#installing_operating_systems](http://wiki.eeeuser.com/#installing_operating_systems)

And then you can ask questions on the forum:
[http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)

---

### Post by heiowge on 2008-07-16
Thanks.  I'll give it a whirl.

---

### Post by heiowge on 2008-07-17
No-one's bothering to answer!!!:(

Back here.

---

### Post by heiowge on 2008-07-18
bump

---

### Post by heiowge on 2008-07-19
double bump please?

---

### Post by heiowge on 2008-07-19
Ok, don't sweat it.  Installed hardy and worked around those problems instead.

---

