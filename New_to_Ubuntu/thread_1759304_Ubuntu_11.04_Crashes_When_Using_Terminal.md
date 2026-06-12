---
title: "Ubuntu 11.04 Crashes When Using Terminal"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by age99 on 2011-05-15
Hi, each time that I open a terminal, Ubuntu 11.04 crashes.  All the menus disappear, and I can only access things through the terminal, or by opening individual workspaces and programs. 

Anyone else experiencing this?

---

### Post by age99 on 2011-05-16
This is the bug report produced when the unity crashes:

> System: Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
X Vendor: The X.Org Foundation
X Vendor Release: 11001000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Ambiance
Icon Theme: ubuntu-mono-dark
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 198782976 vsize: 198782976 resident: 66871296 share: 30138368 rss: 66871296 rss_rlim: 18446744073709551615
CPU usage: start_time: 1305478333 rtime: 408 utime: 333 stime: 75 cutime:0 cstime: 1 timeout: 0 it_real_value: 0 frequency: 100



---- Critical and fatal warnings logged during execution ----

** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
** GLib-GObject **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 


----------- .xsession-errors ---------------------
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1632): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/age/1703: No such file or directory.
No stack.
--------------------------------------------------


---

