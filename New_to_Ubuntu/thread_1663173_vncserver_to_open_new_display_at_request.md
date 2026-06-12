---
title: "vncserver to open new display at request"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by crazy.nattu on 2011-01-09
I am configuring vncserver for ubuntu 10.10 64 amd server edition. I found out that I can open new display
every time run vncserver ( say it starts new session phoenix :1 ) from command line and then I connect to it with vncviewer phoenix:1. Now for each new display I have run vncserver first on the phoenix and then connect to it with remote host like vncviewer phoenix:2 , 3 etc. I want that vncserver start a new display on each request automatically and connects it to the new request automatically. i.e. I should not have to create vncserver :1 , vncserver :2 before hand
is it possible ? 

To accomplish this I created an entry for xinetd.d like below
service vncserver
{
    id = vncserver
    type = UNLISTED
    disable = no
    socket_type = stream
    wait = no
    user = root
    server = vncserver
    log_type = FILE /var/log/vncserver.log
    log_on_success = PID HOST USERID EXIT DURATION TRAFFIC
    log_on_failure = HOST USERID ATTEMPT
}

but this don't start the vncserver more over the log file  /var/log/vncserver.log does not get created at all.
Also where can I get detailed explanation of ~.vnc/xstartup used by vncserver. I am not able to understand how things are working exactly from the man page of vncserver

---

