---
title: "My internet access stopped working"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by PaulBx on 2013-10-06
Have a real head-scratcher here, hope someone can help.

I'm running the latest Lubuntu and have been using the software update up to a couple days ago on my Lenovo laptop. Everything worked.

Yesterday it stopped connecting to the internet. I am currently using a Verizon hotspot for both the Lenovo and this machine I'm typing on now (my old Dell Mini 9). So since the Dell (running Puppy Linux) runs this setup, the problem must be in the Lenovo. The hotspot has both wireless and ethernet-over-usb, both of which work for the Dell and neither of which now work for the Lenovo (although they did work there previously).

I tried disabling the ufw firewall on the Lenovo but that didn't help.

When I do an "ifconfig" I get "UP BROADCAST RUNNING MULTICAST", just like it normally does (on whichever interface I'm trying to use). The "RX bytes" and "TX bytes" show some data transfer going on, and there are no errors.

I can ping both the hotspot and 8.8.8.8.

OK, so I was thinking this sounds like some sort of DNS problem. However I cannot access the hotspot by putting 192.168.1.1 in the browser on the ethernet link; the thing just times out, just like any other website I try to access. However it is strange, when I put that address in the browser, the timeout message responds with a timeout message pointing to a URL (mifi.something) rather than the numeric address I entered, so maybe DNS is still involved in that.

I'm at a loss what to try next. Any suggestions will be appreciated.

---

### Post by PaulBx on 2013-10-06
Oh, I thought I'd try email (my browser/email client is Seamonkey). If I try to get email it gets nothing. If I try to send a test email to myself, I get this message:
"Sending of message failed. An error occurred sending mail: SMTP server smtp.tctwest.net is unknown. The server may be incorrectly configured. Please verify that your SMTP server settings are correct and try again."

BTW in case you are wondering, I did nothing special in the last few days to this machine. Just web browsing and email.

---

### Post by PaulBx on 2013-10-06
It's definitely DNS!

I just hooked the Lenovo to an old Linksys wrt54g router I had, and entered 192.168.1.1 in my browser and it accessed the router just fine. I'm pretty sure that router just serves up the web page from within the router, not using DNS at all, while the hotspot seems to go out on the internet for content.

So now I have to figure out how DNS works. Probably some file down in /etc got borked.

---

### Post by steeldriver on 2013-10-06
With newer versions of Ubuntu (including Lubuntu, afaik) the default setup is via a service called resolvconf and you shouldn't manually edit the /etc/resolv.conf file - if you've already done so then you may need to reconfigure it

```
sudo dpkg-reconfigure resolvconf
```

I'd suggest answering 'Yes' to the "Prepare /etc/resolv.conf for dynamic  updates?" question and 'No' to the one about temporarily appending your  existing config to the dynamic one. Then reboot.

This is only a guess - there are other possibilities based on what you have posted so far.

---

### Post by PaulBx on 2013-10-06
Yes, it's that. I had been running arch linux and recently moved to lubuntu. I had some scripts there to access a VPN server which fiddled with resolv.conf and sometimes it leaves it in a wrong state (not restoring the original data), but I would just manually restore resolv.conf when that happened. Now over here resolv.conf is dynamic so I will have to figure out how this is supposed to work. Is there a way to just go back to a manual resolv.conf? I will look at the wiki and so forth to figure things out. So far the resolvconf man page is not very illuminating...

---

### Post by PaulBx on 2013-10-06
OK, your dpkg-reconfigure recipe got my internet working again, thanks so much! (there was no question about temporarily appending the existing one)

Strangely, I see only the nameserver 127.0.1.1 in there. I wonder where it's going for the service? Maybe I'm running a name server and don't even know it. This stuff makes my head hurt. I had a better handle on it back in the days when everything was manually configured...  :confused:

Now I will have to look at my old VPN scripts and modify them to use resolvconf I guess.

---

### Post by steeldriver on 2013-10-06
If your resolv.conf is showing 127.0.1.1 it means that the system is using dnsmasq - a local caching DNS forwarder. That's also normal for newer (desktop) versions. The upstream servers will either be pushed from your router via DHCP or may be set manually via network-manager / nm-connection-editor (in the IPv4 Settings tab).

[https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

My understanding is that resolvconf/dnsmasq are intended to make VPN routing easier but I don't have any experience with that, I'm sure someone else will be able to help you if you get stuck.

---

### Post by PaulBx on 2013-10-06
I changed the script that used to overwrite resolv.conf to this: ```
 #!/bin/sh  case "$1" in    up) export action="up" ;;    down) export action="down" ;;    *) echo "No action specified." && exit 1 ;; esac      if [ "$action" = "up" ]; then    echo $foreign_option_1 | sed -e 's/dhcp-option DOMAIN/domain/g' -e 's/dhcp-option DNS/nameserver/g' >  /etc/resolv.conf.openvpn    echo $foreign_option_2 | sed -e 's/dhcp-option DOMAIN/domain/g' -e 's/dhcp-option DNS/nameserver/g' >> /etc/resolv.conf.openvpn    echo $foreign_option_3 | sed -e 's/dhcp-option DOMAIN/domain/g' -e 's/dhcp-option DNS/nameserver/g' >> /etc/resolv.conf.openvpn /sbin/resolvconf -a "tap0.openvpn" < /etc/resolv.conf.openvpn fi  if [ "$action" = "down" ]; then    /sbin/resolvconf -d "tap0.openvpn" fi 
```  It seems to do the job! I did not bother to add any code in there for if resolvconf did not exist.  I was wondering what the network manager was. I have both an /etc/network and an /etc/NetworkManager directory. I just use what is default with lubuntu 13.04. whatever that is. It's the doohickey on the taskbar just to the left of the clock. That thing also has a way to set up VPN connections but I haven't looked into it. I just start mine at the command line.  Huh, the forum software just smashed my post together, throwing away the newlines. Wonder why...

---

