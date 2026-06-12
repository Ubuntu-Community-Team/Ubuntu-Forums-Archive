---
title: "Ubuntu 16.04 ssh restart failing"
date: 2016-08-16
forum: Networking &amp; Wireless
---

### Post by xav-evialog on 2016-08-16
I have Ubuntu 16.04 server edition installed on a remote server.
I am using ssh to connect on it. Today after an update/upgrade, I had new openssh-server package version installed (1:7.2p2-4ubuntu2.1) but configure step failed with : [FONT=courier new]invoke-rc.d: initscript ssh, action "restart" failed.
[/FONT]
I know that restarting ssh while being connected through ssh should not be a problem.
I have rebooted my server and ssh is working fine.
When I try manually [FONT=courier new]/etc/init.d/ssh restart[/FONT] the restart is failing.
systemctl status ssh.service result is:
[FONT=courier new]... sshd[9157]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.[/FONT]
journalctl -xe result is:
[FONT=courier new]... sshd[10114]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.[/FONT]
[FONT=courier new]... sshd[10114]: error: Bind to port 22 on :: failed: Address already in use.[/FONT]
[FONT=courier new]... sshd[10114]: fatal: Cannot bind any address.[/FONT]
[FONT=courier new]... systemd[1]: ssh.service: Main process exited, code=exited, status=255/n/a[/FONT]

I did not change anything to my ssh config, I am using the default one.
Any suggestion to solve this ssh restart issue?

Today, I tried to add a cron to reconfigure ssh. The goal was to reconfigure ssh while no ssh connection was active...
The reconfigure failed with the same restart issue...

---

