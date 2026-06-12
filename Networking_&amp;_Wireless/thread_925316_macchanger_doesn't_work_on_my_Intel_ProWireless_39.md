---
title: "macchanger doesn't work on my Intel Pro/Wireless 3945ABG"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Landslide on 2008-09-20
I have a laptop with an Intel 3945 wireless card built in. To access my network, I have to force a specific MAC address (we have really strict network admins), which is other than the default on the card. I've been using Ubuntu on this laptop since Dapper, and I've always just used the macchanger script from the repos to force the proper MAC, by calling it in rc.local. 

Ever since Hardy though, I have been completely unable to get it to work. First, I noticed that the interface name has changed from eth0 to wlan0. When I try to call macchanger with wlan0, however, it spits out this error:

ERROR: Can't change MAC: interface up or not permission: Device or resource busy.

Now, I'm using sudo, and it doesn't work in rc.local either, so I know it's not a permissions issue. So, I take the logical next step of trying to bring the wlan0 interface down, then change the mac, then bring it back up. Unfortunately, when I try that, I get the error message:

ifdown: interface wlan0 not configured

...even though ifconfig wlan0 spits out all the relevant info about my card.

My Windows machine (strictly for using Propellerhead Reason) connects to the internet with a D-Link WNA-2330. I popped it into my laptop and installed the Windows drivers with ndiswrapper and got it working... and then I tested macchanger on it. It works fine! So now I'm really perplexed. What is it about the *native* Intel drivers on my built-in card that keeps macchanger from working, when a Windows driver through ndiswrapper will work?

I really hope I can get macchanger working with my built-in wireless. I don't wanna have to spend the cash on another D-Link external card, when I have a perfectly good wireless card on my laptop and I only need the extra card to connect to one particular network.

Any ideas?

---

### Post by mgtr on 2009-02-09
Hey, 

I was having the same problem.  I just installed 8.10 intrepid and macchanger was not working with my intel 3945 card.  

I right clicked on the network icon near the system time and disabled wireless.  Then I tried changing the mac address and it worked.  

I brought the adapter back up the same way I took it down and checked the mac address with ifconfig and the change worked.  I am not sure this will work for you, but it should be easy to check.

---

### Post by Landslide on 2009-02-09
Awesome, that worked! Many thanks! Something about Network Manager is messing it up.

Also, using this method I was able to script it in rc.local like before, like this:

/etc/init.d/NetworkManager stop
macchanger --mac XX:XX:XX:XX:XX:XX wlan0
/etc/init.d/NetworkManager start

I realize that disabling NM entirely is a bit overkill but I haven't seen any ill side effects.

---

