---
title: "Strange error in X"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by cjnkns on 2009-01-26
For the second time I have seen a strange error when logging into X.

First, when I did a fresh install of ubuntu used it for a while the when I logged out and tried to log back in. I received a dialog box stating something like my session only lasted less than 10 seconds..etc... I can't remember the rest.

But, I just tired to install openbox. I logged out and tried to log back in using openbox/gnome and saw the same/similar message as stated above.
The first time I had to reinstall, luckily I have not had to yet as I chose to log in under gnome instead of openbox.

anyone familiar with this? What should I do if I see it again? :(

---

### Post by cjnkns on 2009-01-27
Hmm I am the only one who has seen this issue. That's a bummer :(

---

### Post by urukrama on 2009-01-27
That dialog is not so uncommon.

Have a look in ~/..xsession-errors That might give you a clue of why X crashed as soon as it was loaded.

How do you login? Do you use GDM?

---

### Post by cjnkns on 2009-01-27
Sorry, but I can not figure out how to find this directory/file?

---

### Post by cjnkns on 2009-01-27
Ehh scratch that - I found it in my home directory I was looking for a folder named X... any way here is the output (doesn't tell me much)





> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Window manager warning: Failed to read saved session file /home/carl/.config/metacity/sessions/10c9247769b704ce1d123302360647018900000058320002.ms: Failed to open file '/home/carl/.config/metacity/sessions/10c9247769b704ce1d123302360647018900000058320002.ms': No such file or directory
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:5968): WARNING **: Unable to add monitor: Not supported
gnome-session[5832]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC
evolution-alarm-notify-Message: Setting timeout for 12379 1233036000 1233023621
evolution-alarm-notify-Message:  Tue Jan 27 00:00:00 2009

evolution-alarm-notify-Message:  Mon Jan 26 20:33:41 2009

Throttle level is 5
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-appearance-properties:6270): Gtk-WARNING **: Unable to locate theme engine in module_path: "nodoka",

(gnome-appearance-properties:6270): Gtk-WARNING **: Unable to locate theme engine in module_path: "nodoka",
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1233036000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
alarm-notify.c:240 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1851 (alarm_queue_init)
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Tue Jan 27 00:00:00 2009
 
alarm-notify.c:217 (load_calendars) - Loading Calendar file:///home/carl/.evolution/calendar/local/system 
alarm-notify.c:389 (alarm_notify_add_calendar) file:///home/carl/.evolution/calendar/local/system - Calendar Open Async... 0x8688a80
alarm-notify.c:217 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:389 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x8689980
alarm-notify.c:217 (load_calendars) - Loading Calendar file:///home/carl/.evolution/tasks/local/system 
alarm-notify.c:389 (alarm_notify_add_calendar) file:///home/carl/.evolution/tasks/local/system - Calendar Open Async... 0x868fba0
alarm-notify.c:217 (load_calendars) - Loading Calendar file:///home/carl/.evolution/memos/local/system 
alarm-notify.c:389 (alarm_notify_add_calendar) file:///home/carl/.evolution/memos/local/system - Calendar Open Async... 0x8692d20
alarm-notify.c:317 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:1985 (alarm_queue_add_async) - 0x8689980
alarm-queue.c:594 (load_alarms_for_today) - From Mon Jan 26 00:00:00 2009
 to Mon Jan 26 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-notify.c:317 (cal_opened_cb) file:///home/carl/.evolution/calendar/local/system - Calendar Status 0
alarm-notify.c:317 (cal_opened_cb) file:///home/carl/.evolution/tasks/local/system - Calendar Status 0
alarm-notify.c:317 (cal_opened_cb) file:///home/carl/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:1985 (alarm_queue_add_async) - 0x8688a80
alarm-queue.c:594 (load_alarms_for_today) - From Mon Jan 26 00:00:00 2009
 to Mon Jan 26 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:1985 (alarm_queue_add_async) - 0x868fba0
alarm-queue.c:594 (load_alarms_for_today) - From Mon Jan 26 00:00:00 2009
 to Mon Jan 26 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:1985 (alarm_queue_add_async) - 0x8692d20
alarm-queue.c:594 (load_alarms_for_today) - From Mon Jan 26 00:00:00 2009
 to Mon Jan 26 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:1821 (check_midnight_refresh)
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:234 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:594 (load_alarms_for_today) - From Tue Jan 27 00:00:00 2009
 to Tue Jan 27 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:550 (load_alarms) - Disconnecting old queries 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:234 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:594 (load_alarms_for_today) - From Tue Jan 27 00:00:00 2009
 to Tue Jan 27 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:550 (load_alarms) - Disconnecting old queries 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:234 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:594 (load_alarms_for_today) - From Tue Jan 27 00:00:00 2009
 to Tue Jan 27 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:550 (load_alarms) - Disconnecting old queries 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:234 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:594 (load_alarms_for_today) - From Tue Jan 27 00:00:00 2009
 to Tue Jan 27 00:00:00 2009

alarm-queue.c:531 (load_alarms) 
alarm-queue.c:550 (load_alarms) - Disconnecting old queries 
alarm-queue.c:560 (load_alarms) - Setting Call backs 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Wed evolution-alarm-notify-Message: Setting timeout for 86400 1233122400 1233036000
evolution-alarm-notify-Message:  Wed Jan 28 00:00:00 2009

evolution-alarm-notify-Message:  Tue Jan 27 00:00:00 2009

** (evolution:16626): DEBUG: mailto URL command: evolution %s
** (evolution:16626): DEBUG: mailto URL program: evolution
** (evolution:8274): DEBUG: mailto URL command: evolution %s
** (evolution:8274): DEBUG: mailto URL program: evolution
ERROR: Could not get information from repository: [http://do.davebsd.com/repo/0.6.0/official/main.mrep](http://do.davebsd.com/repo/0.6.0/official/main.mrep)
System.Net.WebException: Error: NameResolutionFailure
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadFile (IProgressMonitor monitor, System.String url) [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadObject (IProgressMonitor monitor, System.String url, System.Type type) [0x00000] 
  at Mono.Addins.Setup.RepositoryRegistry.UpdateRepository (IProgressMonitor monitor, System.Uri baseUri, Mono.Addins.Setup.RepositoryRecord rr) [0x00000] 
ERROR: Could not get information from repository: [http://do.davebsd.com/repo/0.6.0/community/main.mrep](http://do.davebsd.com/repo/0.6.0/community/main.mrep)
System.Net.WebException: Error: NameResolutionFailure
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadFile (IProgressMonitor monitor, System.String url) [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadObject (IProgressMonitor monitor, System.String url, System.Type type) [0x00000] 
  at Mono.Addins.Setup.RepositoryRegistry.UpdateRepository (IProgressMonitor monitor, System.Uri baseUri, Mono.Addins.Setup.RepositoryRecord rr) [0x00000] 
ERROR: Could not get information from repository: [http://do.davebsd.com/repo/0.6.0/official/main.mrep](http://do.davebsd.com/repo/0.6.0/official/main.mrep)
System.Net.WebException: Error: NameResolutionFailure
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadFile (IProgressMonitor monitor, System.String url) [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadObject (IProgressMonitor monitor, System.String url, System.Type type) [0x00000] 
  at Mono.Addins.Setup.RepositoryRegistry.UpdateRepository (IProgressMonitor monitor, System.Uri baseUri, Mono.Addins.Setup.RepositoryRecord rr) [0x00000] 
ERROR: Could not get information from repository: [http://do.davebsd.com/repo/0.6.0/community/main.mrep](http://do.davebsd.com/repo/0.6.0/community/main.mrep)
System.Net.WebException: Error: NameResolutionFailure
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadFile (IProgressMonitor monitor, System.String url) [0x00000] 
  at Mono.Addins.Setup.AddinStore.DownloadObject (IProgressMonitor monitor, System.String url, System.Type type) [0x00000] 
  at Mono.Addins.Setup.RepositoryRegistry.UpdateRepository (IProgressMonitor monitor, System.Uri baseUri, Mono.Addins.Setup.RepositoryRecord rr) [0x00000] 
** (evolution:11181): DEBUG: mailto URL command: evolution %s
** (evolution:11181): DEBUG: mailto URL program: evolution
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

sh: ctags: not found
sh: ctags: not found
sh: ctags: not found
sh: ctags: not found
command: ctags -n -f /tmp/tmpj9oss8 /home/carl/.*
command: ctags -n -f /tmp/tmprckD_m /home/carl/.*
command: ctags -n -f /tmp/tmp6N3S4f /home/carl/.*
command: ctags -n -f /tmp/tmpQK-B8v /home/carl/.*
sh: ctags: not found
sh: ctags: not found
sh: ctags: not found

---

