---
title: "Unable to connect to Windows shared folders"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by devswatch on 2008-07-07
I'm using Hardy Heron and for some reason I'm unable to connect to Windows shared folders through Places--> Connect to Server. Strangely I was able to connect before applying some recent upgrades. The error I get while trying to connect is:

Can't display location "smb://192.168.0.26/"
No application is registered as handling this file

The samba version is 3.0.28a-1 ubuntu4.4

Any clues?

---

### Post by sea_monkey987 on 2008-07-07
> **devswatch said:**
> I'm using Hardy Heron and for some reason I'm unable to connect to Windows shared folders through Places--> Connect to Server. Strangely I was able to connect before applying some recent upgrades. The error I get while trying to connect is:

Can't display location "smb://192.168.0.26/"
No application is registered as handling this file

The samba version is 3.0.28a-1 ubuntu4.4

Any clues?

Strangely, I'm getting the same error.  However, putting something like "smb://192.168.0.26" into nautilus works. ](*,)

---

### Post by devswatch on 2008-07-08
Unfortunately even this is not working for me. When I put "smb://192.168.0.26" into nautilus I get the following error:

Can't display location "smb://smb/192.168.0.26
Failed to mount Windows share

---

### Post by robaldred on 2008-07-08
This is either a bug or a feature of gnome 2.22, not sure...

Lifted from known issues:
> 
GVFS and authenticated smb browsing

    *The GVFS filesystem layer used in GNOME 2.22 does not support password authentication when browsing the list of shares on an SMB server, which can result in empty share lists in nautilus when connecting to Windows 2003 hosts in some configurations. Workarounds for this issue include:
          -use Kerberos authentication with preconfigured Kerberos credentials (i.e., running 'kinit' in an Active Directory realm)
          -connect directly to an individual share using smb://<server>/<share> as the target location

Basically you cannot browse a servers list of shares.
You have to go directly into the share location.

Annoying and stupid so they need to fix this me thinks, worked fine in Ubuntu 7.10 & 7.04

I get the same error as you guys, I get round it by simply going direct to he share location by typing in the nautilus address bar: smb://192.168.3.10/data
Then it works.

Hope this helps.
Rob.

---

### Post by superprash2003 on 2008-07-08
> Can't display location "smb://smb/192.168.0.26
Failed to mount Windows share
did you type in smb://smb/192.168.0.26?? cause its supposed to be smb://192.168.0.26 .. ensure you are able to ping 192.168.0.26 from the terminal

---

### Post by mindfall903 on 2008-07-08
in the shell, type:

nautilus smb://<username>@<server>/<share>

where:
-username is the user allowed to connect to the share
-server is the fqdn of the server or the ip address of the server
-share is the correct share name of the share (including $ for hidden shares)

and hit ENTER, a window should pop up, asking for the password. For some reasons, this does not within GNOME, using Places -> Connect to server...
(produces an error message)

if the share is on a windows (as opposed to a samba share), try mapping it from the originating windows workstation first using the "net use" command on the command line first.
also make sure that the firewall allows connections to the share (turn the firewall off if possible for testing)

---

### Post by devswatch on 2008-07-09
Yes..nautilus smb://<username>@<server>/<share> works!!

---

### Post by alones on 2008-07-30
had same issue.
nautilus was giving an error but command line smbclient was complaining tree connect failed: NT_STATUS_INSUFF_SERVER_RESOURCES

Applied following fix on windows machine, it starts to work.

created a new key IRPStackSize (REG_DWORD) = 0x11 (if key exists people advises to increase size by 3) at  
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters

and restart "Server" service at Services Manager

---

### Post by blastoqueen on 2008-08-23
I took alones advice but skipped straight to restarting the Server service on the Windows machine, i.e. I didn't edit the registry at all - and that's what did it for me. It all works perfectly now.

---

