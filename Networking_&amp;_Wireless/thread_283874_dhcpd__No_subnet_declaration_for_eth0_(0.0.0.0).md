---
title: "dhcpd  No subnet declaration for eth0 (0.0.0.0)"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by dwanders on 2006-10-24
I have just finished using the setup steps at easylinux to try and setup a dhcp server for my home LAN, and I am getting the following error each time I try to start it:

Oct 24 18:53:58 localhost dhcpd: Wrote 0 leases to leases file.
Oct 24 18:53:58 localhost dhcpd:
Oct 24 18:53:58 localhost dhcpd: No subnet declaration for eth0 (0.0.0.0).
Oct 24 18:53:58 localhost dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 24 18:53:58 localhost dhcpd:    you want, please write a subnet declaration
Oct 24 18:53:58 localhost dhcpd:    in your dhcpd.conf file for the network segment
Oct 24 18:53:58 localhost dhcpd:    to which interface eth0 is attached. **
Oct 24 18:53:58 localhost dhcpd:
Oct 24 18:53:58 localhost dhcpd:
Oct 24 18:53:58 localhost dhcpd: Not configured to listen on any interfaces!

I currently have the computer I am setting up statically set:
192.168.254.100 255.255.255.0 and this is the server I would like to use.

my dhcpd.conf has:
ddns-update-style none;

subnet 192.168.254.0 netmask 255.255.255.0 {
  range 192.168.254.200 192.168.254.210;
  option domain-name-servers 192.168.254.5;
  option domain-name "daxqu.org";
  option routers 192.168.254.5;
  option broadcast-address 192.168.254.255;
  default-lease-time 600;
  max-lease-time 7200;
}

and I am not sure what I am missing? I also have 
INTERFACES="eth0"
in my /etc/defaults/dhcp3-server

Any help is greatly appreciated.

---

### Post by dwanders on 2006-10-25
Boy this one is tearing up the charts! :)

Well I found that I could try sudo dpkg-reconfigure dhcp3-server and get it to do some stuff, but now when I try and run /etc/init.d/dhcp3-server restart
I am getting this:

invoke-rc.d: initscript dhcp3-server, action "start" failed.

Once again, any help with this matter would be greatly appreciated.

---

### Post by dwanders on 2006-10-29
Wow, I cannot believe there was not one response to this post other than my own. Anyway, for anyone interested, finally got the problem resolved by installing Edgy, and GDHCPD to configure it. After that it seems to be running like a champ.

---

### Post by arstanj on 2007-07-06
Hello,
you should comment out the ltsp config lines in dhcp3 start script(/etc/init.d/dhcp3-server).
I blogged more here [http://www.jusupov.com/2007/07/06/how-to-install-dhcp3-server-in-ubuntu/](http://www.jusupov.com/2007/07/06/how-to-install-dhcp3-server-in-ubuntu/)

---

