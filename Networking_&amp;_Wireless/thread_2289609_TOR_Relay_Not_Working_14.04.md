---
title: "TOR Relay Not Working 14.04"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by coljohnhannibalsmith on 2015-08-05
Hello,

I need help configuring a tor relay.  Here are the contents of my torrc file:

```
## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22

################ This section is just for relays #####################
#
## See https://www.torproject.org/docs/tor-doc-relay for details.

## Required: what port to advertise for incoming Tor connections.
ORPort 9001
## If you want to listen on a port other than the one advertised in
## ORPort (e.g. to advertise 443 but bind to 9090), you can do it as
## follows.  You'll need to do ipchains or other port forwarding
## yourself to make this work.
ORPort 443 NoListen
ORPort 127.0.0.1:9090 NoAdvertise

## The IP address or full DNS name for incoming connections to your
## relay. Leave commented out and Tor will guess.
#Address noname.example.com

## If you have multiple network interfaces, you can specify one for
## outgoing traffic to use.
# OutboundBindAddress 10.0.0.5

## A handle for your relay, so people don't have to refer to it by key.
anoufe ididnteditheconfig #Nickname ididnteditheconfig

## Define these to limit how much relayed traffic you will allow. Your
## own traffic is still unthrottled. Note that RelayBandwidthRate must
## be at least 20 kilobytes per second.
## Note that units for these config options are bytes (per second), not
## bits (per second), and that prefixes are binary prefixes, i.e. 2^10,
## 2^20, etc.
RelayBandwidthRate 100 KBytes  # Throttle traffic to 100KB/s (800Kbps)
RelayBandwidthBurst 200 KBytes # But allow bursts up to 200KB (1600Kb)

## Use these to restrict the maximum traffic per day, week, or month.
## Note that this threshold applies separately to sent and received bytes,
## not to their sum: setting "4 GB" may allow up to 8 GB total before
## hibernating.
##
## Set a maximum of 4 gigabytes each way per period.
AccountingMax 1 GBytes
## Each period starts daily at midnight (AccountingMax is per day)
AccountingStart day 00:00
## Each period starts on the 3rd of the month at 15:00 (AccountingMax
## is per month)
AccountingStart month 3 15:00

## Administrative contact information for this relay or bridge. This line
## can be used to contact you if your relay or bridge is misconfigured or
## something else goes wrong. Note that we archive and publish all
## descriptors containing these lines and that Google indexes them, so
## spammers might also collect them. You may want to obscure the fact that
## it's an email address and/or generate a new address for this purpose.
ContactInfo Random Person <johnw54321 AT gmail dot com>
## You might also include your PGP or GPG fingerprint if you have one:
#ContactInfo 0xFFFFFFFF Random Person <nobody AT example dot com>

## Uncomment this to mirror directory information for others. Please do
## if you have enough bandwidth.
DirPort 9030 # what port to advertise for directory connections
## If you want to listen on a port other than the one advertised in
## DirPort (e.g. to advertise 80 but bind to 9091), you can do it as
## follows.  below too. You'll need to do ipchains or other port
## forwarding yourself to make this work.
#DirPort 80 NoListen
#DirPort 127.0.0.1:9091 NoAdvertise
## Uncomment to return an arbitrary blob of html on your DirPort. Now you
## can explain what Tor is if anybody wonders why your IP address is
## contacting them. See contrib/tor-exit-notice.html in Tor's source
## distribution for a sample.
#DirPortFrontPage /etc/tor/tor-exit-notice.html

## Uncomment this if you run more than one Tor relay, and add the identity
## key fingerprint of each Tor relay you control, even if they're on
## different networks. You declare it here so Tor clients can avoid
## using more than one of your relays in a single circuit. See
## https://www.torproject.org/docs/faq#MultipleRelays
## However, you should never include a bridge's fingerprint here, as it would
## break its concealability and potentially reveal its IP/TCP address.
#MyFamily $keyid,$keyid,...

## A comma-separated list of exit policies. They're considered first
## to last, and the first match wins. If you want to _replace_
## the default exit policy, end this with either a reject *:* or an
## accept *:*. Otherwise, you're _augmenting_ (prepending to) the
## default exit policy. Leave commented to just use the default, which is
## described in the man page or at
## https://www.torproject.org/documentation.html
##
## Look at https://www.torproject.org/faq-abuse.html#TypicalAbuses
## for issues you might encounter if you use the default exit policy.
##
## If certain IPs and ports are blocked externally, e.g. by your firewall,
## you should update your exit policy to reflect this -- otherwise Tor
## users will be told that those destinations are down.
##
## For security, by default Tor rejects connections to private (local)
## networks, including to your public IP address. See the man page entry
## for ExitPolicyRejectPrivate if you want to allow "exit enclaving".
##
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed

## Bridge relays (or "bridges") are Tor relays that aren't listed in the
## main directory. Since there is no complete public list of them, even an
## ISP that filters connections to all the known Tor relays probably
## won't be able to block all the bridges. Also, websites won't treat you
## differently because they won't know you're running Tor. If you can
## be a real relay, please do; but if not, be a bridge!
#BridgeRelay 1
## By default, Tor will advertise your bridge to users through various
## mechanisms like https://bridges.torproject.org/. If you want to run
## a private bridge, for example because you'll give out your bridge
## address manually to your friends, uncomment this line:
#PublishServerDescriptor 0
#   ORPort 443
#   Exitpolicy reject *:*
#   Nickname ididntedittheconfig
#   ContactInfo johnw54321@gmail.com

```

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-07
Just taking a glance at it, there is an error on the nickname line.  That needs to be set properly.  

```

Nickname *ididnteditheconfig*

```

Replace *ididnteditheconfig* with a unique identifier of your own choice for the **Nickname** option.   If you are running several relays it would be good to set the **MyFamily** option as well.  
Also, if you are going to be just a Tor relay and not an exit node, you must set the exit policy to reflect that.  

```

ExitPolicy reject *:* # no exits allowed

```

Then open a hole in your firewall so incoming connections can reach the ports you configured in ORPort and/or DirPort.

After Tor is restarted, check the logs to be sure it is ok.

---

### Post by coljohnhannibalsmith on 2015-08-08
I made the changes you suggested; but there is nothing in /var/log/tor/log. In fact it's empty.

Hannibal

---

### Post by Lars Noodén on 2015-08-08
Tor is quite chatty in the logs so it is probably not running.  Can you check the syntax of your configuration file?

```

/usr/sbin/tor --verify-config

```

---

### Post by coljohnhannibalsmith on 2015-08-08
sophie@sophie-Inspiron-1545:~$ /usr/sbin/tor --verify-config
Aug 08 12:03:20.211 [notice] Tor v0.2.6.10 (git-71459b2fe953a1c0) running on Linux with Libevent 2.0.21-stable, OpenSSL 1.0.1f and Zlib 1.2.8.
Aug 08 12:03:20.211 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
Aug 08 12:03:20.211 [notice] Read configuration file "/etc/tor/torrc".
Aug 08 12:03:20.215 [warn] Option 'AccountingStart' used more than once; all but the last value will be ignored.
Aug 08 12:03:20.215 [notice] Based on detected system memory, MaxMemInQueues is set to 2935 MB. You can override this by setting MaxMemInQueues by hand.
Configuration was valid
sophie@sophie-Inspiron-1545:~$ 

It seems the configuration is valid; but still no logs.

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-08
Is it actually running and listening to a port?

```

sudo netstat -ntlp | grep tor

```

---

### Post by coljohnhannibalsmith on 2015-08-08
Here's the output. I don't know what it all means:

s```
ophie@sophie-Inspiron-1545:~$ sudo netstat -ntlp | grep tor
[sudo] password for sophie: 
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      1184/tor        
tcp        0      0 127.0.0.1:9054          0.0.0.0:*               LISTEN      5920/tor        
tcp        0      0 127.0.0.1:9055          0.0.0.0:*               LISTEN      5920/tor        
tcp        0      0 127.0.0.1:9056          0.0.0.0:*               LISTEN      5943/tor        
tcp        0      0 127.0.0.1:9057          0.0.0.0:*               LISTEN      5943/tor        
tcp        0      0 127.0.0.1:9058          0.0.0.0:*               LISTEN      5946/tor        
tcp        0      0 127.0.0.1:9090          0.0.0.0:*               LISTEN      1184/tor        
tcp        0      0 127.0.0.1:9059          0.0.0.0:*               LISTEN      5946/tor        
tcp        0      0 0.0.0.0:9030            0.0.0.0:*               LISTEN      1184/tor        
tcp        0      0 0.0.0.0:9001            0.0.0.0:*               LISTEN      1184/tor        
sophie@sophie-Inspiron-1545:~$ 
```

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-08
I have logs now. I'm being told to check my firewall. Since I don't have one, I installed GuFw, turned it on; and selected incoming allow and outgoing allow.

I'll restart selector and check logs again.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-08
I'm still being told to check my firewall; but there was an increase in internet traffic when tor established a circuit. I was able to determine this with conky.

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-09
Are you allowing TCP packets in on ports 9030 and 9001 in your firewall (gufw) ?

```

tcp        0      0 0.0.0.0:9030            0.0.0.0:*               LISTEN      1184/tor        
tcp        0      0 0.0.0.0:9001            0.0.0.0:*               LISTEN      1184/tor        

```

---

### Post by coljohnhannibalsmith on 2015-08-09
I've disabled the firewall.

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-09
It would be enough to just let those two ports in.  

If your machine is on a LAN troubled by NAT and does not have an external address itself, then you will have to also forward those two ports from the router to your machine.

---

### Post by coljohnhannibalsmith on 2015-08-09
They were open when the firewall was enable; so it shouldn't be a problem now. I'm also not on a Lan.

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-09
> **coljohnhannibalsmith said:**
> I'm still being told to check my firewall; 

Can you show the exact error message?

Tor, as a relay, should just run and not be noticeable except for increased network traffic.

---

### Post by coljohnhannibalsmith on 2015-08-09
> **Lars Noodén said:**
> Can you show the exact error message?

Tor, as a relay, should just run and not be noticeable except for increased network traffic.

```
Aug 09 08:35:03.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Aug 09 08:35:03.000 [notice] Bootstrapped 100%: Done
Aug 09 08:35:03.000 [notice] Now checking whether ORPort 99.196.146.177:9001 and DirPort 99.196.146.177:9030 are reachable... (this may take up to 20 minutes -- look for log messages indicating success)
Aug 09 08:54:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 08:54:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:14:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:14:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:34:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:34:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:54:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 09:54:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:14:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:14:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:34:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:34:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:54:56.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 10:54:56.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.

```

I hope this helps.

---

### Post by Lars Noodén on 2015-08-09
Ports 9001 and 9030 are somehow blocked on your machine or on the way to your machine. Do you have anything between your machine and the Internet that could be interfering? 

Have you checked using an external scan to see if the two ports are open?  Maybe something like [http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by coljohnhannibalsmith on 2015-08-09
> **Lars Noodén said:**
> Ports 9001 and 9030 are somehow blocked on your machine or on the way to your machine. Do you have anything between your machine and the Internet that could be interfering? 

Have you checked using an external scan to see if the two ports are open?  Maybe something like [http://canyouseeme.org/](http://canyouseeme.org/)

[COLOR=red]**Error:**[/COLOR] I could **not** see your service on **99.196.146.177** on port (**9001**)
Reason: Connection timed out


[COLOR=red]**Error:**[/COLOR] I could **not** see your service on **99.196.146.177** on port (**9030**)
Reason: Connection timed out

[SIZE=2]I have a wireless router between me and the Internet; but I'm connected through the Ethernet passthrough. I use the wireless for my smartphone; with a voip app.[/SIZE]

---

### Post by bashiergui on 2015-08-09
The IP address 99.196.146.177 is registered to wildblue.net/ viasat communications. Their Acceptable Use Policy states that residential customers can't run services that provide network content to anyone outside of your local area network. 
[http://www.exede.com/documents/master/acceptable-use-policy.pdf](http://www.exede.com/documents/master/acceptable-use-policy.pdf)

Your ISP might actively block tor exit nodes on the residential plans, but at the very least they seem to be disaplowed by the Policy. The Tor blog has a post suggesting how to run an exit node without getting it blocked or shut down:
[https://blog.torproject.org/blog/tips-running-exit-node-minimal-harassment](https://blog.torproject.org/blog/tips-running-exit-node-minimal-harassment)

---

### Post by coljohnhannibalsmith on 2015-08-09
When I connect directly to the satellite modem I get the following logs. Also multiple instances of tor are spawned:

```
Aug 09 15:45:28.000 [notice] Tor 0.2.6.10 (git-71459b2fe953a1c0) opening new log file.
Aug 09 15:45:28.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
Aug 09 15:45:28.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
Aug 09 15:45:29.000 [notice] Configured to measure statistics. Look for the *-stats files that will first be written to the data directory in 24 hours from now.
Aug 09 15:45:29.000 [notice] Your Tor server's identity key fingerprint is 'anoufe E5AA1371353AEFE04A555CBB18BE87260ABB9728'
Aug 09 15:45:29.000 [notice] Bootstrapped 0%: Starting
Aug 09 15:45:36.000 [notice] Bootstrapped 80%: Connecting to the Tor network
Aug 09 15:46:02.000 [notice] Bootstrapped 85%: Finishing handshake with first hop
Aug 09 15:47:48.000 [notice] Bootstrapped 90%: Establishing a Tor circuit
Aug 09 15:47:51.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Aug 09 15:47:51.000 [notice] Bootstrapped 100%: Done 
```

When I connect through the Ethernet passthrough on my wireless router, I get these logs:

```
Aug 09 16:07:09.000 [notice] Your Tor server's identity key fingerprint is 'anoufe E5AA1371353AEFE04A555CBB18BE87260ABB9728'
Aug 09 16:07:09.000 [notice] Bootstrapped 0%: Starting
Aug 09 16:07:16.000 [notice] Bootstrapped 80%: Connecting to the Tor network
Aug 09 16:07:17.000 [notice] Guessed our IP address as 99.196.146.177 (source: 128.31.0.39).
Aug 09 16:07:18.000 [notice] Bootstrapped 85%: Finishing handshake with first hop
Aug 09 16:07:21.000 [notice] Bootstrapped 90%: Establishing a Tor circuit
Aug 09 16:07:25.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Aug 09 16:07:25.000 [notice] Bootstrapped 100%: Done
Aug 09 16:07:25.000 [notice] Now checking whether ORPort 99.196.146.177:9001 and DirPort 99.196.146.177:9030 are reachable... (this may take up to 20 minutes -- look for log messages indicating success)
Aug 09 16:27:17.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 16:27:17.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 16:47:17.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 16:47:17.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:07:17.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:07:17.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:27:17.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:27:17.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:47:17.000 [warn] Your server (99.196.146.177:9001) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Aug 09 17:47:17.000 [warn] Your server (99.196.146.177:9030) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
```

There's obviously a differece here. Is there anyway to configure my router to permit the passthrough in both directions; or do I have to connect directly through the satellite modem every time?

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-08-11
Have you tried changing ports it runs on (ORPort and DirPort) to something other than the defaults, or contacting your ISP?

---

### Post by coljohnhannibalsmith on 2015-08-11
> **Lars Noodén said:**
> Have you tried changing ports it runs on (ORPort and DirPort) to something other than the defaults, or contacting your ISP?

Look at what I did in the config file, oops. I corrected this and kept the default ports. Please see attachment.

I've also discovered that I have to bypass the router to make the relay available from the outside; but it looks like it's working now. See below:

```
Aug 11 09:10:58.000 [notice] Our IP Address has changed from 99.196.146.177 to 172.242.164.65; rebuilding descriptor (source: METHOD=INTERFACE).
Aug 11 09:11:08.000 [notice] Self-testing indicates your ORPort is reachable from the outside. Excellent. Publishing server descriptor.
Aug 11 09:11:40.000 [notice] Performing bandwidth self-test...done.
Aug 11 09:17:25.000 [notice] Self-testing indicates your DirPort is reachable from the outside. Excellent.

```

I wish I could find something like an A/B switch for this instead of moving cables around.

Thanks, Hannibal

---

