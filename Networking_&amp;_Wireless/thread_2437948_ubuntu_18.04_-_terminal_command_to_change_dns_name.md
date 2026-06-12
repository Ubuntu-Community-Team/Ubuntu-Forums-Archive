---
title: "ubuntu 18.04 - terminal command to change dns nameserver"
date: 2020-03-03
forum: Networking &amp; Wireless
---

### Post by crabbychicken on 2020-03-03
Hi,

I used to modify:

/etc/resolv.conf

but that does not do the trick anymore - bad news for me.

Is there a terminal command that I can put in a bash script to change dns servers?

I need to set the dns to 192.168.11.11 to block access to the internet while I update my grub install without downloading updates from the internet.

I then want to switch the dns back to 192.168.1.1 for web browsing.

Things have changed and I can't seem to figure anything out - I'm using ubuntu 18.04 desktop - files inside /etc/netplan did not do anything.

I can switch things in the network manager gui but I need a bash script option.

Big thanks.

---

### Post by TheFu on 2020-03-03
resolv.conf is controlled by one of many different possible management tools, because letting humans edit the file was too hard.  If you are using network-manager to control those settings, then you need to use network-manager to change them. There is an nm-cli program.

---

### Post by webaake on 2020-03-04
systemd-resolved took over the old resolv.conf. It's not good. But you can disable it and go back to the old way. In my case I got a performance increase with DNS resolving. How to:

[https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu](https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu)

---

### Post by Rick St. George on 2020-03-05
I'm havaing the same problem, trying to change and get rid of Google crap and Mozilla's change to utilize ONLY CloudFlare DNS servers. So much conflicting info, and there is nothing in my NetPlan folder. So just how can we find out what is changing, modifying, utilizing other cross-scripts etc. on our computers?  Even the above (quoted below) has conflicting info that didn't work for everyone in that thread.  > **webaake said:**
>  DNS resolving. How to: [https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu](https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu)  There should be definitive documentation on this subject matter.  I'm running Xubuntu & UbuntuStudio v18.04 LTS. Anyone have a clue? for the rest of us!?!? If so, please post a Link to it and make it a STICKY.  Thanks!

---

### Post by TheFu on 2020-03-05
Perhaps this is the documentation?    [https://manpages.ubuntu.com/manpages/bionic/man1/nmcli.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/nmcli.1.html)
If you have **nmcli** installed, that information is already on the machine.
```

       nmcli con modify ABC +ipv4.dns 8.8.8.8
           appends a Google public DNS server to DNS servers in ABC profile.
```

Because Ubuntu is highly customizable, there are multiple different DNS solutions.  Swapping out the systemd one isn't hard, if that is what your system is using instead of network-manager.  Been using dnscrypt-proxy here for about a year on desktops.

Google found this for xubuntu 18.04: [https://docs.xubuntu.org/1804/user/C/internet-networks.html](https://docs.xubuntu.org/1804/user/C/internet-networks.html)
Looks like they use nmcli.

---

### Post by webaake on 2020-03-06
Here's a link to the original resolvconf, the basic DNS resolver that's been forever: [https://en.wikipedia.org/wiki/Resolvconf](https://en.wikipedia.org/wiki/Resolvconf)

As a side note; systemd seems to engulf more and more of system services and it is harder to configure manually than for example a simple resolv.conf file. Or /etc/resolvconf/resolv.conf.d/tail

---

### Post by SeijiSensei on 2020-03-06
On modern distributions that use systemd-resolved for name resolution, you can control the servers it consults by modifying the "DNS" and "FallbackDNS" lines in /etc/systemd/resolved.conf.  You could maintain two copies of that file and choose the one you need when you want to change servers.  You'd need to run "sudo systemctl restart systemd-resolved" after you've made the change.

See "[man resolved.conf]("https://manpages.debian.org/testing/systemd/resolved.conf.5.en.html")" for more details.

---

