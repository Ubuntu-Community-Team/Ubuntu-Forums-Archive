---
title: "Is 'active (exited) Since &lt;date&gt; 2 minutes ago' a correct status for SAMBA?"
date: 2019-09-30
forum: Networking &amp; Wireless
---

### Post by steve19652 on 2019-09-30
[COLOR=#242729][FONT=Arial][FONT=inherit]Hey, I am new to Linux/Ubuntu, and I am not sure if this is a correct place to ask but I will try.
I just set up a **openmediavault **distro.
It's a distro with FTP server, web server, SAMBA server....
[FONT=inherit]It's in my old PC, I can ping it from windows PC, I can ping windows PC from that.
[/FONT][FONT=inherit]I can access it trough HTTP (port 80), the web panel.
[/FONT][FONT=inherit]I can also connect to it by SFTP, upload and download files.
[/FONT][FONT=inherit]I have created a Share folder, enabled SMB.
[/FONT][FONT=inherit]But.... I can't connect to network drive from Windows (Windows 10) directly, I can't map it, it is not visible in Network at all...
[/FONT][FONT=inherit]Workgroup is the same in settings.
[/FONT][FONT=inherit]I can't even access it by typing IP/share name directly in Windows explorer.
[/FONT][FONT=inherit]I started suspecting that it might be a Samba issue, because Windows 10 firewall is off.
[/FONT][FONT=inherit]I typed [/FONT]***systemctl status smbd***[FONT=inherit] to check the samba status and got that:[/FONT][/FONT]
```
smbd.service - LSB: start SMB/CIFS deamon (smbd)
Loaded: loaded (/etc/init.d/smbd)
Active: active (exited) since Sun 2019-09-29 11:43:21 EDT: 2min 48s ag
o Process: 80B ExecStart=/etc/init.d/smbd start (code=exited,status=0/SUCCESS)
```
[FONT=inherit]So, is this a correct status for Samba?[/FONT]
[FONT=inherit]Is something wrong with my Samba? Or why can't I connect to it?[/FONT]

[/FONT][/COLOR]

---

### Post by Morbius1 on 2019-09-30
From what I can tell openmediavault is Debian based so I would suggest asking your question in the openmediavault forum.

You would think samba is samba but it's not. Default settings in Debian would make a samba server inoperable to the average Ubuntu user.

---

