---
title: "No internet after upgrade from 16.04 to 18.04"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by herido on 2018-08-23
After the prompted upgrade from 16.04 LTS to 18.04 the interet icon in the top right corner was gone and all that is left is the VPN section.

In "Settings > Network" there is a ethernet cable option. The settings are all automatic and that used to work ok.

I tried this solution but no success!> [https://askubuntu.com/questions/1021884/no-internet-after-upgrade-from-16-04-to-18-04](https://askubuntu.com/questions/1021884/no-internet-after-upgrade-from-16-04-to-18-04)

I can't even ping the router. Where should I look now?

---

### Post by Autodave on 2018-08-23
I rarely have any luck upgrading: I always do a clean install.

Can you connect with a cable and download 18.04? If so, burn that to a DVD or your USB stick and boot from that. Then check to see if you wireless will work. If so, I would save myself a lot of hassle and do a clean install.  Make sure that you back up everything that you need to save first!!!!!

---

### Post by geoff20 on 2018-08-23
I have had the same experience with the same advice.
If this is a problem then the option to upgrade should not be offered.
Being told that you should have done a clean install is not good enough after it has happened.
Exactly what should you back up so that a clean install will only require you to activate the back up so that settings and software are reinstalled with minimum effort and time.
I spent hours setting up 16.04 again after the upgrade and I'm still trying to work out why I lost networking.
I have backed up 16.04 but I'm not convinced that if I upgrade again to 18.04 with a fresh install it will be a simple process.

---

### Post by herido on 2018-08-24
Well, I'm going to do a fresh install then.

Thank you for the suggestions.

---

### Post by merlinus on 2018-08-27
I had the exact same problem with all three of my computers after upgrading.  This solved the issue for both wired and wireless connectivity:

$ gksudo gedit /etc/resolvconf/resolv.conf.d/base

Then put your nameserver list in like so:

nameserver 8.8.8.8

$ gksudo gedit /etc/resolvconf/resolv.conf.d/head

nameserver 8.8.8.8

Then update resolvconf:

$ sudo resolvconf -u

---

### Post by thomas-runge on 2018-09-18
I agree this is a workaround, but it's not a final solution.

For Laptops that are travelling there's definitely an issue if they're using their company DNS when in office. The company DNS is not available in external locations, while 8.8.8.8 might not be good enough in the office.
We need a final solution that makes use of the DNS server(s) provided by DHCP.

Thomas

---

