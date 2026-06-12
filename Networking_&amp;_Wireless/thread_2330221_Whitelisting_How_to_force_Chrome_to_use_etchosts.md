---
title: "Whitelisting: How to force Chrome to use /etc/hosts?"
date: 2016-07-09
forum: Networking &amp; Wireless
---

### Post by ericbradshaw on 2016-07-09
The directions for [Do It Yourself Whitelisting]("https://help.ubuntu.com/community/ParentalControls#Do_It_Yourself_Whitelisting") work great when using Firefox, but Google Chrome bypasses /etc/hosts, allowing unrestricted Internet access. Does anyone know a method to force Chrome to use the hosts file?

---

### Post by &amp;KyT$0P# on 2016-07-09
Ubuntu uses dnsmasq for DNS, so why not force your entire DNS setup to read from the HOSTS file?

Run this in a Terminal:
```
echo 'addn-hosts=/etc/hosts
domain-needed' | sudo tee /etc/NetworkManager/dnsmasq.d/hosts.conf
```

Then restart NetworkManager.  For 14.04 and earlier:
```
sudo service network-manager restart
```
For 15.04 and later:
```
sudo systemctl restart NetworkManager
```

Does it work?

---

### Post by ericbradshaw on 2016-07-09
Okay, followed your instructions. Firefox - still blocked from everything except the addresses in the hosts (whitelist) file. *For that matter, apt-get and AptURL is blocked as well, so I couldn't have installed Google Chrome new if it wasn't already there*. Unfortunately, the already installed Google Chrome web browser continues to have access to anything I could think of to search for. To be sure, I cleared Google Chrome's history since the beginning of time and (after restarting the NetworkManager and still having access to whatever I wanted) restarted the computer. The Internet is still wide open to Chrome. In case it makes a difference, I'm testing this on Lubuntu 16.04.

---

### Post by &amp;KyT$0P# on 2016-07-09
It works as expected for me on both Lubuntu 14.04 and Xubuntu 16.04.

The way you describe the HOSTS file seems confused to me -
> hosts (whitelist) file
HOSTS is not a "whitelist" of any sort it's just a local file mapping domains <==> IP addresses.  That guide is really confusing for anyone who doesn't understand this stuff already :?
You should revert all the changes you made following that guide (but keep a copy of your modified HOSTS) - let's use only dnsmasq for the whitelisting.

We use dnsmasq here for *blacklisting* domains, I would think it'd be possible to use it like whitelist: configure it to answer queries only from local sources by default, but the whitelisted domains get forwarded upstream to the "standard servers".  Don't see offhand how to specify "any domain", so maybe you can give it a list of all Internet top-level domains to block by default?  Configuration could look kind of like this (just an example, **not tested** and far from complete!) :
```
# whitelist only specific domains, block everything else

# Blacklisting TLDs by default
server="/com/"
server="/net/"

# the whitelist entries look like this one
server="/google.com/#"

```

This blocks all .com and .net not specified in HOSTS or otherwise locally, except for [*.]google.com which will be forwarded to whatever upstream DNS servers are listed, like normal.

Lines starting with # are comments, none of them required and you can type anything you want there.  To load any changes you make to the configuration, restart NetworkManager as above.
Also, configuration files just get placed in [FONT=Courier New]/etc/NetworkManager/dnsmasq.d[/FONT] and have extension [FONT=Courier New].conf[/FONT]

For more information about this, and what it's doing, refer to the man page of dnsmasq (type man dnsmasq in Terminal).

Before you try any of this, I strongly recommend reading up about DNS and HOSTS so that, not only your understandable confusion can be fixed, also you will have a much easier time understanding the dnsmasq man page.

---

### Post by him610 on 2016-07-09
FWIW, you may have a better chance of achieving your goal if you concentrate on your router.

---

### Post by ericbradshaw on 2016-07-09
him610: I had tried router settings, OpenDNS and continue to use  FoxFilter anyway, but this method works for absolute Parental Control as long as I don't install Chrome.
halogen2: I appreciate both your replies and  acknowledge my ignorance about how dnsmasq works for blacklisting, or  would/should work for whitelisting. I called /etc/hosts a whitelist  file because that's how I use it on my children's computers. I have  hundreds of sites listed in it like so:
```
204.122.20.18 scienceclub.org www.scienceclub.org
50.87.232.29 sciencetoymaker.org www.sciencetoymaker.org
66.241.145.14 sciencespot.net www.sciencespot.net
```
and provided the /etc/nsswitch.conf file says
```
hosts:          files
```
instead of
```
hosts:          files dns
```
on Lubuntu 14.04, or
```
hosts:          files
```
instead of
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```
on Lubuntu 16.04 - this  method absolutely works to block my children's computers from anything  beside what we (my wife and I) have approved of for my children to see. But it doesn't work with Chrome and I was hoping  someone could explain why not - and/or let me know how I could force Chrome to use the /etc/hosts file like Firefox does.

---

### Post by &amp;KyT$0P# on 2016-07-09
I don't know about Chrome, but I tested Chromium browser and it does read /etc/hosts.  If Chrome is the same, probably it's just accessing DNS regardless of the other configuration file.
Again, that guide seems a bit misguided (or outdated?), just because it looks to work doesn't mean it's a good idea.

Since it's surprisingly hard to find any simple explanations of DNS & the like, try starting with this: [https://kb.iu.edu/d/adns]("https://kb.iu.edu/d/adns")
And you can extract a list of top-level domains from the list from [here]("https://publicsuffix.org/")

If you can get dnsmasq-based whitelisting working, you will find it much simpler, more flexible, more effective, and easier to maintain than the way you're currently going about it.  Note that it does away with the need to manually specify every subdomain, plus no more manually-specified IP addresses to hassle about keeping up-to-date.  How hard can it be to just have a couple lists of YOUR choice of domains formatted a certain way and run one command and you're good to go?

---

### Post by ericbradshaw on 2016-09-07
The /etc/hosts file is supposed to override a DNS request, but  Chrome is in fact bypassing /etc/hosts and performing  its own DNS lookups through it's own servers: [https://bugs.chromium.org/p/chromium/issues/detail?id=117655](https://bugs.chromium.org/p/chromium/issues/detail?id=117655)

I use the Do It Yourself Whitelisting method [[http://computers4christians.org/FAQ/OS/HowTo/School/Whitelist.html](http://computers4christians.org/FAQ/OS/HowTo/School/Whitelist.html)] because it allows for absolute control over what my children see, even advertising. It may not be as easy or flexible; but it is definitely more effective. Fortunately, my children can live without Chrome on their computers.

---

