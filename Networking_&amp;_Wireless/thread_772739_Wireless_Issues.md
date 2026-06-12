---
title: "Wireless Issues"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by MarshyTheKid on 2008-04-28
A couple nights ago I tried to upgrade from 7.10 to 8.04. It updated some but failed and I restarted. I couldn't boot back into Ubuntu do to an error, but check disk fixed it. It booted up then, but nm-applet would not show up. I had to change nm-applet.conf and add myself to a group. It would run then, but it doesn't detect anything. When it comes up as I start up my laptop, my only option is manual configuration. If I run it in the terminal it comes up, but it says "No network devices have been found" It also has these warning.

```
$ nm-applet

** (nm-applet:6208): WARNING **: <WARN>  nma_dbus_nm_state_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.AccessDenied) A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager" member "state" error name "(unset)" destination "org.freedesktop.NetworkManager")



** (nm-applet:6208): WARNING **: <WARN>  nma_dbus_update_devices_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.AccessDenied) A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager" member "getDevices" error name "(unset)" destination "org.freedesktop.NetworkManager")



** (nm-applet:6208): WARNING **: <WARN>  nma_dbus_update_wireless_enabled_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.AccessDenied) A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager" member "getWirelessEnabled" error name "(unset)" destination "org.freedesktop.NetworkManager")



** (nm-applet:6208): WARNING **: <WARN>  nma_dbus_update_dialup_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.AccessDenied) A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager" member "getDialup" error name "(unset)" destination "org.freedesktop.NetworkManager")



** (nm-applet:6208): WARNING **: <WARN>  nma_dbus_vpn_update_vpn_connections_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.AccessDenied) A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager.VPNConnections" member "getVPNConnections" error name "(unset)" destination "org.freedesktop.NetworkManager")





```
Also I still cannot successfully upgrade(I've tried from update manager and from the alternate cd)


Can anyone help me with getting my wireless back working?

My nm-applet.conf file reads:
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy group="netdev">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
	
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
		<allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy at_console="true">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>

		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>

        <limit name="max_replies_per_connection">512</limit>
</busconfig>


```
I would just reformat but since finals are coming up in school, its not a good time.

---

### Post by MarshyTheKid on 2008-04-28
Hmm. I tried $sudo nm-applet
and it works fine... Still not as a normal user

---

### Post by MarshyTheKid on 2008-04-28
Hmm. I tried $sudo nm-applet
and it works fine... Still not as a normal user
And I tried adding ```
<policy group="netdev">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
	
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
		<allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
```
to the NetworkManager.conf file too. After a reboot, nothing changed. I feel I am so close!

---

### Post by MarshyTheKid on 2008-07-11
Any help?
Running nm-applet as a super user worked until I fixed another problem(dpkg --configure -a) Now it won't work again

---

### Post by zflea on 2008-08-18
flea@turionx2:~$ nm-applet 

** (nm-applet:7691): WARNING **: <WARN>  nma_dbus_update_wireless_enabled_cb(): dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files


...


**flea@turionx2:~$ sudo /etc/init.d/dbus reload**
 * Reloading system message bus config...                                [ OK ] 
**flea@turionx2:~$ sudo /etc/init.d/dbus restart**
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
flea@turionx2:~$ ps aux | grep nm
*flea      7645  0.0  0.9 204768 18148 pts/0    S    12:08   0:00 nm-applet*

---

