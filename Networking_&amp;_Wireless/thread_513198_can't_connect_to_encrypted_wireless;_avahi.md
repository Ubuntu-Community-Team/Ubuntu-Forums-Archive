---
title: "can't connect to encrypted wireless; avahi"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by shrndegruv on 2007-07-30
so i have a fresh FF install.  

I *can* connect to unencrypted network.  I cannot connect to encrypted.  when connected to an open network, ifconfig -a shows eth0 and eth1 (eth0 my ethernet port, eth1 the wireless).  When I try to connect to closed wep network, I get a third interface eth1:avah, which has an ip; however i cannot ping even the gateway (my wireless router) -- I get a destination unreachable for each ping.

Have people seen this?  

My kernel driver is ipw2200, which seems to load fine (like I said, can connect to my network when I leave it open).  

thanx

---

### Post by walkerk on 2007-07-30
169.254.xxx.xxx ...?

avahi automatically assigns an address within the above network when your computer can't pull an ip address from dhcp. check to ensure your router has dhcp enabled.

---

### Post by shrndegruv on 2007-07-30
Im pretty sure dhcp is working, after all, when I connect to the open network (my router, not some other one in range), I am getting my ip address via dhcp.  I didn't mention that in my original post....

---

### Post by shrndegruv on 2007-07-30
ok now that I am at home i cna work on this again.  The avahi interface  does have a 169.254xxxxx ip address.  My router is configured to do dhcp...

---

### Post by walkerk on 2007-07-30
exactly.. dhcp isn't working correctly.. 169.254.xxx.xxx is a default ip address given when a dhcp server is down. (so that people within an internal network can still operate w/out outside access... in an emergency)

your dhcp isn't working. you'd most likely pull a 192.168.xxx.xxx address.. perhaps a 172.16.0.0 &#8211; 172.31.255.255.. doubtful though

---

### Post by walkerk on 2007-07-30
is your box set up to pull from dhcp?

---

### Post by shrndegruv on 2007-07-30
how do i tell it to be?
 

it is in the network manager

---

### Post by shrndegruv on 2007-07-30
when i restart networking with /etc/init.d/networking restart it is having trouble getting an ip with dhcp.  why would that happen.  Im pretty sure my router is configured for dhcp.

---

### Post by shrndegruv on 2007-07-30
i am looking at my router setting right now.  dhcp is a go.  Im looking at my interfaces file. dhcp is a go.  WTF!?

---

### Post by kevdog on 2007-07-30
Just try typing the following at the command line, since it should give us some good output particularly if dhcp isnt working.  Assuming eth1 is your wireless interface:

Please turn off WEP/WPA/MAC Filtering on the Router not to confuse the situation

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo ifconfig eth1 mode managed
sudo iwconfig eth1 essid *YOUR_ROUTER's_ESSID*
sudo dhclient eth1

---

### Post by shrndegruv on 2007-07-31
ok i tried those commands.  I commented out everything in network/interfaces except lo.

I think you meant 
sudo iwconfig eth1 mode managed (not ifconfig)

after all the iwconfig commands, just running iwconfig shows eth1 unassociated with the correct essid.

dhclient fails to get an ip (no DHCPOFFERS received).

for my netgear router, under lan ip setup, i have the box checked for "use router as dhcp server"

for my wireless settings, i have authentication type set to open and enc strength set to disable.

---

### Post by walkerk on 2007-07-31
are you using network-manager? sorry, we are on different continents... had to sleep last night :P

---

### Post by shrndegruv on 2007-07-31
i tried with network manager all last night. It could see my network, just wouldnt connect.  Wouldnt connect to any other open networks withing range either.  sometimes would connect briefly but then signal strength would drop to zero.

Im on irc right now if you are on too.  ubuntu channel, hvgotcodes name.

[edit] -- i disabled the network manager because it was constatnly bringing my interfaces up.

---

### Post by walkerk on 2007-07-31
call me ignorant.. what irc server? :O i've never been on the ubuntuforums irc server..

---

### Post by shrndegruv on 2007-07-31
irc.freenode.net

channel ubuntu

---

### Post by shrndegruv on 2007-07-31
ok an update -- determined that for some reason the driver balked when trying to obtain an ip address via dhcp from the router.  No idea why.

---

### Post by shrndegruv on 2007-08-01
doh.  Resetting my router to factory settings fixed the problem

---

### Post by walkerk on 2007-08-01
> **shrndegruv said:**
> doh.  Resetting my router to factory settings fixed the problem

Glad to hear buddy. I was thinking last night and we went up nearly every alley.. couldn't think of anything else. It was the router all along. LOL :)

---

### Post by shrndegruv on 2007-08-01
yeah man thanx for all the help.

That was a tough one; wired connections dhcp'd no problem.  Who would have thunk it.  What was the network manager you suggested?  Wicd?  also what was I sposed to remove before installing wicd?  And the repo?

---

### Post by walkerk on 2007-08-01
> **shrndegruv said:**
> yeah man thanx for all the help.

That was a tough one; wired connections dhcp'd no problem.  Who would have thunk it.  What was the network manager you suggested?  Wicd?  also what was I sposed to remove before installing wicd?  And the repo?

[[COLOR="DarkOrange"]WICD[/COLOR]]("http://wicd.sourceforge.net")

First check to see if you have the network-manager and network-manager-gnome packages archived just in case you want to switch back to Network Manager:
```
cd /var/cache/apt/archives

ls | grep network-manager
```

If you don't see the packages you can download them to this folder using the -d option:
```
sudo apt-get -d install network-manager network-manager-gnome
```
[I]
When you install WICD it uninstalls Network Manager.. same deal the other way around as well.[/I]

**To install WICD do the following:**
```
echo 'deb http://wicd.longren.org feisty extras' | sudo tee -a /etc/apt/sources.list

sudo apt-get update

sudo apt-get install wicd
```

Now just goto Applications > Internet > Wicd to setup it up. If using WPA be sure to set the correct driver.

No need to load WICD manually at boot as init.d will load daemon.py (with root privledges, so you don't have to enter your password) at boot up.

If you want the systray icon you'll need to add it to System > Preferences > Sessions...
```
Name: WICD Tray
Command: /opt/wicd/tray.py
```
*(for edgy use edgy-tray.py, for dapper use dapper-tray.py)*

[B]
If you wish to switch back to network-manager, the packages should be in your archive:[/B]
```
cd /var/cache/apt/archives
```

Verify the file names: (2 packages)
```
ls | grep network-manager
```

Install the packages:
```
sudo dpkg -i network-manager-***.deb

sudo dpkg -i network-manager-gnome-***.deb
```

---

### Post by kevdog on 2007-08-01
Great instructions walkerk, however possibly you should add to you statment:
> 
sudo apt-get -d install wicd

The following
```

sudo apt-get -d install wicd network-manager network-manager-gnome
```

That way in case something doesnt go right with wicd, you could revert backwards.

---

### Post by walkerk on 2007-08-01
> **kevdog said:**
> Great instructions walkerk, however possibly you should add to you statment:


The following
```

sudo apt-get -d install wicd network-manager network-manager-gnome
```

That way in case something doesnt go right with wicd, you could revert backwards.

Good call.. I'll add that.

---

### Post by shrndegruv on 2007-08-01
again thanx brah.

Now once I get suspend to disk going Ill be in business and can get down to work.

after i reinstalled (I went thru those posts you mentioned and borked the computer somehow when i updated driver/firmware versions), and connected, i installed compiz-fusion in about, hmm, 2 minutes (used to take about 15 on gentoo); its amazing how well it runs on my modest ati x300 graphics card.  basically everything works without too much strain on the processor (even reflection and the new super+tab app switcher) except the blurring.

---

### Post by walkerk on 2007-08-01
> **shrndegruv said:**
> again thanx brah.

Now once I get suspend to disk going Ill be in business and can get down to work.

after i reinstalled (I went thru those posts you mentioned and borked the computer somehow when i updated driver/firmware versions), and connected, i installed compiz-fusion in about, hmm, 2 minutes (used to take about 15 on gentoo); its amazing how well it runs on my modest ati x300 graphics card.  basically everything works without too much strain on the processor (even reflection and the new super+tab app switcher) except the blurring.

LOL. Hosed your box because of the router :P

---

### Post by shrndegruv on 2007-08-01
> 
LOL. Hosed your box because of the router :P


yeah.  since it was still basically a fresh install, i decided would be faster to just reinstall than try and fix it.

---

