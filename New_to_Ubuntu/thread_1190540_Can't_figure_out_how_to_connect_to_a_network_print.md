---
title: "Can't figure out how to connect to a network printer!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by william_js on 2009-06-18
Well, I took the dive and I'm trying out linux. It's much easier than the last time I tried, about 4 years ago. The only thing is, I can't figure out how to connect to an internet printer for the life of me! I'm about to pull out my hair and throw my laptop across the room in frustration. 

I'm trying to connect to Michigan State University's netprint system. On the webpage (
[http://techbase.msu.edu/article.asp?id=3071&service=netprint#s44649](http://techbase.msu.edu/article.asp?id=3071&service=netprint#s44649)
) it says:

NetPrint is built on the Internet Printing Protocol (IPP) standard, and will work with any IPP client that is able to support authentication and SSL.  Linux, Solaris, or other UNIX systems can use CUPS as an IPP client.   
 To use NetPrint with another operating system, or to set up NetPrint manually, you will need the following information: 
Printer location: [https://netprint.msu.edu:30443/printers/netprint](https://netprint.msu.edu:30443/printers/netprint)
 Printer type: HP Laserjet 8100 Series PC
 Username: Your MSU NetID
 Password: Your MSU NetID password


So, I go into system->administration->printing and then server->new->printer. THen I select Internet printing Protocal (IPP). THen I enter netprint.msu.edu as the host and /printers/netprint as the queue. I then go ahead and set up the printer as indicated (laserjet 8100). But there is no place to put in the password, etc. Is this hopeless? Should I switch back to vista?

Thanks!

---

### Post by 123456789123456789123456 on 2009-06-18
You have to tell Ubuntu that it is IPP with SSL, as far as I can tell, there are two types, one is regular, with no username or password required, for home printing thorugh internet, which some people use, this is most common.  However if it uses, SSL you need authorization to use it.  I think you go ahead and configure it, after you have it added, go into the preferences of the printer you added, and tell it SSL, and the user name and password.  I have not added one, but I bebileve that is the quickest work around, there may be a more direct approach to it though, But I don't know what that is.

---

### Post by SirrKitt on 2009-06-18
You could try and setup CUPS from hand.
Haha; although, that seems like a bit of unnecessary work.
If it's installed, point the browser to 127.0.0.1:631 and I believe you could attempt at using that.
d:
Been a while since I've actually used CUPS like that, but I could try and help you with it if you'd really like to.

---

### Post by QIII on 2009-06-18
I went through the setup process as you probably did, until the point where I was asked if I wanted to print a test page.

Did you attempt to print one?

Maybe you get a userid/password prompt at that point.

---

### Post by william_js on 2009-06-18
In response to previous posts:

1) there is no place to enter username and password in preferences
2) I have tried to print a test page, which just sits in the "document print status" queue for ever. No prompt for username and password appears.
3)  pointing my browser to 127.0.0.1:631 doesn't help. It's just an html interface for the linux printer setup menu.

So, I think I have to configure cups manually, if someone would be kind enough to help, that would be great. I'm not sure, but I think I have to change my /etc/cups/cupsd.conf file. The contents are pasted below: (Also, can someone tell me how to get past "you do not have the permissions necessary to change this file" error? (like I said, I'm really new at this!)

Here is my /etc/cups/cupsd.conf file. I have no idea what to do with it.

LogLevel warning
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
DefaultAuthType Basic
<Location />
  # Restrict access to the server...
  Order allow,deny
</Location>
<Location /admin>
  Encryption Required
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

---

