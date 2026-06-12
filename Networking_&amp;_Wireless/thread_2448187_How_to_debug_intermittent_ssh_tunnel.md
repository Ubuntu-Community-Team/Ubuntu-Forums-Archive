---
title: "How to debug intermittent ssh tunnel?"
date: 2020-08-04
forum: Networking &amp; Wireless
---

### Post by dwater on 2020-08-04
I use an ssh tunnel from my ubuntu laptop to ubuntu running on an AWS server.

I use this command: `ssh user@server -D8080 -v -N` and set the system's socks proxy to localhost:8080.

I am mainly streaming videos through chrome and/or firefox.

It works a treat, for "a while", but sooner or late it will 'hang', whereby the stream will stop, and I cannot get any web site on other tabs either. If I wait, it will eventually unblock itself for a period of time (seconds, minutes) before blocking again. If I have the debug option on sshd, I see a flurry of activity when it unblocks...

I don't know where the blockage is happening, so I'm not sure where to start.

Any idea how I can attempt to debug this?

---

### Post by TheFu on 2020-08-04
keepalive settings?
I use : 
```
ssh -f -C -D $PORT  server  -NT &
```
for the ssh-proxy to the home LAN.
Other settings, if any, are inside the ~/.ssh/config file.

Another option is to try out **sshfs**. This is usually not fast enough for hi-def video, but fine for music and DVD quality videos. Using the SOCKS proxy, plex will transcode to a lower bitrate. With sshfs, I have to do that manually with ffmpeg almost always. My upstream bandwidth isn't crazy fast.

---

