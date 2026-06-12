---
title: "problem in integrating facebook plugin into pidgin"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by vishnuscorpion on 2010-11-30
**i have karmic koala installed....i have installed facebook plugin as well as pidgin from the syp.package manager...but am having problem in integrating it to pidgin..wen i sign in it shows erroe msg:invalid username/password...and the debugged results areas shown**> 23:31:49) prefs: Reading /home/****/.purple/prefs.xml
(23:31:49) prefs: Finished reading /home/****/.purple/prefs.xml
(23:31:49) dbus: okkk
(23:31:49) plugins: probing /usr/lib/pidgin/gevolution.so
(23:31:49) plugins: probing /usr/lib/pidgin/musicmessaging.so
(23:31:49) plugins: probing /usr/lib/pidgin/convcolors.so
(23:31:49) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(23:31:49) plugins: probing /usr/lib/pidgin/gestures.so
(23:31:49) plugins: probing /usr/lib/pidgin/xmppconsole.so
(23:31:49) plugins: probing /usr/lib/pidgin/iconaway.so
(23:31:49) plugins: probing /usr/lib/pidgin/notify.so
(23:31:49) plugins: probing /usr/lib/pidgin/themeedit.so
(23:31:49) plugins: probing /usr/lib/pidgin/vvconfig.so
(23:31:49) plugins: probing /usr/lib/pidgin/pidginrc.so
(23:31:49) plugins: probing /usr/lib/pidgin/markerline.so
(23:31:49) plugins: probing /usr/lib/pidgin/cap.so
(23:31:49) plugins: probing /usr/lib/pidgin/ticker.so
(23:31:49) plugins: probing /usr/lib/pidgin/sendbutton.so
(23:31:49) plugins: probing /usr/lib/pidgin/history.so
(23:31:49) plugins: probing /usr/lib/pidgin/extplacement.so
(23:31:49) plugins: probing /usr/lib/pidgin/xmppdisco.so
(23:31:49) plugins: probing /usr/lib/pidgin/spellchk.so
(23:31:49) plugins: probing /usr/lib/pidgin/timestamp.so
(23:31:49) plugins: probing /usr/lib/pidgin/timestamp_format.so
(23:31:49) plugins: probing /usr/lib/pidgin/nautilus.so
(23:31:49) plugins: probing /usr/lib/purple-2/buddynote.so
(23:31:49) plugins: probing /usr/lib/purple-2/autoaccept.so
(23:31:49) plugins: probing /usr/lib/purple-2/perl.so
(23:31:49) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(23:31:49) plugins: probing /usr/lib/purple-2/ssl-nss.so
(23:31:49) plugins: probing /usr/lib/purple-2/dbus-example.so
(23:31:49) plugins: probing /usr/lib/purple-2/libzephyr.so
(23:31:49) plugins: probing /usr/lib/purple-2/libgg.so
(23:31:49) plugins: probing /usr/lib/purple-2/libyahoojp.so
(23:31:50) plugins: probing /usr/lib/purple-2/psychic.so
(23:31:50) plugins: probing /usr/lib/purple-2/libsametime.so
(23:31:50) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(23:31:50) plugins: probing /usr/lib/purple-2/idle.so
(23:31:50) plugins: probing /usr/lib/purple-2/ssl.so
(23:31:50) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(23:31:50) plugins: probing /usr/lib/purple-2/libmyspace.so
(23:31:50) plugins: probing /usr/lib/purple-2/libicq.so
(23:31:50) plugins: probing /usr/lib/purple-2/tcl.so
(23:31:50) plugins: probing /usr/lib/purple-2/libirc.so
(23:31:50) plugins: probing /usr/lib/purple-2/libaim.so
(23:31:50) plugins: probing /usr/lib/purple-2/libqq.so
(23:31:50) plugins: probing /usr/lib/purple-2/libxmpp.so
(23:31:50) util: Reading file xmpp-caps.xml from directory /home/vishnu-h/.purple
(23:31:50) jabber: creating hash tables for data objects
(23:31:50) plugins: probing /usr/lib/purple-2/offlinemsg.so
(23:31:50) plugins: probing /usr/lib/purple-2/libsimple.so
(23:31:50) plugins: probing /usr/lib/purple-2/log_reader.so
(23:31:50) plugins: probing /usr/lib/purple-2/statenotify.so
(23:31:50) plugins: probing /usr/lib/purple-2/libnovell.so
(23:31:50) plugins: probing /usr/lib/purple-2/libyahoo.so
(23:31:50) plugins: probing /usr/lib/purple-2/liboscar.so
(23:31:50) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(23:31:50) plugins: probing /usr/lib/purple-2/libymsg.so
(23:31:50) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(23:31:50) plugins: probing /usr/lib/purple-2/joinpart.so
(23:31:50) plugins: probing /usr/lib/purple-2/newline.so
(23:31:50) plugins: probing /usr/lib/purple-2/libmsn.so
(23:31:50) plugins: probing /usr/lib/purple-2/libjabber.so
(23:31:50) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(23:31:50) plugins: probing /usr/lib/purple-2/libbonjour.so
(23:31:50) plugins: probing /usr/lib/purple-2/libfacebook.so
(23:31:50) prefs: /purple/status/scores/offline changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/available changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/invisible changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/away changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/extended_away changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/idle changed, scheduling save.
(23:31:50) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(23:31:50) util: Reading file accounts.xml from directory /home/vishnu-h/.purple
(23:31:50) util: Reading file status.xml from directory /home/vishnu-h/.purple
(23:31:50) certificate: CertificateVerifier x509, singleuse requested but not found.
(23:31:50) certificate: CertificateVerifier singleuse registered
(23:31:50) certificate: CertificatePool x509, ca requested but not found.
(23:31:50) certificate: CertificateScheme x509 requested but not found.
(23:31:50) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(23:31:50) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(23:31:50) certificate: CertificatePool ca registered
(23:31:50) certificate: CertificatePool x509, tls_peers requested but not found.
(23:31:50) certificate: CertificatePool tls_peers registered
(23:31:50) certificate: CertificateVerifier x509, tls_cached requested but not found.
(23:31:50) certificate: CertificateVerifier tls_cached registered
(23:31:50) prefs: /purple/logging/format changed, scheduling save.
(23:31:50) prefs: /purple/logging/format changed, scheduling save.
(23:31:50) prefs: /purple/proxy/type changed, scheduling save.
(23:31:50) prefs: /purple/proxy/host changed, scheduling save.
(23:31:50) prefs: /purple/proxy/port changed, scheduling save.
(23:31:50) prefs: /purple/proxy/username changed, scheduling save.
(23:31:50) prefs: /purple/proxy/password changed, scheduling save.
(23:31:50) certificate: CertificateScheme x509 requested but not found.
(23:31:50) certificate: CertificateScheme x509 registered
(23:31:50) util: Reading file smileys.xml from directory /home/****/.purple
(23:31:50) util: File /home/vishnu-h/.purple/smileys.xml does not exist (this is not necessarily an error)
(23:31:50) stun: using server 
(23:31:50) GLib-GObject: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(23:31:50) sound: Initializing sound output drivers.
(23:31:50) prefs: /pidgin/conversations/placement changed, scheduling save.
(23:31:50) gtkmedia: Registering media element types
(23:31:50) certificate: CertificateVerifier tls_cached unregistered
(23:31:50) certificate: CertificateVerifier singleuse unregistered
(23:31:50) certificate: CertificatePool tls_peers unregistered
(23:31:50) certificate: CertificatePool ca unregistered
(23:31:50) main: Unloading normal plugins
(23:31:50) plugins: Unloading plugin NSS
(23:31:50) certificate: CertificateScheme x509 unregistered
(23:31:50) plugins: Unloading plugin SSL
(23:31:50) util: Writing file accounts.xml to directory /home/vishnu-h/.purple
(23:31:50) util: Writing file /home/****/.purple/accounts.xml
(23:31:50) account: Destroying account 0x857e4e0
(23:31:50) GLib: g_hash_table_remove_internal: assertion `hash_table != NULL' failed
(23:31:50) account: Destroying account 0x857e3b0
(23:31:50) GLib: g_hash_table_remove_internal: assertion `hash_table != NULL' failed
(23:31:50) account: Destroying account 0x857f338
(23:31:50) GLib: g_hash_table_remove_internal: assertion `hash_table != NULL' failed
(23:31:50) main: Unloading all plugins
(23:31:51) plugins: Unloading plugin Perl Plugin Loader
(23:31:51) plugins: Unloading plugin SILC
(23:31:51) plugins: Unloading plugin Zephyr
(23:31:51) plugins: Unloading plugin Gadu-Gadu
(23:31:51) plugins: Unloading plugin Yahoo JAPAN
(23:31:51) plugins: Unloading plugin Sametime
(23:31:51) plugins: Unloading plugin MySpaceIM
(23:31:51) plugins: Unloading plugin ICQ
(23:31:51) plugins: Unloading plugin Tcl Plugin Loader
(23:31:51) plugins: Unloading plugin IRC
(23:31:51) plugins: Unloading plugin AIM
(23:31:51) plugins: Unloading plugin QQ
(23:31:51) plugins: Unloading plugin XMPP
(23:31:51) jabber: destroying hash tables for data objects
(23:31:51) plugins: Unloading plugin SIMPLE
(23:31:51) plugins: Unloading plugin GroupWise
(23:31:51) plugins: Unloading plugin Yahoo
(23:31:51) plugins: Unloading plugin MSN
(23:31:51) plugins: Unloading plugin Bonjour
(23:31:51) plugins: Unloading plugin Facebook
(23:31:51) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
(23:31:51) util: Writing file prefs.xml to directory /home/***/.purple
(23:31:51) util: Writing file /home/****/.purple/prefs.xml
Exiting because another libpurple client is already running.
anyone help me plz..

---

### Post by Jahid65 on 2010-11-30
you don't need to use plug-in. To setup facebook chat in pidgin go to [http://www.facebook.com/sitetour/chat.php](http://www.facebook.com/sitetour/chat.php)

---

### Post by Segofam on 2010-12-05
Jahid65 > Thank you so much :)
I had been trying for weeks to get Facebook to work in Pidgin.
There are so many people trying to do the same.
How do we get this notice up on Ubuntu's notice board?

---

