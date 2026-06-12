---
title: "xsane network issue"
date: 2020-10-04
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2020-10-04
Folks,

Running 18:04 LTS

I have an old Epsom Perfection scanner attached to a Raspberry Pi computer.

Appreciate this is really an issue with my Raspberry Pi but as I am an Ubuntu user and commands are all virtually the same I am hoping someone may be able to throw some light on this.

Had this working some time back when Raspberry Pi used Jessie but now Xsane on my Ubuntu Desktop says **no devices found**.

Saned is installed on the Pi, the saned.conf on the Pi allows my local network and on my Ubuntu machine I have the Pi address set in /etc/saned/net.conf
If from my Ubuntu machine I nmap the Pi it shows [B]6566/tcp open  sane-port

[/B]Now I seem to be having problems with the service, various commands issued below shows the service as masked and attempts to unmask seem unsuccessful though no error shown..

```
pi@Pi-Server:/etc/sane.d $ sudo service saned start
Failed to start saned.service: Unit saned.service is masked.
pi@Pi-Server:/etc/sane.d $ sudo systemctl unmask saned.service
pi@Pi-Server:/etc/sane.d $ sudo service saned start
Failed to start saned.service: Unit saned.service is masked.
pi@Pi-Server:/etc/sane.d $ sudo systemctl enable saned.service
Synchronizing state of saned.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable saned
Failed to enable unit: Unit file /lib/systemd/system/saned.service is masked.
pi@Pi-Server:/etc/sane.d $ sudo systemctl start saned.service
Failed to start saned.service: Unit saned.service is masked.
```

Appreciate if anyone can throw some light on this.

Geoff

---

