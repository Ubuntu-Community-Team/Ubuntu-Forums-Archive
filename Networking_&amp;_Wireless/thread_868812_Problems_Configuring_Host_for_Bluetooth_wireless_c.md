---
title: "Problems Configuring Host for Bluetooth wireless connection"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by eletha on 2008-07-24
hey everyone, 

I'm trying to set up a wireless network using bluetooth but I'm a newbie at network config, though I've spent a lot of time on these mailing lists reading advice and instructions. I can bring up my PC's Bluetooth device with hcitool. I can also bring up the BT device with hcitool on my client (gumstix). But they do not recognize each other. And my "pand" commands return nothing and in the syslog I get the following messages when trying to connect:

<b>Syslog</b>
Jul 24 08:58:36 ubuntu1 dhcpd: Not configured to listen on any interfaces!
 Jul 24 09:17:50 ubuntu1 smbd[30120]: [2008/07/24 09:17:50, 0] auth/auth_util.c:create_builtin_administrators(792)
Jul 24 09:17:50 ubuntu1 smbd[30120]:   create_builtin_administrators: Failed to create Administrators
Jul 24 11:07:18 ubuntu1 kernel: [11564.352000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Jul 24 11:07:19 ubuntu1 hcid[30885]: Bluetooth HCI daemon
Jul 24 11:07:19 ubuntu1 pand[30887]: Bluetooth PAN daemon version 3.19
Jul 24 11:07:19 ubuntu1 pand[30887]: Bind failed. Permission denied(13)
Jul 24 11:07:19 ubuntu1 hcid[30885]: Could not become the primary owner of org.bluez
Jul 24 11:07:19 ubuntu1 hcid[30885]: Unable to get on D-Bus
Jul 24 11:07:22 ubuntu1 pand[6225]: Accept failed. Interrupted system call(4)
Jul 24 11:07:22 ubuntu1 hcid[6197]: Stopping SDP server
Jul 24 11:07:22 ubuntu1 input[6208]: Unregistered manager path
Jul 24 11:07:22 ubuntu1 input[6208]: Unregistered manager path
Jul 24 11:07:22 ubuntu1 input[6208]: Exit
Jul 24 11:07:22 ubuntu1 hcid[6197]: Unregister path: /org/bluez/hci0
Jul 24 11:07:22 ubuntu1 hcid[6197]: Unregister path: /org/bluez
Jul 24 11:07:22 ubuntu1 hcid[6197]: Shutting down local server
Jul 24 11:07:22 ubuntu1 hcid[6197]: Exit
Jul 24 11:07:22 ubuntu1 audio[6207]: Removing service record 0x10000 failed: Message did not receive a reply (timeout by message bus)
Jul 24 11:07:22 ubuntu1 audio[6207]: Unregistered manager path
Jul 24 11:07:22 ubuntu1 audio[6207]: Exit
Jul 24 11:07:23 ubuntu1 hcid[30910]: Bluetooth HCI daemon
Jul 24 11:07:23 ubuntu1 hcid[30910]: HCI dev 0 registered
Jul 24 11:07:23 ubuntu1 pand[30913]: Bluetooth PAN daemon version 3.19
Jul 24 11:07:23 ubuntu1 pand[30913]: Failed to connect to the local SDP server. Connection refused(111)
Jul 24 11:07:23 ubuntu1 hcid[30910]: HCI dev 0 already up
Jul 24 11:07:23 ubuntu1 hcid[30910]: Device hci0 has been added
Jul 24 11:07:23 ubuntu1 hidd[30915]: Bluetooth HID daemon
Jul 24 11:07:23 ubuntu1 hcid[30910]: Starting security manager 0
Jul 24 11:07:23 ubuntu1 hcid[30910]: Device hci0 has been activated
Jul 24 11:07:23 ubuntu1 hcid[30910]: Starting SDP server
Jul 24 11:07:23 ubuntu1 hcid[30910]: Created local server at unix:abstract=/var/run/dbus-CVChzayKQh,guid=380cee4334df99d1221755004888464b
Jul 24 11:07:23 ubuntu1 input[30923]: Bluetooth Input daemon
Jul 24 11:07:23 ubuntu1 input[30923]: Registered input manager path:/org/bluez/input
Jul 24 11:07:23 ubuntu1 input[30923]: Failed to listen on control channel
Jul 24 11:07:23 ubuntu1 audio[30922]: Bluetooth Audio daemon
Jul 24 11:07:23 ubuntu1 audio[30922]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Jul 24 11:07:23 ubuntu1 audio[30922]: Unix socket created: 5
Jul 24 11:07:23 ubuntu1 hcid[30910]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Jul 24 11:07:23 ubuntu1 hcid[30910]: Default authorization agent (:1.18, /org/bluez/auth) registered
Jul 24 11:07:23 ubuntu1 audio[30922]: add_service_record: got record id 0x10000
Jul 24 11:07:23 ubuntu1 audio[30922]: add_service_record: got record id 0x10001
Jul 24 11:07:23 ubuntu1 audio[30922]: Registered manager path:/org/bluez/audio
Jul 24 11:07:53 ubuntu1 init: tty4 main process (4980) killed by TERM signal
Jul 24 09:23:00 ubuntu1 smbd[30193]: [2008/07/24 09:23:00, 0] auth/auth_util.c:create_builtin_users(758)
Jul 24 09:23:00 ubuntu1 smbd[30193]:   create_builtin_users: Failed to create Users
Jul 24 09:23:00 ubuntu1 smbd[30193]: [2008/07/24 09:23:00, 0] smbd/service.c:make_connection_snum(928)
Jul 24 09:23:00 ubuntu1 smbd[30193]:   Can't become connected user!
Jul 24 09:23:00 ubuntu1 smbd[30193]: [2008/07/24 09:23:00, 0] auth/auth_util.c:create_builtin_administrators(792)
Jul 24 09:23:00 ubuntu1 smbd[30193]:   create_builtin_administrators: Failed to create Administrators



<b>Here is my configuration:</b>
Gumstix OE
Ubuntu 7.10 (gutsy)

<b>Using DHCP3 with subnets as follows</b>
#Config changed to enable BT communication, July 24, 2008
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.10, 192.168.1.24, 192.168.1.1;
option domain-name "mydomain.example";

# This is a very basic subnet declaration.
# This subnet is specific for my gumstix bluetooth device bnep0
# which was given in /etc/network/interfaces an IP 192.168.10.90
# but then the iptables option command was given 192.168.10.91
#(post-up iptables -t nat -A POSTROUTING -s 192.168.10.91/24 -j MASQUERADE)

 subnet 192.168.10.91 netmask 255.255.255.0 {
 range 192.168.1.10 192.168.1.100;
 range 192.168.1.150 192.168.1.200;
 option routers 192.168.10.90;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
}

<b>Output of various HCI commands:</b>

PC (Host) Messages:
$ hcid -n&
$ Bluetooth HCI daemon
hcid[17952]: Could not become the primary owner of org.bluez
hcid[17952]: Unable to get on D-Bus

Gumstix (Client) messages:
$ hcid -n&
$ Bluetooth HCI daemon
hcid[855]: Could not become the primary owner of org.bluez
hcid[855]: Unable to get on D-Bus


It seems I am missing some steps in the server side configuration or in making the gumstix bluetooth visible/discoverable because they simply do not recognize each other.  How do I set up the proper addresses for this network? (I can manually set up the interface and addresses on my client) Any help would be great.

Thank you!
-Eletha

---

### Post by eletha on 2008-08-12
No more DBUS problems after reinstalling bluez-utils, bluez-libs, and libdubs-1-3 all over again. 

Here is the syslog account of what my HCI daemon is complaining about.


```

Aug 12 12:29:41 ubuntu1 hcid[6147]: Bluetooth HCI daemon
Aug 12 12:29:41 ubuntu1 hcid[6147]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
Aug 12 12:29:41 ubuntu1 hcid[6147]: Starting SDP server
Aug 12 12:29:41 ubuntu1 hidd[6165]: Bluetooth HID daemon
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered manager path:/org/bluez/serial
Aug 12 12:29:41 ubuntu1 hcid[6147]: Unix socket created: 12
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered manager path:/org/bluez/audio
Aug 12 12:29:41 ubuntu1 hcid[6147]: bridge pan0 created
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered manager path:/org/bluez/network
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered server path:/org/bluez/network/nap
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered server path:/org/bluez/network/gn
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered server path:/org/bluez/network/panu
Aug 12 12:29:41 ubuntu1 pand[6180]: Bluetooth PAN daemon version 3.19
Aug 12 12:29:41 ubuntu1 hcid[6147]: Registered input manager path:/org/bluez/input
[B]Aug 12 12:29:41 ubuntu1 hcid[6147]: Failed to listen on control channel
Aug 12 12:29:41 ubuntu1 hcid[6147]: HCI dev 0 registered
Aug 12 12:29:41 ubuntu1 pand[6180]: Bind failed. Address already in use(98)[/B]
Aug 12 12:29:41 ubuntu1 hcid[6147]: HCI dev 0 up
Aug 12 12:29:41 ubuntu1 hcid[6147]: Device hci0 has been added
Aug 12 12:29:41 ubuntu1 hcid[6147]: Starting security manager 0
Aug 12 12:29:41 ubuntu1 hcid[6147]: Device hci0 has been activated
```


Also, this is the result of the command hcid -n&

As root user:


```
hcid[18637]: Bluetooth HCI daemon
hcid[18637]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
hcid[18637]: Starting SDP server
hcid[18637]: Registered manager path:/org/bluez/serial
hcid[18637]: Unix socket created: 12
hcid[18637]: Registered manager path:/org/bluez/audio
**hcid[18637]: Can't init plugin /usr/lib/bluetooth/plugins/network.so**
hcid[18637]: Registered input manager path:/org/bluez/input
**hcid[18637]: Failed to listen on control channel**
hcid[18637]: HCI dev 0 registered
hcid[18637]: HCI dev 0 already up
hcid[18637]: Device hci0 has been added
hcid[18637]: Starting security manager 0
hcid[18637]: Device hci0 has been activated
```

The plugin that is having a problem is in fact located in the path described above, so I don't know why it can't be initialized. 

Can anyone help me debug these errors or at least some hints into what they mean and how I can look into them?

thanks,

Eletha

---

### Post by ub78 on 2008-08-28
hey man, did you have any success finally?
I'm also trying to set up a bluetooth network, but I thought of using NAP instead of hcid. Here's my post:
[http://ubuntuforums.org/showthread.php?t=902293](http://ubuntuforums.org/showthread.php?t=902293)

Any help is highly appreciated...Thanks!
And good luck.. ;)

---

