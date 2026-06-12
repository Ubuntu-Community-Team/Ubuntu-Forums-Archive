---
title: "[SOLVED] Is this a Lan driver problem?"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by leetrefz on 2007-11-15
I've just set up my new VIA PX computer. Xubuntu runs great except for the internet. It worked through my router on the first boot, but from the 2nd boot on it's only worked one mystical time. Usually the green light in the LAN port flashes nonstop. My router and cable work with another computer. I've downloaded the LAN driver from VIA Arena. It's readme says it's for Ubuntu 6.1 and that the archive I downloaded has 3 files: binary, source, & patch for kernel 2.6.19 though I only see the patch. It goes on to tell me how to use the OS built in driver inc in Ubuntu 6. "It will automatically enable the controller after installation" 'but if it doesn't, do it manually with: > #modprobe via-rhine
#ifup eth0 <IP address> 'with DHCP server no need for IP address.' not sure what a DHCP server is, but I think I should have a dynamic address. have tried those commands as is and with the router address. As a casual user I don't know if it matters if LAN cable is in when putting in those commands. They just carriage return, no other feedback. LAN port still blinks like a maniac, firefox: "looking up http..." 

When shutting down I get a look at this piece of modern art:
> NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1195099974.971758] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1195099974.972073] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device eth0.

NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - connection is closed.

NetworkManager: nm_dbus_signal_device_status_change: assertion - `cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion - `cb_data->data->dbus_connection' failed
There's nothing else I've tried or know to try, no matter how elementary. Thanks for any help, but please, I'm not the kind to be able to fill in the blanks in any terminal effusion.

---

