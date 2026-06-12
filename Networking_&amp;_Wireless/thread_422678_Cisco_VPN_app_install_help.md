---
title: "Cisco VPN app install help"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by jester805 on 2007-04-25
I'm a Linux newbie and dual-booting FeistyFawn & XP Pro on my laptop.  I downloaded the Cisco VPN client from Cisco's website.  The file I got is:  **vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz**

I extracted the files to a new folder on my desktop.  When I try to run the **vpn_install **shell script, I use the default parameters, but it always comes back with this error:

> Making module
make -C /lib/modules/2.6.20-15-generic/build -I/usr/src/linux-headers-2.6.20-15/include SUBDIRS=/home/dnolan/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/dnolan/Desktop/vpnclient/linuxcniapi.o
/home/dnolan/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/dnolan/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dnolan/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Any ideas?  Should I even be running the vpn_install script?  Am I going about this all wrong?

Thanks.

---

### Post by Metacarpal on 2007-04-25
Their install script really doesn't like the current kernel.  I ran into this problem myself.  I recommend installing network-manager-vpnc and vpnc from the repositories.

Once you get them both installed, you'll be able to left-click your Network-Manager applet, and find a VPN Connections sub-menu.  From there, click Configure VPN, then Add.  I think you'll be pleased with the results.

You can import existing configuration files, or enter the settings manually.  (If you need manual settings in addition to your imported config, there's an easy-to-find tab marked "Optional" to do it.)  Let me know if you need any additional tips!

---

### Post by jester805 on 2007-04-25
That worked great, but it drops my connection after about 1 minute.  Any ideas on that?

Thanks for the help!

---

### Post by Metacarpal on 2007-04-25
That's odd.  Mine stays up indefinitely.  Post it up in a new thread, see if anyone has any ideas.

Ooh - just checked Launchpad; are you using Ubuntu or Kubuntu?  Looks like there's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/44290") with the knetworkmanager implementation of this, at least.  Don't know if it affects the Gnome version or not.

---

### Post by jester805 on 2007-04-25
Here is what was in the error logs when I got disconnected.  Where it says "laptop" that's my Ubuntu box that I'm connecting from:


> Apr 25 21:18:01 laptop vpnc[12402]: connection terminated by dead peer detection

Apr 25 21:18:01 laptop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 4 -> 6. 

Apr 25 21:18:01 laptop NetworkManager: <information>^IClearing nscd hosts cache. 

Apr 25 21:18:01 laptop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

Apr 25 21:18:01 laptop avahi-daemon[4740]: Withdrawing address record for 192.168.5.6 on eth1.

Apr 25 21:18:01 laptop avahi-daemon[4740]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.5.6.

Apr 25 21:18:01 laptop avahi-daemon[4740]: Interface eth1.IPv4 no longer relevant for mDNS.

Apr 25 21:18:01 laptop avahi-daemon[4740]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.5.6.

Apr 25 21:18:01 laptop avahi-daemon[4740]: New relevant interface eth1.IPv4 for mDNS.

Apr 25 21:18:01 laptop avahi-daemon[4740]: Registering new address record for 192.168.5.6 on eth1.IPv4.

Apr 25 21:18:02 laptop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.vpnc): could not stop connection 'vpnserver' because service was 6.

---

