---
title: "Intel 4965AGN problem-Ubuntu Gutsy 7.10"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by antonis9891 on 2008-02-20
Hi. As the title says, I use ubuntu 7.10, but I can't connect to my wireless network. I know that the driver for this card are included in Ubuntu 7.10. Network Manager can't see my network, so I clicked on "Connect to other wireless network" and I typed the ssid and I clicked connect with no result. Also I tried manual configuration, and again nothing. I tried with wap2 security, and with no encryption.
Thanks

---

### Post by antonis9891 on 2008-02-20
I have tried wicd but it says no wireless networks found. The driver is recognized because when I go to connection information in Network Manager, it says driver iwl4965. The router is working properly, as I it works perfect when I'm in windows. Please if somebody knows.....

---

### Post by jblackthorne on 2008-02-20
I just posted another thread regarding 802.11a issues.  :

[http://ubuntuforums.org/showthread.php?t=703049](http://ubuntuforums.org/showthread.php?t=703049)

Though, 802.11g has worked fine for me.  I can also confirm that iwlwifi works on 802.11g with WPA-PSK TKIP, and on an Atheros-based Access Point too.  Which type of network are you trying to connect to (802.11a,/b/g/n)?  Assuming you are trying to connect to 802.11g, here are a few things to try.

1.Validate your network adapter is being identified: type “sudo lspci -vv” (that is two "V" chars)
	
	You should see something like: 
	02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0


2.Validate the iwlwifi driver is working
	* type “sudo iwconfig wlan0”.  That should show the current state of the wlan0 device

3.Try a scan.  Type 'sudo iwlist wlan0 scanning'.  You should see a list of available networks in the area.

Do all 3 of the above work ok? Oh, by the way, the “WICD” application does not help because it does not include any alternative drivers to the iwlwifi.  WICD is certainly a nice alternative to nm-applet, but it won't solve your problem.

---

### Post by antonis9891 on 2008-02-21
Thanks for the answer. I typed the first command, and I saw sth like that, the first three lines are similar. Typed also the second command and I received the connection information. Of course I had signal level 0 etc. When I tried to run the last command, it returned: "wlan0     Failed to read scan data : Resource temporarily unavailable"

---

### Post by jblackthorne on 2008-02-21
Please post your kernel ring buffer:

type: sudo dmesg|grep wl

also, please provide kernel details:

type: uname -a

---

### Post by Kriss.no on 2008-02-22
I have the same problem with a Lenovo Thinkpad X61 on only one location. At my office the machine works flawlessly on wlan, but at home I have the exact same problem as the thread starter. The funny thing is that I have three machines with windows Vista and XP and they all connect immediately.

I have also tested with a Lenovo Thinkpad T60 with Ubuntu 7.10 and this one had the same problems. The scary thing is that both computers works everywhere else but not at home. What info do you guys need? 
Ubuntu 7.10 with kernel 2.6.22-14-generic is being used.

---

### Post by antonis9891 on 2008-02-22
kernel ring buffer:
[   18.776000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   18.776000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   18.776000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   19.152000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   19.152000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   35.068000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Kernel details:
Linux antonis-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by jblackthorne on 2008-02-22
So far, all your tests look completely normal in that the driver is 1.1.0 and installed correctly.   However, your kernel ring buffer proves that there never was any connect attempt to the driver.  My guess is that since nm-applet has not connected before, it is not even trying to connect now.   Here is what I would suggest trying next:

1.Upgrade the firmware
1.Disclaimer:  I am not a linux developer and found this procedure by searching the Ubuntu launchpad support forum.  I followed this procedure myself and it has solved a number of issues I was having .  So far, I can only confirm this has worked great for me on kernel 2.6.22-14-generic.  Since you have the exact same driver and kernel setup that I do, I think it is probably safe to try out.

Upgraded the Intel 4965 firmware:


&#8226; download the firmware (iwlwifi-4965-ucode-4-44.1.20) - [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz)

&#8226; Copy both of the following files to a backup directory: 



./lib/firmware/2.6.22-14-generic/iwlwifi-4965.ucode

./lib/firmware/2.6.22-14-generic/iwlwifi-4965-1.ucode



&#8226; extract the contents of - iwlwifi-4965-ucode-4.44.1.20.tgz

&#8226; change directory into the extracted folder

&#8226; cp iwlwifi-4965-1.ucode iwlwifi-4965.ucode

&#8226; cp iwlwifi-4965* /lib/firmware/$(uname -r)/

&#8226; reboot

 


2.Retest the wireless connectivity with an open wireless network on 802.11g.

&#8226; after reboot:
1.Setup your 802.11g network so that it is open with no encryption for now.  This just elinates other things that can be potentially wrong for now.

CRITICAL NOTE: Before proceeding, ensure that the Ethernet cable is disconnected.  Networking is prioritized such that if an ethernet connection exists, it will not even attempt to connect with wireless.

2.click the nm-applet (Network Monitoring applet in the top bar)
3.Click &#8220;Connect to other wireless network&#8221;
4.Choose your wireless netowork
5.After the flashing lights stabalize or go out, check for errors with "sudo dmesg|grep wl"
6.If that does not work, please provide those dmesg lines back in this post.

---

### Post by antonis9891 on 2008-02-23
It didn't work again. Here is the output:
[   19.472000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   19.472000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   19.484000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   19.844000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   19.844000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   76.584000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  267.164000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by Kriss.no on 2008-02-24
*bump*

---

### Post by jblackthorne on 2008-02-25
I have been slow in responding because I have been doing quite a bit of research into the Intel 4965 chipset and related drivers.  I have to tell you, I am really frustrated and confused here.  First, let me start with the bad news.  Your dmesg output after attempting the test I gave you tell us that:

* Your iwlwifi and mac80211 subsystem are working fine.  This is not a problem with Gutsy. 
* Your wireless card is not even identifying your ESSID (wireless network name).  Steps to wireless connection are:
1.Identification
2.Association
3.Authentication
4.Address reservation (if applicable)
5.Completion

Your dmesg buffer shows that you are not even completing steps 1 or 2.  Hence, this is not a WPA/WEP (wpa_supplicant) related issue.  Steps 1 or 2 completing would give you a dmesg log of something like this:

[ 1836.761858] wlan0: Initial auth_alg=0
  (that line shows successful association and acknowledgment of the wireless 802.11g network.

So what does that mean?  Well, let's start with the easy stuff.  

* Please post details of your router, brand, model. 
* Please figure out which chipset you have.  You can look that up here: [http://wiki.openwrt.org/TableOfHardware?action=show&redirect=toh](http://wiki.openwrt.org/TableOfHardware?action=show&redirect=toh)

Try the following:

* change your ESSID to something short (8 chars or less) and in all lower case with alpha chars and numbers only.  Special characters and spaces can be problematic for some drivers.
* Ensure that all encryption is disabled.  Yes, I asked this before, but just be sure
* execute “sudo iwlist scan” about 8 times with 30 second intervals in between.  Please respond, do you see anything at all?  Do you see your ESSID listed?

If the above still does not work, then I am afraid we have bad news..your router may not be compatible with the Intel 4965 Linux driver current revision.

I think I mentioned before that I am personally invested in this driver issues because I have been having issues with my personal access point too in that my 802.11a ESSID is not visible or usable.  My access point is old, but a “Wi-Fi Certified” Atheros chip set based access point.  Being that Intel and Cisco created the “Wi-Fi Certification” standard, my Dlink DWL-7100 a/b/g access point should work.  

Here are some interesting notes though.  Dual boot my same laptop with Vista, I can connect to the 802.11a network.  However, and a BIG note, is that the connection speed tops out 280kbits/sec standing 3 feet from the access point.  That is absolutely horrible and unacceptable performance.  So to summarize my test, neither the latest Windows drivers direct from Intel nor the Linux driver from Intel work with my access point correctly. 

With that said, I have been interested to see if a later release of the Linux driver might be more successful.  Gusty ships with iwlwifi driver version 1.1.0.  I tried the following:

* Loaded up Hardy Heron Alpha 5 which ships with iwlwifi 1.2.0.  Same result, no luck in connecting to 802.11a.
* Downloaded the latest Intel drivers for mac80211, ucode, and iwlwif driver 1.2.25.  Compiled a custom kernel and tested.  I have the x64 kernel deb if any one wants it. Result: Still does not connect to my Wi-Fi certified 80211a access point.

Considering the whole picture, my assertion is that Intel is probably not prioritizing backwards compatibility with older technology, Wi-Fi certified or not.   Hence, I have now give up and ordered a Dlink DIR-655 router.  The 655 is a reasonably priced and very highly rated router in case you would like a recommendation.  Any way, I wish I had better news to report.  Though, I have exhausted every path I can think of.  Good luck on your final tests.  I hope your outcome does not result in a hit to your wallet too.

I welcome suggestions or feedback from any one else.  Any thoughts?

---

### Post by jblackthorne on 2008-02-25
Kriss.no. Please check this thread from beginning to end.  Try each test and post the requested results.  Maybe we will be luckier with you. :)

---

### Post by antonis9891 on 2008-02-26
Thanks for your help. My router is Linksys WAG200G: [http://www-au.linksys.com/servlet/Satellite?pagename=Linksys/Common/VisitorWrapper&c=L_Product_C2&cid=1172712873708&childpagename=AU/Layout]("http://www-au.linksys.com/servlet/Satellite?pagename=Linksys/Common/VisitorWrapper&c=L_Product_C2&cid=1172712873708&childpagename=AU/Layout")
I can't find this router in the site you mentioned. So, I have changed the ssid to net (I think that is very simple). No encryption, and I executed iwlist scan, got this message the first time: wlan0     Failed to read scan data : Resource temporarily unavailable
and the second, third time I tried, i got this:
wlan0     Interface doesn't support scanning : Network is down
Thanks again

---

### Post by jblackthorne on 2008-02-26
> **antonis9891 said:**
> Thanks for your help. My router is Linksys WAG200G

LOL..well, according to the LinkSys spec sheet, your WAG200G is "Wi-Fi" Certified.  So, it should work right away with Intel's chips, right?  Though, the funny thing is that Wi-Fi Alliance does not confirm Linksys's assertion.  Here is the complete list of all Linksys products and yours is not on the certification list:

[http://certifications.wi-fi.org/wbcs_certified_products.php?search=1&advanced=1&lang=en&filter_company_id=121&filter_category_id=&filter_subcategory=&filter_cid=&date_from=&date_to=&x=35&y=12](http://certifications.wi-fi.org/wbcs_certified_products.php?search=1&advanced=1&lang=en&filter_company_id=121&filter_category_id=&filter_subcategory=&filter_cid=&date_from=&date_to=&x=35&y=12)

That kind of looks funny to me.  Your gateway/access point came out just in 2006.  Still, I am kind of wondering if the simple answer here is that maybe your wireless chipset is not supported by the iwl4965 driver or chipset.  

- Have you dual-booted into any other OS and connected successfully with that machine to that wireless access point?  If so, what kind of throughput did you get?

> **antonis9891 said:**
> 
wlan0     Interface doesn't support scanning : Network is down

Hmm.. ok, let;s just be sure that the driver is working and re-validate all the things that can be wrong once more.  Please try to following:

Validate the drivers are installed by entering the following in a console:
sudo modprobe mac80211
sudo modprobe iwl4965

Both of those commands should execute with no return messages.  (No messages means that the drivers loaded or are loaded successfully).  If you get any messages back at all, please post them.

Next, let's manually bring your wireless up and down.  Enter the following:

sudo ifconfig wlan0 down (that should return multiple blank lines, but no errors)
ifconfig (wlan0 should no longer appear in the list)
sudo ifcofnig wlan0 up (again, you should see no messages)
ifconfig (wlan0 should now be back in the list)

Next, validate network configuration:

* Left-Click the Network Manger applet in the toolbar and choose "Manual Configuration"
* Validate "Wireless Connection" is in the list and that "Roaming Mode" is enable
* Close network settings

* Left-Click the Network Manger applet in the toolbar and choose "Connect to Other Wireless Network" and enter your network settings.
* The Light rotation should start and your laptop is now trying to find and connect to your wireless.

If you get all the way to here, then your iwlwifi drivers are working fine.  Well, at least as fine as the 1.1.0 version can.

If you want to try one more thing, you can try downloading the Hardy Heron Alpha 5 Live CD and booting up with that.  Just boot it up, but there is no need to install anything.  The live cd should detect the 4965 and load up the correct drivers.  Like I mentioned in a previous post, it ships with drivers version 1.2.0.  This is the easiest way you can test new drivers without having to compile code or install new kernels.  If by some amazing chance Hardy Heron's driver's work, then I can give you a 64bit kernel pre-loaded with iwlwifi drivers 1.2.5.   Though, I have been running 1.2.5 for a few days now and have not seen any difference at all.  I still cannot access my 802.11a, nor has my connection speed to my older access point improved at all.  I am just counting down the days before my new DIR-655 arrives in the mail to fix my own issues.

If Hardy Heron Alpha 5 still does not work, then I think we are right back to the fact that your Wireless Access Point is not compatible with your laptop chipset.  You could keep the WAG200G as a ADSL modem, but disable the wifi radio and add on a new access point.  That would be the lest expensive upgrade path I can suggest.

Good luck, and please post back your results.  I am curious to see how you do.

---

### Post by antonis9891 on 2008-02-27
So, here are the results. Firstly, yes, this router works with vista. I have dual boot Vista-Ubuntu. I followed the process for the drivers, and all seem to be ok. No errors with modprobe commands, and I succesfully brough my network up and down. I downloaded the live cd, but the problem remains. Neither that saw my network. I have to mention that this network connection worked perfectly with opensuse 10.3, but when I installed nvidia drivers it had problem too.

---

### Post by SiriusTux on 2008-03-09
I had the same problem with the Toshiba Tecra wireless card 4965AGN connecting to an old D-Link AP, so the only solution is to change the AP........:(

---

### Post by muddyh2o on 2008-03-11
same problem on an hp 8710w

---

### Post by jblackthorne on 2008-03-11
Just an update for any one having problems with iwlwifi drivers on the 4965 chipset:

* The DLink DIR-655 Router works pretty well on the standard 1.1.0 driver included standard in Gutsy.  I get 2.5 - 3 megabytes/sec sustained download rate while using WPA2 with AES encryption.  That is much much better than my older access point.  If you are considering upgrading your current router, this one is not bad

* Even with the positive rate noted above, the iwlwifi driver is only connecting at 802.11g and refuses to connect at 802.11n.  This is a known driver bug Intel seems to be working on.  Windows Vista on the same machine connects to the DIR-655 at full 802.11n rate and can download at a sustained rate of 8megabytes/sec.  That is over double the connection rate in Linux.

Summary: I hate to be negative, but I am very disappointed in Intel's development quality.  There is no excuse for the Windows drives to be so much better than the Linux drivers.  In fact, I am baffled as to why this late in development Intel still has over 61 bugs open on the iwlwifi drivers:

[http://bughost.org/bugzilla/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=iwlwifi&content=n](http://bughost.org/bugzilla/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=iwlwifi&content=n)

Any way, Gutsy patrons, we are stuck waiting driver updates shipped in Hardy to provide more stability and better access point support.

---

