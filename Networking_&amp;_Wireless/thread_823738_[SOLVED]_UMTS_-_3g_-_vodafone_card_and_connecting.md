---
title: "[SOLVED] UMTS - 3g - vodafone card and connecting"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by benste on 2008-06-09
Hy all, I want to use a Vodafone mobile connect card - All works fine with the vodafone-mobile... linux driver (which is utility),

but after connecting,

there is no host aviable via ping and firefox..
but there seems to be traffic - someone an idea? -> firefox also say that it's starting in offline mode - it didn'r dicover the card??

add:
tried umtsmon v 0.7

> Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
LCP: timeout sending Config-Requests
Connection terminated.
Terminating on signal 15
Modem hangup


<<PPP did not provide any stderr information>>

---

### Post by benste on 2008-06-17
no one here??

---

### Post by benste on 2008-06-27
No one??
- the new vodafone mobile connect card driver doesn't even start the gui - it hangs in the loading screen
> benste@vaiofe31m:~$ vodafone-mobile-connect-card-driver-for-linux-debug
Removing stale pidfile /tmp/vmc.pid
2008/06/27 18:54 +0200 [-] Log opened.
2008/06/27 18:54 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.2) starting up
2008/06/27 18:54 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/06/27 18:54 +0200 [-] Loading /opt/vmc/usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/06/27 18:54 +0200 [-] Loaded.
2008/06/27 18:54 +0200 [-] Changing process name to VMCCdfL
2008/06/27 18:54 +0200 [-] Log opened.
2008/06/27 18:54 +0200 [-] twistd 2.5.0 (/home/benste/ 2.5.2) starting up
2008/06/27 18:54 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/06/27 18:54 +0200 [-] Loading /opt/vmc/usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/06/27 18:54 +0200 [-] Loaded.
2008/06/27 18:54 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/06/27 18:54 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8bb59cc>
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdfilterlegacy
2008/06/27 18:54 +0200 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: gobject.Warning: Two different plugins tried to register 'BasicEngineFc'.
2008/06/27 18:54 +0200 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: gobject.Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
2008/06/27 18:54 +0200 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: Failed to load Pango module '/usr/lib/pango/1.6.0/modules/pango-basic-fc.so' for id 'BasicScriptEngineFc'
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/06/27 18:54 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nGlobeTrotter HSUPA Modem\r\n\r\nOK\r\n'
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('GlobeTrotter HSUPA Modem',), ('OK',)]
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/06/27 18:54 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nGlobeTrotter HSUPA Modem\r\n\r\nOK\r\n'
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('GlobeTrotter HSUPA Modem',), ('OK',)]
2008/06/27 18:54 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/06/27 18:55 +0200 [-] /opt/vmc/lib/python/site-packages/twisted/internet/gtk2reactor.py:175: gobject.Warning: Two different plugins tried to register 'BasicEngineFc'.
2008/06/27 18:55 +0200 [-] /opt/vmc/lib/python/site-packages/twisted/internet/gtk2reactor.py:175: gobject.Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed


---

### Post by benste on 2008-06-27
solved when using v2 beta3 and gksu

---

