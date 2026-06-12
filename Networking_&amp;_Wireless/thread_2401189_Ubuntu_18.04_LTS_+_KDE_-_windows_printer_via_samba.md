---
title: "Ubuntu 18.04 LTS + KDE - windows printer via samba button &quot;Browse&quot;"
date: 2018-09-14
forum: Networking &amp; Wireless
---

### Post by mishgenn on 2018-09-14
I installed ubuntu 18.04 LTS, then installed the KDE. 
Samba is installed, the working group is listed.
I try to connect the windows printer via samba, but button "Browse" inactive.
How fix?

---

### Post by SeijiSensei on 2018-09-14
Go to [http://localhost:631](http://localhost:631) on the Ubuntu machine.  Choose Adding Printers and Classes, then Add Printer.  Enter your username and password in the dialog box.  Do you see your printer now?

---

### Post by mishgenn on 2018-09-17
No.
If I prescribe manually:smb //WORKGROUP/HP2035 I can connect to the printer. I would like the connection to be convenient for the user - through the browse button.

---

### Post by SeijiSensei on 2018-09-17
Why would you make users browse for a printer unless you have multiple devices on your network?  If you only have one printer, it should just be the default so that users can hit the Print button and not worry about anything else.

---

### Post by mishgenn on 2018-09-17
I have several printers on the network. Sometimes there is a need to change the list of printers on the computer. I know that in Ubuntu 14.04 or 16.04 there was such a problem. but it was solved.

[ATTACH=CONFIG]281113[/ATTACH]

---

### Post by Morbius1 on 2018-09-18
I'm telling you up front that I have little experience troubleshooting printer issues these days since all of my printers are automatically discovered through cups-browsed. 

So I ran Kubuntu 18.04 in a live session and yes the "Browse" button is disabled.

I got all this to work but you are not going to like it:

[1] Install the missing package:
```
sudo apt install python3-smbc
```
[2] Run this command to invoke the Ubuntu printers utility - not the KDE one:
```
system-config-printer
```
The "Browse" button is now not disabled but when you select it you will get a [COLOR=#0000cd]**No Print Shares**[/COLOR] error message.

You are getting that because Ubuntu 18.04 can't browse for any samba assets be they hosts with shares or printers unless they are mDNS enabled. As long as you don't have any Win10 machines in your network you can fix that by:

[3] Install the samba client:
```
sudo apt install smbclient
```
[4] Then edit **/etc/samba/smb.conf** and right under the workgroup = WORKGROUP line add this one:
```
client max protocol = NT1
```

Even after all that the KDE version of this will still have the Browse button disabled. You will have to use system-config-printer directly.

*[COLOR=#0000cd]**EDIT: This might make it a bit more acceptable:**[/COLOR]*

After you do all the above edit **/usr/share/applications/system-config-printer.desktop**

Find this line:
> NotShownIn=KDE;GNOME;
And remove the KDE part:
> NotShownIn=GNOME;

Now the Ubuntu Printers launcher will show up in the KDE menu under Menu > System > Printers

---

### Post by mishgenn on 2018-09-19
Will continue...

1.
> **Morbius1 said:**
> 
After you do all the above edit **/usr/share/applications/system-config-printer.desktop**

Find this line:[INDENT]NotShownIn=KDE;GNOME;
[/INDENT]
 And remove the KDE part:[INDENT]NotShownIn=GNOME;
[/INDENT]


If do it, a critical error occurs when viewing the network environment in, for example, Dollphin (In Dolphin go to the Network, but we don't saw PC's, then Ctrl-L and enter smb://workgroup. after them we can see network PC's. But if NotShownIn=GNOME; we have critical error).

2.
I have already installed python3-smbc, samba as clietn and samba as server.
When i start system-config-printer and try add windows printer via samba, press "Browse" i have message "No Print Shares. make sure that the samba service is marked as trusted in the firewall settings"...
But in Dolphin I can see my network PC's (In network I have PC's with Windows XP, Windows 7, windows server 2003 and Windows 10(if SMB 1.0 activated in Windows 10))

3. 
> **Morbius1 said:**
> 
[4] Then edit **/etc/samba/smb.conf** and right under the workgroup = WORKGROUP line add this one:
```
client max protocol = NT1
```


In this case No Print Share there is no error **(****SOMETIMES!**). Sometimes, as before - No Print Share. 
But when there is no error, I see only the Windows 2003 server, my PC with Ubuntu and no more any PC's (In Dolphin and in system-config-printer)...

In log:
> [2018/09/19 14:27:14.209186,  0] ../source3/smbd/trans2.c:3451(smbd_do_qfsinfo)
  smbd_do_qfsinfo: not an allowed info level (0x201) on IPC$.
[2018/09/19 14:27:14.231820,  0] ../source3/smbd/trans2.c:3451(smbd_do_qfsinfo)
  smbd_do_qfsinfo: not an allowed info level (0x105) on IPC$.

Can something with access rights?

my samba config:
> [global]
    name resolve order = bcast host
    dns proxy = no
    netbios name = srvr1
    os level = 20
    security = user
    wins support = yes
    workgroup = WARKGROUP
        client max protocol = NT1
    map to guest = bad user
    server string = Firma-MGV-lnx
        log file = /var/log/samba/log.%m

---

### Post by Morbius1 on 2018-09-19
Looks like I can't help you.

Compared to Nautilus or Thunar, dolphins relative inability to "discover" samba/smb assets and it's complete inability to "discover" those registered or published by avahi/mDNS/zeroconf should have nothing to do with any changes to [B]system-config-printer.desktop.

[/B]That leads me to wonder about your setup. You say it is** "**ubuntu 18.04 LTS, then installed the KDE". Does that mean you can open Nautilus? Does it have the same problem?

---

### Post by mishgenn on 2018-09-19
> **Morbius1 said:**
> Looks like I can't help you.

  You say it is** "**ubuntu 18.04 LTS, then installed the KDE". Does that mean you can open Nautilus? Does it have the same problem?

Yes. I have the same problem. So I returned the KDE parameter and now a critical error does not arise.

this parameters in samba config
> wins support = yes
    workgroup = WARKGROUP
        client max protocol = NT1
allow you to see the network environment in Dolphin, but button "Browse" in system-config-printer don't work stable...
Surprisingly. Probably have to deal with this situation ...

---

