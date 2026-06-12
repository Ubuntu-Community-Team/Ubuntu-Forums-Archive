---
title: "Print from wireless connection (Laptop running WinXP Pro)"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by donniemack1 on 2009-05-11
I am running Ubuntu 9.04 home edition on my home PC.  I have a laptop that connects to the internet via a wireless router attached to my cable modem and is working fine.  I have a hpdeskjet 960c printer that is local to my Ubuntu pc.  The laptop no longer sees the printer since I installed Ubuntu.  The printer is working fine and is printing from the pc.  
 
I'm very much a newbie.  Can someone step me through what I need to do to get the laptop to see the printer through the wireless coneection?  I know I've not set something up right.  I do have the printer shared on the Ubuntu machine.  Please help.

thanks in advance,
donniemack1

---

### Post by mprince on 2009-05-11
This link should help you:

[http://www.petersblog.org/node/726](http://www.petersblog.org/node/726)

---

### Post by mprince on 2009-05-11
To edit your smb.conf file type this into a terminal:

```
sudo gedit /etc/samba/smb.conf
```

Make sure you remove any semicolons in the [printers] section of that file.

---

### Post by donniemack1 on 2009-05-12
> **mprince said:**
> To edit your smb.conf file type this into a terminal:

```
sudo gedit /etc/samba/smb.conf
```Make sure you remove any semicolons in the [printers] section of that file.  

Thanks for the information.  I'm very much a newbie so I need to know a little more info.  Assume I can open the terminal, but, that's about it.  I typed in "sudo gedit /etc/cups/cupsd.conf and following is what I got.  I edited the Listen directive as you suggested.  Where do I type the restart command???  I typed it in the terminal window and nothing happened.  Please give me some step by step detail.  

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

Thanks very much,
[email]donniemack1@gmail.com[/email]

---

### Post by mprince on 2009-05-12
That link was to edit the samba config file (smb.conf). Did you try that? 

You must have read somewhere else about the 'Listen' command.

--

Just out of curiosity, do you have a check in the box that says [I]'Share published printers connected to this system'
[/I]
It should be in the top menu under *System>Administration>Printing*

---

### Post by donniemack1 on 2009-05-12
> **mprince said:**
> That link was to edit the samba config file (smb.conf). Did you try that? 

You must have read somewhere else about the 'Listen' command.

--

Just out of curiosity, do you have a check in the box that says [I]'Share published printers connected to this system'
[/I]
It should be in the top menu under *System>Administration>Printing*
Yes, sharing is checked.  I really appreciate your comments, however, when typing the cmds you suggested, another window opens and I'm sure that's where the changes are to be added.  You said to add statements to the GENERAL section.  I can't identify the "general" section, also, where in that section do you add the cmds?  Also, where in the PRINTERS section do you add the info suggested, then how to you save and get out of terminal.  I'm sorry, but, I just don't know how to do this yet and I'm doing a ton of reading.  

In the previous post I show what was contained in /etc/samba/smb.conf.  If you could give me an idea where to make these changes and exactly what to do to save it.  I assume all commands are typed into the terminal window, not the file window that is open.  Does this at all make sense??  

thanks again,
donniemack1

---

### Post by donniemack1 on 2009-05-12
The following is what i get when I type:  sudo /etc/init.d/samba restart

[COLOR=Blue][B] sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found[/B][/COLOR]

---

