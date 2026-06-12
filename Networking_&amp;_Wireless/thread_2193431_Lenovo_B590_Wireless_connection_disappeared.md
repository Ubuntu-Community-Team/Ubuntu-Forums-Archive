---
title: "Lenovo B590: Wireless connection disappeared"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by Bob_Dennis on 2013-12-12
I was happily using a wireless connection earlier today, and (after closing down and restarting) it won't reconnect.  The router and hardware are fine--I have a dual-boot machine and I am posting this via Windows 7.  I can't find anything to scan for available networks, though I know I've seen and used that before.

What I have:  Ubuntu Studio running on a Lenovo B590, dual-boot.  Note:  The initial problem came after I had been using Ubuntu, closed down, and then restarted again in Ubuntu, so it's not a result of the dual-boot (at least I don't think so).

What I've tried:  Opening the network window from both the icon and the settings menu.  I get a list of networks I have connected to before, and can edit and delete them.  However, no list of what it can see now.  I tried turning off and on again the network connections and the wireless connections, in various orders.  When I have both of them checked (which I presume means "turned on"), and I close down and restart Ubuntu, I get a screen warning saying that there is no network connection.  I tried deleting the wireless network I want to use, in the hope that it would reappear, but no joy. 

This is not the only oddity:  in case it's relevant, my Midi sound synth also disappeared without warning ( several weeks ago) and I haven't been able to get it back. I wonder if there's a settings file that's somehow getting corrupted.   However, if they are not connected, I'm most concerned about the wireless connection.

Any suggestions, other than switch back to Windows permanently?;)

---

### Post by varunendra on 2013-12-14
The first thing I would suggest is to boot with a Live CD/USB and run 'fsck' on your Ubuntu partition. See if it reports (and fixes) any errors on the partition.

If the partition seems to be intact, no errors, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Bob_Dennis on 2013-12-14
Problem seems to have fixed itself.  I tried again to connect by wireless, didn't recognize any signals.  Then I plugged in an Ethernet cable to retrieve your script and the wireless connection immediately reappeared.  Wireless connection continues to work through several reboots after the Ethernet cable was removed.  

I tried "fsck" on the partition that had "ext4" format, got clear result.

Is it still useful to get the report from the script you suggest?  I have zero idea what plugging in an Ethernet cable might have done, or whether the problem has fixed itself permanently.

---

### Post by varunendra on 2013-12-15
Most probably (and I am 99% sure) this is a DHCP lease issue.

You may be having difficulty in getting IP address from your DHCP (in the router) via wireless. Last time you rebooted, the lease might have expired and it couldn't get a new lease (or renewed IP) from the DHCP on next boot. As soon as you connected via cable, it got its new lease and so is connected again.

If that's right, you may face the same issue as soon as the current lease is expired again (you may log into your router's admin console to see how long the current lease is valid for).

Also, if that is (was) indeed the problem, it is a bit difficult to determine whether the problem was internal or in the router.

Usually the best workaround (not a fix) to such issues in small networks, is to assign manual IP instead of depending on the DHCP.

The wireless_script report may not offer much insight into this, but it may give us some clues to see if we can try something to optimize the networking so that the problem doesn't occur again.

---

### Post by Bob_Dennis on 2013-12-27
Thanks very much.  It's probably enough to know that i might have to renew the lease.

---

