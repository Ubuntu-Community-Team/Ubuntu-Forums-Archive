---
title: "which is the problem - cups or samba printing problem??"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by jsast21 on 2009-08-16
I installed ubuntu 9.04 server yesterday and am accessing it remotely via ssh. My goal was to create a file server for the other computers on my home network - and it works perfectly for that.

But now I am wondering if I can plug in a usb printer to the server and print to it via samba in windows. I did some google searching and it looks like I need two things - CUPS installed and samba configured to print.

So I installed cups via:
```
sudo apt-get install cupsys
```

and then I made sure samba was set up to print by modifying the smb.conf file:
```

interfaces = lo eth0
bind interfaces only = true

Edit these lines to enable guest access in Samba:

security = share

Finally, change the [printers] share definition so that it looks like this:

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700

```

So my usb printer is plugged in and I restarted cups via:
```
 /etc/init.d/samba restart 
```

And now I have no idea what to do next. In windows, I can go to network and then to the server. There is a printers folder but it is empty. And I am not sure how to send a test page to the printer from the command line in ubuntu 9.04. 

I did read that I need the .ppd file for my printer. So I downloaded hp550nc1.ppd.gz - but I have no idea what to do with that file or where to put it.

Could someone please point me in the right direction?

Thanks very much.

Regards,

Joe.

---

### Post by Shig on 2009-08-16
Hi Joe

Check out **[this]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#id2633487")** part of the Samba manual, it has a good basic configuration for setting up samba to use cups printing. Try the example config first and see if it load your printer.

---

### Post by jsast21 on 2009-08-16
> **Shig said:**
> Hi Joe

Check out **[this]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#id2633487")** part of the Samba manual, it has a good basic configuration for setting up samba to use cups printing. Try the example config first and see if it load your printer.

Great, I will try it now and let you know. Thank you.

Joe.

---

### Post by halitech on 2009-08-16
did you add your printer to the server computer first?

---

### Post by jsast21 on 2009-08-16
The settings are the same. How can I know if it is working? Is there a way to send a test page to the printer from the command line? I am not sure what the printer name is.

Thanks 

Joe.

---

### Post by jsast21 on 2009-08-16
> **halitech said:**
> did you add your printer to the server computer first?

I am not sure how to add the printer beyond setting up the smb.conf file. Is there another step that I am missing?

Since there is no gui, I am kind of in new territory.

---

### Post by halitech on 2009-08-16
> **jsast21 said:**
> I am not sure how to add the printer beyond setting up the smb.conf file. Is there another step that I am missing?

Since there is no gui, I am kind of in new territory.

yeah, you need to tell the computer there is a printer attached. By no gui I assume you mean you installed the server version. in that case, open a web browser on another machine and go to [http://ip_address_of_server:631](http://ip_address_of_server:631) and add the printer

---

### Post by jsast21 on 2009-08-16
> **halitech said:**
> yeah, you need to tell the computer there is a printer attached. By no gui I assume you mean you installed the server version. in that case, open a web browser on another machine and go to [http://ip_address_of_server:631](http://ip_address_of_server:631) and add the printer

Yes, it is 9.04 server. Using firefox from my windows machine, I get a failed to connect error when I do that ([http://192.168.1.100](http://192.168.1.100)). But I can ssh into the box fine and I can see it and use the shared folders from Microsoft networking, so I know the server is up and running.

---

### Post by halitech on 2009-08-16
> **jsast21 said:**
> Yes, it is 9.04 server. Using firefox from my windows machine, I get a failed to connect error when I do that ([http://192.168.1.100](http://192.168.1.100)). But I can ssh into the box fine and I can see it and use the shared folders from Microsoft networking, so I know the server is up and running.

if the server ip is 192.168.1.100 then you would need to use [http://192.168.1.100:631](http://192.168.1.100:631) to connect to the CUPS server to add the printer

---

### Post by jsast21 on 2009-08-16
> **halitech said:**
> if the server ip is 192.168.1.100 then you would need to use [http://192.168.1.100:631](http://192.168.1.100:631) to connect to the CUPS server to add the printer

The [http://192/168.1.100:631](http://192/168.1.100:631) is what is giving me the failed to connect error.

---

### Post by halitech on 2009-08-16
I wonder if cups is configured to not allow remote access...

here is a copy of my cupsd.conf file
```
LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
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

```

---

### Post by jsast21 on 2009-08-16
Thanks - I modified my cupsd.conf file to match yours. I also restarted cups with /etc/init.d/cups restart. I did notice on other forums though that people are using cupsd. There is a man page on my system for cupsd, but the only cup* file I have in /etc/init.d/ is cups. Is this a problem?

---

### Post by halitech on 2009-08-16
cupsd is the daemon (I believe) but cups is what is running (at least on my system)

can you now connect using the browser?

---

### Post by jsast21 on 2009-08-16
Good news and bad news:

That worked! and I was able to connect to it using my browser. I set up the printer and it accepted it. Here is the output:

Description: HP Printer on the server
Location: Server
Printer Driver: HP OfficeJet 500 Foomatic/cdj550
Printer State: idle, accepting jobs, published.
Device URI: usb://hp/officejet%205500%20series?serial=MY48CG104X96

But then when I send a test page, nothing happens. Here is the output of the testpage:

ID  	Name  	User  	Size  	Pages  	State  	Control 
HP_Printer-1  	Test Page  	jsast21  	17k  	Unknown  	completed at Sun 16 Aug 2009 11:58:27 AM EDT 

I am googling at the same time you are helping me, and I really appreciate it. 

What do you think could be causing the problem of everything looking ok, but nothing printing?

And again, thanks very much for your time.

Joe.

---

### Post by halitech on 2009-08-16
there are a couple of drivers to us

[http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_500](http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_500)

did you install hpijs before adding the printer?

---

### Post by jsast21 on 2009-08-16
> **halitech said:**
> there are a couple of drivers to us

[url]http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_500[/url
did you install hpijs before adding the printer?


No, I did not install hpijs - I wasn't sure what that was or if I needed it.

UPDATE!! As I was typing this, the test page went across. I am now able to wirelessly print through the printer attached to the server from both windows and linux machines!!

Thanks very much for all of your time and help. wow - that was something. This whole setting up a home server and getting it to run was the coolest learning experience. I appreciate your help and patience.

---

### Post by halitech on 2009-08-16
even though it is working, you may want to install hpijs to get better speed out of your prints (unless other test prints are working fine now)

glad to hear you have things working now and yes, setting up servers in a new environment is an experience :)

---

### Post by jsast21 on 2009-08-16
> **jsast21 said:**
> 
UPDATE!! As I was typing this, the test page went across. I am now able to wirelessly print through the printer attached to the server from both windows and linux machines!!

Thanks very much for all of your time and help. wow - that was something. This whole setting up a home server and getting it to run was the coolest learning experience. I appreciate your help and patience.

How do I change the subject to [SOLVED]?

---

### Post by halitech on 2009-08-16
go back to your original post and change the subject to include [Solved]

---

### Post by HermanAB on 2009-08-16
Restart the CUPS service.

---

