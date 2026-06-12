---
title: "ssh X11 forwarding between eeepc and ubuntu"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by mendieta on 2007-12-08
[I]UPDATE: I SOLVED this problem. For some reason, I had a line in .bashrc setting the DISPLAY to 
:0". I must have had this for years in my /home ... 

Anyways, I'll leave this thread in case it helps someone set up there eeepc to work nice with sssh and (K/X/Ed)Ubuntu[/I]

Hi,

I couldn't figure this out so far (searched here, googled, etc). I am trying to do ssh from my eeepc running stock Xandros, to my Kubuntu desktop. Unfortunately, X11 Forwarding only works one way (if I login from Kubuntu into the eeepc). If I login from the eeepc into Kubuntu, I need to manually set up the DISPLAY to the eeepc_IP:0 (it gets automatically  set  to ":0"). After that, it works fine (konqueror running in Kubuntu displays in the eee). But I want X11 forwarding to work.

The annoying thing is that both ssh_config and sshd_config are setup the same way in both boxes. 

```

/home/user> grep -i x11 /etc/ssh/*config
/etc/ssh/ssh_config:ForwardX11 yes
/etc/ssh/ssh_config:ForwardX11Trusted yes
/etc/ssh/sshd_config:X11Forwarding yes
/etc/ssh/sshd_config:X11DisplayOffset 10
```

Here is what I see in a typical login (I only show the debuggin info after the login, where X gets into play, 

```

/home/user> ssh -vX lmilano@192.168.1.46
[deleted output here]
lmilano@192.168.1.46's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux grisell 2.6.22-14-rt #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat Dec  8 15:00:50 2007
debug1: client_input_channel_open: ctype x11 rchan 2 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 55386
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: channel 1: FORCE input drain
debug1: channel 1: free: x11, nchannels 2
```

Other than that, the xserver in the eee listens to tcp (and xhost is set to +)

```

/home/user>  cat /etc/X11/xinit/xserverrc
#!/bin/sh
# $Id: xserverrc 189 2005-06-11 00:04:27Z branden $
exec /usr/bin/X11/X -dpi 100 -br
#exec /usr/bin/X11/X -dpi 100 -br -nolisten tcp
```

Any ideas what could be wrong ? Thanks so much in advance!

---

