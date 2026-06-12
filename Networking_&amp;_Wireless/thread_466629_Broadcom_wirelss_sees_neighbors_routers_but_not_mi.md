---
title: "Broadcom wirelss sees neighbors routers but not mine"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by steveyeager on 2007-06-06
I have an HP Pavilion dv6113us which uses a broadcom 4311 wireless card.  I am running the Ubuntu 7.07 live cd and used fwcutter to extract the required files from at least 2 versions of the broadcom windows drivers.  Applying these files to the appropriate directories, going into manual configuration of my network connections, disabling the wired card and accepting gets my wireless light to turn on and function.  In roaming mode, I can see about 6 of my neighbor's routers, but I cannot see mine.  

Now, I have two other computers in my house.  Both are using SMC wireless usb adapters and both see the router and connect correctly.

The router is a D-Link 614+.  I am using WEP 64-bit hex as open. 

Again, my other two computers connect just fine.  However, if I enter these settings manually, it still failes to see or connect to my router.

What other settings can I try?  Why can I see so many other routers and not mine?

Please help.

---

### Post by Atomic Dog on 2007-06-06
Well I'll ask the obvious... the SSID is being broadcast right?

You manually entered the info in Network Manager and it still wouldn't connect... Weird, but at work one wireless Linksys A&G seems to disappear too so I am not doubting this is happening to you.

---

### Post by steveyeager on 2007-06-07
I did enter the information directly, just as I had for my other wireless computers and they worked.  However, my notebook only sees the router settings and never detects the router.

I do not know what setting on my router actually broadcasts the ssid.  I can only assume it is broadcasting it.  How can I verify that?

My D-link 614+  supports a and b speeds.  It does not support g.

Any other thoughts?

---

### Post by kevdog on 2007-06-07
First I dont know what your interface name is -- possibly wlan0 or eth0??

Whatever the interface name, try
iwlist *interface name* scanning

This should tell you if your card detects your home network whether the SSID is broadcast or not.

For example
iwlist eth0 scanning

---

### Post by steveyeager on 2007-06-08
I ran iwlist and again saw my neighbors routers but not mine.  So, how can alter/verify my router settings to broadcast the ssid?

---

### Post by cro on 2007-06-08
I had this problem myself, and here's how I solved it:

This post:
[http://ubuntuforums.org/showpost.php?p=2594263&postcount=6](http://ubuntuforums.org/showpost.php?p=2594263&postcount=6)

and this page
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

"I followed this very carefully, except that I used the latest 1.43 ndiswrapper instead of the 1.35 version documented in the guide."

(And then I updated the WIKI page with the 1.43 details)

Unfortunately this setup does NOT work under the -16 kernel revision, only the -15.

---

### Post by steveyeager on 2007-06-23
I am not looking to use ndiswrapper.  I have the native (if you can call it that) driver working, it just sees other routers and not mine.  I need to identify why it cannot see mine and if I need to alter my driver, try another driver, or alter my router (or get another router).

Someone else has to have had this problem before and solved it without the ndiswrapper.

---

### Post by p_quarles on 2007-06-23
Most routers have an administrative interface that works with your web browser. Use one of the computers that can connect to the router, find out the router's LAN IP address, and type that address into your browser. Check to make sure that SSID broadcasting is on. It'll be in "Wireless Settings" or whatever the equivalent is.

---

### Post by steveyeager on 2007-06-26
I was able to verify, after much searching through the many pages of configurations, that I am in fact broadcasting my ssid.

So, how do we diagnose this further?

---

