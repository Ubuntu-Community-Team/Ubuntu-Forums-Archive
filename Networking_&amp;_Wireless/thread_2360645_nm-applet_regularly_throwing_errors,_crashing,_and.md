---
title: "nm-applet regularly throwing errors, crashing, and not showing my access point"
date: 2017-05-06
forum: Networking &amp; Wireless
---

### Post by john+smith on 2017-05-06
The following issues are on Ubuntu MATE 16.04 with Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01) on a Intel(R) Core(TM) i7-3537U CPU @ 2.00GHz with 8GB RAM

Background:

[LIST]
[*]nm-applet regularly does not show my access point
[LIST]
[*]To get around this, I can sometimes use "Connect to Hidden Wi-Fi Network", and enter it manually or select it from the list, but it doesn't always work
[/LIST]

[*]Additionally, it regularly crashes, after which I reopen it in a terminal via `dbus-launch nm-applet` that I just leave open. In this terminal, I always receive the following error upon launch:
[/LIST]
```

(nm-applet:11328): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed

```


[LIST]
[*]Following that, I receive the following error over and over again:
[/LIST]
```

(nm-applet:28196): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed

```


[LIST]
[*]And while that happens regularly, it's usually able to bounce back. However, it often regularly crashes entirely
[/LIST]
```

(nm-applet:4996): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'NMAWifiDialog'

(nm-applet:4996): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion 'instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

```
[LIST]
[*]At this point, sometimes the wireless is still intact, but sometimes it isn't, which restarts the cycle.
[*]Another less important quip I'll mention is just how sluggish nm-applet seems to be
[LIST]
[*]The wifi icon in the tray freezes while working instead of animating like it used to
[*]There's a noticeable lag when clicking on the icon and getting the list of APs
[*]The "Connect to Hidden Wi-Fi Network" dialog has a noticeable delay between opening and rendering
[/LIST]
[/LIST]

Questions
[LIST]
[*]Is this behavior normal?
[*]Are there alternatives to these issues, which I didn't have in Ubuntu 10 or 14?
[*]What are your suggestions?
[/LIST]

---

### Post by ace28 on 2017-05-13
Hi there,

I have similar issues with the nm-applet. I'm using Ubuntu MATE 16.04 and a Broadcom BCM43227.

For some time now my wifi had random disconnects and the nm-applet regularly crashes, especially after I wake up my laptop from closing it, therefore after a standby.

Sometimes I get an error message from Ubuntu stating:


[LIST]
[*]nm-applet crashed with SIGSEGV in g_main_context_dispatch()
[/LIST]

After a crash like this I could only restart my laptop to get wifi and the applet back. Only recently I discovered that I can revive the applet by calling it in the terminal by simply calling:


[LIST]
[*]nm-applet
[/LIST]

There I also constantly get the error message:


[LIST]
[*](nm-applet:11904): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
[/LIST]


But apart from this, the workaround seems to work. When the applet suffers a crash, I just restart it from the terminal.

I hope this post may help with finding a solution to this issue. Please let me know if I can help with additional details :) 

Best regards,

ace28

---

