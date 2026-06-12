---
title: "&quot;TorK cannot connect to Tor!&quot;"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by auraithx on 2008-06-18
Running Ubuntu 8.04 Hardy Heron

Keep getting this error message in TorK the error message reads: 

> Nothing. TorK tried to connect to Tor and failed **Reason**: If you are trying to manage a remote or already-running instance of Tor you may not have configured the address and/or port of the Tor server correctly

These are my settings
> Address/Port of Tor instance 127.0.0.1:9051

and Tor is definitely running.
```
mark@mark-desktop:~$ tor
Jun 18 12:49:09.106 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Jun 18 12:49:09.147 [notice] Initialized libevent version 1.3e using method epoll. Good.
Jun 18 12:49:09.147 [notice] Opening Socks listener on 127.0.0.1:9050
Jun 18 12:49:09.147 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 18 12:49:09.147 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 18 12:49:09.147 [err] Reading config failed--see warnings above.
mark@mark-desktop:~$ 

```

---

### Post by auraithx on 2008-06-19
no one?

---

### Post by uthturn on 2008-06-21
my guess is that you may be trying to run a kde app in gnome. I want that program too. I tried running torpark in wine but it didn't work for me. Someone please let me know if there is a gnome alternative. I saw where u could use the tor network but it did not seem as though u could switch back and forth easily

---

### Post by khaard on 2008-11-20
Try my way in that post
[http://ubuntuforums.org/showthread.php?t=800115]("http://ubuntuforums.org/showthread.php?t=800115")

---

