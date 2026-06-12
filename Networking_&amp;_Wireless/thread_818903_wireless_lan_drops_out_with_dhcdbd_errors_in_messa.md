---
title: "wireless lan drops out with dhcdbd errors in messages"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by melon_bread on 2008-06-04
Hi everyone,

I've recently upgraded to a new kernel 2.6.24-17-generic (running hardy heron 8.04 - latest updates), and ever since them my wireless connection drops out after about 1/2 an hour of use. It stays down and can't find the wireless network. I get the following in /var/log/messages.

```
Jun  2 02:16:40 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun  2 02:16:40 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun  2 02:16:40 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun  2 02:16:40 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jun  2 02:17:45 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:17:45 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_rebinding_time = -1
Jun  2 02:17:45 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:17:45 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_renewal_time = -1
Jun  2 02:17:45 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:17:45 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1
Jun  2 02:23:51 maki kernel: [ 1336.818363] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 02:25:38 maki kernel: [ 1376.694070] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_rebinding_time = -1
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_renewal_time = -1
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_renewal_time = -1
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1
Jun  2 02:25:46 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:46 maki dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_rebinding_time = -1
Jun  2 02:25:46 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun  2 02:25:46 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun  2 02:25:46 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun  2 02:25:46 maki dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jun  2 02:25:47 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:47 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_rebinding_time = -1
Jun  2 02:25:47 maki dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun  2 02:25:47 maki dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_renewal_time = -1
```

I've done a google search and found that this has happened before on an older version of ubuntu (around 2006) and its been fixed since then. I know that dhcdbd provides an interface to dhclient that allows Networkmanager to talk to the interfaces. 

So I'm not sure if this is a wireless problem or something to do with my Networkmanager or both.

If anyone can help me resolve this that would be great!

thanks

melon_bread

---

### Post by AmonSacha on 2008-06-21
Bump: I'm having the same exact problem 
I'm using the RT2500 driver

---

### Post by jsblackmaro on 2008-07-22
I am having that same problem  Heres what I get:

message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name

I saw in a post I need to modify my etc/network/interfaces file with my essid, and key.  Is this correct?

Please help.  I can move the mouse, and it freezes, and gives this message!

---

### Post by fredb987 on 2008-11-09
I'm running Ubuntu 8.04.01 and was having the same exact problem with wlan0 dropping out and the mouse freezing up briefly. My logs were filled with hundreds of these error messages:


[INDENT]Nov  8 10:53:33 nx7300 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu[/INDENT]


This drove me crazy ALL DAY yesterday. This started after updating the kernel to 2.6.24-21, I think.

But here's what fixed it! Removing this section from my xorg.conf file:


[INDENT]#Section "Module"
#	Load "i2c"
#	Load "bitmap"
#	Load "ddc"
#	Load "extmod"
#	Load "freetype"
#	Load "glx"
#	Load "int10"
#	Load "type1"
#	Load "vbe"
#	Load "dri"
#EndSection[/INDENT]


I added the above section to my /etc/X11/xorg.conf file in order to test something which was completely unrelated to the wlan issue. At any rate, one of the loaded modules seems to be the culprit, because removing the section immediately fixed the issue!

Strange connection here - can anyone tell me what relation my xorg settings would have with my wireless connection?

Thanks,
Fred

---

