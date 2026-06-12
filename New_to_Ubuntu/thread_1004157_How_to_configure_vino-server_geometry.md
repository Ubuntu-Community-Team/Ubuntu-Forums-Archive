---
title: "How to configure vino-server geometry?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by igor@polevoy.org on 2008-12-06
The vino-server comes configured with standard resolution 1024x768. This means that I cannot utilize the screen on my client machine, which has higher resolution. When I use tightvncserver instead of vino, I can provide the same resolution (geometry) as I have on the client machine desktop. The problem with this approach is that tightvncserver does not show the full desktop. Instead, it only shows one terminal window and nothing else (no desktop, no panels, icons, etc). 

I really do not care what server to use, as long I can specify geometry and can access entire desktop. Is there a way to achieve this? This seems to be simple, but I spent a couple of hours chasing this problem, to no avail.

Thanks for help in advance!
igor

---

### Post by stockandawe on 2008-12-19
I am looking to find the same information. 

I believe vino-serer is the default vnc server in 8.04. I see that the vino-server process runs with some command-line options:

```
$ ps ax | grep vino
12248 ?        S      0:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=22
```

I can kill the process, but it restart immediately. It should be service somewhere that runs the command. We need to change that command so that it adds the geometry information as a command line option.

Alternatively, if you are using vncviewer as your client, you could do:

 ```
vncviewer -geometry 800x600 <remote ubuntu server>
```

---

