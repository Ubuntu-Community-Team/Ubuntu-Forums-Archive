---
title: "DNS resolution problem on my computer"
date: 2021-11-01
forum: Networking &amp; Wireless
---

### Post by lstanfel on 2021-11-01
I installed ubuntu (20.04.3 LTS) on my laptop several weeks ago, but am still a newbie.  Apologies in advance for any dumb questions.

Today I cannot access the internet via either wireless or wired interfaces.  Seems to be a DNS resolver problem of some kind.  Web pages do not load, and time out with a DNS error.  When I run a dig command it just times out and says no server could be reached.

I have tried manually configuring DNS servers in the settings for both wired and wireless interfaces, and that didn't do anything.

I used systemctl to stop and then start systemd-resolved.

Rebooted router, PC, etc. 

Did nmcli networking off, and then on.

Flushed DNC cache with systemd-resolve -- flush-caches

BTW, from the CLI terminal I can ping IP addresses successful, I just can't resolve anything via DNS.

Any suggestions?

Thanks!
Larry

---

### Post by TheFu on 2021-11-02
So ... you have 2 choices.  If this is a desktop PC with a GUI, then you probably want to manually set the DNS servers through the GUI.  Open the network settings, find the IPv4 tab and DNS, then set them to the fast and privacy-honoring Cloudflare DNS servers.
1.1.1.1 and 1.0.0.1
See if that doesn't resolve the issue.

If you like, you can modify the /etc/systemd/resolved.conf config file using **sudoedit**.  There are hints for the options inside the file and there is a manpage which explains each.  Probably just need to put 1.1.1.1 into the DNS and 1.0.0.1 into the FallbackDNS, then restart the systemd-resolved daemon using the 
** sudo systemctl restart systemd-resolved** command.

Or, if you are like me, you can block resolved from running and manually configure the /etc/resolv.conf file like we did for 20 yrs before and never had any issues. That's more involved and generally good only for LAN networks running a local DNS.  The /etc/resolv.conf  is usually setup as a symlink to somewhere else, so that needs to be broken and quickly replaced with a real file correctly formatted.  I'm loath to show the correct file setup because I disable some of the new-fangled stuff they put into there to support mDNS (avahi) junk and my LAN connects to multiple internal and external domains, so it wouldn't apply to a typical home user.  Doesn't hurt to look at the existing file ... make a backup of that file before attempting any changes so you can put it back if things to really wrong.

---

### Post by lstanfel on 2021-11-02
Thank you for the suggestions, I will give that a try.  Note I already already attempted to manually configure DNS servers using the GUI, but that didn't work.  I'll update this shortly with results.

---

### Post by lstanfel on 2021-11-02
Still no dice.  As expected, using the GUI to configure 1.1.1.1 and 1.0.0.1 didn't work.  I edited the resolved.conf file as you suggested and added entries for DNS and FallbackDNS (they were blank), then restarted resolved.  Still not working.

Is it possible that a 3rd party VPN application could have broken this somehow?   I have been using the ProtonVPN application, and it was functional albeit not very reliable (sometimes requiring a force quit and restart to get it to connect). I uninstalled it earlier, but that didn't help either.

---

### Post by TheFu on 2021-11-02
> **lstanfel said:**
> Still no dice.  As expected, using the GUI to configure 1.1.1.1 and 1.0.0.1 didn't work.  I edited the resolved.conf file as you suggested and added entries for DNS and FallbackDNS (they were blank), then restarted resolved.  Still not working.

Is it possible that a 3rd party VPN application could have broken this somehow?   I have been using the ProtonVPN application, and it was functional albeit not very reliable (sometimes requiring a force quit and restart to get it to connect). I uninstalled it earlier, but that didn't help either.

YES!  VPNs routinely break DNS.  It depends on a number of network things and how they setup the routing.  Get this stuff working without a VPN first.  Also, forget the "brand name" of the VPN, which vpn software is actually used?  Typically, that would be openvpn or wireguard, but some might use IPSec for the more secure options.

---

### Post by lstanfel on 2021-11-02
Thanks.  In my defense the system was running before I installed the VPN application. :-)

Back to your earlier suggestion.. the /etc/resolv.conf file doesn't have much in it:
nameserver 127.0.0.53
options edns0 trust.ad

I'm not sure what to do now.  Am I going to need to reinstall the whole OS?

---

### Post by TheFu on 2021-11-02
> **lstanfel said:**
> Thanks.  In my defense the system was running before I installed the VPN application. :-)

Back to your earlier suggestion.. the /etc/resolv.conf file doesn't have much in it:
nameserver 127.0.0.53
options edns0 trust.ad

I'm not sure what to do now.  Am I going to need to reinstall the whole OS?

Hardly. DNS is an extremely minor issue.  Did you change the resolved.conf file already?
You should disable the VPN, for now.

---

### Post by lstanfel on 2021-11-02
Thank you again for your help on this.   But yes, the current situation is:
-- protonvpn uninstalled
-- resolved.conf file now has 1.1.1.1 and 1.0.0.1 is primary and backup DNS addresses
-- resolv.conf is untouched, but has a 'nameserver 127.0.0.53' line in the config.  Don't know if that conflicts with anything else.

...and system is still not resolving DNS as far as i can tell.

---

### Post by TheFu on 2021-11-02
Can you prove those claims by posting the config files here, wrapped in code tags?
/etc/systemd/resolvd.conf
/etc/resolv.conf
ls -Fl /etc/resolv.conf

**Drastic solution:**
I don't know if I mentioned this, but you can disable resolved, and do like I posted above in #2 3rd paragraph.  I actually purge all network-manager stuff from my systems to prevent conflicts with settings I put into /etc/netplan/ config files.  That's mostly a server thing, but long ago I was burned by network-manager and started purging it. I prefer manually configured, static, IPs on my systems.  For a laptop, I use wifi when away from home and use wicd-curses to manage that, but when at home, it has a wired ethernet connection.

Before you do these things, there are a number of threads in these forums about 20.04 DNS issues where the solution was in the /etc/systemd/resolvd.conf. Seek those out and try what they say first.

---

### Post by lstanfel on 2021-11-03
FYI, I believe this is solved.  In case anybody else has this problem... here's what I did:

I opened a ticket with the VPN software provider and they suggested I run a [COLOR=#2B2E2F][FONT=SFMono-Regular]nmcli connection show --active [/FONT][/COLOR]command, and then delete the connections with a 'vpn' prefix.  There was, in fact, one such connection and when I killed it my DNS started working.  So I think an earlier force quit I did of the VPN application left that connection in place, and broke DNS.

---

### Post by drezl on 2022-10-29
> **lstanfel said:**
> FYI, I believe this is solved.  In case anybody else has this problem... here's what I did:

I opened a ticket with the VPN software provider and they suggested I run a [COLOR=#2B2E2F][FONT=SFMono-Regular]nmcli connection show --active [/FONT][/COLOR]command, and then delete the connections with a 'vpn' prefix.  There was, in fact, one such connection and when I killed it my DNS started working.  So I think an earlier force quit I did of the VPN application left that connection in place, and broke DNS.

Hey thanks for sharing it really helped me out. I had the same issue.  I have protonVPN and after a power outage I had a vpn session stuck blocking DNS from working.

 @nuc:~$** nmcli connection show --active**
 NAME                      UUID                                  TYPE   DEVICE         
 RFC 2549                  12345678-abcd-1234-5678-1234567890ab  wifi   wlp3s0         
 pvpn-ipv6leak-protection  12345678-abcd-1234-5678-1234567890ab  dummy  **ipv6leakintrf0 **

 @nuc:~$ **nmcli device delete ipv6leakintrf0**
 Device 'ipv6leakintrf0' successfully removed.

 @nuc:~$ nmcli connection show --active
 NAME      UUID                                  TYPE  DEVICE 
 RFC 2549  12345678-abcd-1234-5678-1234567890ab  wifi  wlp3s0 
 @nuc:~$

I actually signed up to the forum just now to say thank you :)

---

