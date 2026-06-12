---
title: "Bluemon with k800i"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by blackcougar on 2007-02-16
Hi,

I've got my SE K800i working fine with multisync and even as a bluetooth remote control following the posts on this forum:
[http://ubuntuforums.org/showthread.php?t=298957](http://ubuntuforums.org/showthread.php?t=298957)
[http://www.ubuntuforums.org/showthread.php?t=241500](http://www.ubuntuforums.org/showthread.php?t=241500)

However I want to get bluemon to run 
```
gnome-screensaver-command -l
```
whenever I walkaway with the phone

I have connected to the phone with:
```
> sudo hcitool cc 00:19:63:07:69:EF
```
... started bluemon with
```
> sudo bluemon -t 70 -a -v -s -b 00:19:63:07:69:EF
Bluetooth monitoring system startup, version 1.3

```
but when i run
```
> sudo bluemon-query 
nothing connected

```
Now my phone says it is connected so I'm not sure what is not working

Any ideas, fixes, suggestions?

---

