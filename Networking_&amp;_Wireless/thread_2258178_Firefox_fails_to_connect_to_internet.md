---
title: "Firefox fails to connect to internet"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by errand on 2014-12-25
&#8203;Hi All,

I have a strange problem. My Firefox browser fails to connect to internet, later I've noticed that my Dropbox can't connect and if I use apt-get update I receive error massage  "W: Failed to fetch http:..." and can't connect to any repository. Everything started with a sudo apt-get problem "sudo: unable to resolve host *hostname*"
I've changed /etc/hosts and /etc/nsswitch.conf  files but to no avail and returned them to their previous stage but got the other problems. My other browsers can connect.
I use Ubuntu 14.04
my /etc/hosts:
```
127.0.0.1 localhost
127.0.1.1 Plato.Daniel


# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

my /etc/nsswitch.conf
```
# /etc/nsswitch.conf#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat
group:          compat
shadow:         compat


hosts:          files 
networks:     mdns4_minimal [NOTFOUND=return] dns mdns4 files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis



```
Hope somebody can help.
Thanks

---

### Post by whitesmith on 2014-12-25
> **errand said:**
> &#8203;My other browsers can connect.

Shot in the dark: Rename .mozilla to .mozilla-sav (without FF running, of course). When FF comes up again it will create its own files, since this is a new install. Work now? If it does, you have a configuration problem. Regards.

---

### Post by schragge on 2014-12-25
Are you behind a proxy? Or maybe it's a [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") problem? Have you tried to reach say google.com by typing in one of its IPs, e.g. 173.194.32.227

---

### Post by whitesmith on 2014-12-25
Since the OP's other browsers can connect, it can't be DNS or any systemwide issue, unless FF connects through through a VPN or something else that he probably would have mentioned, since he seems thorough.

---

### Post by errand on 2014-12-26
> **whitesmith said:**
> Shot in the dark: Rename .mozilla to .mozilla-sav (without FF running, of course). When FF comes up again it will create its own files, since this is a new install. Work now? If it does, you have a configuration problem. Regards.
It was shot in the dark. I renamed the original .mozilla dir and started FF the new FF didn't connect either. I'm not behind proxy. Must be something else but I don't see it :mad:.

---

### Post by errand on 2014-12-26
> **schragge said:**
> Are you behind a proxy? Or maybe it's a [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") problem? Have you tried to reach say google.com by typing in one of its IPs, e.g. 173.194.32.227
I'm not behind proxy. I've tried what you suggested and I was able to connect to google.com. Hmm...

---

### Post by schragge on 2014-12-26
Then it seems to be a DNS (Domain Name System) issue after all. Try to put [Google Public DNS]("http://en.wikipedia.org/wiki/Google_Public_DNS") (8.8.8.8 or 8.8.4.4) as an additional DNS server and see what happens. You can do it through nm-applet. It's behind the two arrows **[SIZE=+1]&#8645;[/SIZE]** icon in notification area. **Edit**, select your connection, **Edit** again, select the **IPv4 Settings** tab, put 8.8.8.8 into **Additional DNS servers**, then **Save**.

---

### Post by errand on 2014-12-27
Unfortunately that didn't help. In my first post I wrote that Dropbox and apt-get don't connect either. I've tried to use from Terminal wget but it can't fetch anything. It can't resolve the domains if I run apt-get update I get that " Could not resolve 'archive.canonical.com' ". I agree that it is a DNS issue but seems to be buried deeper.:confused:

---

### Post by schragge on 2014-12-27
Ok. Let's troubleshoot the issue. We'll start with the local caching DNS server (dnsmasq). Does it run at all? Is it properly configured?
```

pgrep -a dnsmasq
dnsmasq --test

```
Now, let's disable it, and see if we're better off without caching DNS requests. Comment out the line *dns=dnsmasq* in file */etc/NetworkManager/NetworkManager.conf* by putting # before it, then restart NetworkManager:
```

sudo sed -i 's/^dns=dnsmasq/#&/' /etc/NetworkManager/NetworkManager.conf
sudo service network-manager restart

```
If this doesn't help, next we'll look at NetworkManager itself. This command should report its state:
```
nm-tool
```

---

### Post by errand on 2014-12-27
Hi, 
I did everything but to no avail, still only Chrome is connected.
pgrep -a dnsmasq:
[COLOR=#222222][FONT=Verdana]> 2013 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d[/FONT][/COLOR]

dnsmasq --test:
> dnsmasq: syntax check OK.

sudo sed -i '/^dns=dnsmasq/s/^/#/' /etc/NetworkManager/NetworkManager.conf:
```
sudo: unable to resolve host Plato
```





nm-tool output:
> [COLOR=#222222][FONT=Verdana]NetworkManager Tool[/FONT][/COLOR]

State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1E:8C:6F:96:FE


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [Sofia] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        00:1C:BF:6B:8D:7F


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Vivacom-ap55:   Infra, 64:70:02:B4:47:EE, Freq 2462 MHz, Rate 54 Mb/s, Strength 86 WPA WPA2
    
  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1
    DNS:             8.8.8.8




---

### Post by schragge on 2014-12-27
> **errand said:**
> 
```
sudo: [COLOR=red]unable to resolve host Plato[/COLOR]
```

That's interesting. Are you able to use sudo at all? Try
```
sudo /bin/echo test
```
Are you still getting the same error message?

Citing [sudoers(5)]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html") manpage:
> Beware that when using DNS for host name resolution, turning on _fqdn_ requires **sudoers** to make DNS lookups which renders **sudo** unusable if DNS stops working (for example if the machine is disconnected from the network).  Also note that just like with the hosts file, you must use the &#8220;canonical&#8221; name as DNS knows it.
That is, you may not use a host alias (CNAME entry) due to performance issues and the fact that there is no way to get all aliases from DNS.

This flag is _on_ by default.

---

### Post by schragge on 2014-12-27
> **errand said:**
> &#8203;
my /etc/hosts:
```

...
127.0.1.1 [COLOR=red]Plato.Daniel[/COLOR]
...

```

This is a very strange name for Linux host (I mean, the domain part *Daniel*). The 127.0.1.1 is used for systems without permanent IP address. Usually it contains only hostname without the domain part. I'd expect here something like
```

127.0.0.1 localhost
127.0.1.1 plato

```
If your system however has a permanent IP address, it should be there instead of 127.0.1.1 together with [fully qualified domain name]("http://en.wikipedia.org/wiki/Fully_qualified_domain_name") of your system. Something like
```

127.0.0.1      localhost
192.168.0.101  plato.daniel.com plato

```

See [explanation]("https://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_hostname_resolution") in the Debian Reference.

> 
my /etc/nsswitch.conf
```

...
hosts:          [COLOR=red]files[/COLOR]
networks:       [COLOR=red]mdns4_minimal [NOTFOUND=return] dns mdns4[/COLOR] files
...

```

Here I would expect
```

hosts:      files  mdns4_minimal [NOTFOUND=return] dns mdns4
networks:   files

```
Looks like the rest of the first line somehow ended up on the second one. Currently, most programs on your system using standard GNU libc mechanisms probably don't use DNS for name resolution at all as *files* means they would only look up host names in */etc/hosts*. Some programs may consult */etc/host.conf* instead of */etc/nsswitch.conf* to determine the order in which host name resolution services are used.

If you're unable to edit */etc/hosts* and */etc/nsswitch.conf* because **sudo** refuses its duty, try [pkexec]("http://manpages.ubuntu.com/manpages/trusty/en/man1/pkexec.1.html") in its stead.

---

### Post by errand on 2014-12-27
This is what I got.
sudo /bin/echo test:

> sudo: unable to resolve host Plato

test




---

### Post by schragge on 2014-12-27
Well, sudo seems to work even if it cannot resolve the host name. Can you please edit */etc/nsswitch.conf* as shown in my previous post?

---

### Post by errand on 2014-12-27
I don't have permanent  IP address *sudo still *works even though it gives that message. I did cat /etc/hosts and /etc/nsswitch.conf again and noticed something unusual:
```

...
127.0.0.1[COLOR=#ff0000] localhost.localdomain localhost::1 Plato.Daniel localhost6.localdomain6 localhost6 localhost ip6-localhost ip6-loopback[/COLOR]
127.0.1.1 Plato.Daniel
...

```

I'm not sure how 127.0.1.1 has changed. My understanding is that you think that I should take ".Daniel" part. I'll read the Debian reference. Do you think that my comp. is compromised? I did change /etc/nsswitch.conf file here is the output:

```
passwd:         compatgroup:          compat
shadow:         compat


hosts:          files 
networks:     files mdns4_minimal [NOTFOUND=return] dns mdns4 


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis



```

Interestingly, after I changed the file and restarted the computer my Dropbox icon disappeared. Dropbox did try to install again but couldn't make connection with the server. It is too late for me I'll check the links that you sent me tomorrow. Thank you! I really appreciate you help!

---

### Post by schragge on 2014-12-27
First of all, your /etc/nsswitch.conf is still **wrong**. It should be
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat
group:          compat
shadow:         compat


hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

```

No, I don't think your computer is compromised. Why?

---

### Post by errand on 2014-12-28
Success! Everything is working browsers, Dropbox and sudo. Here is my latest *cat *output:

/etc/hosts
```
127.0.0.1 localhost.localdomain localhost::1 Plato.Daniel localhost6.localdomain6 localhost6 localhost ip6-localhost ip6-loopback


127.0.1.1 Plato


# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



```

/etc/nsswitch.conf
```
# /etc/nsswitch.conf#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat
group:          compat
shadow:         compat


hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files  


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files



```

> [COLOR=#000000]No, I don't think your computer is compromised. Why?[/COLOR]

The reason why I asked was that I didn't change any settings and suddenly, first my sudo command couldn't resolve host and then /etc/hosts file was changed without any input from me. How that line in /etc/hosts> [COLOR=#000000][FONT=Ubuntu Mono]127.0.0.1[/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono] localhost.localdomain localhost::1 Plato.Daniel localhost6.localdomain6 localhost6 localhost ip6-localhost ip6-loopback
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]127.0.1.1 Plato.Daniel[/FONT][/COLOR] changed is mystery to me and I'd like to understand what happened. I looked at the permissions of my /etc dir and there are some things that I don't understand e.g.```
lrwxrwxrwx   1 root root       15 Nov  6 21:18 blkid.tab -> /dev/.blkid.tab
``` I don't remember doing anything with that and can't find why permission changed and there is a link. I was looking through the logs but didn't find anything. One final question do I have to reverse?> [COLOR=#000000]Comment out the line [/COLOR]*dns=dnsmasq in file [I]/etc/NetworkManager/NetworkManager.conf by putting # before it...*[/I]

Thanks!

---

### Post by schragge on 2014-12-28
Yep. Uncomment that line in /etc/NetworkManager/NetworkManager.conf, your system should work fine with dnsmasq enabled by now.

[thread=1896148]Some programs[/thread] are known to modify /etc/hosts silently. And as it seems [thread=554771]NetwokManager is among them[/thread].

/etc/blkid.tab is a cachefile created by [blkid(8)]("http://manpages.ubuntu.com/manpages/trusty/man8/blkid.8.html"). It's probably [just an unfortunate design choice](https://lists.debian.org/debian-user/2007/04/msg00177.html) to keep it under /etc. On newer systems (I think, starting from Ubuntu 14.10) it's located in /run/blkid/blkid.tab instead.

---

