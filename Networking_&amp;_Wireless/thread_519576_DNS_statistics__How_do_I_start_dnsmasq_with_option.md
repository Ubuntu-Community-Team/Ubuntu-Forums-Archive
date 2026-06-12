---
title: "DNS statistics / How do I start dnsmasq with options every time?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by tillkowski on 2007-08-07
I only have a basic understanding of this, I'll try to be as clear as possible about my problem:

My server runs dnsmasq for DHCP and DNS services. I want to find out which domain name requests it receives from my local network.

The plan is this:
[LIST=1]
[*]Enable logging in /etc/dnsmasq.conf, this will make dnsmasq write pretty much everything to /var/log/syslog
[*]Specify a separate file to write the output to (Apparently this is possible by starting dnsmasq with the option --log-facility=[filename] )
[*]Do some cron / shell script / OOo magic
[*]See statistic of requested domains
[/LIST]

Currently I'm stuck at step 2. I know I can restart dnsmasq with the command ```
#/etc/init.d/dnsmasq restart
``` and I took a glimpse at the script (/etc/init.d/dnsmasq). I'm guessing there's an easy way to modify it to always start dnsmasq with an option, but I'm not sure how and I don't want to break anything.

Can somebody please help me out?

If anyone has a better idea of how to get  statistics, I'm open to suggestions. An account at OpenDNS doesn't work for me because my ISP doesn't give me a fix IP. I'm also reluctant to configure a full-blown DNS server because the configuration manual confused the hell out of me.

---

### Post by stiV on 2008-04-02
i know it's a little late ... but you could use the output from dnsmasq and try writing a plugin for "munin" - it's pretty easy ;)

---

