---
title: "Did a recent update break Network Manager?"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Dralt on 2007-06-09
3 days ago, Network Manager stopped working for me...

This is what I found in my most recent boot syslog:

```
Jun  9 13:11:22 Mario NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Jun  9 13:11:22 Mario NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Jun  9 13:11:22 Mario NetworkManager: <information>^IDeactivating device eth1. 
Jun  9 13:11:22 Mario avahi-daemon[5084]: New relevant interface eth1.IPv4 for mDNS.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.200.
Jun  9 13:11:22 Mario avahi-daemon[5084]: New relevant interface eth0.IPv4 for mDNS.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Network interface enumeration completed.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Registering new address record for 169.254.7.129 on eth1.IPv4.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Registering new address record for 192.168.1.200 on eth0.IPv4.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Registering HINFO record with values 'I686'/'LINUX'.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Withdrawing address record for 169.254.7.129 on eth1.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.129.
Jun  9 13:11:22 Mario avahi-daemon[5084]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  9 13:11:22 Mario NetworkManager: <WARNING>^I nm_hal_deinit (): libhal shutdown failed - Connection is closed 
Jun  9 13:11:22 Mario NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 11.  Generating backtrace... 
Jun  9 13:11:22 Mario NetworkManager: <information>^ISuccessfully reconnected to the system bus. 
Jun  9 13:11:22 Mario NetworkManager: ******************* START **********************************
Jun  9 13:11:22 Mario NetworkManager: (no debugging symbols found)
Jun  9 13:11:22 Mario NetworkManager: Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Jun  9 13:11:22 Mario NetworkManager: (no debugging symbols found)
Jun  9 13:11:22 Mario last message repeated 4 times
Jun  9 13:11:22 Mario NetworkManager: nabled]
Jun  9 13:11:22 Mario NetworkManager: [New Thread -1212163632 (LWP 5066)]
Jun  9 13:11:22 Mario NetworkManager: [New Thread -1212167280 (LWP 5079)]
Jun  9 13:11:22 Mario NetworkManager: (no debugging symbols found)
Jun  9 13:11:22 Mario last message repeated 12 times
Jun  9 13:11:22 Mario NetworkManager: 0xffffe410 in __kernel_vsyscall ()
Jun  9 13:11:22 Mario NetworkManager: ******************* END **********************************
J
```

"segmentation fault" does damage user confidence, you know.

Synaptic's log shows I installed and uninstalled gxine.

I also installed the latest kernel update (yesterday), but I had that same problem before that.

Anyone saw the same thing?

---

### Post by Dralt on 2007-06-09
Further diagnostic shows nm-applet just hangs and never print anything out:

```
@Mario:~$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
@Mario:~$ killall nm-applet
@Mario:~$ nm-applet

```

I'm kind of pissed off.

---

### Post by Dralt on 2007-06-09
Didn't say so previously, but this configuration worked great for weeks...this is since I installed Feisty Fawn...

---

### Post by Dralt on 2007-06-09
I reinstalled all avahi packages, all hal-related package and all network manager-related packages. Still no dice.

I am running out of ideas...

---

### Post by Dralt on 2007-06-10
So, it turns out NetworkManager will crash at random on start-up.

I went about and started it by hand several times in a row using:

```
sudo NetworkManager --no-daemon
```

And after a few rounds, it finally went through without crashing...

Man, I am so mad. Everything has been working great on that machine since Feisty was released. Before that, everything worked great with Dapper for more than a year.

Now, I installed a couple of official updates and it all goes to hell.

It reminds of Windows, which also loses features over time.

Can anyone help me get to the bottom of this or should I consider buying a Mac?

---

### Post by Dralt on 2007-06-10
I also with the kernel release before last...and the problem is the same...

From the logs, it seems something went wrong in the way NetworkManager interacts with dbus or hal.

I still have no idea how to fix this.

---

### Post by regal_dunce on 2007-06-13
I can at least confirm your problem.  I spent forever trying to get my wireless to work with Fesity (worked fine with edgy) and now since the update I can't use wireless in the newest kernel either.  If I boot to the previous kernel from my grub menu, then everything works fine...

If you find a fix to this, please post!

---

### Post by cwhill on 2007-06-15
Uggg...I agree and confirm this! Everything was perfect prior to this upgrade now it takes forever to get logged in. My system is able to get an IP but it hangs for almost 2 minutes on log in. Even Vista does a better job at not hosing a major app like this...(OK that was uncalled for I'm venting)

---

### Post by cwhill on 2007-06-15
I tried reverting to a previous kernel and it still didn't work.

---

### Post by Meserias on 2008-01-18
[SIZE="2"][SIZE="3"]After a recent update I have NO network connection in my Ubuntu 7.10. Something its verrrryy BAD with latest OFFICIAL updates for **[COLOR="Red"]AVAHI[/COLOR]**
If someone sees this message please post a solution here in these forums.
TESTING it's very important please so UBUNTU Team PLEASEEE TEST before releasing a update...at least let the network functionality untouched.[/SIZE][/SIZE]  :confused::mad::(](*,)[-o<:^o

---

