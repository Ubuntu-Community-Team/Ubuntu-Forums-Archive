---
title: "Access Ubuntu 16.04 workstation with Nvidia 1080 from Mac (XQuartz) via SSH"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by schumusa on 2016-12-12
I am accessing a ubuntu 16.04 workstation with Nvidia graphics cards from my Mac with Sierra 10.12.1 and XQuartz 2.7.9. 

After a recent upgrade (unfortunately don't know which elements) I can still connect to the ubuntu workstation with ssh -X workstation and run commands through the command line and even start small graphics windows through commands like xclock.

However, when I try to run firefox (e.g. to launch a jupyter notebook) on the Ubuntu server with 'firefox -no-remote' I get the messages:[COLOR=#000000][FONT=arial black]
ExceptionHandler::GenerateDump cloned child 1729
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
Segmentation fault (core dumped)

[/FONT][/COLOR]
When I start nautilus with 'nautilus' I also get the message 'Segementation fault (core dumped)'. 

I checked my xterm settings in the ssh_config and sshd_config files, they all seem to be ok. I also reinstalled firefox, xauth and other programs - no change. Since the CPU on the ubuntu server does not have a built in graphics processor (6850k) my hypothesis is, that somehow there is a problem that the Nvidia graphics card is not recognised when I call on nautilus or firefox through xterm. 

Any help greatly appreciated!!!

Erik

---

