---
title: "MPD from repositories"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Harry789 on 2009-11-25
Hi 

Has anyone got an updated guide for installing MPD on Ubuntu (preferably 9.10) where install is from repos ?

I have such a headache building the database

[email]lau@laan97ac-laptop:~/.mpd[/email]$ mpd --create-db
listen: Failed to listen on *:6600: Address already in use
Aborted
[email]lau@laan97ac-laptop:~/.mpd[/email]$ stop mpd
stop: Unknown job: mpd
[email]lau@laan97ac-laptop:~/.mpd[/email]$ mpd
listen: Failed to listen on *:6600: Address already in use
Aborted
[email]lau@laan97ac-laptop:~/.mpd[/email]$ sudo mpd --create-db
[sudo] password for lau: 
listen: Failed to listen on *:6600: Address already in use
Aborted
[email]lau@laan97ac-laptop:~/.mpd[/email]$

---

### Post by cariboo on 2009-12-03
Do you already have an instance of mpd running? Or is there something else listening on port 6600.

You can check using nmap in a terinal or System-->Administration-->Network Tools-->Port Scan.

To stop mpd if it is running open a terminal and type:

```
ps ax | grep mpd
```

note the pid and then kill it.

```
sudo kill <pid>
```

---

