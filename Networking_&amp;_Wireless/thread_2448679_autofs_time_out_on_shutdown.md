---
title: "autofs time out on shutdown"
date: 2020-08-11
forum: Networking &amp; Wireless
---

### Post by raxker on 2020-08-11
[COLOR=#2E3436][FONT=&quot]I just want to share this solution so hopefully someone else benefits from it.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&quot]I am using autofs to mount Samba shares (this is much fasters than using smb:// in dolphin.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&quot]On Shutdown the "Remote Network" sits there for ages waiting for a timeout and delays the reboot/shutdown.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&quot]Even after a manual shutdown of autofs, df -h still shows the samba shares. During shutdown the network get disconnected first because its mounted by Network Manager in KDE Plasma by the user and disconnect as soon as plasma logs you out and before the shutdown.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&quot]On shutdown the samba mounts can not be cleanly unmounted (because of no more network) and have to wait for the timeout. annoying.[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&quot]I found a simple solution: I added [/FONT][/COLOR][COLOR=#2E3436][FONT=&quot]**ExecStop=umount -t cifs -af **[/FONT][/COLOR][COLOR=#2E3436][FONT=&quot]to [/FONT][/COLOR][COLOR=#2E3436][FONT=&quot][B]/lib/systemd/system/autofs.service


[/B][/FONT][/COLOR]   [COLOR=#2E3436][FONT=&quot][B]
[/B][/FONT][/COLOR][COLOR=#636363][FONT=Menlo][Unit][/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Description=Automounts filesystems on demand[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]After=network.target ypbind.service sssd.service network-online.target remote-fs.target[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Wants=network-online.target nfs-client.target[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Documentation=man:autofs(8)[/FONT][/COLOR]

[COLOR=#636363][FONT=Menlo][Service][/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Type=forking[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]PIDFile=/run/autofs.pid[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]EnvironmentFile=-/etc/default/autofs[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]ExecStart=/usr/sbin/automount $OPTIONS --pid-file /var/run/autofs.pid[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]ExecReload=/bin/kill -HUP $MAINPID[/FONT][/COLOR]
_**[COLOR=#636363][FONT=Menlo]ExecStop=umount -t cifs -af[/FONT][/COLOR]**_
[COLOR=#636363][FONT=Menlo]TimeoutSec=1[/FONT][/COLOR]

[COLOR=#636363][FONT=Menlo][Install][/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]WantedBy=multi-user.target


[/FONT][/COLOR]

---

