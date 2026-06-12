---
title: "I can create a samba share, but I can't access to it"
date: 2021-10-18
forum: Networking &amp; Wireless
---

### Post by jfca283 on 2021-10-18
Hello, 
I'm using Ubuntu 20.04.
I installed samba, and I add my user to the samba group.
Then, using Nautilus, I share a folder.
But when I try to access to it, using my cellphone or android-tv(KODI app) connected to the net, I just can't see it.
What am I doing wrong?
```
juan@juan-OptiPlex-7010:~$ sudo systemctl status smbd
&#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2021-10-18 13:21:41 -03; 17min ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 47871 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 47875 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 6 (limit: 19088)
     Memory: 8.7M
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;47875 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;47877 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;47878 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;47879 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;48153 /usr/sbin/smbd --foreground --no-process-group
             &#9492;&#9472;48197 /usr/sbin/smbd --foreground --no-process-group

oct 18 13:21:41 juan-OptiPlex-7010 systemd[1]: Starting Samba SMB Daemon...
oct 18 13:21:41 juan-OptiPlex-7010 systemd[1]: Started Samba SMB Daemon.
oct 18 13:37:31 juan-OptiPlex-7010 smbd[48178]: pam_unix(samba:session): session closed for user nobody
oct 18 13:37:42 juan-OptiPlex-7010 smbd[48197]: pam_unix(samba:session): session opened for user juan by (uid=0)
juan@juan-OptiPlex-7010:~$ hostname
juan-OptiPlex-7010

```
Some years ago, this process was straightforward. Using Nautilus I was able to see any share over my network. 
Thanks for your time and interest.
Have a nice day.

---

### Post by TheFu on 2021-10-18
What does "installed samba" mean?
There are multiple packages needed on the client side, especially if a GUI is used. Sorry, I don't know the exact names and the names may have changed depending on the release used.
I've never had luck getting samba shares working using a GUI.
In early 2020, the defaults for Samba and for Windows changed to improve security. This means that older devices many not work with those new defaults.

When my 20.04 Ubuntu Mate desktop connects to an 18.04 samba server, I use smb://hadar/thefu/ as the URL in the address bar for Caja (caja is the file manager for Mate).  This opens a window to enter credentials.    Username, Windows Domain, password and there are 3 options for how long to remember these credentials.  Browsing the "Windows Network" doesn't work. That seems to be a 20.04 and later problem.  I have only 1 CIFS share on hadar, but smb://hadar/ does show it.

Caveats:
* hadar is known and advertised through my LAN DNS server. If you don't have a LAN DNS server, you can try either the mDNS or IP address instead.  
* mDNS name would use Avahi and typically be hadar.local

I have samba-common and a few packages for gvfs installed - gvfs gvfs-backends gvfs-bin, for example. No samba-client and no samba and no gio* packages. I think the gvfs packages are necessary for Gnome GUI programs.

And on the other samba clients, you'll need to look up the highest version of the CIFS/Samba protocol supported.  Lots of free Android clients only support the 20 yr old NT1 version, which is terrible for security. On those clients, I just use sftp instead. 1,000,000x more secure to use sftp.

---

