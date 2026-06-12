---
title: "Configuring CUPS on a server install"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by d1337 on 2005-06-23
Need some insight.  I have an IBM M Pro dual P3 box that I have installed Ubuntu using 'server' method...so I haven't a desktop as I don't need one, or so I thought.  On vanilla Debian boxes, I've been able to go about printer config using ssh & lynx pretty easily.  Ubuntu seems to have admin tasks disabled for security reasons.  All said and done, ssh into the box & lynx [http://localhost:631](http://localhost:631) brings up CUPS, but doesn't seem to recognize any passwords.  Instead, you're instructed to 

MENU SYSTEM --> ADMINISTRATION -->> PRINTING

Quite possibly a simple answer for someone, but after some searching, I didn't find anything.  Some help would be greatly appreciated.

TIA,
d1337

---

### Post by nictuku on 2005-06-24
Hi. See this entry in my blog:

[http://www.cetico.org/blog/2004/12/solution-for-web-admin-interface-for.html#c111469180679007701](http://www.cetico.org/blog/2004/12/solution-for-web-admin-interface-for.html#c111469180679007701)

---

### Post by d1337 on 2005-06-24
Nictuku,
Thanks a bunch.  While I opted to stick with Stephens comment from your blog,  worked like a charm.  Once I am finished setting up my printer on the server, I will most likely change it back to make it secure in the sense that the Ubuntu devel team intended it to be.  I appreciate your help and time.

Thanks,
d1337

---

### Post by d1337 on 2005-07-14
Now that it's been a few weeks, I'm still fighting with this printer.  I am able to connect my HP PSC-1310 from either of my workstations with no issue using the GUI (incredibly simple).  But my goal and need is to get it to print from my server.  I have puttered through practically every post dealing with cups and printing to try to fix this and have gotten so close.  In the end, I have scp'd my entire /etc/cups directory from my workstation to my server.  My server is seeing the printer and has actually labeled the USB port as  

USB Printer #1 (hp psc 1310 series ) 

but I keep getting

 Error:

     server-error-internal-error

So, I cat'd /var/log/cups/error_log and have come up with what I think is the problem, but can't wrap my brain around the solution.  It appears to be with permissions...

d [14/Jul/2005:19:20:42 -0500] add_printer(0xb7ae4c3c[7], ipp://localhost/printers/PSC-1310)
I [14/Jul/2005:19:20:42 -0500] Setting PSC-1310 device-uri to "usb://hp/psc%201310%20series%20?serial=CN42H160PSO2" (was "usb://hp/psc%201310%20series%20?serial=CN42H160PSO2".)
I [14/Jul/2005:19:20:42 -0500] Setting PSC-1310 printer-is-accepting-jobs to 1 (was 1.)
I [14/Jul/2005:19:20:42 -0500] Setting PSC-1310 printer-state to 3 (was 3.)
d [14/Jul/2005:19:20:42 -0500] copy_model("/usr/share/cups/model/HP-PSC_1310-hpijs.ppd", "/etc/cups/ppd/PSC-1310.ppd")
E [14/Jul/2005:19:20:42 -0500] add_printer: Unable to copy PPD file from /usr/share/cups/model/HP-PSC_1310-hpijs.ppd to /etc/cups/ppd/PSC-1310.ppd - Permission denied!
d [14/Jul/2005:19:20:42 -0500] send_ipp_error(0xb7ae4c3c[7], 500)
D [14/Jul/2005:19:20:42 -0500] Sending error: server-error-internal-error
D [14/Jul/2005:19:20:42 -0500] ProcessIPPRequest: 7 status_code=500
d [14/Jul/2005:19:20:42 -0500] ProcessIPPRequest: Adding fd 7 to OutputSet...
d [14/Jul/2005:19:20:42 -0500] WriteClient: Removing fd 7 from OutputSet...
d [14/Jul/2005:19:20:42 -0500] ReadClient: 7, used=0, file=-1
d [14/Jul/2005:19:20:42 -0500] ReadClient: httpGets returned EOF...
D [14/Jul/2005:19:20:42 -0500] CloseClient: 7
d [14/Jul/2005:19:20:42 -0500] CloseClient: Removing fd 7 from InputSet and OutputSet...
d [14/Jul/2005:19:20:42 -0500] PID 11044 exited with no errors.
d [14/Jul/2005:19:20:42 -0500] DeleteCert: removing certificate for pid 11044
d [14/Jul/2005:19:20:42 -0500] WriteClient: Removing fd 6 from OutputSet...
d [14/Jul/2005:19:20:42 -0500] WriteClient: Removing fd 8 from InputSet...
d [14/Jul/2005:19:20:42 -0500] WriteClient: 6 Closing data file 8.
d [14/Jul/2005:19:20:42 -0500] WriteClient: 6 Removing temp file /var/spool/cups/00000008
D [14/Jul/2005:19:20:42 -0500] CloseClient: 6
d [14/Jul/2005:19:20:42 -0500] CloseClient: Removing fd 6 from InputSet and OutputSet...
I [14/Jul/2005:19:20:42 -0500] [Job 12] Connecting to ibm on port 631...
I [14/Jul/2005:19:20:42 -0500] [Job 12] Network host 'ibm' is busy; will retry in 30 seconds...
d [14/Jul/2005:19:20:43 -0500] select_timeout: 11 seconds to process active jobs


Sorry if that is too much info, just wanted to include enough so that someone may be able to see something I can't...see my stats, I'm a noob.  Any help would thrill me as I'd like to get past this and onto more problems to share with the community :)

---

### Post by d1337 on 2005-07-31
Just wanted to post an update to my printing issue.  After doing some toying, I realized that default Ubuntu install is relatively lightweight.  Since this is a new project of mine, I didn't have much on the server and opted to start from scratch.  An option would have been to install what is needed for X, but I decided that I'd prefer a clean install to wipe all the changes that I had made (with issues other than the printing problem).

In a nutshell, I reinstalled Ubuntu with the expert switch.  Didn't make many changes, I just like going step by step...just in case I learn something :)  Even with X running, I have only 48 processes going (after adding gkrellmd) and am using less than 80mb of my RAM.  I'm certain that I can play with runlevels and squeeze it down a bit more, especially while not in X, but I also think that this is acceptable for a server.  After the re-install, setting up printing was simple.  I have and HP PSC-1315 which will use the HP PSC-1310 that seems to be already loaded as a potential driver (hpijs-foomatic).  Using USB connectivity, my server saw the printer and spit a test page, with color, without issue .  From past experience, it may be neccessary to get the appropriate drivers from [LinuxPrinting.org](http://linuxprinting.org) 

Most of my reasoning for this reply is to share some insight on simple network printing setup, even across a mixed LAN (like my two dual boot WinXP boxes) without running Samba.  I'll include a few bits of my /etc/cups/cupsd.conf file as well.  From another Ubuntu box, and I'd assume most any Linux distro with an Administration tab in the GUI (have used the same on a Vanilla Debian box as well as a Libranet box), use Printing --> Global Setting --> Detect Lan Printers and it should most likely see the printer connected to the server allowing you to set it up as a network printing device (this may or may not be the best idea).  A few clips from cupsd.conf on the server to allow this
```
# NOTE: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you'll
# probably need to listen on port 443 (the "https" port...)
#
# NOTE 2: In order for the command-line and web interfaces to work, you
# must have at least one Port or Listen line that allows access from the
# local loopback address (localhost).
#

#Port 80
#Port 443
Port 631
#Listen 127.0.0.1:631

```
Not certain as to the why, but I had to comment the last line before it would take for me.  Also insure that browsing is on in /etc/cups/cupsd-browsing.conf and that it's included
```
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network. For Ubuntu, this setting has been externalized to
# a separate configuration file cupsd-browsing.conf. This allows to change the
# browsing setting with /usr/share/cups/enable_browsing (or manually) without
# modifying this main configuration file, which avoids dpkg questions on
# conffile upgrades.

Include cupsd-browsing.conf

```
and this is cupsd-browsing.conf, albeit simple
```
dboyle@########:~$ cat /etc/cups/cupsd-browsing.conf
#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network.  Disabled by default.
#

Browsing On

```
Notice that this is broadcast and/or listen

a few other snips, and then I'll explain it from the Windows side which I think will be quite beneficail for some folks.
```
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library and scheduler.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".
#

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

```
```
<Location /jobs>
#
# You may wish to limit access to job operations, either with Allow
# and Deny lines, or by requiring a username and password.
#
AuthType Basic
AuthClass User
</Location>

#<Location /printers>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
AuthType None
Order Deny,Allow
Deny from All
Allow from 192.168.0.*
#
#</Location>

```
```
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*

#Encryption Required
</Location>

#
# End of "$Id: cupsd.conf.in,v 1.17 2005/01/03 19:29:45 mike Exp $".
#
```
I would recommend naming all of your boxes or having a well thought IP addressing system in the /etc/hosts file (of all machines).  I'm a newbie, but I think that this could help tighten up security in the above scenario...I'll be tackling that next.  The reason I mentioned this is that the ipp protocol can be use on the LAN or from the internet.  I don't yet know the ins and outs of it, but using ipp could allow someone from the net to access your printer.  In my scenario this is a goal, in others, it would bite to come home one afternoon to see that someone has printed 300 black pages and burnt through your $80 toner cartridge that you just put in.

If your box doesn't see the printer on your server, you may need to give it a location.  In fact, in hindsight, this may be a better method and more secure.  Regardless, you can point the location of the printer using the ipp protocol...

ipp://YOURSERVERNAMEorSERVERIPADDRESS/printers/THEPRINTERNAME

The printer name should be the name as recognized by your server.  In my instance , it is ipp://#######/printers/psc-1310.  This has done the trick for me, but your milage may vary.

PRINTING FROM WINDOWS (without Samba)
Not to bash Samba, but if you don't need it...you don't need it.  The most current Windows releases include support for ipp (by the way, that's internet printing protocol).  If you're using a common printer that MS includes the driver by support, try this first...

Make sure that you have modified the hosts file on windows to include the IP address and name of your server.  WINDOWS WILL NOT USE (at least to my knowledge) JUST AN IP ADDRESS FOR THE FOLLOWING SCENARIO.  Sorry, I'm in Ubuntu now and can't truly recall, but do a search for hosts on your c: drive (assuming).  There are two that seem to do the trick, one is lmhosts and the other is hosts.  Just add to the end, using wordpad or something

IP ADDRESS OF YOUR SERVER (tab) SERVER NAME

I added

192.168.0.254      MYSERVERNAME

Then, when trying to add a network printer through the control panel, use the location as follows.

[http://MYSERVERNAME:**631**/printers/psc-1310](http://MYSERVERNAME:**631**/printers/psc-1310)

Again, use the printer name as recognized by your server.  I've done this on a small network only, so it didn't take me forever to do just two boxes...and if you have a bunch of machines, Samba may be your best bet.  Using :631 is required as far as I can tell...haven't had any luck without it.

If that doesn't work, on one occassion I had to physically plug my printer into my XP box first to get it to take the driver.  But after that, the driver was available and I had full featured printing immediately.  You may need to do this and then follow the steps above again.  As opposed to adding a new printer, you can edit the location as above in Windows.  In Linux, I've always had to remove and try again if I've had to toy with location.

There's my update.  I'd like to expand upon this with the scanning features etc of my printer, but I haven't gotten there yet (if it's even possible).  Hope this helps someone...I know that it would've helped me.  I am subscribed to this thread, so if you have questions, I'll do my best.

d1337

---

### Post by tabinin on 2006-02-11
Thanks a million for your posts!  You made the madness stop.  Samba is gone, ipp is up and running thanks to you.

---

