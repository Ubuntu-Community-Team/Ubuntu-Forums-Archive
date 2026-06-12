---
title: "smtpd: subprocess post-installation script returned error exit status 1"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by kalinic on 2009-02-13
I've installed Sendmail as my MTA (Mail Transfer Agent) on my web server, and from what I understood, I needed to install smtpd to enable php mail function to send emails.
**What I got was:**

user@intr:~$ sudo apt-get install smtpd
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smtpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up smtpd (2.0-8.1) ...
 * Stopping Mail Transport Agent (MTA) sendmail                          [ OK ] 
/bin/cp: cannot create regular file `/var/spool/smtpd/etc/resolv.conf': No such file or directory
/bin/cp: cannot create regular file `/var/spool/smtpd/etc/localtime': No such file or directory
/bin/cp: cannot create regular file `/var/spool/smtpd/lib': No such file or directory
/bin/cp: cannot create regular file `/var/spool/smtpd/lib': No such file or directory
/bin/cp: cannot create regular file `/var/spool/smtpd/lib': No such file or directory
/bin/cp: cannot create regular file `/var/spool/smtpd/lib': No such file or directory
chown: cannot access `/var/spool/smtpd': No such file or directory
chown: cannot access `/var/spool/smtpd/altspool': No such file or directory
dpkg: error processing smtpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 smtpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@intr:~$ 

Any idea what might be causing this error? I did the installation trough the Synaptic Package Manager.

By the way, I only choose sendmail and smtpd, as I installed postfix and exim before, and for some reason it wasn't working.
This is the script that is suppose to be sending the email:

$from_header = "From: [COLOR="Red"]<senders email>[/COLOR]";
$to = "[COLOR="Red"]<recipients email>[/COLOR]";
$subject = "Test Email";
$msg = "Test message from the Intranet";
if (mail($to, $subject, $msg, $from_header)) {
	$to = "[COLOR="Red"]<second recipients email>[/COLOR]";
	mail($to, $subject, $msg, $from_header);
	echo("<p>Message successfully sent!</p>");
} else {
	echo("<p>Message delivery failed...</p>");
}

Thanks for any help!!

---

