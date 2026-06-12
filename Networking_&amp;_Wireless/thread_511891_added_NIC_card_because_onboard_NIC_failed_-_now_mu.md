---
title: "added NIC card because onboard NIC failed - now must ifup after boot for dhcp"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by jcoles on 2007-07-28
As the title says, I added a NIC card to my system after my onboard NIC failed. Now I must ifdown and then ifup after boot to get my address via dhcp.

My new NIC card is eth1, even though the onboard NIC is disabled in the BIOS. ifconfig reports only lo and eth1, so I assume eth0 is inactive.

Based on information in other threads, I added the following to the /etc/network/interfaces file:
auto eth1
iface eth1 inet dhcp

No change. I also changed the /etc/iftab file to reflect the new NIC by changing the MAC address and changing eth0 to eth1:
eth1 mac 00:80:C6:E7:10:2A arp 1 

Again no effect. I restarted the machine between these changes. Once I get an IP address, I can stop and start the networking service with no problem but if I restart I have no IP address until I run "ifdown eth1" followed by  "ifup eth1".

Does anyone have any idea what I might have missed?

---

### Post by noob12 on 2007-07-28
Did you remove eth0 from /etc/network/interfaces?

To what extent is eth0 really dead?  Is it showing up in **lspci** or **lshw -C network** listings?
Is it still showing up in **ifconfig -a**

I would try doing a manual ```
sudo /etc/init.d/networking stop
```
followed by ```
sudo /etc/init.d/networking start
```
and watch the output for clues in the errors.

---

### Post by noob12 on 2007-07-28
Sorry, I didn't see that you had disabled the onboard NIC in the BIOS.

Another clue might be found in ```
dmesg
``` after boot.

---

### Post by jcoles on 2007-07-29
If I run

[FONT="Fixedsys"]sudo /etc/init.d/networking restart[/FONT]

after boot, the problem is solved. The NIC does DHCPDISCOVER and receives its IP. This tells me there cannot be anything wrong in configuration files such as /etc/network/interfaces. 

The networking script is supposed to run during boot-up. Why doesn't it establish the network then? I see nothing in the dmesg or messages log that suggests failure, so I wonder if somehow the script is no longer being run. 

I suppose I could add the networking restart command to rc.local. But I don't like resorting to kluges for basic functionality. 

Thanks for the suggestions anyway.

---

### Post by noob12 on 2007-07-29
I'm not suggesting any kluges, I'm just trying to help diagnose the problem.  Then hopefully there is a clean fix.

The **/etc/init.d/networking** script should get run at boot provided you have the symlink to it in **/etc/rcS.d**.  That's an "S" not a five (5).  You should see
> 
% ls -l /etc/rcS.d/S40networking 
lrwxrwxrwx 1 root root 20 2007-07-11 02:03 /etc/rcS.d/S40networking -> ../init.d/networking


Unless you had removed it I don't see any reason why it wouldn't be there, and it should get run at startup.

When you boot initially does **ifconfig -a** show that the interface is UP but has no assigned address?  This would be another clue that /etc/init.d/networking had run but DHCP had failed.

Log messages from dhclient can normally be found in **/var/log/daemon.log** and **/var/log/syslog** (but not /var/log/messages).

What may be happening is that the device is taking a bit longer to establish link state when the driver is first loaded and this is preventing DHCP from working.  The timeout is configured in **/etc/dhclient3/dhclient.conf**; (man dhclient.conf for the full story).

You may be able to get more diagnostics at boot by setting **VERBOSE=yes** in **/etc/default/rcS**.  Normally when /etc/init.d/networking is run at boot you don't see the console output of ifup.

Don't have any more ideas for you.  Good luck.

---

### Post by jcoles on 2007-08-04
Perhaps this daemon.log entry is a clue:

Aug  4 06:16:28 thispc NetworkManager: <information>^Ieth1: Driver 'tulip' does not support carrier detection. ^IYou must switch to it manually. 

Not sure how to "switch to it manually". Somehow, "sudo service networking restart" executed after boot must accomplish this. 

Noob's point about a link to /etc/init.d/networking in /etc/rcS.d checks out. But there are no dhclient messages in the log until I restart networking either manually or in rc.local.

---

### Post by walkerk on 2007-08-04
> **jcoles said:**
> Perhaps this daemon.log entry is a clue:

Aug  4 06:16:28 thispc NetworkManager: <information>^Ieth1: Driver 'tulip' does not support carrier detection. ^IYou must switch to it manually. 

Not sure how to "switch to it manually". Somehow, "sudo service networking restart" executed after boot must accomplish this. 

Noob's point about a link to /etc/init.d/networking in /etc/rcS.d checks out. But there are no dhclient messages in the log until I restart networking either manually or in rc.local.

It does seem to be able to detect the card automatically. I believe Ralink cards are similar (as they require a manual ifup after boot): you could right a simple script to do this. (I guess you might not want to rely on this method..)

**network.sh**
```
#!/bin bash
sudo /etc/init.d/networking restart
```

change it to executable:
```
chmod +x network.sh
```

now you can add it to System>Preferences>Sessions


or even appending the following to your rc.local: (might do the trick)
```
sudo /etc/init.d/networking restart
```

---

