---
title: "X11 session manager problem"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by madu on 2009-02-08
Hello,

I dont know if this is relevant, but installing nvclock and reducing my vidoe card clocks seems to have screwed my system. Couple of days after using  nvclock, the system crashed suddenly after a reboot and went to low-graphics mode. I was able to run by de-activating the Nvidia drivers. 

Anyway I did a clean install of Ubuntu 8.10 again but seems the problems still persist. COmpiz and everything is working fine, but when I try to run CUDA programs, I get errors which I didnt get before.

I am wondering if this is a hardware error.

Part of SYSLOG:

[B]Feb  8 20:25:57 desktop acpid: client connected from 19621[0:0] 
Feb  8 20:25:58 desktop acpid: client connected from 19621[0:0] 
Feb  8 20:25:59 desktop gdmgreeter[19649]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Feb  8 20:26:01 desktop pulseaudio[19752]: ltdl-bind-now.c: Failed to find original dlopen loader.

Feb  8 20:26:01 desktop pulseaudio[19762]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

Feb  8 20:26:01 desktop pulseaudio[19762]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Feb  8 20:26:02 desktop x-session-manager[19668]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Feb  8 20:26:12 desktop x-session-manager[19668]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Feb  8 20:26:22 desktop x-session-manager[19668]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 

Feb  8 20:26:22 desktop pulseaudio[19762]: module-x11-xsmp.c: X11 session manager not running.

Feb  8 20:26:22 desktop pulseaudio[19762]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb  8 20:26:51 desktop acpid: client connected from 19025[0:0] 
Feb  8 20:26:51 desktop acpid: client connected from 19025[0:0] 
Feb  8 20:30:56 desktop dhclient: DHCPREQUEST of 192.168.0.2 on eth0 to 192.168.0.1 port 67
Feb  8 20:30:56 desktop dhclient: DHCPACK of 192.168.0.2 from 192.168.0.1
Feb  8 20:30:56 desktop dhclient: bound to 192.168.0.2 -- renewal in 1494 seconds.[/B]

something else I noticed is, when I ran a CUDA program, it showed the device as Nvidia GTX 260 correctly earlier. Now it just  shows some ascii characters in place of the device name.

Any help is really appreciated.

Cheers.

---

