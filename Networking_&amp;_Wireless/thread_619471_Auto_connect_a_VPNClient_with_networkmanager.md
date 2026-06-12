---
title: "Auto connect a VPNClient with networkmanager"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by azelter on 2007-11-21
I have successfully configured a VPN connection to a pptp VPN server using network manager. However, I would like this connection to become active every time I log on without having to click on the network manager icon and activate the connection by hand. I have followed the instructions at:

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

which state that in order to automatically start your VPN connection on log-in you should:
1/ add the command nm-applet to your sessions
2/ execute the command:
/usr/lib/network-manager-vpnc/nm-vpnc-auth-dialog -s <service_name> -n <connection_name>
where connection name is the name of your connection and service_name can be one of the following: (a) the PPTP plugin, 'org.freedesktop.NetworkManager.pptp'; (b)  the Cisco VPNC plugin, 'org.freedesktop.NetworkManager.vpnc', or (c) the OpenVPN plugin, 'org.freedesktop.NetworkManager.openvpn'

thus in my case the command should be:

/usr/lib/network-manager-vpnc/nm-vpnc-auth-dialog -s 'org.freedesktop.NetworkManager.pptp' -n 'My VPN Connection'

This results in the error:
This dialog only works with the 'org.freedesktop.NetworkManager.vpnc' service

If I look to see what else is around.
ls /usr/lib/network-manager-vpnc gives:
libnm-vpnc-properties.la        nm-vpnc-auth-dialog
libnm-vpnc-properties.so        nm-vpnc-service
libnm-vpnc-properties.so.0      nm-vpnc-service-vpnc-helper
libnm-vpnc-properties.so.0.0.0

ls /usr/lib/network-manager gives:
ifblacklist_migrate.sh     libnm-ppp-properties.so.0.0.0  nm-vpn-properties
libnm-ppp-properties.so    nm-crash-logger
libnm-ppp-properties.so.0  nm-ppp-auth-dialog

But nowhere do I see anything related to pptp.

As I said, using the GUI this connection works fine. I want to be able to automount nfs partitions that depend on the VPN being up, however, and this is impossible unless I can bring the VPN up automatically. Ideally I would have the VPN brought up before login, but that's not so important that I want to go to the effort of configuring pptp by hand and skipping networkmanager altogether.

Any help appreciated.

Thanks,
Alex

---

### Post by goobsoft on 2008-06-02
I get the same error on Hardy.  I wish this worked.

---

### Post by azelter on 2008-06-02
Yeah. I never did solve the problem with networkmanager. It seems it is not a common enough requirement for if to get fixed. The only way to make it automatic is to configure pptp by hand and bypass nm entirely.

---

