---
title: "autossh sessions not removed"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2014-06-01
I have this thing were I monitor and maintain servers and media centers for family. Mostly Ubuntu boxes, using autossh to log in to my server so I have an ssh tunnel into the system I maintain. They all use variations on this command;

autossh -R 2060:localhost:22 [email]user@my.server.com[/email]

Now, this all worked perfectly, except for a brand new 14.x ubuntu box I just built. Clean system with only XBMC on there. Now for some reason, autossh keeps starting new sessions without the old ones terminating. Meaning, that after a few hours I have a whole list of ssh sessions from the user chris on the new box to my server, but since they all try to take the same port back out, none of them work. I have to kill all the sessions by hand, then wait for autossh to connect again, to be able to work.

On the server box the output of ps faux | grep chris looks like this;

```
ps faux | grep chris
root     16751  0.0  0.0   8860   648 pts/46   S+   23:18   0:00  |                       \_ grep chris
root      8315  0.0  0.2 123904  4448 ?        Ss   21:07   0:00  \_ sshd: chris [priv]
chris     8369  0.0  0.1 123904  2148 ?        S    21:07   0:00  |   \_ sshd: chris@pts/19
chris     8375  0.0  0.0   4440   652 pts/19   Ss+  21:07   0:00  |       \_ -sh
root      9168  0.0  0.2 123904  4448 ?        Ss   21:17   0:00  \_ sshd: chris [priv]
chris     9279  0.0  0.1 123904  2152 ?        S    21:17   0:00  |   \_ sshd: chris@pts/34
chris     9280  0.0  0.0   4440   652 pts/34   Ss+  21:17   0:00  |       \_ -sh
root      9733  0.0  0.2 123904  4448 ?        Ss   21:27   0:00  \_ sshd: chris [priv]
chris     9774  0.0  0.1 123904  2156 ?        S    21:27   0:00  |   \_ sshd: chris@pts/37
chris     9783  0.0  0.0   4440   648 pts/37   Ss+  21:27   0:00  |       \_ -sh
root     10336  0.0  0.2 123904  4456 ?        Ss   21:37   0:00  \_ sshd: chris [priv]
chris    10475  0.0  0.1 123904  2164 ?        S    21:38   0:00  |   \_ sshd: chris@pts/38
chris    10484  0.0  0.0   4440   652 pts/38   Ss+  21:38   0:00  |       \_ -sh
root     10971  0.0  0.2 123904  4460 ?        Ss   21:48   0:00  \_ sshd: chris [priv]
chris    11032  0.0  0.1 123904  2168 ?        S    21:48   0:00  |   \_ sshd: chris@pts/39
chris    11033  0.0  0.0   4440   652 pts/39   Ss+  21:48   0:00  |       \_ -sh
root     11600  0.0  0.2 123904  4460 ?        Ss   21:58   0:00  \_ sshd: chris [priv]
chris    11694  0.0  0.1 123904  2168 ?        S    21:58   0:00  |   \_ sshd: chris@pts/41
chris    11699  0.0  0.0   4440   648 pts/41   Ss+  21:58   0:00  |       \_ -sh
root     12289  0.0  0.2 123904  4460 ?        Ss   22:08   0:00  \_ sshd: chris [priv]
chris    12335  0.0  0.1 123904  2160 ?        S    22:08   0:00  |   \_ sshd: chris@pts/42
chris    12336  0.0  0.0   4440   652 pts/42   Ss+  22:08   0:00  |       \_ -sh
root     12815  0.0  0.2 123904  4460 ?        Ss   22:18   0:00  \_ sshd: chris [priv]
chris    12854  0.0  0.1 123904  2160 ?        S    22:19   0:00  |   \_ sshd: chris@pts/33
chris    12855  0.0  0.0   4440   648 pts/33   Ss+  22:19   0:00  |       \_ -sh
root     13472  0.0  0.2 123904  4456 ?        Ss   22:29   0:00  \_ sshd: chris [priv]
chris    13599  0.0  0.1 123904  2164 ?        S    22:29   0:00  |   \_ sshd: chris@pts/43
chris    13602  0.0  0.0   4440   648 pts/43   Ss+  22:29   0:00  |       \_ -sh
root     14014  0.0  0.2 123904  4456 ?        Ss   22:39   0:00  \_ sshd: chris [priv]
chris    14060  0.0  0.1 123904  2160 ?        S    22:39   0:00  |   \_ sshd: chris@pts/44
chris    14061  0.0  0.0   4440   652 pts/44   Ss+  22:39   0:00  |       \_ -sh
root     14685  0.0  0.2 123904  4460 ?        Ss   22:49   0:00  \_ sshd: chris [priv]
chris    14758  0.0  0.1 123904  2160 ?        S    22:49   0:00  |   \_ sshd: chris@pts/45
chris    14759  0.0  0.0   4440   648 pts/45   Ss+  22:49   0:00  |       \_ -sh
root     15341  0.0  0.2 123904  4456 ?        Ss   22:59   0:00  \_ sshd: chris [priv]
chris    15390  0.0  0.1 123904  2136 ?        S    23:00   0:00  |   \_ sshd: chris@pts/7
chris    15395  0.0  0.0   4440   648 pts/7    Ss+  23:00   0:00  |       \_ -sh
root     16283  0.0  0.2 123904  4460 ?        Ss   23:10   0:00  \_ sshd: chris [priv]
chris    16325  0.0  0.1 123904  2160 ?        S    23:10   0:00      \_ sshd: chris@pts/15
chris    16326  0.0  0.0   4440   648 pts/15   Ss+  23:10   0:00          \_ -sh

```

Does anyone have any idea what could be causing this? All google searches for this just lead me to instructions on how to use autossh, but nohting on troubleshooting.

---

### Post by CrimsonRider on 2014-06-02
Noone? This is starting to be a quite serious problem and I can't figure what is wrong.

---

### Post by matt_symes on 2014-06-02
Hi

I've never come accross autossh so don't expect the world of help from me :)

Just installed it though as it looks like it may be useful for me so thanks.

Anyway, after reading through the man page, have you set the env var AUTOSSH_DEBUG ?

This should log debugging information to syslog.

There is also AUTOSSH_LOGLEVEL and AUTOSSH_LOGFILE if you don't want to pollute syslog.

You can post that back here.

Kind regards

---

