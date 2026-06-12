---
title: "Cannot resolve host names but can resolve IP addresses - 18.04"
date: 2018-11-15
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2018-11-15
Hello everyone,

I've been using ssh to connect to computers in my house for several years and have never had a real problem with it until now. I can ping and ssh to these hosts with no problem so long as I use the IP address. I cannot, however, connect or ping them with their host names. All I get is:

```
ssh: Could not resolve hostname _host name goes here_: Temporary failure in name resolution
```

There's nothing temporary about it.

I can't seem to find the cause of this. I've read elsewhere that Ubuntu no longer resolves hostnames. Logically, that leaves me to believe it's done at the router. I thought it might be prudent to check here first before I wipe the router's NVRAM and reconfigure it.

The router has an active DHCP server and these hosts all have static IP addresses set at the router, which also knows their host names (dhcp is on for visitors). I do occasionally ssh in from a remote location. I wrote a config file (~/.ssh/config) a while back that allows me to use abbreviations for hostnames and it goes through a dynamic DNS lookup for when I'm away from home. Perhaps using this to connect two machines on the same LAN caused this problem? The router uses port forwarding for outside connections (which works fine) but on the LAN, it's IP address or no connection. I've now disabled the ~/.ssh/config file by renaming it but getting the same error.

The router uses Tomato firmware which is based on Linux 2.6. I can ssh to the router to check files but not seeing any problems. There is a file /etc/dnsmasq/hosts/hosts that has  all of the ip addresses listed with their corresponding hostnames. I've tried both service dnsmasq restart as well as service nscd restart. It says ok after each but I still cannot ssh from one machine to the other with the hostname. 

Is there somewhere else I need to be looking? I'm happy to gather add'l info. if needed.

Thanks!!

---

### Post by TheFu on 2018-11-15
Unix systems have used IP name resolution for decades to provide forward and reverse name lookups.  The methods for this to work are:
* /etc/hosts
* DNS
* NIS/NIS+
If you want name resolution to work properly, those are the methods required. There is nothing automatic about it. Never has been.

Around  5 yrs ago, perhaps a little longer, zeroconf became possible.  On Ubuntu, this is implemented using the **avahi** tool.  On small networks, this can work well. It doesn't scale for larger networks like a business would have.  Avahi has been part of Ubuntu desktops for a few releases now - perhaps since 14.04, but don't quote me.  There is 1 funny thing about avahi.  It requires accessing devices using a .local TLD.  {hostname}.local, so if the hostname is snoopy for your remote Ubuntu system and you want to ssh to it, then using **ssh snoopy.local** would be the command.  Other IP services would work the same way.

If you don't want to use the .local TLD, setup name resolution using one of the other methods.  For 5 systems or less, using the /etc/hosts is probably easiest.  For more systems, setting up a DNS is probably worth it, but don't allow the DNS to be accessed publicly.  Running a secure DNS isn't trivial.

dd-wrt and tomato have the ability to run a DNS server. Setting it up is highly manual.  I haven't used tomato in about 7 yrs, but dd-wrt uses cryptic, specific, DNS entry formats in the DNSmasq options, nothing at all like BIND uses.  [https://wiki.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server](https://wiki.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server)  It is ugly.
Looks like tomato has an ugly DNS setup too in the Dnsmasq Custom configuration: [https://en.wikibooks.org/wiki/Tomato_Firmware/Installation_and_Configuration#DNS/DHCP_Configuration](https://en.wikibooks.org/wiki/Tomato_Firmware/Installation_and_Configuration#DNS/DHCP_Configuration)

For many home networks, a good compromise is to setup a raspberry pi as the local DNS server. While doing that, also setup **pi-hole** to block ads and "bad parts" of the internet.

But for today, now, I'd just try using avahi .local stuff.  It only works if all the systems you want to reach support the zeroconf protocol that avahi uses.

Hook 'em!

---

### Post by scottbomb on 2018-11-17
My config. isn't anything special. I've never had to touch the networking settings. I have .ssh populated with the usual key files and such and was always able to just "ssh otherhost" and connect with no problem. The router handles DNS. I've never had to use .local or edit etc/hosts. Now I have to do "ssh 192.168.1.xxx" to get the 18.04 machines to connect.

I wrote .ssh/config with about 30 entries to get name resolution working again. The file saves me now but was never needed before. I'll live with it but can't help wonder if this has been discussed elsewhere but my searches have come up empty.

I have several virtual machines running 16.04 so I did a test just now and they resolve the hostnames just fine. I did the same with a Fedora VM. My iPhone's ssh application can resolve names. All resolve except the 18.04 machines, which I just upgraded a couple of weeks ago (wiped system HDs and did fresh installs). As an additional test, I re-downloaded and installed a fresh-out-of-the-box Kubuntu 18.04 VM instance and it couldn't resolve hostnames either. I can only conclude that something related to name resolution changed between 16.04 and 18.04 and is now failing. I'll look into filing a bug report.

---

### Post by TheFu on 2018-11-17
The ~/.ssh/config is handy for using different keys for different systems, different specific configs and nice to have aliases.

I'm just guessing.  IPv6 vs IPv4 in the system priorities?  Does your router provide local DNS in IPv6?
I disable all IPv6 on my systems.  One of my 16.04 systems had IPv6 ssh setup as the primary after an upgrade.  Took me a few hours to find the fix.  Oddly, all the other 16.04 systems with the same upgrade didn't show the same behavior. That bothered me.  Let me check something ... 
sshd_config needed this:
```
AddressFamily inet
```
The sshd_config manpage:
```
     AddressFamily
             Specifies which address family should be used by sshd(8).  Valid
             arguments are “any”, “inet” (use IPv4 only), or “inet6” (use IPv6
             only).  The default is “any”.
```

There is also a system-wide method to make IPv4 the primary inet.  Not sure I can remember how. Just heard about it last week. /etc/gai.conf   I don't know much more about it.

---

### Post by scottbomb on 2019-01-01
Thank you for the advice, Fu. I decided to roll things back a little.

Apparently I'm not the only one who's having problems with 18.04's networking. This guy offers a way to revert to the more known-good configuration using /etc/network/interfaces. I might be keeping network-manager and all the rest on the laptop but for desktop systems, I know don't need network-manager. All hosts on the network resolve now without the need for entries in a .ssh/config file (which never helped ping).

On the bright side, I learned a little more about Linux networking today so that was cool.

Edit: It helps to post the [URL to which I'm referring.]("https://xenomorph.net/linux/ubuntu/misc/network/")

I did have to tweak a couple of things. One needs to remove network-manager. I don't allow Google anywhere near my machines so the nameserver is my gateway, the router.

---

