---
title: "ubuntu 14.04 ignores entry in /etc/hosts?"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by Mike_Küster on 2015-05-25
Hello,

this is my first post here and I hope, that is the right forum ...

I want to run my PHP development environment now in a virtual machine running Ubuntu 14.04 LTS. My Host - PC is runnig Windows 8.1 and I used for several years an virtual ubuntu server as development webserver.

My problem:

On the web server is an VirtualHost "example.com" with an alias "www.example.com". I changed my windows hosts file, in order to access the example.com website on the development server. Every thing is fine. Now I installed the normal desktop ubuntu 14.04 in another virtual machine an changed the /etc/hosts file in the same way as on the windows maschine:

```
...
192.168.1.60 www.example.com
192.168.1.60 example.com
...
```

I can ping to the www. and the non www. domain, but from the browser, I can only access the example.com domain. The [www.example.com]("http://www.example.com") could not be opened. :(
From the Window PC I can access both URLs, but from the deskop ubuntu only the example.com. So the webserver is ok. If I remove the example.com line, I couldn't access the site, so I is the right file and no caching seems to be envolved?

Do you have any suggestions for me?

Thanks,

Mike

Update: Hm, seems that this forum ignores german Umlauts while getting my profile from ubuntu one. Kster should be Küster ... ;)

---

### Post by SeijiSensei on 2015-05-25
The correct syntax uses a single IP address, the hostname, and one or more aliases like this:
```

192.168.1.60 www.example.com example.com

```

---

### Post by Mike_Küster on 2015-05-25
Hello SeijiSensei,

thanks for your fast response. That works (and is in contrast to the windows hosts file, where I can use several line for one ip)!

Ciao,
Mike

---

### Post by SeijiSensei on 2015-05-25
Glad I could help.  Sorry about that Umlaut!  If you have time, please open a thread in the [Forum Support](http://ubuntuforums.org/forumdisplay.php?f=48) to alert the moderators to this problem.

I didn't know the syntax was different in Windows. The manual page for the hosts file is available with "man hosts" and states:
> 
This file is a simple text file that associates IP addresses with hostnames, one line per IP address.  For each host a single line should be  present with the following information:

     IP_address canonical_hostname [aliases...]

Fields  of the entry are separated by any number of blanks and/or tab characters.

These specifications date back to the origins of the Internet.  Microsoft lifted the BSD stack pretty much intact when it added TCP/IP networking to Windows so I would have expected the hosts file syntax to be the same.

---

### Post by Mike_Küster on 2015-05-26
I opened a thread at the support forum for the "umlauts" ;)

This is the comment of the default windows hosts file:
```
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#    127.0.0.1       localhost
#    ::1             localhost

```
It's not clear, that more names in one row would work. I followed the: "Each entry should be kept on an individual line."  

But what does that mean? Each IP entry or each IP/name entry? ;)

Ciao,
Mike

---

