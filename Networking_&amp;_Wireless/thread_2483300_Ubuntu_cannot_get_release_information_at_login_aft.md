---
title: "Ubuntu cannot get release information at login after changing proxy settings"
date: 2023-01-25
forum: Networking &amp; Wireless
---

### Post by dbarnard2 on 2023-01-25
I have three servers, one running 18.04LTS and two running 20.04LTS. Since the time these servers were configured, my company's internet connection had a proxy which was mandated by our ISP. We have just changed ISPs, and the new provider doesn't use a proxy server. Prior to the changeover, I researched all the places the proxy settings needed to be changed. None of them had $HTTP_PROXY, $HTTPS_PROXY, or $FTP_PROXY variables set. All of them had a proxy configuration in /etc/apt/apt.conf.d which I deleted. one of them had proxies configured in /etc/wgetrc which I commented out. one of them had proxy settings in a .gitconfig file which I deleted. There were also several application-specific configurations which I updated as needed.

Following the changeover, everything is working as expected, including apt, wget, curl and the specific applications. However on two of the servers, the 18.04LTS and one of the 20.04LTS machines, where I am used to getting the message "New release '22.04.1 LTS' available. Run 'do-release-upgrade' to upgrade to it.", I am now getting the error "Failed to connect to [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts). Check your Internet connection or proxy settings". The third machine continues to show the upgrade message as expected.

I can access the referenced URL using curl, so I know that it's not a connectivity or DNS issue. I'm presuming that there must be another place where the proxy was configured during initial setup, but can't find any hints online. Does anyone know of anywhere else on the system where this proxy could be configured?

---

### Post by TheFu on 2023-01-25
I wouldn't spend any time on the 18.04 system. Support for it ends in a few months. Time to move it to a fresh install.  I'm in the same boat - a few 18.04 servers that need to be moved.  I won't be doing any upgrades. They will be fresh installs to avoid cruft from all the internal server changes and deprecated parts like ifupdown, netplan, resolved, and a few other areas.

---

### Post by lacrosby on 2023-01-26
Hey try this:

See if there is a value here

gsettings get org.gnome.system.proxy

back it up or document it, than clear it with this command, it takes affect immediately:

gsettings set org.gnome.system.proxy mode 'none'

---

