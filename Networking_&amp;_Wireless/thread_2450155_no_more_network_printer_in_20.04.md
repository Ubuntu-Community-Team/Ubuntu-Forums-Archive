---
title: "no more network printer in 20.04"
date: 2020-09-08
forum: Networking &amp; Wireless
---

### Post by xzurukneg on 2020-09-08
I'm asking here [after askubuntu.]("https://askubuntu.com/questions/1272185/20-04-cant-find-brotherdcp-network-printer-when-16-04-does-dcp-j752dw")
My printer (Brother DCP-j752DW) work well with 16.04 (and others), using the box rooter (a freebox-4k from french ISP).
You can see my working configuration on link above.
In short it's:
**smb://freebox/Brother%20DCP-J752DW**  on **mafreebox.freebox.fr**

Now, on fresh install of xubuntu20.04 (via netboot "mini.iso"), everything is good, quick install, all up-to-date at first boot (great!) excepted no online-printer.:-(
Since my askubuntu post, I did this:
[LIST=1]
[*]installed **python3-smbc (1.0.15.6-2build2) **reclaimed by printer (system-config-printer) when I tried to it via "search" button (quite surprised!). Note software-center was proposed to install it but finally can't install it! (I'll like to know why?!) So I used the good old synaptic, my old ubuntu preferred app. Now "search" button works but printer still don't find anything, and said to check firewall. 
[*]So, I did ```
:~$ ufw allow samba
```
Now search button works (ppfffiuuu) and find the freebox (good), but can't access WORKGROUP, the router share group, and ask a password. BUT there is no password! 
[/LIST]

So I'm quite disappointed, the problem seem to be on the network side, but asking for a non existing password is out of what I can understand. I suppose direct usb is working, it's pretty sure but I really don't acre of direct usb, I need online printer access.
I still use 16.04 because of this.

 Thanks for advices!

---

### Post by xzurukneg on 2020-09-14
Well.. I wish this post is not in wrong section.

I can confirm print works with USB (20.04). looks like no problem on driver side.
Also, 18.04 don't have the password problem and can access to the workgroup printer, but can't finish the install (error message, "just can't").  
All previous ubuntu version  access the network printer nicely, on same or other machines. 
I really need to update my system and access to this network printer.

So I have compare **cups --debug** from working config with 16.04 and 20.04, on my machine: I have opened systemconfigPrinter> "add" >networkprinter>search
[B]For 16.04 :
[/B]it find the printer
```
working config with 16.04:~$ system-config-printer --debug
+<newprinter.NewPrinterGUI object at 0x7fbee9cc5a20 (newprinter+NewPrinterGUI at 0x1e37000)>
Connected as user kx16
+<printerproperties.PrinterPropertiesDialog object at 0x7fbee9ce1828 (printerproperties+PrinterPropertiesDialog at 0x1e77140)>
<authconn.Connection object at 0x7fbf08cefeb8>: Operation += Récupération des informations de la file d'attente
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
<authconn.Connection object at 0x7fbf08cefeb8>: Operation ended
+<ppdcache.PPDCache object at 0x7fbee9cf17b8>
refresh
Created subscription 4559, events=['printer-added', 'printer-modified', 'printer-deleted', 'printer-state-changed']
Next notifications fetch in 1s
update_jobs
Deferred populateList by 200ms
Deferred populateList by 200ms
Deferred populateList by 200ms
<authconn.Connection object at 0x7fbf08cefeb8>: Operation += Récupération des informations de la file d'attente
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
<authconn.Connection object at 0x7fbf08cefeb8>: Operation ended
get_notifications
update_jobs
Next notifications fetch in 60s
Connected as user kx16
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set

(system-config-printer.py:5700): Gtk-CRITICAL **: gtk_tree_store_insert_after: assertion 'G_NODE (sibling->user_data)->parent == G_NODE (parent->user_data)' failed

(system-config-printer.py:5700): Gtk-CRITICAL **: gtk_tree_store_set_value: assertion 'VALID_ITER (iter, tree_store)' failed

(system-config-printer.py:5700): Gtk-CRITICAL **: gtk_tree_store_set_value: assertion 'VALID_ITER (iter, tree_store)' failed
Fetching devices
Using polkit-1 connection class
+<asyncipp._IPPAuthOperation object at 0x7fbee9cfabe0>
New IPPConnection
+<_IPPConnectionThread(Thread-1, initial daemon)>
+<asyncipp.IPPAuthConnection object at 0x7fbee9cfab38>
Awaiting further instructions
Exception assessing DevicesGet API: DBusException('The name org.opensuse.CupsPkHelper.Mechanism was not provided by any .service files',)
+<asyncpk1.PK1Connection object at 0x7fbee9cfa4a8>
+<asyncconn.Connection object at 0x7fbee9cec6d8>
fetchDevices
+<asyncconn._AsyncMethodCall object at 0x7fbed3795e48>
<asyncconn._AsyncMethodCall object at 0x7fbed3795e48>: calling <bound method PK1Connection.getDevices of <asyncpk1.PK1Connection object at 0x7fbee9cfa4a8>>
Converted ()/{'auth_handler': <bound method _AsyncMethodCall.auth_handler of <asyncconn._AsyncMethodCall object at 0x7fbed3795e48>>, 'error_handler': <bound method _AsyncMethodCall.error_handler of <asyncconn._AsyncMethodCall object at 0x7fbed3795e48>>, 'reply_handler': <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7fbed3795e48>>, 'exclude_schemes': ['dnssd', 'snmp', 'bluetooth']} to (0, [], ['dnssd', 'snmp', 'bluetooth'])
+_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>
Calling PK method DevicesGet
D-Bus call failed: DBusException('The name org.opensuse.CupsPkHelper.Mechanism was not provided by any .service files',)
<asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>: calling <function IPPConnection._make_binding.<locals>.<lambda> at 0x7fbee809a730>
+<asyncipp._IPPAuthOperation object at 0x7fbed3795f98>
Next task: (<method 'getDevices' of 'cups.Connection' objects>, (), {'exclude_schemes': ['dnssd', 'snmp', 'bluetooth']}, <bound method _PK1AsyncMethodCall._ipp_reply_handler of <asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>>, <bound method _IPPAuthOperation.error_handler of <asyncipp._IPPAuthOperation object at 0x7fbed3795f98>>, <bound method _IPPAuthOperation.auth_handler of <asyncipp._IPPAuthOperation object at 0x7fbed3795f98>>)
-<asyncipp._IPPAuthOperation object at 0x7fbee9cfabe0>
Call <method 'getDevices' of 'cups.Connection' objects>
...success
Awaiting further instructions
<asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>: chaining up to <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7fbed3795e48>>
<asyncconn._AsyncMethodCall object at 0x7fbed3795e48>: to reply_handler at <bound method Connection._subst_reply_handler of <asyncconn.Connection object at 0x7fbee9cec6d8>>
DESTROY: <asyncconn._AsyncMethodCall object at 0x7fbed3795e48>
<asyncconn.Connection object at 0x7fbee9cec6d8>: chaining up to <bound method _GetDevicesCall._reply_handler of <cupshelpers.cupshelpers._GetDevicesCall object at 0x7fbed3795eb8>>
fetchDevices
+<asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>
<asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>: calling <bound method PK1Connection.getDevices of <asyncpk1.PK1Connection object at 0x7fbee9cfa4a8>>
Converted ()/{'auth_handler': <bound method _AsyncMethodCall.auth_handler of <asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>>, 'error_handler': <bound method _AsyncMethodCall.error_handler of <asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>>, 'reply_handler': <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>>, 'include_schemes': ['dnssd', 'snmp', 'bluetooth']} to (0, ['dnssd', 'snmp', 'bluetooth'], [])
+_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>
Calling PK method DevicesGet
D-Bus call failed: DBusException('The name org.opensuse.CupsPkHelper.Mechanism was not provided by any .service files',)
<asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>: calling <function IPPConnection._make_binding.<locals>.<lambda> at 0x7fbee809a730>
+<asyncipp._IPPAuthOperation object at 0x7fbee80b5240>
Next task: (<method 'getDevices' of 'cups.Connection' objects>, (), {'include_schemes': ['dnssd', 'snmp', 'bluetooth']}, <bound method _PK1AsyncMethodCall._ipp_reply_handler of <asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>>, <bound method _IPPAuthOperation.error_handler of <asyncipp._IPPAuthOperation object at 0x7fbee80b5240>>, <bound method _IPPAuthOperation.auth_handler of <asyncipp._IPPAuthOperation object at 0x7fbee80b5240>>)
-<asyncipp._IPPAuthOperation object at 0x7fbed3795f98>
Call <method 'getDevices' of 'cups.Connection' objects>
DESTROY: <asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>
-<asyncconn._AsyncMethodCall object at 0x7fbed3795e48>
-_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7fbed3795ef0>
...success
Awaiting further instructions
<asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>: chaining up to <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>>
<asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>: to reply_handler at <bound method Connection._subst_reply_handler of <asyncconn.Connection object at 0x7fbee9cec6d8>>
DESTROY: <asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>
<asyncconn.Connection object at 0x7fbee9cec6d8>: chaining up to <bound method _GetDevicesCall._reply_handler of <cupshelpers.cupshelpers._GetDevicesCall object at 0x7fbee80b5198>>
DESTROY: <asyncconn.Connection object at 0x7fbee9cec6d8>
DESTROY: <asyncpk1.PK1Connection object at 0x7fbee9cfa4a8>
DESTROY: <asyncipp.IPPAuthConnection object at 0x7fbee9cfab38>
Stopping worker thread
Next task: None
Thread exiting
-<asyncipp._IPPAuthOperation object at 0x7fbee80b5240>
-<asyncconn.Connection object at 0x7fbee9cec6d8>
DESTROY: <asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>
-<asyncconn._AsyncMethodCall object at 0x7fbee80b51d0>
-<asyncpk1.PK1Connection object at 0x7fbee9cfa4a8>
-_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7fbee80b5208>
No firewall 
Examining firewall
<firewallsettings.SystemConfigFirewall object at 0x7fbee9ce2518> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
<firewallsettings.SystemConfigFirewall object at 0x7fbee9ce2518> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
<firewallsettings.SystemConfigFirewall object at 0x7fbee9ce2518> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
Firewall all OK, no changes needed
-<asyncipp.IPPAuthConnection object at 0x7fbee9cfab38>
-<_IPPConnectionThread(Thread-1, stopped daemon 140457940424448)>
Calling <bound method PrinterFinder._do_find of <probe_printer.PrinterFinder object at 0x7fbeebb27668>>
hplip: trying
hplip: no good (return code 1)
jetdirect: trying
jetdirect: mafreebox.freebox.fr:9100 CLOSED
jetdirect: done
ipp: trying
ipp: can't connect to server/printer
ipp: no good
snmp: trying
snmp: done
lpd: trying
lpd: couldn't connect
lpd: done
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
Using netbios name DDX-STUDIO.
Using workgroup WORKGROUP.
smb: trying
parsed path: fname='smb://mafreebox.freebox.fr/' server='mafreebox.freebox.fr' share='' path='' options=''
SMBC_check_options(): server='mafreebox.freebox.fr' share='' path='' options=''
pysmb: got password callback
lp_load_ex: refreshing parameters
Freeing parametrics:
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
Processing section "[global]"
doing parameter preferred master = no
doing parameter local master = no
doing parameter domain master = no
doing parameter client lanman auth = yes
doing parameter lanman auth = yes
doing parameter socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
doing parameter lock directory = /home/kx16/.smb/
doing parameter name resolve order = bcast host
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface enp0s7 ip=2a01:e0a:426:a2f0::edd2:6f54 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface enp0s7 ip=192.168.0.10 bcast=192.168.0.255 netmask=255.255.255.0
pysmb: got password callback
Device found: smb://mafreebox.freebox.fr/Brother%20DCP-J752DW
smb: done
Done
get_notifications
update_jobs
Next notifications fetch in 60s
get_notifications
update_jobs
Next notifications fetch in 60s
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
Using netbios name DDX-STUDIO.
Using workgroup WORKGROUP.
pysmb: got password callback
lp_load_ex: refreshing parameters
Freeing parametrics:
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
Processing section "[global]"
doing parameter preferred master = no
doing parameter local master = no
doing parameter domain master = no
doing parameter client lanman auth = yes
doing parameter lanman auth = yes
doing parameter socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
doing parameter lock directory = /home/kx16/.smb/
doing parameter name resolve order = bcast host
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface enp0s7 ip=2a01:e0a:426:a2f0::edd2:6f54 bcast= netmask=ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
added interface enp0s7 ip=192.168.0.10 bcast=192.168.0.255 netmask=255.255.255.0
get_notifications
update_jobs
Next notifications fetch in 60s
^CTraceback (most recent call last):
  File "/usr/share/system-config-printer/newprinter.py", line 2922, in device_row_separator_fn
    def device_row_separator_fn (self, model, iter, data):
```
[B]
For 20.04:
[/B]it block asking password to access workgroup
```
20.04:~$ system-config-printer --debug
/usr/share/system-config-printer/system-config-printer.py:315: DeprecationWarning: Gtk.ActionGroup.list_actions is deprecated
  for action in printer_manager_action_group.list_actions ():
/usr/share/system-config-printer/system-config-printer.py:316: DeprecationWarning: Gtk.Action.set_sensitive is deprecated
  action.set_sensitive (False)
/usr/share/system-config-printer/system-config-printer.py:324: DeprecationWarning: Gtk.ActionGroup.get_action is deprecated
  act = printer_manager_action_group.get_action (action)
/usr/share/system-config-printer/system-config-printer.py:354: DeprecationWarning: Gtk.UIManager.ensure_update is deprecated
  self.ui_manager.ensure_update ()
/usr/share/system-config-printer/system-config-printer.py:355: DeprecationWarning: Gtk.UIManager.get_accel_group is deprecated
  self.PrintersWindow.add_accel_group (self.ui_manager.get_accel_group ())
/usr/share/system-config-printer/system-config-printer.py:364: DeprecationWarning: Gtk.UIManager.get_action is deprecated
  action = self.ui_manager.get_action ("/new-printer")
/usr/share/system-config-printer/system-config-printer.py:365: DeprecationWarning: Gtk.Action.create_menu_item is deprecated
  newprinteritem = action.create_menu_item ()
+<newprinter.NewPrinterGUI object at 0x7f05cb609100 (newprinter+NewPrinterGUI at 0x2f9d900)>
Connected as user kx20
/usr/share/system-config-printer/system-config-printer.py:663: DeprecationWarning: Gtk.Action.get_proxies is deprecated
  for widget in action.get_proxies ():
+<printerproperties.PrinterPropertiesDialog object at 0x7f05c8332240 (printerproperties+PrinterPropertiesDialog at 0x2fd24c0)>
<authconn.Connection object at 0x7f05d097a400>: Operation += Récupération des informations de la file d'attente
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
<authconn.Connection object at 0x7f05d097a400>: Operation ended
/usr/share/system-config-printer/system-config-printer.py:976: DeprecationWarning: urllib.parse.splittype() is deprecated as of 3.8, use urllib.parse.urlparse() instead
  (scheme, rest) = urllib.parse.splittype (object.device_uri)
+<ppdcache.PPDCache object at 0x7f05c832dbb0>
/usr/share/system-config-printer/system-config-printer.py:2236: DeprecationWarning: Gdk.threads_enter is deprecated
  Gdk.threads_enter ()
refresh
Created subscription 79, events=['printer-added', 'printer-modified', 'printer-deleted', 'printer-state-changed']
Next notifications fetch in 1s
update_jobs
Deferred populateList by 200ms
Deferred populateList by 200ms
Deferred populateList by 200ms
Deferred populateList by 200ms
<authconn.Connection object at 0x7f05d097a400>: Operation += Récupération des informations de la file d'attente
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
<authconn.Connection object at 0x7f05d097a400>: Operation ended
/usr/share/system-config-printer/system-config-printer.py:2187: DeprecationWarning: Gdk.threads_leave is deprecated
  Gdk.threads_leave ()
get_notifications
update_jobs
Next notifications fetch in 60s
Connected as user kx20
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Device  added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,)>
Device network added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,network)>
Device smb added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,smb)>
Selected connection type. URI: 
Fetching devices
Using polkit-1 connection class
+<asyncipp._IPPAuthOperation object at 0x7f05c835bdc0>
New IPPConnection
+<_IPPConnectionThread(Thread-1, initial daemon)>
+<asyncipp.IPPAuthConnection object at 0x7f05c835bfd0>
Awaiting further instructions
DevicesGet new API: True
+<asyncpk1.PK1Connection object at 0x7f05c835bee0>
+<asyncconn.Connection object at 0x7f05c835bf10>
fetchDevices
+<asyncconn._AsyncMethodCall object at 0x7f05cb59b640>
<asyncconn._AsyncMethodCall object at 0x7f05cb59b640>: calling <bound method PK1Connection.getDevices of <asyncpk1.PK1Connection object at 0x7f05c835bee0>>
Converted ()/{'exclude_schemes': ['dnssd', 'snmp', 'driverless', 'bjnp', 'bluetooth'], 'reply_handler': <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59b640>>, 'error_handler': <bound method _AsyncMethodCall.error_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59b640>>, 'auth_handler': <bound method _AsyncMethodCall.auth_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59b640>>} to (0, 0, [], ['dnssd', 'snmp', 'driverless', 'bjnp', 'bluetooth'])
+_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59b670>
Calling PK method DevicesGet
<asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59b670>: calling <dbus.proxies._DeferredMethod object at 0x7f05cb59b850>
<asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59b670>: no error, calling reply handler <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59b640>>
<asyncconn._AsyncMethodCall object at 0x7f05cb59b640>: to reply_handler at <bound method Connection._subst_reply_handler of <asyncconn.Connection object at 0x7f05c835bf10>>
DESTROY: <asyncconn._AsyncMethodCall object at 0x7f05cb59b640>
<asyncconn.Connection object at 0x7f05c835bf10>: chaining up to <bound method _GetDevicesCall._reply_handler of <cupshelpers.cupshelpers._GetDevicesCall object at 0x7f05cb59b5e0>>
fetchDevices
+<asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>
<asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>: calling <bound method PK1Connection.getDevices of <asyncpk1.PK1Connection object at 0x7f05c835bee0>>
Converted ()/{'include_schemes': ['dnssd', 'snmp', 'driverless', 'bjnp', 'bluetooth'], 'reply_handler': <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>>, 'error_handler': <bound method _AsyncMethodCall.error_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>>, 'auth_handler': <bound method _AsyncMethodCall.auth_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>>} to (0, 0, ['dnssd', 'snmp', 'driverless', 'bjnp', 'bluetooth'], [])
+_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59bac0>
Calling PK method DevicesGet
<asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59bac0>: calling <dbus.proxies._DeferredMethod object at 0x7f05cb59bca0>
Adding device with URI ipp
Device ipp added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,ipp)>
   Created physical device <PhysicalDevice.PhysicalDevice (,,,None,None,ipp)>
   Physical device <PhysicalDevice.PhysicalDevice (,,,None,None,ipp)> is a completely new device
Adding device with URI lpd
Device lpd added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,lpd)>
   Created physical device <PhysicalDevice.PhysicalDevice (,,,None,None,lpd)>
   Physical device <PhysicalDevice.PhysicalDevice (,,,None,None,lpd)> is a completely new device
Adding device with URI ipps
Device ipps added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,ipps)>
   Created physical device <PhysicalDevice.PhysicalDevice (,,,None,None,ipps)>
   Physical device <PhysicalDevice.PhysicalDevice (,,,None,None,ipps)> is a completely new device
Adding device with URI cups-brf:/
Device cups-brf:/ added to physical device: <PhysicalDevice.PhysicalDevice (Generic,CUPS-BRF,,None,None,cups-brf:/)>
   Created physical device <PhysicalDevice.PhysicalDevice (Generic,CUPS-BRF,,None,None,cups-brf:/)>
   Physical device <PhysicalDevice.PhysicalDevice (Generic,CUPS-BRF,,None,None,cups-brf:/)> is a completely new device
Adding device with URI https
Device https added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,https)>
   Created physical device <PhysicalDevice.PhysicalDevice (,,,None,None,https)>
   Physical device <PhysicalDevice.PhysicalDevice (,,,None,None,https)> is a completely new device
Adding device with URI socket
Device socket added to physical device: <PhysicalDevice.PhysicalDevice (,,,None,None,socket)>
   Created physical device <PhysicalDevice.PhysicalDevice (,,,None,None,socket)>
   Physical device <PhysicalDevice.PhysicalDevice (,,,None,None,socket)> is a completely new device
DESTROY: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59b670>
-<asyncconn._AsyncMethodCall object at 0x7f05cb59b640>
-_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59b670>
<asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59bac0>: no error, calling reply handler <bound method _AsyncMethodCall.reply_handler of <asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>>
<asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>: to reply_handler at <bound method Connection._subst_reply_handler of <asyncconn.Connection object at 0x7f05c835bf10>>
DESTROY: <asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>
<asyncconn.Connection object at 0x7f05c835bf10>: chaining up to <bound method _GetDevicesCall._reply_handler of <cupshelpers.cupshelpers._GetDevicesCall object at 0x7f05cb59ba30>>
DESTROY: <asyncconn.Connection object at 0x7f05c835bf10>
DESTROY: <asyncpk1.PK1Connection object at 0x7f05c835bee0>
DESTROY: <asyncipp.IPPAuthConnection object at 0x7f05c835bfd0>
Stopping worker thread
Next task: None
Thread exiting
-<asyncipp._IPPAuthOperation object at 0x7f05c835bdc0>
-<asyncconn.Connection object at 0x7f05c835bf10>
DESTROY: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59bac0>
-<asyncconn._AsyncMethodCall object at 0x7f05cb59ba90>
-<asyncpk1.PK1Connection object at 0x7f05c835bee0>
-_PK1AsyncMethodCall: <asyncpk1._PK1AsyncMethodCall object at 0x7f05cb59bac0>
-<asyncipp.IPPAuthConnection object at 0x7f05c835bfd0>
-<_IPPConnectionThread(Thread-1, stopped daemon 139662828361472)>
No firewall 
Examining firewall
<firewallsettings.SystemConfigFirewall object at 0x7f05cb57b850> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
<firewallsettings.SystemConfigFirewall object at 0x7f05cb57b850> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
<firewallsettings.SystemConfigFirewall object at 0x7f05cb57b850> in _get_fw_data: _fw_data is (None, None)
Using cached firewall data
Firewall all OK, no changes needed
Selected connection type. URI: network
Calling <bound method PrinterFinder._do_find of <probe_printer.PrinterFinder object at 0x7f05c834a310>>
hplip: trying
hplip: no good (return code 1)
jetdirect: trying
jetdirect: :9100 CLOSED
jetdirect: done
ipp: trying
ipp: can't resolve 
ipp: no good
snmp: trying
snmp: done
lpd: trying
lpd: couldn't connect
lpd: done
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
  smb2: 10
  smb2_credits: 10
  dsdb_audit: 10
  dsdb_json_audit: 10
  dsdb_password_audit: 10
  dsdb_password_json_audit: 10
  dsdb_transaction_audit: 10
  dsdb_transaction_json_audit: 10
  dsdb_group_audit: 10
  dsdb_group_json_audit: 10
Using netbios name STUDIO20.
Using workgroup WORKGROUP.
smb: trying
parsed path: fname='smb:///' server='WORKGROUP' share='' path='' options=''
SMBC_check_options(): server='WORKGROUP' share='' path='' options=''
pysmb: got password callback
lp_load_ex: refreshing parameters
Freeing parametrics:
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
  smb2: 10
  smb2_credits: 10
  dsdb_audit: 10
  dsdb_json_audit: 10
  dsdb_password_audit: 10
  dsdb_password_json_audit: 10
  dsdb_transaction_audit: 10
  dsdb_transaction_json_audit: 10
  dsdb_group_audit: 10
  dsdb_group_json_audit: 10
pm_process() returned No
lp_servicenumber: couldn't find homes
Could not load config file: /home/kx20/.smb/smb.conf
lp_load_ex: refreshing parameters
Freeing parametrics:
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
  smb2: 10
  smb2_credits: 10
  dsdb_audit: 10
  dsdb_json_audit: 10
  dsdb_password_audit: 10
  dsdb_password_json_audit: 10
  dsdb_transaction_audit: 10
  dsdb_transaction_json_audit: 10
  dsdb_group_audit: 10
  dsdb_group_json_audit: 10
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter logging = file
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
lp_servicenumber: couldn't find homes
lp_load_ex: refreshing parameters
Freeing parametrics:
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
  smb2: 10
  smb2_credits: 10
  dsdb_audit: 10
  dsdb_json_audit: 10
  dsdb_password_audit: 10
  dsdb_password_json_audit: 10
  dsdb_transaction_audit: 10
  dsdb_transaction_json_audit: 10
  dsdb_group_audit: 10
  dsdb_group_json_audit: 10
pm_process() returned No
lp_servicenumber: couldn't find homes
Could not append config file: /home/kx20/.smb/smb.conf.append
added interface enp0s7 ip=192.168.0.10 bcast=192.168.0.255 netmask=255.255.255.0
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
  smb2: 10
  smb2_credits: 10
  dsdb_audit: 10
  dsdb_json_audit: 10
  dsdb_password_audit: 10
  dsdb_password_json_audit: 10
  dsdb_transaction_audit: 10
  dsdb_transaction_json_audit: 10
  dsdb_group_audit: 10
  dsdb_group_json_audit: 10
pysmb: operation failed: ConnectionRefusedError(111, 'Connexion refusée')
pysmb: authentication pass: 2
pysmb: try auth as guest
pysmb: got password callback
pysmb: operation failed: ConnectionRefusedError(111, 'Connexion refusée')
pysmb: authentication pass: 3
pysmb: try as kx20
get_notifications
update_jobs
Next notifications fetch in 60s
```

I think I will make a bug report for pysmb .

---

