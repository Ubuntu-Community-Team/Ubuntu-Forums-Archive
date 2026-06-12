---
title: "Can't seem to configure ethernet  on Focal 20.04.3 LTS (Server)"
date: 2022-01-09
forum: Networking &amp; Wireless
---

### Post by mighty-maestro on 2022-01-09
I've loaded Ubuntu 20.04.3 Server onto an Intel NUC (NUC5i3RYH)

The WiFi works fine but as a server I want to utilise the ethernet port. I have been around and around in circles and looked up so much help that now I am confused.

Here is the results from the ifconfig, the route -n, the resolv.conf and /etc/netplan/00-installer-confg.yaml files.
I've loaded net-tools. There is no /etc/network/interfaces file.
I know this should be simple, but I've had so much trouble with the NUC, that I have lost confidence in this problem.

Thanks for any help.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289768&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289770&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289769&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289767&stc=1[/IMG]

---

### Post by The Cog on 2022-01-09
In ifconfig, two flags are very important. 
Firstly UP is there - that means the OS wants the interface to come up, i.e. it is enabled. Good.
Secondly, RUNNING is missing. This is the flag that says the cable has been detected and the link has come up. Bad. Check that the cable is plugged in.

If you use the **ip link** command instead of **ifconfig**, you would be looking for LOWER_UP instead of RUNNING. Ip link has the advantage of showing NO_CARRIER if there is no cable signal detected.

If you are sure the cable is good and ip link still says no carrier, then maybe it's time to check the drivers - **sudo lspci -v** will show the driver in use. But that reaches the limit of my drivers knowledge I'm afraid.

---

### Post by chili555 on 2022-01-09
I think the spacing, indentation, etc. are a bit off in your netplan file. Please see:

```
cat /usr/share/doc/netplan/examples/static.yaml
```Please amend the file and follow with:

```
sudo netplan generate
sudo netplan apply
sudo dmesg | grep enp

```
Please post the result.

---

