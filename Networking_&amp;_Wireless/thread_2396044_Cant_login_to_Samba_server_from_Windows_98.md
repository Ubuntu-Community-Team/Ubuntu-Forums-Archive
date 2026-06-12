---
title: "Cant login to Samba server from Windows 98"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by Niklas_Andersson on 2018-07-10
Hi!

I have installed an openmediavault server on a old HP Probook 4510s from 2007 with a Celeron 1.66 Ghz CPU and 2 GB of ram with 320 GB WD Black harddrive. So openmediavault offers a whole bunch of p2p communication protocols. And my problem is that i cant use my login credenticals when trying to connect to the Samba Workgroup Client. Instead it prints out ```
\\192.168.1.x\IPC$
``` if i try to connect manually in explorer.

Or if i try to connect through Network Neighborhood it just gives me a message saying that access is denied. 

[IMG]https://i.imgur.com/zDs5pZP.png[/IMG]

[IMG]https://i.imgur.com/1eok8Xm.png[/IMG]

My smb.conf file looks like this:
```
[global]
workgroup = WORKGROUP
server string = %h server
dns proxy = no
log level = 0
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
syslog only = yes
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = no
unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
socket options = TCP_NODELAY IPTOS_LOWDELAY
guest account = nobody
load printers = no
disable spoolss = yes
printing = bsd
printcap name = /dev/null
unix extensions = yes
wide links = no
create mask = 0777
directory mask = 0777
use sendfile = yes
aio read size = 16384
aio write size = 16384
local master = yes
time server = no
wins support = no
lanman auth = Yes
ntlm auth = Yes
client lanman auth = Yes
client plaintext auth = Yes
client ntlmv2 auth = yes
#======================= Share Definitions =======================
[RetroStuff]
path = /srv/dev-disk-by-label-file
guest ok = no
read only = no
browseable = yes
```

Have reading some tutorials on the web and yesterday when i was trying to do this but on my Windows 2000 machine it works when i added this lines:
```
lanman auth = Yesntlm auth = Yes
client lanman auth = Yes
client plaintext auth = Yes
client ntlmv2 auth = yes
```

According to the tutorial ([http://www.troubleshooters.com/linux/win9x_samba.htm](http://www.troubleshooters.com/linux/win9x_samba.htm)) this was going to work on 9x too. But it didn't. 


So now iam asking here. How can i solve this ? Have i missed a line that i need to add ?

Regards

---

