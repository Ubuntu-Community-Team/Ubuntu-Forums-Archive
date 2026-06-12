---
title: "Have no wireless after recent header update"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by larrikin71 on 2008-10-28
Hi,

 I have the following adapter on my computer :-

       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
 
which i had working recently until i updated my linux with the latest headers, now ubuntu isnt even recognizing my wireless card anymore.

This is what i am getting after  sudo lshw -C network

 *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

I got this card working before by doing this 

sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local

I figured i would give this another go but all i get is :
sudo: unable to resolve host derren-laptop

Any help would be appreciated as it took my quite a while to get this operating in the first instance.

Regards
Derren

---

### Post by beta.tester on 2008-10-28
Hi derren

I was having similar problems to you. I have a Sony VGN-N38E/W laptop with the Atheros pci express wifi card. However I tried the RC version of 8.10 and it has worked a charm, even after an update (which prior to this mucked up all my wifi settings).

Could I suggest you load the 8.1 RC version (or wiat for the release on the 30th October) and run it live! When I did that it picked up my network straight away (I only had to click on the network icon, enter my wpa/tsk password and away it has gone ever since ;) It does ask for a keyring master password which I also entered. Not sure if this will help, but it certainly fixed my problem. (I then reinstalled the 8.10 RC version and it has been working as it should, even after a lot of updates, including another kernel. I simply rebooted and everything was working.

Something has changed for the better from the latest beta to the RC version that has fixed this problem for me, and I hope, for you and others also.

kind regards   john

---

### Post by xr0ckstar on 2008-10-28
Hey there im a total noob. But i may have a suggestion. I was having problems with my wireless card not being detected after trying to install the network-manager. I think the System>Administration>network app i was using was conflicting with my new network-manager. I was having problems such as " eth:1 interface does not exist " and " eth:1 avahi " . These problems occured after trying to set my wireless card on roam with Sys>admin>Network .  My wireless was working flawless out of the box when i first installed. So i got my Ubuntu install disc, put it in and did a " recover broken system " The disc searches your hardware and ask for your network connection, I chose my wireless connection interface it succesfully loaded up the same way it did when i installed Ubuntu. chose my root drive blah blah blah and restarted my computer. Then i went to my network manager and put in the name of my SSID which i set to hidden, and it connected fine, so now i just use network-manager and i dont mess with the other networking applets.  SOrry if this sounds confusing or messy as far as instructions.  Hope this helps somebody out  

-Peace

---

### Post by beta.tester on 2008-10-28
Hi rockstar

firstly welcome to Ubuntu (the best distro :)

What version are you referring to? The problems (for me) was after an update my wifi settings were lost and I had to manually "connect to hidden network" from the connection icon. With 8.10 Rc it finds it for me and I simply had to enter the password and all was well, and it continued to work after updates that included a newer kernel revision ;)

I hope you get a big kick out of Ubuntu that we all do that use it.

Nice to see a new member trying to help others, that is what Ubuntu is all about :)

Kind regards and welcome again,   john

---

### Post by larrikin71 on 2008-10-28
Hey thanks for the replies..!!

K so i went to System > Administration > Network  and there was no sign of the wireless card being detected so i retried madwifi to no avail, the card still didn't show up.

The next thing i did was connect to the net with a wired connection which at first didn't detect my router but after logging out and back in did.

But still no wireless...

So i rebooted my system...and voila! i have wireless....so if anyone else is having trouble it seems those updates make your system a little bit temperamental but i have been running wirless since yesterday and have had no problems since.

thanks to all

---

### Post by xr0ckstar on 2008-10-29
> **beta.tester said:**
> Hi rockstar

firstly welcome to Ubuntu (the best distro :)

What version are you referring to? The problems (for me) was after an update my wifi settings were lost and I had to manually "connect to hidden network" from the connection icon. With 8.10 Rc it finds it for me and I simply had to enter the password and all was well, and it continued to work after updates that included a newer kernel revision ;)

I hope you get a big kick out of Ubuntu that we all do that use it.

Nice to see a new member trying to help others, that is what Ubuntu is all about :)

Kind regards and welcome again,   john

I am using Ubuntu Studio 8.04 ... yes i am enjoying ubuntu.  After seeing how far along ubuntu came I had to give it a try. I tried to use linux about 4 years ago but got fed up with not being able to run wireless. i experimented with fedora and red hat back then.. so here I am back in the linux world for round two...    Larrikin glad to see u got your wireless working  :guitar:

---

