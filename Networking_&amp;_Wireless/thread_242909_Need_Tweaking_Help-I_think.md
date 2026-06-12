---
title: "Need Tweaking Help-I think"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by adMOMistrator on 2006-08-24
:-?  Could someone please help me figure out what's wrong with my network?  I have an XP, a desktop with EduBuntu and a laptop with EduBuntu (both installed in the last week) on an ethernet network.  Its connected through a hub with the adsl modem that can act as a router.  The destop with buntu can find the net just fine on install every time.  The laptop has serious issues.  I have had it on the internet all day a couple of times, but if I walk away and it goes to sleep, or I turn it off, the network doesn't work-and I have no idea what I did to make it work.  Its been two days this time:(

I did a fresh install yesterday as a workstation instead of server hoping that would help-no.  It can't configure the net right during install.  So I copied the settings from the desktop and put them in-no luck.  The laptop knows its on the net, the updater even lights up-but I can't connect to anything-or if I connect, it doesn't get back, or something.

Here's the network settings I copied from the working desktop:

Eth0 prop-   DHCP
DNS Serv-    192.168.1.254  (this is entered twice)
Search Dom-   launchmodem.com
Hosts:
     ff00::0   ip6- mcastprefix
     127.0.0.1   localhost edubuntu       (**does it mean anything that   both pc's call themselves edubuntu??)
     fe00::0  ip6- localnet
     ff02::2   ip6- allrouters
     ff02::1   ip6- allnodes
    ::1    ip6- localhost ip6- loopback
    127.0.1.1   edubuntu.launchmodem.com edubuntu
    ff02::3   ip6- allhosts


So then I went to the laptop (IBM T20) listed net devices-  Intel Ethernet Pro 100 (PCI)    unknown networking interface dev type- net.80203 capabilities net, net. 80203
So I have the eth0 set up exactly the same as the working pc, except for some reason I currently have the Host list slightly different (doesn't seem to matter-I've changed it 100 times).  The list is missing 127.0.1.1 edubuntu.launchmodem.com edubuntu   and in its place has  192.168.1.10 edubuntu

I ran ifconfig on the laptop and here's what I got: **I see that it looks like I may have an IP addr problem in the host list, but if I try to change it doesn't seem to help. (I changed it while trying to figure this out-read it on forum somewhere).

eth0 
Link encap: Ethernet  HWaddr 00:20:E0:64:15:57
inet addr: 192.168.1.97 Bcast 255.255.255.255 Mask: 255.255.255.0
inet6 addr:fe80:  :220:e0ff:fe64: 1557/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
RX Packets: 302 errors:0 dropped:0 overruns:246 frame: 246
TX Packets: 581 errors:0 dropped: 0 overruns: 502 carrier: 0 
collisions: 0 txqueuelen: 1000
RX bytes: 281782 (275.1 KiB) TX bytes: 168627 (164.6 KiB)

lo
Link encap: Local Loopback
inet addr: 127.0.0.1  Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
RX Pack: 34 err:0 drop:0 or: 0 frame: 0
TX Pack: 34 err: 0 drop: 0 or: 0 carrier: 0
collisions: 0 tx: 0
RX bytes:5349 (5.2 KiB) TX bytes:  5349 (5.2 KiB)


I'm pretty stupid about this still, but it looks like its going up but not down--but I dunno!
Please be VERY specific with any help-this is only my 2nd week with linux :-D

Thanks A Bunch!

---

### Post by bull8042 on 2006-08-24
Someone can correct me if I am wrong, but those network settings look screwy to me. Your system network settings should be found in /etc/network/interfaces.
Mine look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Pretty simple, but I use Network-Manager for my network configuration because I enabled WPA for my wireless. Eliminates the need for ifplugd, hotplug, etc to switch between wired and wireless.
Just out of curiousity, which file contains the config you posted?

---

### Post by adMOMistrator on 2006-08-25
I went to term and typed ifconfig (on the non-working laptop) and got that config list.  
 I read your post before I came back to the forum and installed network manager.  I had to go back and comment out the network interfaces like I read on the NM stuff.  Everything looked ok, and NM seems to have changed the settings, but I still can't get online.  I ran ifconfig and it still says basically the same thing.

When I open Firefox and try to surf, it will say that its locating the site and hang forever.  Sometimes it will switch the title bar to the new site and say transferring-but never gets there.  Sometimes it just looks, but never finds the site at all.

Its really baffling me.  The net card's lights are lighting up, so is the hub.  The update mgr knows that updates are avail, and the network indicator on the bar says its ok.  Network manager thinks its enabled, and the settings on the eth0 and NM seem to be about the same.  

Could it be some kind of buffer overrun problem?  Could it be broken hardware?  Do network cards get flakey like that, never work, then work for a bit, then not work again?  Is there any way to test either of these?  
*The whole reason I installed Edubuntu on the laptop was when it had XP pro on it and I tried to connect to the network, I couldn't.  And when I did finally get it where I thought I had it, IE wouldn't load any pages and the status bar ran like crazy with a bunch of gobbledy gook.  I had hoped that it was either a spy or IE was broken-or that it was because of the pro wdws settings.  Now I wonder if the net card isn't messed up.

Any other suggestions??  I'm about ready to chuck this piece out the window.

Thanks :-)

---

### Post by bull8042 on 2006-08-25
The fact that the OS is showing that updates are available may not necessarily be an acurate indication of prior connectivity. If it is a brand new install, it probably defaults to prompting you to check for updates that are assuredly available.
I had a similar problem before, the wireless was actually communicating with the router, but the router would never issue an IP. So check two things:
1 - Make sure your router is set with DHCP server enabled and a range of IPs specified. (192.168.0.1-10 or something like that) and be sure your wireless network (eth0) is set to DHCP.
2 - Power down then back up both your router and modem. I also had a problem a while back during a new router install where the router could see the modem, but internet was not available. I had forgotten to power them both off after connecting them together. Sounds dumb, but it may be just that simple.

---

### Post by adMOMistrator on 2006-08-26
First-I am using a WIRED ethernet connection.  2nd-I have actually browsed the internet on it with previous and the current install.  Just I have spent literally hours playing with the network connection before getting it to work, so by the time it works I have no idea what settings it is using.  And if I walk away long enough for the screen to go off, or I turn the pc off-the connection doesn't work when I come back.  Sometimes it even comes back on with the network deactivated.

I got it on the internet ok the night before I tried NM, I took note of the settings and shut down the pc to see if it was really working this time.  When I got back in-no internet.  Now after NM its doing what I described in the last post.

The router has done fine with the other pc (s)-and Network Mgr even picke up a new ip address for the laptop-which didn't get changed in the net connection interface or the ifconfig.  I went and tried to get the IP to match-and it looks like it matches now, but still no internet.  

I tried resetting the modem/router yesterday-twice, as a matter of fact-because I screwed up with the power like you mentioned, and lost my whole internet for a min :-( LOL

Something I noticed yesterday-I watched the network lights on the laptop on boot yesterday.  They both came on and looked to be blinking in sync like everthing was working (at the hub too), But then all of a sudden when buntu got to a certain point of the startup-the green one turned off.  Like some program or setting kicks in and shuts down the connection that is working.

Any thoughts?  Could it have something to do with the bind issue with NM that I saw something about (I have no clue what that is)?  Or could there be some wierd setting in the bios?  I bought it off ebay and it has some issues-I bought it as 900Mhz, it says its 680-the guy insists its 900.  Sometimes when it starts up, it stops and asks if you want to attempt to boot at 100 something or abort.  And XP said there was an unknown piece of hardware in the network area that had no driver.  Buntu hasn't mentioned it that I have seen-but it does have a mini pci bridge -whatever that is.  I gotta admit, I'm as new to networking as I am to Linux.


Thanks So much for your patience & help

---

### Post by bull8042 on 2006-08-26
OK, I am trying to help you with your wireless, and you are using a wired connection. OOPS!! Sorry, I was on the wrong page.
Honestly, I am a Linux convert of a bit less than a year, so the help I can offer is limited. I used Gnome for the first 6 months, but have since gone to KDE because my laptop is a 3.2 Ghz and can handle the eye candy. Anyway, in KDE, go to "System Settings": "Network Settings": select "Administrator Mode", then select "Ethernet Network Device". In the popup, I selected "Automatic", "dhcp" from the pulldown, and checked the box for "Activate when computer starts".
With that configuration, if I have a cable plugged in when I boot the computer, it will use the wired connection. If not, it will initialize the wireless connection.
I am sure you have done that already, but that is all I had to do.
When I was using Gnome, I had to install "ifplugd" and "hotplug" so the computer wouldn't pause forever during boot trying to initialize a non-existing wired connection. However, even before I installed them, it would default to the wired connection and properly configure it when available.
I really don't know what to tell you to try next. The hardware thing you mentioned is a bit perplexing and would make me wonder if you have a flakey network adapter. 
I have installed "Breezy" and "Dapper" on a couple of laptops and a few desktops numerous times and never had any type of configuration problems out of the box. One thing that does come to mind though. I have been told to always have a wired connection during the install so it configures it properly. I usually have to re-try the connection during the install until it says it sucessfully found the network. A re-install may be something, a last resort, for you.
If you created a separate partition for /home, then when you re-install, mount the partition as /home and don't format it. All of your desktop launchers, background, etc will still be in place when you boot back up. This includes your mail, bookmarks, etc. It has worked great for me. I can re-install Kubuntu and all of the programs that I had before in about 30 minutes and everything is still the way like it.
Sorry I can't be of more assistance. There are some very qualified people here who can fix your problem if it is not the hardware, assuming they read your post. You might try submitting a new post with a different subject line to catch their attention.
Good luck,
Bull

---

### Post by adMOMistrator on 2006-08-26
Thanks a bunch :-)  I was just thinking that I would try to re-install Edubuntu and when it says it can't auto configure the net, I could use the settings that Network Mgr has.  It can't hurt.  

Thanks Again :-)

---

