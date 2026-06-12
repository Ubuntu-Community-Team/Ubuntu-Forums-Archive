---
title: "ping gui doesn't seem to work"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by audit on 2010-11-09
When I go to "system => administrative => network tools" and go to the Ping
tab where I enter an address. The response is always "packets received 0".

If I ping from the terminal I get the result I expect. Is this a bug or am I doing something stupid?

---

### Post by SuaSwe on 2010-11-09
Just so we know, could you confirm exactly what you're typing in/selecting in Terminal vs Network Tools?

---

### Post by audit on 2010-11-10
This is what I typed to the terminal:
```
ping -c 5 google.com
```
This is the output from the terminal:
```
PING google.com (72.14.204.147) 56(84) bytes of data.
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=1 ttl=53 time=43.1 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=2 ttl=53 time=44.2 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=3 ttl=53 time=44.8 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=4 ttl=53 time=43.2 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=5 ttl=53 time=42.1 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 42.113/43.528/44.832/0.973 ms
```

I typed the same address into the "Ping - Network Tools" Network Address box two minutes later and my out put was :
Packets Transmitted 5
Packets Received 0

---

### Post by GabrielYYZ on 2010-11-10
same thing happens to me if i try to ping anything from the network tools GUI. i guess i didn't pay too much attention to it or reported it as a bug 'cause it is a very minor issue and, to be honest, i'm more comfortable with ping/trace/whois from the terminal.

---

### Post by toekneewood on 2010-11-10
I have just done the same test.  Terminal OK.  GUI has sent 5 and received 0.  mmm very odd.

---

### Post by toekneewood on 2010-11-10
Just ran the application from the CLI so that I could see the application output.  The results are as follows.  Hopefully someone might be able to spot the problem
```

twood@twood-desktop:~$ gnome-nettool 
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): GLib-GObject-WARNING **: invalid cast from `GtkToggleAction' to `GtkWidget'
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
command: /bin/ping ping -b -c 5 -n 192.168.1.1
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_entry_set_text: assertion `text != NULL' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
(gnome-nettool:9322): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

```

---

### Post by toekneewood on 2010-11-10
Looks like someone has logged a bug report for this one
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/663014](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/663014)

---

### Post by NightwishFan on 2010-11-10
Thanks, I have this problem as well. I will look at the bug report.

---

### Post by johnmay on 2010-12-05
Quite frustrating when trying to use guest internet connection on 64 bit host that almost works! AARRGGHH

---

