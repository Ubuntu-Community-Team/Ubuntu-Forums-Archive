---
title: "Can't access networking configuration (crashes)"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by Skidpad on 2007-04-07
After having a fine working Edgy since installation 3 months ago, I now have my first major problem.

Coincidental or not, I had tried to access a hotel's wi-fi earlier this week.  (Yes, I was staying there).  After changing the networking configuration as I have done in the past to access new networks (I don't use Network Manager), I thought I was home free.  When I still couldn't access the hotel wi-fi,  I tried to go back into the configuration panel again, and I was confronted with a "Bug Reporting Tool".

This tool gathered information about my system, but would not let me back into the configuration panel.  I eventually gave up at the hotel and shutdown my laptop.

Now home, I still can't access my networking configuration.  The system goes into bug reporting mode each time I attempt to open it; System>Administration>Networking.

Anyone have any tips on how to fix this?  I've searched the forum and found all kinds of crash info, but none that really described this.

I've connected my laptop via my wired connection as well, but it didn't work either.  Both connections (wired/wireless or eth0/ra0, separately) appear to be getting an IP address from my router, but cannot access the 'net.

Any help would be greatly appreciated!

---

### Post by RomeReactor on 2007-04-07
Hi. I doubt it's a problem related to the configuration of your card; so try this in a terminal

```
gksudo network-admin
```

to bring up the Networking program and look at the output in the terminal. It should give us a clue as to what is causing the crash.

---

### Post by Skidpad on 2007-04-08
Thanks for the response Rome!

Here's the output:

[B]jim@LinuxLaptop:~$ gksudo network-admin
(network-admin:25129): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(bug-buddy:25142): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (bug-buddy:25142): WARNING **: Couldn't load icon for Open Folder

(bug-buddy:25142): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
jim@LinuxLaptop:~$ 
    [/B]

(I'm trying to attach one of the actual crash files for any additional help it may provide)

:EDIT For some reason I can't attach the crash file (invalid format) even though it is a .txt file <19.5 kb...so here is another copy/paste:

[B]
Memory status: size: 49545216 vsize: 0 resident: 49545216 share: 0 rss: 11386880 rss_rlim: 0
CPU usage: start_time: 1175982229 rtime: 0 utime: 79 stime: 0 cutime:72 cstime: 0 timeout: 7 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

[Thread debugging using libthread_db enabled]
[New Thread -1225304400 (LWP 6072)]

(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7389323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f1d1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb763c8f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#5  0xb7613536 in g_datalist_id_set_data_full ()
   from /usr/lib/libglib-2.0.so.0
#6  0xb76f3852 in g_object_class_override_property ()
   from /usr/lib/libgobject-2.0.so.0
#7  0xb770f6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#8  0xb76f6952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#9  0xb76f4bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#10 0xb76f573f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#11 0xb76f58f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#12 0xb788cd97 in pango_context_new () from /usr/lib/libpango-1.0.so.0
#13 0xb78b7ee7 in pango_cairo_font_map_create_context ()
   from /usr/lib/libpangocairo-1.0.so.0
#14 0xb790b29f in gdk_pango_context_get_for_screen ()
   from /usr/lib/libgdk-x11-2.0.so.0
#15 0xb7bc47e5 in gtk_widget_create_pango_context ()
   from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb7bc48ee in gtk_widget_get_pango_context ()
   from /usr/lib/libgtk-x11-2.0.so.0
#17 0xb7bc496b in gtk_widget_create_pango_layout ()
   from /usr/lib/libgtk-x11-2.0.so.0
#18 0xb7a94a49 in gtk_label_get_angle () from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb7a99d4e in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#21 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#22 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#23 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#24 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#25 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#26 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#27 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7a6c040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#30 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#31 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#32 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#33 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#34 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#35 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#36 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb79d306f in gtk_alignment_new () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#41 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#42 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#43 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#44 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#45 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#46 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#47 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#49 0xb79e024f in gtk_button_set_alignment ()
   from /usr/lib/libgtk-x11-2.0.so.0
#50 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#51 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#52 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#53 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#54 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#55 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#56 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#57 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#58 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#59 0xb79d87c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#60 0xb7a6b710 in gtk_hbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
#61 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#62 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#63 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#64 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#65 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#66 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#67 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#68 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#69 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#70 0xb7bbd450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#72 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#73 0xb76ef87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#74 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#75 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#76 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#77 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#78 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#79 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#80 0xb7bce990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#81 0xb76fc199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#82 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#83 0xb76ef79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#84 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#85 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#86 0xb7703e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#87 0xb7b11cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#88 0xb7b11f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#89 0xb7bc6b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#90 0xb7bced10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#91 0xb7bd7fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#92 0xb76fcb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#93 0xb76edfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#94 0xb76ef79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#95 0xb770002a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#96 0xb77010b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#97 0xb7701279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#98 0xb7bc7b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#99 0x08057ade in ?? ()
#100 0x0818d0b8 in ?? ()
#101 0x080c21c0 in ?? ()
#102 0x0805b2a0 in ?? ()
#103 0x00000003 in ?? ()
#104 0x00000000 in ?? ()
[/B]

Thanks again

---

### Post by Roland of Gilead on 2007-04-08
I'm getting the same behavior on my wife's Thinkpad T40 running Edgy.

The built-in wireless device (Centrino ipw2200), interestingly enough, registers as eth1 rather than wlan0.

I run it using a static IP address, connecting to a Linksys WRT54GP2 (Vonage) router.  The wireless device stops communicating via IP after the first couple minutes of usage.  The status panel still shows a link and packet activity, but all IP comms are lost.  No pings, nothing.  Route data looks fine, too.

Bouncing the wireless device (ifdown/ifup) does nothing...but oddly enough, bouncing the *router* will restore comms.  But only for a few minutes.


EDIT:
Probably should mention, my WLAN does not use any encryption at all...I just use MAC filtering at the router, so no WPA or WEP keys to blame.  Not the most secure setup, but out here in the burbs, I'm not worried.

---

### Post by Skidpad on 2007-04-08
^^^  Interesting.  Have you tried the laptop on another network?  That would certainly tell you a lot about what's going on.

As for me, I am confident my network (admin) is functional; the reason I can't access anything is that the network configuration is still looking at the setup I created while at the hotel - I changed the DNS settings, and I believe it is still looking for those.

The problem is networking crashes when I try to open it up to change my settings back to "Home".

Anybody?

---

### Post by RomeReactor on 2007-04-08
> ** (bug-buddy:25142): WARNING **: Couldn't load icon for Open Folder

Skidpad, it looks like the Networking program can't locate an icon; that may be why it's crashing. I'm not sure. However, it's part of a larger package called **gnome-system-tools**, and probably reinstalling it could solve your problem with it, though I'm not too keen on recommending you do that--This are some of the programs provided by that package:

```
/usr/bin/network-admin
/usr/bin/services-admin
/usr/bin/shares-admin
/usr/bin/time-admin
/usr/bin/users-admin
```

Perhaps someone else can recommend you a different solution, but for now either you:

A) Install **network-manager** to configure your wireless card; or

B) Manually edit the "/etc/network/interfaces" file to get your wireless up and running; or

C) Reinstall gnome-system-tools through Synaptic.

---

### Post by Skidpad on 2007-04-09
RomeReactor: first of all, Thanks again for your help - your last post was the impetus for me to have a place to start digging in my system and finally resolve this.  I couldn't load Network Manager - or anything else for that matter - because I had no network connection whatsoever.  Your post got me digging, and here is what I found:

1:  My etc/network/interfaces file was still plugged with the hotel info - IP address, everything.  I gksudo'd/gedit'd into the file and deleted that useless info.

2: After doing that, it was obvious that there was another file somewhere that still held network settings - the hotel info was still popping up in my Conky, and my network icon in my upper panel.  Hmm.  Time to keep digging.

3: I eventually got to my etc/hosts file.  This too, contained the hotel info, and once again, I nuked it.

4: I was on onto something.  When I went back into my network configuration it didn't crash!!  Home- free, right?  Wrong.

5: Even after restarting X, I couldn't access my network.  More head-scratching.  All my settings seemed correct, and my network configuration even changed back and forth when I selected Home/Work.  

6: So I tried a full reboot, and I knew I was in business once my Conky came up - I had an IP address from MY network, and my signal strength indicator in my upper panel was functioning.  So once again, back into FireFox I go, and Viola!  Success!

It all seems to be functioning fine now.  Either the system crashed for unknown reasons while configuring my network settings, or I goofed up royally when inputting the settings.  No matter now, it was a learning experience, and that's what this is all about, isn't it?

:)

---

### Post by RomeReactor on 2007-04-09
Glad to hear you got it working! Troubleshooting problems is certainly a good way to learn about one's system :KS

---

### Post by hollerith on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/67936](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/67936) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have this problem - its something in the /etc/hosts file.  I connect to work and home and its a real pain.  

[See this bug:]("https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/67936")

---

### Post by Nemo Omnibus on 2007-06-14
Hi Folks,  I am new to this forum but have the same issue (for the last week) when attempting to access network-admin from System=>Administration=>Networking.  Bombs out when I use gksudo network-admin on the command line too (Plenty of examples of the error output above -Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed., etc.).  /etc/hosts hasn't changed since Dec. 2006 so I do not think it is an  issue.  /etc/network/interfaces, likewise, hasn't changed.  About the only thing I did before this bug presented itself was configure a WI-FI connection manually at a friends house, i.e. ran iwconfig with his SSID, channel info. etc.  I could then connect via his un-secured WI-FI.  After that every attempt to access nework-admin crashes.  I have googled, I have looked at bug reports and postings and I can not find a relevant fix.  Currently running Ubuntu Edgy 6.10 2.6.17-11.  I use ubuntu on my work machine and connect from home, etc. and it is causing me some severe grief.

Is there anyone out there who has a definitive fix/answer for this?  Any and all help is much appreicated.

---

### Post by Skidpad on 2007-06-15
Hi Nemo.  Your situation/problem sounds identical to mine - except yours happened at a friend's house, and mine crashed while attempting to connect to my hotel's wi-fi.  

Did you try my solutions in post #7 above?  I had to purge (delete) the hotel network info from my *etc/network/interfaces* and *etc/hosts* files.  After a reboot, I was back in business - and have been ever since, at home & at work.

---

### Post by h0me5k1n on 2007-07-10
Thanks Skidpad, hollerith and RomeReactor.  network-admin was constantly crashing upon opening.

edited /etc/network/interfaces and /etc/hosts to remove redundant entries from a recently connected network and it now woks without a reboot.

---

