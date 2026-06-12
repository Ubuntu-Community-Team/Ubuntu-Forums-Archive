---
title: "stop: Unknown instance:"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by publicface on 2013-12-11
kubuntu 12.04

service networking restartstop: Unknown instance: 
networking stop/waiting

Why does it do the above?
~~~~~~~~~~
cat /etc/network/interface


auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1 8.8.8.8
auto wlan0
iface wlan0 inet static
        address 192.169.0.11
        netmask 255.255.255.0
        network 192.169.0.0
        broadcast 192.169.0.255
        gateway 192.168.0.1
        wpa-ssid TP-LINK_Axxyyzz
        wpa-psk myPasswd

~~~~~~~~~~~~

and this?

ifup -a
RTNETLINK answers: File exists
Failed to bring up wlan0.



~~~~~~~
iwconfig

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.





Thank you in advance

---

### Post by Bucky Ball on 2013-12-11
What does it tell you when you run:

sudo service networking start

? Also, when is this error appearing? You don't actually say.

---

### Post by publicface on 2013-12-13
Thank you for your response.  In regard to your questions:


[COLOR=#000000][FONT=Ubuntu]The command:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]sudo service networking start[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]The output:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]networking stop/waiting

The command: [/FONT][/COLOR]
[COLOR=#000000]service networking restart

The output:
stop: Unknown instance: [/COLOR]
[COLOR=#000000]networking stop/waiting[/COLOR]

The command:
[COLOR=#000000]ifup -a
[/COLOR]
The output:
[COLOR=#000000]RTNETLINK answers: File exists[/COLOR]
[COLOR=#000000]Failed to bring up wlan0.[/COLOR]

Thank you for taking the time to respond.

> **Bucky Ball said:**
> What does it tell you when you run:

sudo service networking start

? Also, when is this error appearing? You don't actually say.

---

### Post by steeldriver on 2013-12-13
The 'Unknown instance' error has been happening for some time (months) for me on a 12.04 server box, I have not managed to figure out why - but it does not appear to prevent the service from working. My guess is it's some issue between upstart and init.d, because init.d will start/stop it (although it's deprecated, because it's supposed to be an upstart job) i.e.

```

$ sudo service networking restart
stop: Unknown instance:
networking stop/waiting

```

It clearly isn't stopped since I'm doing this via ssh ;)

```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
ssh stop/waiting

ssh start/running, process 3107
 * Reconfiguring network interfaces...                                   [ OK ]

```

I think the more serious error in your case is the RTNETLINK error, I believe that may be caused by specifying 2 gateways with the same metric - you may need to give an explicit metric for one or both interfaces to resolve that

---

### Post by publicface on 2013-12-13
Thank you for responding.

At your suggestion, I changed the gateway lines from:
[COLOR=#000000]gateway 192.168.0.1
[/COLOR][COLOR=#000000]gateway 192.168.0.1
[/COLOR]
to:
[COLOR=#000000]gateway 192.168.0.1 metric 0
[/COLOR][COLOR=#000000]gateway 192.168.0.1 metric 1
[/COLOR][COLOR=#000000]
I don't know if that's correct?
[/COLOR]
However:
# ifup -a 
Output:
RTNETLINK answers: File exists
Failed to bring up wlan0.

Then I realized, the link is already up... so I did:
# ifdown -a
# ifup -a

Output:
ssh stop/waiting
ssh start/running, process 23853
cat: /var/run/wpa_supplicant.wlan0.pid: No such file or directory
RTNETLINK answers: File exists
Failed to bring up wlan0.

Since there was a change in the output, I took the gateway metrics back out and repeated the experiment

# ifdown -a
# ifup -a

Output:

ssh stop/waiting
ssh start/running, process 24245
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
RTNETLINK answers: File exists
Failed to bring up wlan0.
~~~~~~~~~~~~~~~~
For the record, I'm at the console, not using ssh.

---

### Post by steeldriver on 2013-12-13
I'm not actually sure what the right answer is - especially since you actually have the *same* gateway IP - the metric *probably* needs to go on a separate line, and you *may* only need to specify it for one interface e.g.

```

auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1 8.8.8.8
auto wlan0
iface wlan0 inet static
        address 192.169.0.11
        netmask 255.255.255.0
        network 192.169.0.0
        broadcast 192.169.0.255
        gateway 192.168.0.1
        **metric 100**
        wpa-ssid TP-LINK_Axxyyzz
        wpa-psk myPasswd

```

but I'm guessing here - you might want to wait until one of the network gurus stops by

---

### Post by publicface on 2013-12-13
I made your suggested change from:
[COLOR=#000000][COLOR=#000000]gateway 192.168.0.1 metric 0
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]gateway 192.168.0.1 metric 1[/COLOR][/COLOR]
to:[COLOR=#000000][COLOR=#000000]
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]gateway 192.168.0.1[/COLOR][/COLOR]
metric 100

# ifdown -a
# ifup -a

ssh stop/waitingssh start/running, process 26835
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
RTNETLINK answers: File exists
Failed to bring up wlan0.

---

### Post by publicface on 2013-12-13
To be honest I don't understand the focus on the gateway.  There is one gateway, the router.  All packets must go to the router to get off my machine.  So I fail to understand why two interfaces can't have the same gateway.  Packets coming in over wireless go out through the router.  Packets coming in the wired path, also go out through the router.  Why the focus on metrics and gateways when there is only one path for the packets to go?

Obviously I don't know the answer here or I wouldn't have posted a question, but it seems to me that "RTNETLINK answers: File exists" must be talking about a file... possibly an interface? Possibly wlan0?

In any event, I can't help but notice there are now at least two issues... the new one being the wpa_supplicant.  This thread: [http://ubuntuforums.org/showthread.php?t=263136&page=16](http://ubuntuforums.org/showthread.php?t=263136&page=16) would appear to have some interesting thoughts & ideas, but after 16 pages it's unclear if the problem is actually solved or not.

---

