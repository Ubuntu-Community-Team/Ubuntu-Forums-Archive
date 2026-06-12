---
title: "Pidgin crashes while loading on Hardy"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Saghaulor on 2008-05-01
After a botched upgrade from Gutsy to Hardy, I'm running a fresh install of Hardy AMD64.

Every time I try to load pidgin it crashes while loading. I've completely removed it via synaptic, and then reinstalled it, and it continues to crash.

Any ideas?

---

### Post by Saghaulor on 2008-05-01
Apparently I have to run pidgin as a sudo. I got it working

---

### Post by bconverse on 2008-05-04
I am having this problem now too, though, Pidgin was working fine for a while in Hardy.  This problem seemed to start yesterday or so, but I can also run it fine as root, anyone else having this problem?

---

### Post by Skerit on 2008-05-07
Yes, my pidgin is refusing to work properly here, too.
(So has firefox, btw, when I load some flash file it sometimes "greys out" on me for a minute or two, but I'm going off topic...)

Running pidgin with root rights isn't really the answer for me.

---

### Post by eOgas on 2008-05-10
Same exact problem here.  I also have the flash thing but it's probably unrelated.  I recall having that on gutsy too.  I too can run pidgin in superuser mode, but it's a hassle to say the least.

I ran it in a terminal and it's crashing with a segmentation fault.  This is what I get when I run [FONT="Courier New"]pidgin --debug[/FONT] in a terminal:
```
(18:48:56) prefs: Reading /home/USER/.purple/prefs.xml
(18:48:56) prefs: Finished reading /home/USER/.purple/prefs.xml
(18:48:56) prefs: purple_prefs_get_string: /pidgin/browsers/command not a string pref
(18:48:56) dbus: okkk
(18:48:56) plugins: probing /usr/lib/pidgin/history.so
(18:48:56) plugins: probing /usr/lib/pidgin/iconaway.so
(18:48:56) plugins: probing /usr/lib/pidgin/gestures.so
(18:48:56) plugins: probing /usr/lib/pidgin/notify.so
(18:48:56) plugins: probing /usr/lib/pidgin/gevolution.so
(18:48:56) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(18:48:56) plugins: probing /usr/lib/pidgin/nautilus.so
(18:48:56) plugins: probing /usr/lib/pidgin/xmppconsole.so
(18:48:56) plugins: probing /usr/lib/pidgin/pidginrc.so
(18:48:56) plugins: probing /usr/lib/pidgin/markerline.so
(18:48:56) plugins: probing /usr/lib/pidgin/ticker.so
(18:48:56) plugins: probing /usr/lib/pidgin/convcolors.so
(18:48:56) plugins: probing /usr/lib/pidgin/timestamp_format.so
(18:48:56) plugins: probing /usr/lib/pidgin/cap.so
(18:48:56) plugins: probing /usr/lib/pidgin/extplacement.so
(18:48:56) plugins: probing /usr/lib/pidgin/timestamp.so
(18:48:56) plugins: probing /usr/lib/pidgin/spellchk.so
(18:48:56) plugins: probing /usr/lib/pidgin/musicmessaging.so
(18:48:56) plugins: probing /usr/lib/purple-2/libicq.so
(18:48:56) plugins: probing /usr/lib/purple-2/libbonjour.so
(18:48:56) plugins: probing /usr/lib/purple-2/buddynote.so
(18:48:56) plugins: probing /usr/lib/purple-2/libyahoo.so
(18:48:56) plugins: probing /usr/lib/purple-2/libirc.so
(18:48:56) plugins: probing /usr/lib/purple-2/libqq.so
(18:48:56) plugins: probing /usr/lib/purple-2/autoaccept.so
(18:48:56) plugins: probing /usr/lib/purple-2/libgg.so
(18:48:56) plugins: probing /usr/lib/purple-2/perl.so
(18:48:56) plugins: probing /usr/lib/purple-2/ssl-nss.so
(18:48:56) plugins: probing /usr/lib/purple-2/psychic.so
(18:48:56) plugins: probing /usr/lib/purple-2/statenotify.so
(18:48:56) plugins: probing /usr/lib/purple-2/idle.so
(18:48:56) plugins: probing /usr/lib/purple-2/log_reader.so
(18:48:56) plugins: probing /usr/lib/purple-2/libaim.so
(18:48:56) plugins: probing /usr/lib/purple-2/libnovell.so
(18:48:56) plugins: probing /usr/lib/purple-2/offlinemsg.so
(18:48:56) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(18:48:56) plugins: probing /usr/lib/purple-2/libxmpp.so
(18:48:56) util: Reading file xmpp-caps.xml from directory /home/USER/.purple
(18:48:56) util: File /home/USER/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(18:48:56) plugins: probing /usr/lib/purple-2/libzephyr.so
(18:48:56) plugins: probing /usr/lib/purple-2/ssl.so
(18:48:56) plugins: probing /usr/lib/purple-2/libmyspace.so
(18:48:56) plugins: probing /usr/lib/purple-2/libmsn.so
(18:48:56) plugins: probing /usr/lib/purple-2/tcl.so
(18:48:56) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(18:48:56) plugins: probing /usr/lib/purple-2/dbus-example.so
(18:48:56) plugins: probing /usr/lib/purple-2/libsametime.so
(18:48:56) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(18:48:56) plugins: probing /usr/lib/purple-2/libsimple.so
(18:48:56) plugins: probing /usr/lib/purple-2/libjabber.so
(18:48:56) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:48:56) plugins: probing /usr/lib/purple-2/liboscar.so
(18:48:56) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:48:56) plugins: probing /usr/lib/purple-2/newline.so
(18:48:56) plugins: probing /usr/lib/purple-2/joinpart.so
(18:48:56) prefs: /purple/status/scores/offline changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/available changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/invisible changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/away changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/extended_away changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/idle changed, scheduling save.
(18:48:56) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(18:48:56) util: Reading file accounts.xml from directory /home/USER/.purple
(18:48:56) util: File /home/USER/.purple/accounts.xml does not exist (this is not necessarily an error)
(18:48:56) util: Reading file status.xml from directory /home/USER/.purple
(18:48:56) certificate: CertificateVerifier x509, singleuse requested but not found.
(18:48:56) certificate: CertificateVerifier singleuse registered
(18:48:56) certificate: CertificatePool x509, ca requested but not found.
(18:48:56) certificate: CertificateScheme x509 requested but not found.
(18:48:56) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(18:48:56) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(18:48:56) certificate: CertificatePool ca registered
(18:48:56) certificate: CertificatePool x509, tls_peers requested but not found.
(18:48:56) certificate: CertificatePool tls_peers registered
(18:48:56) certificate: CertificateVerifier x509, tls_cached requested but not found.
(18:48:56) certificate: CertificateVerifier tls_cached registered
(18:48:56) prefs: /purple/logging/format changed, scheduling save.
(18:48:56) prefs: /purple/logging/format changed, scheduling save.
(18:48:56) prefs: /purple/proxy/type changed, scheduling save.
(18:48:56) prefs: /purple/proxy/host changed, scheduling save.
(18:48:56) prefs: /purple/proxy/port changed, scheduling save.
(18:48:56) prefs: /purple/proxy/username changed, scheduling save.
(18:48:56) prefs: /purple/proxy/password changed, scheduling save.
(18:48:56) certificate: CertificateScheme x509 requested but not found.
(18:48:56) certificate: CertificateScheme x509 registered
(18:48:56) stun: using server 
(18:48:56) sound: Initializing sound output drivers.
(18:48:56) prefs: /pidgin/conversations/placement changed, scheduling save.
(18:48:56) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(18:48:56) gtkblist: added visibility manager: 1
(18:48:56) docklet: created
(18:48:56) util: Reading file blist.xml from directory /home/USER/.purple
(18:48:56) util: File /home/USER/.purple/blist.xml does not exist (this is not necessarily an error)
(18:48:56) pounce: Error reading pounces: Failed to open file '/home/USER/.purple/pounces.xml': No such file or directory
(18:48:56) ui_main: Failed to load the default window icon (scalablepx version)!
(18:48:56) Session Management: ICE initialized.
(18:48:56) Session Management: Connecting with no previous ID
(18:48:56) Session Management: Handling new ICE connection... 
(18:48:56) done.
(18:48:56) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000121046333600000057670080
(18:48:56) Session Management: Using pidgin as command
(18:48:56) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:48:56) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:48:56) util: requested to fetch (http://IPADDRESS:2869/upnphost/udhisapi.dll?content=uuid:7fa34e22-56f5-4a01-b7b0-5b2a8296faed), full=1, user_agent=((null)), http11=1
(18:48:56) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(18:48:56) dns: DNS query for 'IPADDRESS' queued
(18:48:56) Session Management: Received first save_yourself
(18:48:56) Session Management: Received save_complete
(18:48:56) dns: Created new DNS child 28689, there are now 1 children.
(18:48:56) dns: Successfully sent DNS request to child 28689
(18:48:56) dns: Got response for 'IPADDRESS'
(18:48:56) dnsquery: IP resolved for IPADDRESS
(18:48:56) proxy: Attempting connection to IPADDRESS
(18:48:56) proxy: Connecting to IPADDRESS:2869 with no proxy
(18:48:56) proxy: Connection in progress
(18:48:56) proxy: Connected to IPADDRESS:2869.
(18:48:56) util: Request: 'GET /upnphost/udhisapi.dll?content=uuid:7fa34e22-56f5-4a01-b7b0-5b2a8296faed HTTP/1.1
Connection: close
Host: IPADDRESS:2869

'
(18:48:56) util: Response headers: 'HTTP/1.1 200 OK
Content-Length: 3615
Content-Type: text/xml
Server: Microsoft-Windows-NT/5.1 UPnP/1.0 UPnP-Device-Host/1.0 Microsoft-HTTPAPI/1.0
Date: Sat, 10 May 2008 23:48:52 GMT
Connection: close

'
(18:48:56) util: parsed 3615
(18:48:56) util: requested to fetch (http://IPADDRESS:2869/upnphost/udhisapi.dll?control=uuid:1b7baf5a-8fc4-4e8e-a8ae-2ac16e7809ac+urn:upnp-org:serviceId:WANIPConn1), full=0, user_agent=((null)), http11=1
(18:48:56) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(18:48:56) dns: DNS query for 'IPADDRESS' queued
(18:48:56) dns: DNS query for 'IPADDRESS' queued
(18:48:56) dns: Created new DNS child 28693, there are now 1 children.
(18:48:56) dns: Successfully sent DNS request to child 28693
(18:48:56) dns: Created new DNS child 28694, there are now 2 children.
(18:48:56) dns: Successfully sent DNS request to child 28694
(18:48:56) dns: Got response for 'IPADDRESS'
(18:48:56) dnsquery: IP resolved for IPADDRESS
(18:48:56) proxy: Attempting connection to IPADDRESS
(18:48:56) proxy: Connecting to IPADDRESS:2869 with no proxy
(18:48:56) proxy: Connection in progress
(18:48:56) dns: Got response for 'IPADDRESS'
(18:48:56) dnsquery: IP resolved for IPADDRESS
(18:48:56) proxy: Attempting connection to IPADDRESS
(18:48:56) proxy: Connecting to IPADDRESS:2869 with no proxy
(18:48:56) proxy: Connection in progress
(18:48:56) proxy: Connected to IPADDRESS:2869.
(18:48:56) util: Request: 'POST /upnphost/udhisapi.dll?control=uuid:1b7baf5a-8fc4-4e8e-a8ae-2ac16e7809ac+urn:upnp-org:serviceId:WANIPConn1 HTTP/1.1
HOST: IPADDRESS:2869
SOAPACTION: "urn:schemas-upnp-org:service:WANIPConnection:1#GetExternalIPAddress"
CONTENT-TYPE: text/xml ; charset="utf-8"
CONTENT-LENGTH: 310

<?xml version="1.0" encoding="utf-8"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" s:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<s:Body>
<u:GetExternalIPAddress xmlns:u="urn:schemas-upnp-org:service:WANIPConnection:1">
</u:GetExternalIPAddress>
</s:Body>
</s:Envelope>'
(18:48:56) proxy: Connected to IPADDRESS:2869.
(18:48:56) upnp: Local IP:IPADDRESS
(18:48:56) docklet: embedded
Segmentation fault

```

---

### Post by eOgas on 2008-05-11
bump.

---

### Post by naraic on 2008-05-19
yup, i have the same problem. it shows the add account window, then crashes. running 2.4.1. works when i run it as root though. strange

---

### Post by deltateam2 on 2008-11-09
Similar problems persist.

---

### Post by TheSixthPandava on 2008-11-23
I have a problem with Pidgin crashing on Hardy, but not during load, he does that normally [or it seems it is normal] but crashes when I try to send someone a message. I removed it and then installed it again, but it continued to crash. I ran it from sudo and now it seems it is working normally, but I don't see this as a solution.

---

