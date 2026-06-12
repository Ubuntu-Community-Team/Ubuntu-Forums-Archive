---
title: "Mute flash ads?"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-10-17
Is there any way to mute those <snip> flash ads? I tried to setup pulseaudio using the guide [here]("http://ubuntuforums.org/showthread.php?t=789578&highlight=mute+flash"), but I get an error when trying to load the PulseAudio Volume Control application. ```
jason@Barnaby:~$ pulseaudio & pavucontrol 
[1] 15709
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:15710): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(pavucontrol:15710): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
jason@Barnaby:~$
```
Any ideas?

---

### Post by cariboo on 2009-10-17
Please don't swear in your posts, it is against forum policy. 

You can use the adblock and flashblock add-ons for Firefox, to block all ads. Between the two add-ons almost 100% of the ads are blocked.

---

### Post by slughappy1 on 2009-10-17
Oops, sorry. I had my fried post that for me and he has a mouth on him ;-)

But what if I use Chromium too?

---

