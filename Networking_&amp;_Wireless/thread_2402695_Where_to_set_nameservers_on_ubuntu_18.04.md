---
title: "Where to set nameservers on ubuntu 18.04"
date: 2018-10-03
forum: Networking &amp; Wireless
---

### Post by annusar9876 on 2018-10-03
When I google, I get different answers for "where to set nameservers on ubuntu 18.04?" 
could someone answer precisely and how to restart network service or any other steps to follow?
Thanks in advance!!!

---

### Post by chili555 on 2018-10-03
In Settings -> Network and select either Wired or Wireless as appropriate and click the little gear symbol. Select IPv4 settings and turn DNS Automatic to Off. Enter your preferred DNS nameservers: [https://i.stack.imgur.com/xaRXf.png](https://i.stack.imgur.com/xaRXf.png)  Click Apply.

Restart NM:```
sudo service network-manager restart
```You should be all set.

---

### Post by annusar9876 on 2018-10-04
Thanks!! Could you tell how to do the same on command line? My X-window is not showing up. Thanks again..

---

### Post by chili555 on 2018-10-04
> **annusar9876 said:**
> Thanks!! Could you tell how to do the same on command line? My X-window is not showing up. Thanks again..Are you otherwise connected to the internet?```
ip addr show
```If you havd a valid IP address but can't reach the internet, that suggests hat something has gone wrong with the DNS resolution system. You can work around it temporarily, that is, until the next reboot, with this:

```
sudo -i
echo "nameserver 8.8.8.8"  >> /etc/resolv.conf
exit

```Then you should be able to reach the internet.

When you have your other issues fixed, we'll need to troubleshoot and repair the resolve system.

If you do *not* have a valid IP address, then you are not yet connected to the internet and haven't yet received an IP address, gateway and DNS namesever by DHCP. Merely forcing a temporary DNS nameserver without an IP address will not be helpful.

---

### Post by annusar9876 on 2018-10-05
I am using Virtualbox and I dont see ip address assigned (see attachment). What's the next step - how to get valid ip address?

---

### Post by chili555 on 2018-10-05
> **annusar9876 said:**
> I am using Virtualbox and I dont see ip address assigned (see attachment). What's the next step - how to get valid ip address?Generally, networking in VirtualBox is set in Devices > Network > Network Settings. NAT will use the network of the host machine. If the host machine is connected to the internet correctly, NAT will generally allow the guest OS to connect automatically.

Is the setting you are using?

---

### Post by annusar9876 on 2018-10-06
I googled and found your suggestion of doing 'ifdown and ifup", which helped me to get the ip address. So, its resolved now.. Thanks a lot.. :)

---

