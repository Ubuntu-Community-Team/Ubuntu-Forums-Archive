---
title: "WLAN not working with WEP security on"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by MicheleZ on 2007-02-13
Hello there,

I have a orinoco-based WLAN in my Compaq laptop that I use to connect to a D-Link wireless router.
The laptop is dual boot (since a couple of weeks) and I never had problems using the WLAN under Windows.

In ubuntu (Edgy) however I stay connected for a few seconds and then stop receiving packets from the router. The problem appears to be the WEP since if I just open the connection it works fine. 

Is there anybody else who experienced this problem with WEP? 
Is using WPA very complicated? (I am very new to Linux)

Cheers,

Michele

---

### Post by Floppyjoe on 2007-02-13
I don't have any experience with the problem you are having but there is a WPA HOWTO in the WIKI at this URL:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29)

Floppyjoe

---

### Post by LaneLester on 2007-03-13
Michelle, did you ever get wireless with WEP working? I have the same basic setup as yours (works with open, not with WEP, orinoco), and I've spent a whole morning reading these darn wireless threads and trying various tweaks to no avail.

Lane

---

### Post by chili555 on 2007-03-13
Perhaps this will help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

---

### Post by LaneLester on 2007-03-13
> **chili555 said:**
> Perhaps this will help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

Thanks! I had read that one, but not carefully enough. Here are the main points:

> In my experience, failure to connect with WEP is actually caused by two issues and, very rarely, a third.

1. Router and computer don't have the same key.
I confirmed that both are the same 10 digits. Any reason a 10-digit won't work?


> 2. Router and computer don't share the same ESSID
I confirmed that both are exactly the same, including letter case (all upper)

> 3. Restricted vs. Open
This is the one I had misunderstood. So I changed my WRT54G from Auto to Shared Key, edited the interfaces file and restarted networking. But no joy; networking restart still says: No DHCPOFFERS received.

Lane

---

### Post by haz2a on 2007-03-13
I couldn't get WEP to work, but since my AP has WPA which is more secure, I tried that and it did work. However, its not the easiest thing to setup. What I did was:-

First of all make sure the connection is OK without encryption security - no WEP or WPA.
Then setup WPA.

NB: Adapters based on rt2500 (Ralink/RealTek?) chipset - must follow special procedure per:-
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) > find 'rt2500'.

WPA Mode
WPA-PSK (Pre-Shared Key) sometimes called 'personal/home/soho' because operates without a separate key server often used on enterprise corporate networks. This mode automatically and frequently changes the key, so it has good security.

Pkg wpasupplicant will probably already be installed in Ub 6.10, but if not, install it.

I'm not sure if step A is necessary, but I did them all and it worked. Where I've shown the '#' prompt thats cos I did 'sudo -i' to a root prompt, but you could just replace the '#' with 'sudo' each time:-

A. vi /etc/default/wpasupplicant, creating if necessary, and ensure it has the line:-
		ENABLED=0   

B. Store the WPA passphrase  
# wpa_passphrase <essid> (eg: YourAccessPointName)
This will respond with:-
# reading passphrase from stdin
# _ 
Enter the passphrase, eg: between 8 and 64 chrs at the above prompt. 
(Requiring wpa_passphrase to prompt for the passphrase, rather than providing it as a command line argument, prevents the phrase from being stored insecurely in the shell's history).
It will then display:-
network={
      ssid=<ssid>
      #psk="TextPassphrase"              psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
}
Open/create /etc/wpa_supplicant.conf in another terminal tab.
Copy the above code from 'network{' to '}'  to the end of /etc/wpa_supplicant.conf.
It might also be necessary to add: 'proto=WPA' and 'key_mgmt=WPA-PSK' if not auto-detected.
If the WAP uses a hidden SSID then also add: 'scan_ssid=1' as shown below:-
        network={
              ssid=<ssid>
              scan_ssid=1
              proto=WPA
              key_mgmt=WPA-PSK              psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
        }

C. Add the following two lines to /etc/network/interfaces, just below 'lo':-
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf   .

D. Reboot and Try to Connect
Ensure any LAN cable unplugged so that wireless is only choice.
Might be possible to do:  /etc/init.d/network restart  
or:  /etc/init.d/dbus restart  
instead?
NtwkMgr > RC > Networking and Wireless both enabled.
NtwkMgr > LC > SSID (eg: YourAccessPoint)
Should now get box 'Network Key Required' - check task bar in case not on top!
Enter:-
Security > WPA Personal
Password: <passphrase>
Type > AES (or as setup in YourAccessPoint)
GNOME Keyring might now demand a master password > just enter yours.
NtwkMgr should now give a message saying that it is connected and showing the 'signal strength' icon.
Open Ffx and test.

Main WPA Refs
(a)	[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
(b)	[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Then you'll want to install pam-keyring as explained in ref(a) above - more fun!

Good Luck
Haz

---

### Post by chili555 on 2007-03-13
> Any reason a 10-digit won't work?No reason whatever.

One other thing to check. Some Linksys routers by default, broadcast key #3. For some reason, we must have key #1. Check in your router to be sure the proper key is in key #1 and key #1 is broadcast.

Then sudo dhclient <your_wireless_interface> and post back the news.

---

### Post by hardyn on 2007-03-13
If you think that the problem is beyond a setup problem go here:
[https://launchpad.net/bugs/90896](https://launchpad.net/bugs/90896)
and leave a discription.

I and a few others have reciently started having trouble.

---

### Post by LaneLester on 2007-03-13
> **chili555 said:**
> No reason whatever.

One other thing to check. Some Linksys routers by default, broadcast key #3. For some reason, we must have key #1. Check in your router to be sure the proper key is in key #1 and key #1 is broadcast.

Then sudo dhclient <your_wireless_interface> and post back the news.

Sorry, "No DHCPOFFERS received."

Lane

---

### Post by chili555 on 2007-03-13
So, are you using NetworkManager? hardyn's post and a Google search for ubuntu NetworkManager bug are pretty scary.

---

### Post by nagato on 2007-03-13
I'm having a very similar problem with my iwp2200 card and KUbuntu 6.06 Dapper.  If the wlan is unprotected, my laptop connects and runs perfectly, but for some reason it's completely unable to connect to a wlan that is using WEP; I'm sure I'm entering in the correct key too. :P

---

### Post by LaneLester on 2007-03-13
> **chili555 said:**
> So, are you using NetworkManager? hardyn's post and a Google search for ubuntu NetworkManager bug are pretty scary.
I'm just using the Networking thing that automatically installs with (X)Ubuntu.

I've installed some form of Ubuntu three times today. Early on, when I was hacking my way through all the online advice, I got my wireless card activated, but I couldn't get WEP to work. Now with Ubuntu Edgy installed, I've disabled WEP and the wireless card isn't active or something!

I guess I need to wade once more through all the how-tos, wikis, and threads scattered all over the Internet and hope I can stumble across the right combination.

How sadly amusing is all the conversation about Linux replacing Windows for ordinary users. :( 

Lane

---

