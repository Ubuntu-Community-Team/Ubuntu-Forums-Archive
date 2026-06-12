---
title: "WHy DBUS assuming NetworkManager when NM not installed."
date: 2019-10-06
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-10-06
I have purged Network Manager, removed all Network Manager directories yet I am still seeing applications and services that are assuming NM and expressing distress that it is not. 

     whoopsie[1094]: [17:01:15] 
    GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name 
    org.freedesktop.NetworkManager ...


Where in the configuration system is this referenced?

Is it inefficient that the system is configured in this way -- where there are so many parts looking for this one application that does not exist. 

How would it be not better practice for Network Manager to register its existence and advertise its compliance with a system-established protocol. 

The way it seems to be configured is backwards to me. The system should not be running out looking for programs that just *might* be there. Is NM unique in this way or is this standard API for Linux desktops?

---

### Post by Skaperen on 2019-10-06
maybe the packages those applications come from should have a dependency on network-manager.  what is your reason for "purged Network Manager"?

---

### Post by wildmanne39 on 2019-10-06
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by holiday on 2019-10-07
> **Skaperen said:**
> maybe the packages those applications come from should have a dependency on network-manager.  what is your reason for "purged Network Manager"?

```
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provide
```

I find these reference in the dbus config. Can you tell me anything about these. Can I simply remove these references or are there references/dependencies elsewhere that will break. 

```
nm-openvpn-service.conf:		<allow own_prefix="org.freedesktop.NetworkManager.openvpn"/>
nm-openvpn-service.conf:		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
nm-openvpn-service.conf:		<deny own_prefix="org.freedesktop.NetworkManager.openvpn"/>
nm-openvpn-service.conf:		<deny send_destination="org.freedesktop.NetworkManager.openvpn"/>
nm-pptp-service.conf:		<allow own_prefix="org.freedesktop.NetworkManager.pptp"/>
nm-pptp-service.conf:		<allow send_destination="org.freedesktop.NetworkManager.pptp"/>
nm-pptp-service.conf:		<allow send_interface="org.freedesktop.NetworkManager.pptp.ppp"/>
nm-pptp-service.conf:		<deny own_prefix="org.freedesktop.NetworkManager.pptp"/>
nm-pptp-service.conf:		<deny send_destination="org.freedesktop.NetworkManager.pptp"/>

```

I purge NetworkManager because I prefer using networkd and netplan. I like the clean simplicity of that approach.

---

