---
title: "Share printer with other Linux box?"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by celem on 2007-01-15
I have a dual-boot box with XP and Dapper. I also have a laptop with Edgy Eft. From the laptop, I have no problem printing over a WiFi/SAMBA link to my shared XP printer. However, I haven't figured out how to share the same printer when booted in Dapper. Searching the forums and Wiki were no help. Can anyone enlighten me?

---

### Post by Shay Stephens on 2007-01-15
I have all ubuntu here.  And I am sharing a printer.  This is what I did to get it working:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Specifically, I had to setup the computer sharing the printer to be a cups server.  And my computer, the one that sends the jobs to that server/printer is setup as a client.

Now that I know how to do it, it only takes a few minutes to setup when I reinstall from scratch.

This is my client configuration:

```
    # /etc/cups/cupsd.conf
    # Simple CUPS configuration file for a pure client machine:
    # which has:
    # - no printers of its own, (or any local printers will not be shared?)
    # - no need for security within the machine, ie a personal workstation
    # - a network connection to a local network, where it will find CUPS-controlled printer servers
    
    # This setup also allows access to the "Administrative tasks" system at
    # http://localhost:631
    # File based on Ubuntu 5.10 (Breezy Badger) (Linux version 2.6.12-10-386)
    # Server Directives are explained in http://localhost:631/sam.html
    
    # 25/04/2006
    # DavidTangye@netscape.net
    
    ConfigFilePerm 0600
    LogLevel info
    Printcap /var/run/cups/printcap
    RunAsUser Yes
    ### Listen fails. Use Port
    #Listen 127.0.0.1:631
    #Listen 10.0.0.0/8:631
    #Listen 128.0.0.0/16:631
    #Listen 192.168.0.0/24:631
    Port 631
    
    ### Which print servers to use
    Include cupsd-browsing.conf
    BrowseOrder deny,allow
    BrowseDeny from All
    BrowseAllow from @LOCAL
    #BrowseAllow from 10.0.0.0/8
    #BrowseAllow from 172.16.0.0/12
    BrowseAllow from 192.168.0.0/16
     
    <Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    </Location>
     
    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    </Location>
     
    <Location /printers>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    </Location>
     
    <Location /admin>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    </Location>
```

---

### Post by celem on 2007-01-15
Thanks, I try it out and advise.

---

