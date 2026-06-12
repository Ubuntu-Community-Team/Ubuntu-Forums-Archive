---
title: "Wireless working, but with errors - log inc"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Coolit on 2007-01-22
Hi All,

I've just installed Ubuntu 6.10 on my new laptop, setup wireless networking through Network Manager and it works great, it has an Intel 2200BG card fitted so is well supported. I then setup Beryl and AXGL as per the guide on the wiki and they work great also.

The problem is there is a really long delay now until my wireless connects to my network when I login, so I decided to investigate and in real time watched for errors being written to the system log file and there are a few,

> Jan 22 21:58:40 laptop1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jan 22 21:58:55 laptop1 dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jan 22 21:58:55 laptop1 dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Jan 22 21:58:55 laptop1 dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jan 22 21:58:55 laptop1 dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Jan 22 21:58:55 laptop1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Jan 22 21:58:55 laptop1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Jan 22 21:58:55 laptop1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jan 22 21:58:55 laptop1 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

I suspect something that has been installed with the AXGL/Beryl packages has changed or overwritten a file somewhere and so its missing, any ideas?

I would be extremely grateful if someone can help solve the problem, thanks;)

---

### Post by wacqy on 2007-01-25
It probably isn't Beryl's fault. I had this problem as well, and what worked was for me to edit my network interfaces file. Which means no network manager. Try following this: [U][HOWTO: Wireless Security]("http://www.ubuntuforums.org/showthread.php?t=318539")
[/U]

---

### Post by dmorris68 on 2007-03-20
On the contrary, I think Beryl might have something to do with it.  I say that because I had my wireless working fine, without the startup delay, until I installed Beryl.  Ever since I get a really long delay, with the Ubuntu startup splash staying up for a long time, and NetworkManager takes about 1-2 minutes to finally activate the network.  My logs also contain the same message_handler errors as indicated by the OP.

I'm not willing to give up NetworkManager just for this, though.  I roam between different wireless networks, and I never could get wpa_supplicant to auto-roam reliably despite following all the HOW-TO's to the letter.  I more often than not had to stop/start interfaces manually and even logout/reboot on occasion to get wireless working.  Since going back to NM everything has worked beautifully, with this exception since installing Beryl.

---

