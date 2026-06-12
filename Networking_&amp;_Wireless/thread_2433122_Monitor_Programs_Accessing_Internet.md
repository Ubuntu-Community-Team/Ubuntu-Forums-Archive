---
title: "Monitor Programs Accessing Internet?"
date: 2019-12-14
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2019-12-14
I know about iftop to monitor internet connections, but is there a way to monitor which programs access the network/internet? For example, it's ok if firefox accesses the internet, but maybe not xyzmalware.

---

### Post by TheFu on 2019-12-15
I don't know of a specific answer to the question, but ... 

Unix is a multi-user OS from the ground up.  Managing network access isn't on a per-process basis, but it can be done on a per-userid basis.  Or with cgroups, you can limit which processes have access to networking at all. The normal method end-users would access cgroups is either through a sandbox tool like **firejail** or using *linux containers*.
[https://www.linuxjournal.com/content/everything-you-need-know-about-linux-containers-part-i-linux-control-groups-and-process](https://www.linuxjournal.com/content/everything-you-need-know-about-linux-containers-part-i-linux-control-groups-and-process)

These are more to constrain known processes, not to block everything, except X, Y, Z, programs.
For example, I know that a web browser and my email client are high-risk tools, so I run both inside a firejail sandbox.
```
$ /usr/bin/firejail /usr/bin/firefox
$ /usr/bin/firejail /usr/bin/thunderbird
```
Each of these programs has a profile in /etc/firejail/ which specifies what system resources they can and connect access.
Sometimes, I want to run a browser such that nothing is written/saved to disk, ever. A few aliases for that purpose:
```
alias firepchrome='firejail --private chromium-browser --js-flags=--noexpose_wasm --mute-replay-warnings '
alias firepff='firejail --private firefox '

```
--private mode prevents writes.  Every time I use *firepchrome* it thinks this is the very first time I've ever run it. Nothing is saved. No addons, no downloads, no settings.  NOTHING.  That would include malware.
You can play around with a bash shell under firejail to get a feel for what is possible.
```
firejail bash
firejail --private bash
```
Notice the differences?  Which allows sudo?

Linux containers are more of a way for daemons/services to be run under constraints. They aren't really for end-user desktop programs.

Firejail isn't the only tool for sandboxing.  In fact, snap packages use a similar idea to constrain where programs can see, write, access. Unfortunately, snap configuration isn't locally controlled, so if the span package distributor thinks you shouldn't be allowed to write into /tmp/ then you cannot and their isn't any way around it. With firejail, we have local control.  To see which programs are installed as snap packages, use **snap list**

If you want to see which programs are using networking, there are a few tools.  **lsof** is one.  Long, long, ago there was a tool called etherboy that would show a graphic of network connections between IPs based on the protocol used. They went commercial slightly less long ago.  Using netstat, you could build something similar, but it wouldn't be on a per-process level.

You could also set logging levels high in the firewall you are running, then monitor those logs.

---

### Post by rebeltaz on 2019-12-20
Interesting. I will have to look at firejail. It won't work for my current needs, but I can think of uses for it in the future. lsof might be what I'm looking for. I'll have to check it out more in depth. Thank you for taking the time to write that reply! :)

---

