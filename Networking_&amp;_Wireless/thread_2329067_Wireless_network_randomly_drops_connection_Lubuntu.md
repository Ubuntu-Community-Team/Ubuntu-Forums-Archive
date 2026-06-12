---
title: "Wireless network randomly drops connection Lubuntu 16.04 LTS"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by Leon A on 2016-06-27
We are a non-profit educational organization using Lubuntu for educational classroom lab clients, connecting to a small Ubuntu battery powered server with built in wireless Access Point.  The client laptops are re-furbished HP Stream 11 netbooks [Intel Celeron N2840 dual 2.16GHz, 2GB RAM, 32GB onboard SSD] and some use the Realtek 8723be wireless card and others use Broadcom bcm43142 wireless cards. We had originally been using Lubuntu 14.04 but decided to upgrade for the next set of schools this year.
After initial installation and working around the well-known Broadcom compatibility issues (thanks to these forums), all of the clients can connect to the server AP. However, we found that after connecting, they randomly stop communicating.  I can run a series of PINGS and all packets return in normal 2-3ms range for thousands of attempts, then all of a sudden, a laptop will stop receiving icmp packets (or report tens of thousands of seconds delay), and then timeout with report "Destination Host Unreachable" or in some cases "send msg: no buffer space available".  When this happens, other clients configured identically continue to respond with no errors (so that rules out problem at the server AP).   The BCM chipsets seem worse than the RTL chipset, but we've seen the exact problem on both versions. Running ifconfig and iwconfig when PINGs are unsuccessful still shows the non-responding client is connected to the AP and has same IP address.
A work around is to disconnect the wireless connection using graphical network manager icon in lower right, or to toggle the "Airplane" mode key.  After reconnecting, the client usually communicates with AP normally again (Pings 100% successful) but once in a while only a reboot restores connectivity.  Sometimes these droputs happen after 5-10 minutes, and other times it may be hours before a client disconnects. I have about 200 laptops to configure for several schools and this problem is critical because the offline math tutoring program we run from the little server is sensitive to disconnection.  I've searched the Internet and tried many things, but so far no success.  Here is what I've done so far:
1. Fresh install of Lubuntu 16.04 desktop AMD 64bit from Live ISO disc.
2. Fresh install of Lubuntu 16.04 desktop from i386 32bit Live ISO disc.
3. Connect to other wireless networks -different server APs on different channels, corporate domain AP, different physical location (even went out of city to isolated area with no other wifi signals). 
Also compared these same networks while connected with Windows 8 laptops, several Android tablets, and a Dell Latitude 6410 running Lubuntu 14.04LTS, and they did not show any dropouts while the new Lu16.04 devices did.
4. Update everything possible [apt-get update], try different drivers [bcmwl-kernel-source is supposed to be best match for bcm43142, using rtl8723be for RTL]
5. Edited the WiFi power management config file for Realtek by adding in  /etc/modprobe.d/rtl8723be.conf
                                # Disable chipset power mgmt.
                                Options rtl8723be fwlps=0    ips=0    {alternatively =N)
6. Perform upgrade ( sudo apt-get dist-upgrade) on netbook originally running Lubuntu 14.04LTS and connected to corporate network (with external Internet access). While doing this, it successfully downloaded hundreds of MB of files for the upgrade to Lu16.04 and then started installing/configuring them.  Near the end of the process, I noticed the WiFi network dropped out and I had to force reconnect.  It had been stable up until a certain point in the upgrade to 16.04.  After the Upgrade and running apt-get update to make sure everything was latest, I compared that netbook to some of the others that I had updated from the ISO disc clean install and found it acted the same.
In all cases, PINGS will cease, html pages "freeze", and often the Network manager will pop up message in upper right saying "network disconnected".
Today I ran the "wireless info" scripts by Wild Man, Krytorik, chili555, and others as often mentioned in these forums on this netbook with BCM that was upgraded from LU14.04 to LU16.04.  The first report was taken while it was successfully PINGing the server AP [ wireless-info-RA-Ping.txt].  After a couple hours, I caught it failing (Dest host unreachable) and grabbed another capture of the wireless info [ wireless-info-RA-noPing.txt].  Comparing the two report files shows only minor differences in AP signal quality/level, number of packets sent/rcvd, beacon timestamps.  The only significant difference I find is that when it was working, it also showed three other neighboring WiFi networks available that didn't show up when it was not successfully PINGing the intended server AP.  I am attaching both reports in case anyone can find something else different.
One other thing I will mention is that sometimes under Lu 16.04, I've seen the graphical Network Manager icon in lower right of screen change from the 4-bar signal strength icon to the double-box indicating network disconnected, and sometimes clicking it will not show ANY WiFi networks available, even when I may still be successfully PINGing my server AP.   At most other times, the 4 bars show signal level, even when it stops responding to PINGS. So this visual notification doesn't seem to correspond to whether or not the client is really connected, and I am treating it as more an annoyance instead of show-stopper right now so can defer resolution of that until later unless the same fix corrects both the dropping out and the status display. Rebooting always restores the proper display of network status. 

I am at a loss what to try next.  I've been configuring Lubuntu on these netbooks for a year and have learned my way around CLI, so am not quite a newbie, but I am not a real linux expert yet either. Any suggestions?

---

### Post by DuckHook on 2016-06-28
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

Welcome (back) to the forums, Leon A.

I'm no wireless expert, but what you are trying to do is part of such a good thing that I'll jump in, even with my limited knowledge.

My suggestion is one that I suspect you won't like at all... go back to Trusty (14.04) because you know it works. For mission-critical use such as yours clearly is, it is not a good idea to upgrade to the latest and erstwhile greatest until you've carried out an exhaustive test using a limited number of machines. Only after demonstrable compatibility has been established do you then roll out the full upgrade. I realize that this means reinstalling to 200 laptops, but it is a guaranteed-to-work solution and Trusty still has a few months of support left on it... you can consider upgrading to Xenial only after its first point release which will hopefully stabilize a few things.

Having said the above, I reiterate that I am not a network or wireless expert. I'll be the first to acknowledge that my solution is drastic, so let's see if my far more knowledgeable colleagues see this thread and can think of other options.

---

### Post by Leon A on 2016-06-28
Thanks DuckHook for moving this to appropriate forum. I should have mentioned that the schools where we are providing the labs are located in remote jungles of Liberia, Africa and do not have Internet access (hence the self-contained, battery powered content server AP). My main reason for upgrading was to allow the latest version of Khan Academy offline vidoes (KA-Lite) to play on the clients, as the video player/codecs on Trusty are no longer supported on latest version of KA-Lite.  FYI, more info about our Innovative Education project can be found at iei3c.org.  One other thought I had is that maybe this isn't a network/driver problem after all - -could it be a bug in Xenial firewall?  Hopefully someone out there can steer me to resolution soon as we plan to leave for Africa with these 200 laptops in August.

---

### Post by MAFoElffen on 2016-06-29
I also volunteer for a Non-Profit that does computer recycling and refurbishing.

My questions are:
-What is the physical layout of your wireless within your building? Maybe you could post a rough sketch of your building, where the access point is within that building and any range extenders.
-What is your building and it's inner walls made from? (reinforce concrete, concrete blocks, with rebar? Drywal with metal-stud) Just thinking commercial construction.

If you look at a fresnel formula, you have a range, and then a cross-section of the oblique, that takes into consideration the shadows caused by obstructions...

Next... if you add a script to release/renew the wireless IP address, that might be kinder on the wireless dhcp server on your server side, than going to an airplane mode.

One thing to do is to check the lease age in your dhcp server. Then log at your active leases to see if they are getting maxed.

For diagnostics, I use an old WinMobile phone with "WiFiFoFum." It was updated and converted to work on Android and iPhone. It has 2 view modes. The list mode that will tell you any wireless networks that it sees and all the info you would ever want. The radar mode will give you a radar like map with your phone as the center and the range of networks around you. I use it to walk from room to room and check for problems.

Next thing I use is my notebook with Wireshark. Sometimes, especially if you are using a repurposed router as a repeater, if someone accidentally plugs a wired cable into that wireless repeater, it will intermittently cause a broadcast storm that will overwhelm your network. The easiest way I've found to track that down, is by monitoring with Wireshark. The above app, on the phone will tell you exctly where that mac address is, when you need to track that down.

---

### Post by Leon A on 2016-06-29
Appreciate your response, but I've already eliminated the possible issues you mention.  I use an Android WiFi scanner app and verify that the server AP is not on same channel as other nearby networks, and have even driven out of the city to a rural cemetery in middle of farmland where there were no other signals at all, and still had same dropouts. The problem manifests itself even when the client laptop is right next to the server AP, and as I said, other identical laptops may continue with no drop or missing PING at all when one or more others randomly quit.  For the benefit of others, the battery powered linux server AP we use is made by Intel ([http://www.intel.com/content/www/us/en/education/solutions/content-access-point.html](http://www.intel.com/content/www/us/en/education/solutions/content-access-point.html)) and I have lease set for 10 days default, and the problem exists whether I have only one or up to 25 or more laptops connected to it.  
The problem also occurs when I connect to other corporate WAP and even my personal WiFi net at home, and as I've said, I have over 200 identical laptops (except production variance of using either bcm or rtl wireless chips) and all that I've upgraded to Lubuntu 15.10 or 16.04 experience the problem, but we didn't notice it when we were using 14.04 last year.

---

### Post by DuckHook on 2016-06-30
I am taking the liberty of linking to a post you made on another thread that I started: specifically, your post in which you mention something that could be very relevant to your own situation: [http://ubuntuforums.org/showthread.php?t=2328415&p=13511123#post13511123](http://ubuntuforums.org/showthread.php?t=2328415&p=13511123#post13511123)

In the interest of brevity I quote the passage that I think is most relevant:> **Leon A said:**
> it sometimes starts missing PING responses and eventually get to the point of failing, either due to "destination host unreachable" or "sendmsg: no buffer space available"It was a Google search based on this last error message that led me to the solution for my own problem. If yours is due to a similar cause, then the same solution may work for you.

Specifically, on low powered and/or older machines, the TCP buffer size must be increased and other TCP parameters must be tweaked to make up for the poor performance of the underpowered components. The relevant link is: [http://www.cyberciti.biz/faq/linux-tcp-tuning/](http://www.cyberciti.biz/faq/linux-tcp-tuning/)

Try making the same changes that I made to see if these have any effect. Since my whole line of enquiry started with the error code that you got:```
sendmsg: no buffer space available
```...I can only imagine that the causes of  both our problems are related. The full instructions are already contained in my thread, so I link to the relevant post rather than repeat those instructions here: [http://ubuntuforums.org/showthread.php?t=2328415&p=13511431#post13511431](http://ubuntuforums.org/showthread.php?t=2328415&p=13511431#post13511431)

The steps are easily reversed if they don't work.

---

### Post by MAFoElffen on 2016-07-01
Effective range of 802.11n is 75 feet (23 meters) with no obstructions., it would be hard pressed to fit 200 wireless deices within a 75 foot radius. Then to have 200 radios in anroow range in limitted channels, in that small of an area? If you could see radio waves, then you could see the collisions and interference of such.

I also suspect that 200 wireless deices, working at the same time, all streaming videos, through one switch/access point, to one server (with only a single NIC?) would not be bottle necked.

Then there is the leases set to 10 days:
Default value for a wireless lease is 24 hours. Let's do a math problem:
 - Lets say you are using a class C private net. That would be 255 addresses, minus one for the host NID, minus 1 for you broadcast address and minus one for your gateway address. That leaves 252 client IP's.
 - Let's say that private net only had one administrative desktop in that net, with attached shared printer, so it did not take up any other ports...
 -Lets look at a dhcp service, that as a default is initially set to handing out 50 addresses ... but you bump it up to 245 to 250.

10 days is way too long to set a lease. That means those leases are committed for 10 days Espresso stands here have hundreds of people a day. They set their lease to 3-4 hours. I would say for you, 6-8 hours. It does not take long to renew a lease.. a Lease is a convenience.

Next is whether you do streaming using UDP or TCP, but that is another consideration for streaming media.



 - If you you have 200 of the same laptops (using wireless) and have phones, (as you rsiad you were testing with)....

---

### Post by Leon A on 2016-07-06
MAFoElffen,
Sorry I may not have been clear.  We are not using >200 devices all on one system.  We've deployed identical lab kits in many schools, and each kit has only 20 computers plus the content server WAP. Most are in rain forest villages with no other wireless interference around, although we did deploy in a few schools in capital city so Ministry of Education can observe.  I've found that setting longer leases makes for faster connection each morning on bootup, and it helps us in troubleshooting as laptops retain same IP address even during school weekends and holidays (useful for pinging).
The work-arounds suggested above have helped, and the laptops with RTL chips are working reasonably well, but I'm still working on those with BCM chipset.

---

### Post by souradeep100 on 2016-07-10
I am facing the same problem with broadcomm 43142 in ubuntu 16.04. 
I have tried the following:
1)Changing the auth in router to not to use tkip
2)made the wlan mode to b/g/n .
3)Disabling ipv6 through network manager.
4)sudo apt-get dist-upgrade
5)Installing latest broadcom-sta-dkms using synaptic package mananger instead of bcmwl kernel source.
6)changing the regulatory domain to my country. 
Still the problem happens . So you can t try these steps. Then check , if the problem persists.

---

### Post by Leon A on 2016-07-11
Thanks to DuckHook and others in ubuntu forums, I have found work-around for the HP Stream 11 netbooks that use the RTL8723be wifi card, so I am going to mark this thread as resolved.  However, I still have not been able to get the other HP Stream 11s  that use the BCM43142 wifi card to work - they still randomly drop out, so I will open a new thread on the BCM machines.  Thanks everyone.

---

### Post by Leon A on 2016-07-11
These solutions seem to work for the HP Stream 11 units that use the Realtek rtl8723be wifi card, but not for those using Broadcom bcm43142.

---

