---
title: "difference between &quot;network monitor&quot; and network manager??"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by digitalramble on 2007-03-07
OK, I'm trying to figure this out, and it seems to be needlessly complicated.

First off, basic Edgy Eft installation, along with extra KDE components but gnome desktop.

Now, under System -> Networking, I can set up some profiles and such.  It's extremely minimal and has the headdeskingly frustrating stupid-as-batshit habit of insisting on connecting to the most recent wireless connection it made, *not* to a currently available one.  I then have to go in every freaking time I change locations on my laptop (you know, laptop, mobility, roaming, ...?) as root and tell it which profile to use.  That's beyond irritating.

Now, *is* that Network Manager?  Or is Network Manager something else?  If I check via Synaptic Package Manager, it appears to be part of the basic Ubuntu installation (has the k00l ubuntu graphic next to it and everything).  But if it's not this "network monitor" then I don't know where the hell it <i>is</i>.  On the other hand when I check their website, it *does* say that it only switches between the wireless and *wired* connections, and goes back to the *previous* wireless connection it made.  #-o 

All I want is for it to automatically connect to wireless profiles that it has connected to before.  I don't want it to require me to go in and kick things around as root unless we're talking about a brand new never-before-connection.  Is there a way to do this on "Network Monitor"?  Or should I use "Network Manager" (and if so, how do I find it, use it, and give the Monitor the boot)?

Is that so difficult?

I'm also looking at knetworkmanager (which first description says "userfriendly version", heh).

Anything to clear up and clarify this confusion would be welcomed.

---

### Post by spd106 on 2007-03-07
Network Monitor is tray applet for the old network system that is only useful for static addressed networks (no dhcp). It isn't neccessary and can be removed without breaking anything. You can always add it back later.

Network Manager is the new app that is going to replace the above in Feisty. The confusing part is that it also has a tray icon. I suggest you go to this wiki page for a quick guide [https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager)

---

### Post by Fitzcarraldo on 2007-03-07
Just a warning about the method of de-configuring devices described on that wiki page under Configuring Devices: the method given of *going to System -> Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager.* did not work for me -- to successfully de-configure the devices I *had* to use the alternative method of editing the /etc/networking/interfaces file as also described under Configuring Devices on that wiki page.

---

### Post by kristalsoldier on 2007-03-07
First, my wireless IS working. So, I am just asking this for a clarification. I have asked this before but...

See Shot1. Notice there are two 'networking' icons. The one to the left next to the battery icon has an exclamation mark on it. When I right click it, it says it is the network-manager applet. The details are in Shot 3. The icon beside the network manager applet, when right-clicked, says Network-Monitor. The details are in Shot2.

I thought the network manager is supposed to give details of available wireless networks to enable me to choose the one I want. I am talking about something like what you can see in Shot 4 (I am currently using Wifi Radar).

Will it be possible for someone to please clarify what's going on?

Thanks

---

### Post by gradedcheese on 2007-03-07
Yes, left-click on the NetworkManager icon and you will see a list of networks.  But, it ignores any interface enabled in /etc/network/interfaces (so that it doesn't try and manage something being managed the old way).  So, if there are no networks shown, you need to edit /etc/network/interfaces (as the above guide explains) and then reboot.

---

### Post by kristalsoldier on 2007-03-07
> **gradedcheese said:**
> Yes, left-click on the NetworkManager icon and you will see a list of networks.  But, it ignores any interface enabled in /etc/network/interfaces (so that it doesn't try and manage something being managed the old way).  So, if there are no networks shown, you need to edit /etc/network/interfaces (as the above guide explains) and then reboot.

Hey....thanks. It worked!

---

### Post by jgcamp99 on 2007-03-08
> **spd106 said:**
> Network Monitor is tray applet for the old network system that is only useful for static addressed networks (no dhcp). It isn't neccessary and can be removed without breaking anything. You can always add it back later.

Network Manager is the new app that is going to replace the above in Feisty. The confusing part is that it also has a tray icon. I suggest you go to this wiki page for a quick guide [https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager)

I would agree with your first statement about Network Monitor, but when I use a Proxim Orinoco Gold abg 8480-WD, I'm able to indicate ath0 as the wireless device for the card. It's configured as automatically assigned via DHCP.

Now when I use a Netgear MA401RA Rev D, it uses network manager it is assigned to eth1 and is also configured for automatic assignment via DHCP.

---

### Post by kristalsoldier on 2007-03-08
Hi...another question:....When I use the Network-Manager applet, I am asked to enter the keyring password. Is this a common feature? If not, is there any way by which the keyring password can be disassociated with the network manager applet? (*OK. It seems this asking for the keyring PW is a default behaviour...unless I am misreading the posts on this and there is a way to prevent this, though from what I understand, it is just replacing the keyring PW with the login PW. If this is true, I'd prefer to stay with the keyring PW) - so please ignore this part of the query. Thanks*

Also, Let's say I am trying to connect 10 times to a wireless network, 6 times, the network-manager fails to pick it up. But with Wifi Radar, it always picks it up. Is this because network-manager is still a beta?

Thanks

---

### Post by Fitzcarraldo on 2007-03-08
*kristalsoldier*,

The password that Gnome Keyring Manager asks me to enter is nothing to do with my ubuntu user password.

The Gnome Keyring Manager only asks me to enter the default keyring password once: just after I log-in to ubuntu.

The Gnome Keyring Manager stores the password (network key) for my wireless network, and by entering the keyring password when prompted, Gnome Keyring Manager provides Network Manager with my network's password (network key) to enable my PC to access the network.

This is standard functionality, and is done for security purposes. It is designed so that, if someone else has access to your PC and finds out your ubuntu user password, they still would not be able to access your network (and anything else hanging off it).


The above said, I find that one prompt by Gnome Keyring Manager every time I log-in to ubuntu to be a real pain in the backside.

There *is* a way to stop Gnome Keyring Manager from prompting for the default keyring password when you log-in to ubuntu. You can read about it [here](http://www.ubuntuforums.org/showthread.php?t=349984). I believe that method works for ubuntu 6.10 Edgy, but I don't know if it works for 6.06 Dapper or others. Note that the method given in the above-mentioned thread *only works if the Gnome Network Manager's default keyring password is the same as the ubuntu user password*. If Gnome Network Manager's default keyring password is currently not the same as your ubuntu log-in password then there are two ways you can make them the same:

1. change your ubuntu log-in password, or
2. change your Gnome Network Manager's default keyring password, using the procedure given in my second post [here](http://www.ubuntuforums.org/showthread.php?t=378179).


Regarding your last question, Network Manager on my PC (Gateway Solo 9300 notebook PC with Linksys WPC54G v7.1 CardBus wireless adapter) picks up networks 10 times out of 10 and works well, so I'm not sure why it does not in your case.

---

### Post by kristalsoldier on 2007-03-08
> **Fitzcarraldo said:**
> *kristalsoldier*,

Regarding your last question, Network Manager on my PC (Gateway Solo 9300 notebook PC with Linksys WPC54G v7.1 CardBus wireless adapter) picks up networks 10 times out of 10 and works well, so I'm not sure why it does not in your case.

Hi and thanks for your detailed reply/ help. I don't really find entering the keyring PW a problem so, I probably won't change it, but the last point does really bother me. FYI, I am on a Sony Vaio VGN FE-28B laptop with the Intel 9345 abg card, which is fine...I did not have to use ndiswrapper...

What bugs me though is that wifi radar has no problem, but network-manager does. But there is something I noticed - if I switch off and then on again the wireless lan switch on my machine, while network manager is searching for the network, it usually catches on. Now, while this works, I don't think this is an optimal solution. I'll keep looking!

---

### Post by TiredBird on 2007-03-08
I have a laptop running Ubuntu 6.06, (Toshiba Satellite M45-S165), with built-in wireless lan, (ath0), and built-in wired lan, (eth0). I use this laptop in three different configurations:

(1) Wired to my home network - static ip;

(2) Wireless on my home network - static ip with WEP encryption; and

(3) Wireless at various hot spots - dynamic ip with no encryption.

For (1) and (2), I use 'network-admin', (apparently version 2.12.0-5), in order to set the static ip address and the encryption key. However, I have not found an easy and consistent way to switch between the two. (Maybe that's because I don't understand and can't find documentation for the 'location' feature. Clicking on the 'help' button brings up documentation that does not apply to my program.)

For (3), I switch to 'network manager', (version 0.6.2), to be able to select from available wi-fi signals. (There are usually several.) However, in order to make the switch, I have to edit the /etc/network/interfaces file and take out the sections for 'ath0' and 'eth0' that were put in there by 'network-admin'.

Is there some way I can use just one network control program and still switch between the three various configurations, (without having to manually edit the /etc/network/interfaces file)?

---

### Post by kristalsoldier on 2007-03-08
> **TiredBird said:**
> I have a laptop running Ubuntu 6.06, (Toshiba Satellite M45-S165), with built-in wireless lan, (ath0), and built-in wired lan, (eth0). I use this laptop in three different configurations:

(1) Wired to my home network - static ip;

(2) Wireless on my home network - static ip with WEP encryption; and

(3) Wireless at various hot spots - dynamic ip with no encryption.

For (1) and (2), I use 'network-admin', (apparently version 2.12.0-5), in order to set the static ip address and the encryption key. However, I have not found an easy and consistent way to switch between the two. (Maybe that's because I don't understand and can't find documentation for the 'location' feature. Clicking on the 'help' button brings up documentation that does not apply to my program.)

For (3), I switch to 'network manager', (version 0.6.2), to be able to select from available wi-fi signals. (There are usually several.) However, in order to make the switch, I have to edit the /etc/network/interfaces file and take out the sections for 'ath0' and 'eth0' that were put in there by 'network-admin'.

Is there some way I can use just one network control program and still switch between the three various configurations, (without having to manually edit the /etc/network/interfaces file)?


Well...while I use network-manager, I have also used a program called wifi-radar downloaded via Applications>Add/ Remove.

It works and quite well. It will ask you - the first time you connect to a new network - for the relevant details and then will remember it (store it away). You could try it.

Hope this helps for as you can see, I too am struggling to understand how this network-manager works - actually, not so much how it works, but why it is temperamental.

Cheers! EDIT: BTW, I noticed (too late) that you are using Dapper (6.06), note that I am referring to Edgy (6.10).

---

### Post by TiredBird on 2007-03-08
I have added wifi-radar to my setup. It solves part of my problem but creates some others.

I read the man pages on it and the config file but didn't really learn a lot. Is there any real documentation for it? 

I still can't figure out how to get hooked up on wired home lan with static ip from the same laptop I use wireless on the home lan and wireless at various hot spots without manually editing the /etc/network/interfaces file when I switch from wired to wireless.

Also, now I have three programs trying to manage my network connections. I really would like to have just one.

---

### Post by kristalsoldier on 2007-03-09
> **TiredBird said:**
> 

Also, now I have three programs trying to manage my network connections. I really would like to have just one.

Yeah...you AND me!

---

### Post by TiredBird on 2007-03-09
I have scrubbed Network Manager and WiFi-Radar, (removed them from my system), leaving only the original Network Monitor. (network-admin).

I attempted to create different profiles for Network Monitor, putting the different profiles in the XML file at '/etc/gnome-system-tools/network/profiles.xml'. I eventually gave up on that because not all of the parameters acted correctly, (I think the program has a bug in it and it appears that with Network Manager on the horizon, no one is maintaining it. I've been piddling with it for a year now and never been able to get it to work predictably or find any current documentation for it.) 

I have settled on making changes to the '/etc/network/interfaces' file. I have created a look alike file for each of my most common scenarios. (The one called 'wired.home' is the one I use when in my office, wired to the router with a static ip; 'wireless.home' is for using the wireless interface to connect to the home network, using it's essid, an encryption code and a static ip; 'wired' and 'wireless' are the same as their '.home' counterparts except for using dhcp, with the wireless having no essid and no encryption.) 

A script with the name of the profile as a command line argument shuts down the existing interface, makes a link to the profile and starts the new interface. I am going to put icons on my task bar that run the script with the various profile names. I am looking for an application that, when using the generic 'wireless' profile, will scan the available wireless connections and allow me to choose one from a gui.

I searched the net for programs and/or applets that would do what I wanted but couldn't find anything that had it all so I decided to build my own. It looks as if Ubuntu, Gnome and most everyone else is waiting for the 0.7.0 release of Network Manager, but the release date keeps getting pushed back. I decided not to wait any longer.

If anyone is interested I can provide copies of the files I have created. (They are only a few lines each and quite easy to understand.)

---

### Post by zorkerz on 2007-03-11
> **spd106 said:**
> Network Monitor is tray applet for the old network system that is only useful for static addressed networks (no dhcp). It isn't neccessary and can be removed without breaking anything. You can always add it back later.[]("https://wiki.ubuntu.com/WifiDocs/NetworkManager")

Network Monitor is a required package for Ubuntu Desktop.  This appears even to be so in feisty at the moment (although possibly thats a layover from my upgrade).  My understanding is that ubuntu desktop is not actually doing anything in itself but just holds many dependencies so that one knows their desktop has all the requirements.  Im debating removing network monitor and ubuntu desktop but more likely i think i will leave network monitor around even if i now only use network manager just so ubuntu desktop also stays installed.  Is this correct and does it make sense?

---

