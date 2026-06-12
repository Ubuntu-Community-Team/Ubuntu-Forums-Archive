---
title: "Running Nagios"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Raynman37 on 2009-04-09
Hey everyone, I followed the instructions [here]("http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html") to install Nagios on my system.  When I ran the test near the end, I got this:

> Nagios 3.0.6
Copyright (c) 1999-2008 Ethan Galstad ([http://www.nagios.org](http://www.nagios.org))
Last Modified: 12-01-2008
License: GPL

Reading configuration data...

Running pre-flight check on configuration data...

Checking services...
	Checked 8 services.
Checking hosts...
	Checked 1 hosts.
Checking host groups...
	Checked 1 host groups.
Checking service groups...
	Checked 0 service groups.
Checking contacts...
	Checked 1 contacts.
Checking contact groups...
	Checked 1 contact groups.
Checking service escalations...
	Checked 0 service escalations.
Checking service dependencies...
	Checked 0 service dependencies.
Checking host escalations...
	Checked 0 host escalations.
Checking host dependencies...
	Checked 0 host dependencies.
Checking commands...
	Checked 24 commands.
Checking time periods...
	Checked 5 time periods.
Checking for circular paths between hosts...
Checking for circular host and service dependencies...
Checking global event handlers...
Checking obsessive compulsive processor commands...
Checking misc settings...

Total Warnings: 0
Total Errors:   0

Things look okay - No serious problems were detected during the pre-flight check

It says that everything is installed properly...but after I start Nagios and try to go to [http://localhost/nagios/](http://localhost/nagios/) it comes up with an Error 404-Not Found-The requested URL /nagios/ was not found on this server.

Does anyone know what the problem is?

---

### Post by kamboj_singh on 2009-04-15
i have installed nagios and when i am running 
[http://localhost/nagios3](http://localhost/nagios3)
i the browser it generates an error saying 
**internal server error.**
the serevr encountered an internal error or misconfiguration and was unable to complete your request.

i saw the log file. it says that there is no file /etc/nagios3/htpasswd.users


will some body please tell me what the problem is??

---

### Post by spiderbatdad on 2009-04-15
Create the file with the command
```
sudo htpasswd  -c /etc/nagios3/htpasswd.users nagiosadmin
```this creates a user: nagiosadmin, and will ask you for a password. You only use the -c option the first time you run the command to "create" the file.

if you check your file system like /etc/nagios you will find an apache2.conf file. The directory section of this file needs to be added to your virtual hosts file. Nagios is best/easiest (imo) installed via synaptic package manager. Then edit your htdocs, restart apache and start nagios. Access with localhost/nagios3

You probably still need to create the appropriate users and groups as outlined in the nagios ubuntu quickstart guide:
[http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)
though you wont be using the installtion method.

To the OP. I belive your method of installation creates a file in /etc/apache2/conf.d that has directory sections designed to be added to virtual hosts. Still, though nagios appears to start, I doubt you will find a running process...I recommend install nagios 3 from synaptic package manager.

---

### Post by KevKing on 2010-02-09
I stumbled apon this thread by accident, and I would like to give spiderbatdad a big up. 
Many many thanks.  I have been trying to install Nagios for months on a Ubuntu 9.10 server, following a multitude of TUT's.  I could always install & login, but never get anything to display.

I have I beleive 2 versions of nagios installed now, and not sure how to remove the one that was installed using [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html) but that dont matter it is working at last hurrah!!

I would definately recommend installing via synaptec as per spiderbatdad. :D

---

