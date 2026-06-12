---
title: "Dhclient DHCP problem obtaining ip, dns"
date: 2017-02-02
forum: Networking &amp; Wireless
---

### Post by markteras on 2017-02-02
I am running Lubuntu 14.04 ARMHF. Upgraded a bunch of packages and sorta lost dhclient; doesn't obtain DHCP values automatically any more.

Log output:

The error was: 
../../../../lib/isc/unix/socket.c:2322: socket() failed: Permission denied
../../../../lib/isc/unix/socket.c:2322: socket() failed: Permission denied
Can't initialize context: unexpected error
dhcpd self-test failed. Please fix the config file.

Feb  2 09:12:16 ac100 NetworkManager[740]: <info> dhclient started with pid 1985
Feb  2 09:12:16 ac100 NetworkManager[740]: <info> Activation (wlan0) Beginning IP6 addrconf.
Feb  2 09:12:16 ac100 NetworkManager[740]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Feb  2 09:12:16 ac100 kernel: [  689.066120] type=1400 audit(1486023136.662:43): apparmor="DENIED" operation="create" parent=740 profile="/sbin/dhclient" pid=1985 comm="dhclient" family="inet" sock_type="dgram" protocol=17
Feb  2 09:12:16 ac100 kernel: [  689.087744] type=1400 audit(1486023136.692:44): apparmor="DENIED" operation="create" parent=740 profile="/sbin/dhclient" pid=1985 comm="dhclient" family="inet6" sock_type="dgram" protocol=17
Feb  2 09:12:16 ac100 dhclient: Can't initialize context: unexpected error
Feb  2 09:12:16 ac100 NetworkManager[740]: <info> (wlan0): DHCPv4 client pid 1985 exited with status 1


Thanks for any helpful suggestions!

---

### Post by SeijiSensei on 2017-02-02
Where did the copy of dhclient come from?  It's failing the AppArmor test, so it's unlikely you got it from the repositories.  If you got it from somewhere else, remove it and install the repository version.

If you did use the repositories, did you run "sudo apt-get update" before installation?  If not, do that and try again.

---

### Post by markteras on 2017-02-02
Hi, thanks for suggestion. I upgraded packages (upgradable) with Synaptic only and yeah, I did run sudo apt-get update beforehand. It did come from the repos. And in one other log I saw something about it indicatating a bug in someone's code... Dunno. Shutdown message says dhclient not running because older version is preferred. Problem is I had *not* upgraded dhclient nor dhcpcd. What I did upgrade was apparmor... Will try to downgrade things and see. 

Also, does anyone know what does it mean "dhclient not running because older version is preferred" exactly? DHCPCD itself or some other dependent package?

Well, thanks for your time.

---

### Post by markteras on 2017-02-02
Solved the problem. Apparmor downgrade was the solution. Seems like new apparmor version was messing with dhclient for some reason. Thanks.

---

