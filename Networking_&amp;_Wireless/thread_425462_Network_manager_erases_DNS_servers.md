---
title: "Network manager erases DNS servers"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by steve0921 on 2007-04-27
When I upgraded to feisty the network manager was installed and, though it seems to work well, I am having troubles with DNS servers. Whenever it starts (on boot or resume) it erases /etc/resolv.conf except for a commnet saying that it has edited the file.

In looking through the forums, I have seen people for whom dhclient sets their router's IP as the nameserver and erases custom ones, but for me the file is simply empty and network manager reports a DNS server of 0.0.0.0. I changed dhclient.conf according to the fixes for that problem, but mine is still unresolved.

Does anybody know how to fix this?

Also, I tried uninstalling network manager when I got sick of it (removed network-manager, network-manager-gnome and libnm-util0) but there was still a NetworkManager process running that would still screw up resolv.conf.

I would also settle for directions on completely removing network manager.

Thanks.

---

### Post by dannyboy79 on 2007-04-27
you even added the prepend line within your dhclient.conf file per this: [http://ubuntuforums.org/showthread.php?t=295567](http://ubuntuforums.org/showthread.php?t=295567)

---

### Post by steve0921 on 2007-04-27
Yes, I added the prepend line. Also, I removed domain-name-server (or something like that) from the request line as per other instructions I'd found on the forums.

---

### Post by steve0921 on 2007-04-29
In case anybody comes back to this thread, I will resolve it.

I gave up. This issue made network-manager more of a pain than a benefit so I just removed it, and deleted the init.d and rc.d files that didn't seem to be in any packages. I configure networks the old fashioned way, but at least I don't need to edit a config file whenever I wake my computer up.

---

### Post by siloko on 2007-05-02
try using supersede instead of prepend in your dhclient.conf:

supersede domain-name-servers 111.111.111.111

(replacing 111.111.111.111 with the ip address of your ISP's dns server)

worked for me with exactly the same problem . . .

cheers

stuart

---

