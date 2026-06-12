---
title: "Logging into a windows print server on a different subnet"
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by karthik25 on 2015-05-28
Hello,

My university uses some kind of silly UserCode authentication for access to networked printers. I've tried all documented methods to get into the Ricoh/Lanier printers by setting them up as networked printers on my linux box directly - no use. The final solution that was presented to me was to set up a windows-based print server that would allow me to access the printer. I've set up the printer on windows OK and have shared it. 

In order to use the printer from linux, I set up a samba printer, pointed to the windows machine (made sure the workgroup names on the windows machine and samba were the same) and am prompted to log into the windows box. Authentication fails. I think this is because my linux box is at 10.34.xx.xx, while my windows machine is sitting at 10.35.xx.xx. I have full access to the windows and linux machines but no access to routers etc. 

How can I fix this? I am a faintly familiar with networking concepts, but not in any great detail. All help will be greatly appreciated! 


Thanks,

-K

---

### Post by SeijiSensei on 2015-05-28
I don't think it's a networking problem.  The fact that you get an authentication dialog suggests the connection was made.  Just to check, can you ping the Windows box on the 10.35/16 network from the Linux box on 10.34/16?

I'd check the configuration of the shared printer in Windows and make sure it enables public access.  

One other thing you can try is running the "smbclient" application on the Linux box.  Use "smbclient  -L //10.35.x.y".  You will be prompted to log in with your Windows password.  If that fails, run the command again and hit return at the password prompt.  You'll see the list of shares that are publicly visible.  If your Linux username differs from your Windows username, run "smbclient -U username -L //10.35.x.y" and enter your Windows password.  If that works, use an SMB URL with CUPS to point to the printer like this "smb://username@10.35.x.y".  That will force CUPS to use that username.

---

### Post by karthik25 on 2015-05-28
Thanks for that info. I am able to ping the windows machine OK. The printer sharing seems to indicate that it is shared. 

However, the smbclient -L 10.35.x.y fails with at (Error NT_STATUS_IO_TIMEOUT). I tried looking around this forum (and others) for fixes - and nothing popped out immediately. Also, there are no failed entries in the logs (/var/log/samba/*) 

Re-running smbclient -L 10.35.x.y and hitting enter still gives the same error. Any ideas on how to proceed from here?

---

### Post by SeijiSensei on 2015-05-29
Install **nmap** from the repositories and use it to scan the Windows machine for open ports:
```

sudo apt-get install nmap
nmap -sT 10.35.x.y

```
The "-sT" switch tells nmap to do a simple TCP scan without activating any of nmap's "stealth" features.  Do you see port 139 open?  445?   If not, something is in the way.

Is the Windows machine running a firewall?  Perhaps that is blocking connections to those ports.

---

### Post by karthik25 on 2015-05-29
Ok - thanks for pointing me there. It looks like the windows firewall is getting in the way... on disabling the firewall on the machine I am able to see:

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
    Users           Disk      
    VAIOKRG114      Printer   KRG114

Now to figure which rule to modify on the windows end... thanks once again for your help.

Best,

-K

---

