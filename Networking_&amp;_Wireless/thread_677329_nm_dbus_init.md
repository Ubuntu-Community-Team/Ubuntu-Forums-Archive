---
title: "nm_dbus_init"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by diomedesxx on 2008-01-24
Hello, I am running Ubuntu 7.10. After a fresh install I installed the driver for my Linksys WUSB54G for my adapter to work, and blacklisted the old adapter. Every now and again, after around 14-18 hours, my network drops...I can't tell if I can connect to other computers on my LAN or not, as I haven't set up a samba server. The big problem, though, is when I go to reboot, I get the following errors:
```
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
NetworkManager: <WARN> nm_dbs_init(): nm_dbs_init() could not get the system bus. Make sure the message bus daemon is running
```

The computer will simply sit there from there and and will not finish the sshutdown. Sometimes I can CTRL-ALT-DEL and for the reboot to finish, but every two to three reboots I have to flip the switch. See attachment, I have unsteady hands, hence the blur.

update: In the past 6 or so hours, I've had my network drop at least 9 times, 3 of which I had to hard reboot. If I'm lucky, I'll get around 50MB of transfer before it dies.

---

### Post by mlapaglia on 2008-04-15
I've got the same issue now with the latest hardy.

---

### Post by md2017 on 2008-04-18
As have I

---

### Post by tzd on 2008-06-01
Signing onto this one as well. Although, I never tried with reboot but it comes up on shutdown for me. 
Eventually it shuts down so I don't have to use ctrl+alt+del.

I do get the same messages though which should indicate on something's wrong?
[B]
UPDATE:[/B] I've tried the "-i" in halt file fix which unfortunately didn't help at all.
I'm on a fresh install of Kubuntu Hardy 8.04.

---

### Post by geoffree on 2008-06-01
I get the same message but my system doesn't hang.  I'm running Hardy on an IBM Think Centre.  Can we get some expert advice on this thing?  Apparently a lot of people get the same error message.

geoffree

---

### Post by vadivelcamp on 2008-06-02
I also have the same problem with Hardy heron, Moreover, most of the time my xserver is not starting but crashing and it stays in a blank screen forever. I am forcefully rebooting it with the power button. To solve this is am booting in recovery mode and doing xfix and then resuming the booting process. But this workaround does not work always. :( please suggest how to fix this.

---

### Post by vikramaditya on 2008-06-02
Same here (Hardy), although the system doesn't hang or anything. I snapped a photo of the screen and it reads thusly . . .

>  * Checking battery state. . .				[ OK ]
  * Running local boot scripts (/etc/rc.local)			[ OK ]
NetworkManager:  <info>  Caught terminiation signal

NetworkManager:  <debug>  [1212422054.837168]  nm_print_open_socks ( ) :  Open Sockets
List:

NetworkManager:  <debug>  [1212422054.837436]  nm_print_open_socks ( ) :  Open Sockets
List Done.

NetworkManager:  <info>  Deactivating device eth0.

NetworkManager:  <WARN>  nm_hal_deinit ( ) : libhal shutdown failed - Connection is
closed

NetworkManager:  <WARN>  nm_debus_init ( ) :  nm_debus_init ( )  could not get the system
bus.  Make sure the message bus daemon is running!

NetworkManager:  nm_debus_signal_device_status_change:  assertion 'cb_data->d
bus_connection'  failed

NetworkManager:  nm_debus_signal_device_status_change:  assertion 'cb_data->d
bus_connection'  failed

NetworkManager:  nm_debus_signal_device_status_change:  assertion 'cb_data->d
bus_connection'  failed

NetworkManager:  <WARN>  OMG:  Ur so, like, totally screwed!

Note that the word "termination" in line 3 is misspelled, just as it is in the actual screen.  Also, I was unable to resist fabricating that last line. :)

Perhaps relevant, the issue did not exist for me until I installed then uninstalled the dreadful kde 4.0 - I'm pretty sure I ripped out every scrap of it, but maybe there's some elusive vestige hanging on and causing the network manager error.  At any rate, there does not seem to be a user-friendly fix for it.  Can we get a guru to spoonfeed us a solution, please? :)

---

