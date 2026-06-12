---
title: "Ubuntu 14.04, Not network access"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by loutchoa on 2016-01-29
Hello,

I have lost my network accesses: wireless and ethernet are not working. When accessing System Settings->Network, I get the message
"The system network services are not compatible with this version".
It does not seem to be caused by a recent upggrade, at least in /var/log/apt I cannot see a network-manager update today or yesterday, and ethernet was functioning 2 hours ago at work, but not here at home (no problem with other computers...)
 I have a network-manager-gnome 0.9.8.8-Oubuntu4.4 installed. I have no idea what type of log I should provide, and of course any help would be immensely appreciated!

Francois

---

### Post by bswarm2 on 2016-01-29
When I did an update yesterday the same thing happened after restarting. The update broke networking. See if my post helps... [http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)

---

### Post by ajgreeny on 2016-01-29
Enabling the proposed repositories, if that is what you have done, is often not a good idea unless you know how to solve breakages, which are more likely with proposed packages than others.

If you do have them enabled I suggest you disable them and use only the remaining three from in Updates tab of Software-sources.

---

### Post by loutchoa on 2016-01-29
Thanks for the two posters, downgrading libnl did the job, and I unchecked the pre-release !
Cheers,
François

---

### Post by fangorn2 on 2016-01-29
Same problem today after update for me and my 12 year old nephew that I recently convinced to use Ubuntu.
So two machines in the same day after last update. And it seems an old issue: [link1]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1127151") [link2]("http://fossevangelist.blogspot.it/2014/01/the-system-network-service-is-not.html") [link3]("http://askubuntu.com/questions/129436/restarted-computer-during-update-the-system-network-service-is-not-compatible") 
As far as me and my nephew are concerned, after update and restart we receive a warning massage:

Sorry, Ubuntu 14.04 has experienced an internal error

Package: network-manager 0.9.8.8-0ubuntu7.2
Problem Type: Crash
Title: NetworkManager crashed with SIGSEGV in nm_netlink_monitor_attach()
ApportVersion: 2.14.1-0ubuntu3.19
Architecture: amd64
ifupdownConfig: 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
...

Like loutchoa, when accessing System Settings->Network, we get the message "The system network services are not compatible with this version".
By the way we also had the "pre-released updates" box checked in our software updates.
I do not want to update the machine I am using now until we find a common and definitive solution for this long lasting issue.
Considering what other users with same issue have suggested, we are a bit confused by the many solutions that seem to be in Internet, some of them quite disturbing like [this]("https://pratiklahoti.wordpress.com/2012/06/26/ubuntu-12-04-the-system-network-services-are-not-compatible-with-this-version/"). Any help in going through all this will be appreciated.

---

### Post by fangorn2 on 2016-01-30
[**[COLOR=#000000]bswarm2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928080") solution solved my issue and that of many others.
Check if you also have the same libraries installed recently by looking at the history logfile of installed packages in var/log/apt/history.log

---

