---
title: "Netstat"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by themanfromdelmonte on 2011-04-07
I did a "sudo netstat -p -l -N -e" and found a couple of services running that I dont know. I am the only user paul/IDC. Im using 11.04 B3.  Here are the lines that I need help understanding. The complete list is attached.

 LISTENING     13447    1617/ssh-agent      /tmp/ssh-VzxYSlSV1578/agent.1578  
LISTENING     13401    1559/gnome-keyring- /tmp/keyring-vDQMCi/control 
LISTENING     13664    1559/gnome-keyring- /tmp/keyring-vDQMCi/pkcs11  
LISTENING     10727    1621/dbus-daemon    @/tmp/dbus-TOugtBaMcF  
LISTENING     10038    1038/gdm-simple-sla @/tmp/gdm-session-WvKGtPmY  
LISTENING     9446     1074/X              @/tmp/.X11-unix/X0  
LISTENING     8966     1038/gdm-simple-sla @/tmp/gdm-greeter-wSqZEfKd

---

### Post by searchfgold6789 on 2011-04-07
> **themanfromdelmonte said:**
> I did a "sudo netstat -p -l -N -e" and found a couple of services running that I dont know. I am the only user paul/IDC. Im using 11.04 B3.  Here are the lines that I need help understanding. The complete list is attached.

 LISTENING     13447    1617/ssh-agent      /tmp/ssh-VzxYSlSV1578/agent.1578  
LISTENING     13401    1559/gnome-keyring- /tmp/keyring-vDQMCi/control 
LISTENING     13664    1559/gnome-keyring- /tmp/keyring-vDQMCi/pkcs11  
LISTENING     10727    1621/dbus-daemon    @/tmp/dbus-TOugtBaMcF  
LISTENING     10038    1038/gdm-simple-sla @/tmp/gdm-session-WvKGtPmY  
LISTENING     9446     1074/X              @/tmp/.X11-unix/X0  
LISTENING     8966     1038/gdm-simple-sla @/tmp/gdm-greeter-wSqZEfKd

I don't know what the rest of the code means, but I can help you understand them a bit better.

[LIST=1]
[*]The first one is a command executor. (SSH)
[*]The second one and third one deal with some user permissions, etc. (Gnome Keyring)
[*]The third one I am not really sure about but I have it running on my system and have heard about it on many other systems; it is definitely a system process and is important. I think it has to do with the HAL. (DBUS)
[*]The fifth one branches off from GDM, or Gnome Display Manager. It is basically the thing that helps monitors work.
[*]The sixth one is the X server, which is like GDM only a step deeper. (xserver-xorg)
[*]The seventh one also is GDM.
[/LIST]
I'm sorry I couldn't help you more but this is what I know!
  - search

---

