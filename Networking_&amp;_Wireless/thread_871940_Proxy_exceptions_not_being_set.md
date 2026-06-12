---
title: "Proxy exceptions not being set"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by prototype_angel on 2008-07-27
Hi,

My university has a local ubuntu repository, which I use, along with some other repositories for some other software, which are on the internet.

Trouble is, we use a proxy for connecting to the internet. Setting the proxy in the network proxy area seems to do the trick, but I'd like ubuntu to ignore the proxy for 10.3.140.50, and use it for everything else.

In the "advanced configuration" tab of the proxy settings, I've added "10.3.140.50" to the ignore host list, but it doesen't seem to help.

I even tried 10.0.0.0/8 and 10.*.*.*, neither seems to be working.
I'd also like to write a shell script to set this. export HTTP_PROXY="myproxy:port" seems to work fine, so how do I manually add it to the ignore list?

Thanks

---

### Post by prototype_angel on 2008-07-28
I'm not able to set the option in KDE either. Should I reinstall?

---

### Post by jonvel on 2010-03-16
> **prototype_angel said:**
> Hi,

My university has a local ubuntu repository, which I use, along with some other repositories for some other software, which are on the internet.

Trouble is, we use a proxy for connecting to the internet. Setting the proxy in the network proxy area seems to do the trick, but I'd like ubuntu to ignore the proxy for 10.3.140.50, and use it for everything else.

In the "advanced configuration" tab of the proxy settings, I've added "10.3.140.50" to the ignore host list, but it doesen't seem to help.

I even tried 10.0.0.0/8 and 10.*.*.*, neither seems to be working.
I'd also like to write a shell script to set this. export HTTP_PROXY="myproxy:port" seems to work fine, so how do I manually add it to the ignore list?

Thanks

I hate to bring up a 2+ year old topic, but I'm having the same issue.  I can't seem to figure out what the proxy exception format is for this section.  I tried the formats described above (Firefox uses the first one, IE uses the other), but it's not working.

---

### Post by qwill on 2011-10-14
And it's even worse in Oneiric Ocelot (11.10) .. the exception tab and fields have disappeared !!!

The data has to be set using the dconf-editor tool, under the key /system/proxy/ignore-hosts

---

### Post by jllarden on 2011-10-21
Configuring advanced proxy settings is unfortunately cumbersome and error-prone in Oneiric Ocelot (11.10). I thought I had understood the quirks to make it work properly, but I'm forced to use workarounds:
[LIST]
[*]Firefox: I use manual proxy configuration
[*]apt-get/Update Manager: I use /etc/apt/apt.conf.d/99proxy, which I created with contents (adapt to your own proxy):```
Acquire::http::Proxy "http://proxy.mycompany.ch:8080";
Acquire::https::Proxy "https://proxy.mycompany.ch:8080";
```
[/LIST]

---

