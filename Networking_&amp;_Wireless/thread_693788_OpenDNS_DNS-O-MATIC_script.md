---
title: "OpenDNS DNS-O-MATIC script"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by &amp;)ky#)^ on 2008-02-11
Here's a comprehensive shell script I wrote for a friend that updates your IP address at DNS-O-MATIC, the service for OpenDNS and other DDNS clients.  I figure just sticking this script in the appropriate cron directory is easier than setting up a ddns client.

Feel free to play with this script.  Be sure to update the username and password variables at the top.  Enjoy! :)

---

### Post by Edk on 2008-05-17
Hello there!

I know this post is a weee bit old (!) but I have a query or two.

1.  Could I put this in my /etc/rc.local so it would run automatically when I logged in?

2.  Where does it print its messages - success or otherwise?

Thank you for your help

---

### Post by &amp;)ky#)^ on 2008-05-26
No worries about PMing me.  I wouldn't have known about your questions otherwise.

I see no reason why you couldn't copy the script's contents to rc.local.  It should work just fine.  Or you could just add a line to rc.local that reads like /location/to/opendns.sh and it should execute it.  I think that'd probably be a cleaner solution than copying the contents.

As for the messages, they should show up in /var/log/syslog and /var/log/messages.  If you have any other questions, just let me know.

---

### Post by luca.00 on 2008-05-30
in my pc this script don't work, so I've made some little changes

---

### Post by &amp;)ky#)^ on 2008-05-31
Besides not using logger anymore in favor of just echoing the status, the only changes I can see are the removal of quotation marks in the wget command.  Can anyone see why that should make a difference?

I'm using the latest updated minimally customized version of Ubuntu and my version of the script works just fine.

---

### Post by Edk on 2008-06-11
bluej774 - 
I am REALLY sorry that I did not thank you.  Somehow your reply never got to me!  Anyway, thanks a lot.

I chose to add the script to rc.local, and all is well.  I am happy.

However, some of my (very) geeky friends (!!) feel that the script is too lax and insecure!  (Please I am not criticising you at all! I could not have written the script to save my life!) 

If you are interested, their comments are:

[INDENT]1)  use of plain text a "no-no".  Does dnsomatic.com has a method whereby you don't need to send the plain text password over the internet?

2)  A fixed file name for temporary file, so any user can create /tmp/tmp.ddns as a link to an arbitrary file such as /boot/vmlinuz then next time your script runs it overwrites your kernel with its output.  Should be using mktemp(1) or similar.

3)  They also suggest not running it as root (in rc.local) but creating a user specifically for this script.  perhaps there is another way?
[/INDENT]
Anyway, I am happy, but i woudl personally be interested in your observations!

All the best to you

---

### Post by &amp;)ky#)^ on 2008-06-11
You're absolutely right about the plaintext problem.  It is certainly a HUGE security flaw.  As far as I know, there's no way to get around that.  However, I noticed an update to the [dns-o-matic api page]("http://www.dnsomatic.com/wiki/api") that shows you can now update using https on port 443.  That's a bit more secure.

I didn't know about mktemp.  I'm clearly no professional script writer. ;)

I'll look into it and post an updated script with mktemp and the https address.

---

### Post by &amp;)ky#)^ on 2008-06-11
Okay, give this update a try.  It now uses https, so no simple ol' network sniffer attacks can get your username or password.  It also uses mktemp, so no more vulnerability from that rather unlikely whilst single-user scenario you described with the linking and what-not. ;)

As for the whole thing with not letting root run the thing, I've got nothing for that one.  Let me know how it goes.

---

### Post by Edk on 2008-06-11
Brilliant!  Thanks tons.  And thanks for such a rapid reply.

I cannot try it at the moment, but will have a go tomorrow if I can and let you know.  

All the best


Ed

---

### Post by &amp;)ky#)^ on 2008-06-12
Actually, use this copy instead.  I removed the "--no-check-certificate" from the wget command.  If I left it in there, it would be a little faster, but it would apparently open some security vulnerabilities.

---

### Post by Edk on 2008-06-12
You are a star!  I am very grateful for your willingness to help!  I only wish I had something to contribute!  Perhaps I will in time

---

### Post by &amp;)ky#)^ on 2008-06-13
Oh, no problem at all.  I'm glad you brought these issues up to me.  Enjoy the script.

---

### Post by ameir on 2008-06-20
> **bluej774 said:**
> Actually, use this copy instead.  I removed the "--no-check-certificate" from the wget command.  If I left it in there, it would be a little faster, but it would apparently open some security vulnerabilities.

I unfortunately couldn't get it to work without '--no-check-certificate'.  When I ran the wget portion manually without any arguments, it said:

> ERROR: Certificate verification error for updates.dnsomatic.com: unable to get local issuer certificate
To connect to updates.dnsomatic.com insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.

After this change, all was good.  Thanks!

---

