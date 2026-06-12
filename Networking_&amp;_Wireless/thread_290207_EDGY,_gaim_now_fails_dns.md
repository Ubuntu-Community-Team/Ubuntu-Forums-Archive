---
title: "EDGY, gaim now fails dns?"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by jcpunk on 2006-10-31
I just went from dapper to edgy via dist-upgrade and suddenly gaim has begin failing to connect...

here is what I get from gaim -d
```

gaim -d
GTK Accessibility Module initialized
dbus: okkk
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/hotkeys.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/guifications.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libextprefs.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/libgaimperl.so
plugins: /usr/lib/gaim/libgaimperl.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/irchelper.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/encrypt.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/gaim-otr.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /usr/lib/gaim/dbus-example.so
util: Reading file accounts.xml from directory /home/deanna/.gaim
util: Reading file status.xml from directory /home/deanna/.gaim
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
stun: using server 
stun: using server 
sound: Initializing sound output drivers.
util: Reading file blist.xml from directory /home/deanna/.gaim
prefs: Reading /home/deanna/.gaim/prefs.xml
sound: Sound output driver loaded: ESounD output
prefs: Finished reading /home/deanna/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
docklet: plugin loaded
gtkblist: added visibility manager: 1
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/iconaway.so
plugins: Loading saved plugin /usr/lib/gaim/idle.so
plugins: Loading saved plugin /usr/lib/gaim/spellchk.so
pounce: Error reading pounces: Failed to open file '/home/deanna/.gaim/pounces.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 117f000001000116235166900000046880016
Session Management: Using gaim as command
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
g_log: gaim_dbus_pointer_to_id: assertion `id || node == NULL' failed
account: Connecting to account dpray4u
connection: Connecting. gc = 0x84caa70
oscar: oscar_login: gc = 0x84caa70
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: aim_conn_addhandler: adding for ffff/0003
oscar: aim_conn_addhandler: adding for 0017/0003
oscar: aim_conn_addhandler: adding for 0017/0007
oscar: aim_conn_addhandler: adding for 0017/000a
dns: Created new DNS child 5474, there are now 1 children.
dns[5474]: hostname = "" (port = 8080)!!!
dns: DNS child 5474 not responding. Killing it!
Session Management: Received first save_yourself
dns: Got response for ''
dns: EOF reading from DNS child
prefs: /gaim/gtk/blist/list_visible changed, scheduling save.
Session Management: Received save_complete
account: Disconnecting account 0x81efec0
connection: Disconnecting connection 0x84caa70
oscar: Signed off.
connection: Destroying connection 0x84caa70
prefs: /gaim/gtk/blist/list_visible changed, scheduling save.
tray icon: embedded
util: Writing file accounts.xml to directory /home/deanna/.gaim
util: Writing file blist.xml to directory /home/deanna/.gaim
accels: saving accels to /home/deanna/.gaim/accels
util: Writing file prefs.xml to directory /home/deanna/.gaim
autorecon: do_signon called
autorecon: calling gaim_account_connect
account: Connecting to account dpray4u
connection: Connecting. gc = 0x84a2848
oscar: oscar_login: gc = 0x84a2848
oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module advert (family 0x0005, version = 0x0001, tool 0x0001, tool version 0x0001)
oscar: registered module invite (family 0x0006, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module translate (family 0x000c, version = 0x0001, tool 0x0104, tool version 0x0001)
oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
oscar: aim_conn_addhandler: adding for ffff/0003
oscar: aim_conn_addhandler: adding for 0017/0003
oscar: aim_conn_addhandler: adding for 0017/0007
oscar: aim_conn_addhandler: adding for 0017/000a
dns: Created new DNS child 5484, there are now 1 children.
dns[5484]: hostname = "" (port = 8080)!!!
dns: DNS child 5484 not responding. Killing it!
autorecon: done calling gaim_account_connect
dns: Got response for ''
dns: EOF reading from DNS child
account: Disconnecting account 0x81efec0
connection: Disconnecting connection 0x84a2848
oscar: Signed off.
connection: Destroying connection 0x84a2848
util: Writing file accounts.xml to directory /home/deanna/.gaim

```

I would like to point out the **dns: DNS child 5484 not responding. Killing it!** section.... I can nslookup the login server just fine and even telnet to it on the right ports....

Any ideas?

---

