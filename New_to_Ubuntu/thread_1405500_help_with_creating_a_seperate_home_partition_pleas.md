---
title: "help with creating a seperate home partition please"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-12
I've been following these directions given to me in another thread.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I'm getting hung up at a line of code in the second black box...

```
find . -depth -print0 | cpio --null --sparse -pvd /new/
r directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/44: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/8: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/60/39feac3c-22190331.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/60/39feac3c-22190331: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/60: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/host: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/18: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/25: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/27: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/52: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/7: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/53: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/32: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/45: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/34: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/0: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/28: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/2: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/55: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/tmp: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/31: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/6: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/29/40ea25d-12224fbd: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/29/40ea25d-12224fbd.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/29: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/62: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/19: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/56: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/48: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/33/2a481721-505caf2a.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/33/2a481721-505caf2a: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/33: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/42: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/41/55a4069-315bbbb9.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/41/55a4069-315bbbb9: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/41: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/43: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/11: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/3: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/51: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/17: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/63: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/4: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/40: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/35: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/49/1284cf71-7ca4260c.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/49/1284cf71-7ca4260c: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/49: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/12/178f604c-13951ac5.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/12/178f604c-13951ac5: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/12: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/37: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/61: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/46: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/36/568996a4-6d7adc62: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/36/568996a4-6d7adc62.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/36: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/9: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/54: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/24: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/20/68e2a1d4-768809b1.idx: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/20/68e2a1d4-768809b1: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/20: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/muffin: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/lastAccessed: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/14: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/30: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/5: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/26: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/38: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/59: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/47: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/50: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/39: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/23: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0/21: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache/6.0: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/cache: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/ext: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/deployment.properties: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment/log: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java/deployment: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.java: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.adobe: Cannot stat: No such file or directory
cpio: ./mike/.config/user-dirs.dirs: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.config/compiz: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.config/user-dirs.locale: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.config/gtk-2.0: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.config/tracker: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.config: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.icons: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/Templates: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.metacity: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/Videos: Cannot stat: No such file or directory
cpio: ./mike/.wapi/shared_data-mike-laptop-Linux-i686-312-11-0: Cannot open: Permission denied
cpio: ./mike/.wapi/shared_fileshare-mike-laptop-Linux-i686-36-11-0: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.wapi: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gnupg: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.thumbnails: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.childsplay.score: Cannot open: No such file or directory
cpio: ./mike/.bash_history: Cannot open: Permission denied
cpio: ./mike/.gstreamer-0.10/registry.i486.xml: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gstreamer-0.10: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gtk-bookmarks: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.xsession-errors: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gvfs: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/Music: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/Pictures: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/Public: Cannot stat: No such file or directory
cpio: ./mike/.esd_auth: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.mozilla: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/cron-o-meter.sh: Cannot open: No such file or directory
cpio: ./mike/.dmrc: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /usr/share/example-content: Cannot create symlink to `/new//./mike/Examples': No such file or directory
cpio: ./mike/.gksu.lock: Cannot open: Permission denied
cpio: ./mike/.pulse-cookie: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.fontconfig: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/mms.cfg: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/tasks/local: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/tasks/config: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/tasks: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/categories.xml: Cannot open: No such file or directory
cpio: ./mike/.evolution/key3.db: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/cache/tmp/mail.log.4bM7gL: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/cache/tmp/mail.log.I4MynE: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/cache/tmp: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/cache: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/memos/local: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/memos/config: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/memos: Cannot stat: No such file or directory
cpio: ./mike/.evolution/camel-cert.db: Cannot open: Permission denied
cpio: ./mike/.evolution/secmod.db: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/calendar/local: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/calendar/config: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/calendar: Cannot stat: No such file or directory
cpio: ./mike/.evolution/cert8.db: Cannot open: Permission denied
cpio: ./mike/.evolution/mail/local/Outbox.ibex.index: Cannot open: Permission denied
cpio: ./mike/.evolution/mail/local/Outbox.ibex.index.data: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Drafts.cmeta: Cannot open: No such file or directory
cpio: ./mike/.evolution/mail/local/Drafts.ibex.index.data: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Outbox.cmeta: Cannot open: No such file or directory
cpio: ./mike/.evolution/mail/local/Inbox.ibex.index: Cannot open: Permission denied
cpio: ./mike/.evolution/mail/local/Sent.ibex.index.data: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Sent.cmeta: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Sent: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Drafts: Cannot open: No such file or directory
cpio: ./mike/.evolution/mail/local/Drafts.ibex.index: Cannot open: Permission denied
cpio: ./mike/.evolution/mail/local/Inbox.ibex.index.data: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Inbox.cmeta: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Outbox: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local/Inbox: Cannot open: No such file or directory
cpio: ./mike/.evolution/mail/local/Sent.ibex.index: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail/local: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution/mail: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.evolution: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.bashrc: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.macromedia: Cannot stat: No such file or directory
cpio: ./mike/.local/share/tracker/data/common.db: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.local/share/tracker/data: Cannot stat: No such file or directory
cpio: ./mike/.local/share/tracker/tracker.log: Cannot open: Permission denied
cpio: ./mike/.local/share/tracker/mike_tracker_lock: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.local/share/tracker: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.local/share/Trash: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.local/share: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.local: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.pulse/default-source: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.pulse/default-sink: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.pulse/volume-restore.table: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.pulse: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.sudo_as_admin_successful: Cannot open: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gnome2_private: Cannot stat: No such file or directory
cpio: ./mike/.nautilus/saved-session-1N776U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-B2HC7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-M76O7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-8G7M6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-4H2F7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-4TO66U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-CQ5M7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-UNN76U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-MNBO7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-Z3XD8U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-1L5A7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-FTHM7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-NBNK6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-6YD66U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-RUNV7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-S1GE7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-787Y6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-DH0U6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-S0N26U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-W0UR7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-ZZZR7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-P2I36U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-N5K47U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-S7DN7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-F5JH7U: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.nautilus/metafiles: Cannot stat: No such file or directory
cpio: ./mike/.nautilus/saved-session-DW7J7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-4HI46U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-BN866U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-TPJB7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-CB7F7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-4QNE8U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-NDKQ7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-2H206U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-9RH86U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-YQSR6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-SWV16U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-A14O7U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-URT57U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-KRWP6U: Cannot open: Permission denied
cpio: ./mike/.nautilus/saved-session-ZZ4O6U: Cannot open: Permission denied
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.nautilus: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.compiz: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.gconf: Cannot stat: No such file or directory
cpio: cannot make directory `/new//./mike': Permission denied
cpio: /new//./mike/.profile: Cannot open: No such file or directory
cpio: /new//./mike: Cannot stat: Permission denied
```


I know that's a lot but I don't know which details are relevant.

Thanks,
Mike

---

### Post by hortstu on 2010-02-12
thanks found the solution.

---

### Post by QIII on 2010-02-12
Don't know if you'll look back at this, but could you please post your solution for the next guy?
 
We all learn here.

---

### Post by hortstu on 2010-02-12
Well further down the page in the link the author suggests using sudo before the command in question.  That worked... however at startup I did get an error message and I couldn't boot.  I'm going back to the site now trouble shoot.

---

