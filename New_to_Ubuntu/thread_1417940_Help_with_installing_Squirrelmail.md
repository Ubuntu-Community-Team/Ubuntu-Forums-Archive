---
title: "Help with installing Squirrelmail"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Sargalus on 2010-02-27
hello, I just installed squirrelmail and configured it using the guild from the following website

[http://www.debian-administration.org/articles/200](http://www.debian-administration.org/articles/200)

Im stuck at the section where it talks about adding information into the apache configuration file, below is what the guide says to do

Now to make the install web-accessible. With the configuration files  you'll find an Apache configuration snippet you can edit and add to your  Apache config. It's wise to add it to the configuration of Apache-SSL  aswell, so your users can access their mailbox over a secure connection.  After that, reload Apache. We should be done!

Im totally lost at this point as this part of the guide is completely confusing and Im not sure what it's talking about or even what config files to edit and what to add in them.

any help would be greatly appreciated.

---

### Post by johngreth on 2010-02-28
You need to edit etc/apache2/apache2.conf and add:
```
    Alias /squirrelmail /usr/share/squirrelmail

    <Directory /usr/share/squirrelmail>
      Options Indexes FollowSymLinks
      <IfModule mod_php5.c>
        php_flag register_globals off
      </IfModule>
      <IfModule mod_dir.c>
        DirectoryIndex index.php
      </IfModule>

      # access to configtest is limited by default to prevent information leak
      <Files configtest.php>
        order deny,allow
        deny from all
        allow from 127.0.0.1
      </Files>
    </Directory>
```

---

### Post by Sargalus on 2010-02-28
Yeah I have already do something like that already. what I did was

cp /etc/squirrelmail/apache.conf /etc/apache2/sites-avaliable/squirrelmail

then ran

a2ensite squirrelmail

I can bring up the login page but I get this error message

Error connecting to IMAP server: tls://localhost.
0 : 

and if I go to

[http://domainname.com/squirrelmail/src/configtest.php](http://domainname.com/squirrelmail/src/configtest.php) I get the following error message

You don't have permission to access /squirrelmail/src/configtest.php on this server.

I think the two errors are related but not sure. I have spent hours searching google for anything related but nothing.

---

### Post by johngreth on 2010-02-28
By default, /squirrelmail/src/configtest.php is blocked to outside traffic. You could try going to [http://127.0.0.1/squirrelmail/src/configtest.php](http://127.0.0.1/squirrelmail/src/configtest.php) from on the server. If that isn't an option, you could edit /etc/apache2/sites-avaliable/squirrelmail and change
```
# access to configtest is limited by default to prevent information leak
      <Files configtest.php>
        order deny,allow
        deny from all
        allow from **127.0.0.1**
      </Files>
```
to
```
# access to configtest is limited by default to prevent information leak
      <Files configtest.php>
        order deny,allow
        deny from all
        allow from **all**
      </Files>
```
You could also replace 127.0.0.1 with your computer's ip address. Be sure to change it back when you're done because it is a security risk.

Getting this to work may give some insight into what caused the other error message. The "Error connecting to IMAP server" is probably a problem with the mail server, not squirrelmail. You could try accessing the mail server with a different application like evolution mail to see if that is causing the problem.

---

### Post by Sargalus on 2010-02-28
Ok, that seem to let me run configtest.php here are the results

[B]```


```[/B]```


**SquirrelMail configtest**

  This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.
   SquirrelMail version:**1.4.19** Config file version:**1.4.0** Config file last modified:**28 February 2010 18:40:01**  
  Checking PHP configuration...
    PHP version 5.2.10-2ubuntu6.4 OK.
    display_errors: 1
    error_reporting: 6135
    variables_order OK: EGPCS.
    PHP extensions OK. Dynamic loading is disabled.
    [COLOR=red]**ERROR:**[/COLOR] You have enabled any one of magic_quotes_runtime, magic_quotes_gpc or magic_quotes_sybase in your PHP configuration. We recommend all those settings to be off. SquirrelMail may work with them on, but when experiencing stray backslashes in your mail or other strange behaviour, it may be advisable to turn them off.
 Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins OK.
    Themes OK.
    Default language OK.
    Base URL detected as: http://192.168.1.103/squirrelmail/src (location base autodetected)
Checking outgoing mail service....
    SMTP server OK (220 requiem ESMTP Sendmail 8.14.3/8.14.3/Debian-9ubuntu1; Sun, 28 Feb 2010 18:44:27 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1])
Checking IMAP service....

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: SSL operation failed with code 1. OpenSSL Error messages: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number in **/usr/share/squirrelmail/src/configtest.php** on line **406**

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: Failed to enable crypto in **/usr/share/squirrelmail/src/configtest.php** on line **406**

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: unable to connect to tls://localhost:143 (Unknown error) in **/usr/share/squirrelmail/src/configtest.php** on line **406**
    [COLOR=red]**ERROR:**[/COLOR] Error connecting to IMAP server "localhost:143".Server error: (0) 

```

I figured out why I was getting this

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: SSL operation failed with code 1. OpenSSL Error messages: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number in **/usr/share/squirrelmail/src/configtest.php** on line **406**

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: Failed to enable crypto in **/usr/share/squirrelmail/src/configtest.php** on line **406**

**Warning**:  fsockopen() [[function.fsockopen]("http://192.168.1.103/squirrelmail/src/function.fsockopen")]: unable to connect to tls://localhost:143 (Unknown error) in **/usr/share/squirrelmail/src/configtest.php** on line **406**
    [COLOR=red]**ERROR:**[/COLOR] Error connecting to IMAP server "localhost:143".Server error: (0) 
[/code]

I had tls enabled but not running a imapd ssl so I went back into the config and turned of tls and now everything is working fine, just have to get it working with tls enabled if Im correct I need to install imapd-ssl correct?

---

### Post by Sargalus on 2010-02-28
Ok, everything is working accept being able to login. when I try to login I get the following

[COLOR=#cc0000]**ERROR**[/COLOR]Unknown user or password incorrect.[COLOR=#cc0000]**[Go to the login page]("http://webmail.requiemofblood.com/src/login.php")**[/COLOR]
so I viewed the var/log/mail.log file to see what was going on in there and this is what it shows

Feb 28 20:12:50 requiem cyrus/master[6023]: about to exec /usr/lib/cyrus/bin/imapd
Feb 28 20:12:50 requiem cyrus/imap[6023]: executed
Feb 28 20:12:50 requiem cyrus/imap[6023]: accepted connection
Feb 28 20:12:50 requiem cyrus/imap[6023]: badlogin: requiem [127.0.1.1] plaintext mark SASL(-13): user not found: checkpass failed

at this point im lost, Im not sure on how I setup users to be able to access mail or if it's auto when you setup new users, any help or suggestions would be great

p.s can't find anything from google to help with this

---

### Post by johngreth on 2010-02-28
did you install the mail server from tasksel? If not, there might be a problem with the install. When I installed my mail server, I used [webmin]("http://www.webmin.com/") to check on everything. that might help.

---

### Post by Sargalus on 2010-02-28
> **johngreth said:**
> did you install the mail server from tasksel? If not, there might be a problem with the install. When I installed my mail server, I used [webmin]("http://www.webmin.com/") to check on everything. that might help.

I used synaptis and installed cyrus-imapd that way, is there a better way to install it maybe or a better mail server to use all together I know a long time ago I use to use qmail I think it was called or something like that

---

### Post by Gone fishing on 2010-03-01
I suppose there are a few questions:

1 can you connect to the IMAP server securely not using squirrel mail from an external client.
2 if you enable the non-secure cyrus server can you connect via sqirrel mail.
3 Are you use ldap authentication or similar?

---

### Post by Sargalus on 2010-03-01
> **Gone fishing said:**
> I suppose there are a few questions:

1 can you connect to the IMAP server securely not using squirrel mail from an external client.
2 if you enable the non-secure cyrus server can you connect via sqirrel mail.
3 Are you use ldap authentication or similar?

Ok this is what I did
I removed cyrus and sendmail
installed postfix and dovecot
ran dpkg-reconfigure postfix
made sure in my router all needed ports were forwarded to the right computer (noob mistake)

after all that I am not able to go to [http://webmail.requiemofblood.com](http://webmail.requiemofblood.com) and it pulls up squirrel mail and I was able to login

I sent a test email and it sent just fine and I received it in the remote email (gmail account) it came from the address [EMAIL="username@webmail.requiemofblood.com"]username@webmail.requiemofblood.com[/EMAIL] 

I went to change it so it would come from [EMAIL="username@requiemofblood.com"]username@requiemofblood.com[/EMAIL] after that was all done I restarted both postfix and dovecot.

ran into a new problem now

I am able to login still just fine, but unable to send or recieve emails, or do anything else after I click compose to send another test email. I have to close the browser

in the /var/log/mail.log it gives me the following message

Feb 28 23:15:06 requiem postfix/smtpd[9312]: fatal: open database /etc/aliases.db: No such file or directory
Feb 28 23:15:07 requiem postfix/master[9283]: warning: process /usr/lib/postfix/smtpd pid 9312 exit status 1
Feb 28 23:15:07 requiem postfix/master[9283]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

and now squirrelmail is locked up I have to close firefox and reopen.

Edit:

Ok I am able to send emails now no problem, but unable to recieve them at all there are no error mesages anywhere it's like they aren't even reaching me. any one with some ideas please let me know, my brain is starting to hurt

---

### Post by Gone fishing on 2010-03-01
Well it looks like you've messed up the postfix.conf. What I do is install webmin make sure that I can send mail from account to account using webmin this goes directly into postfix rather than using cyrus etc. 

Webmin also has a handy postfix config module.

Then when postfix is working then I get squirrel mail working.

I'm running an opensuse box and used this howto from sourceforge they probably have a similar one fro Ubuntu even if not it would probably be worth looking at.

[http://www.howtoforge.com/perfect-server-opensuse11-p4](http://www.howtoforge.com/perfect-server-opensuse11-p4)

When I get to the server I'll send you a copy of my postfix.conf

---

### Post by Sargalus on 2010-03-01
> **Gone fishing said:**
> Well it looks like you've messed up the postfix.conf. What I do is install webmin make sure that I can send mail from account to account using webmin this goes directly into postfix rather than using cyrus etc. 

Webmin also has a handy postfix config module.

Then when postfix is working then I get squirrel mail working.

I'm running an opensuse box and used this howto from sourceforge they probably have a similar one fro Ubuntu even if not it would probably be worth looking at.

[http://www.howtoforge.com/perfect-server-opensuse11-p4](http://www.howtoforge.com/perfect-server-opensuse11-p4)

When I get to the server I'll send you a copy of my postfix.conf

Thanks man, I got the sending part working just fine now, but unable to recieve emails at all no messasges in any log files either almost like the mail isn't even reaching me, im going to take a look at the link you posted above and see what I can work out, thanks for the help

---

### Post by Sargalus on 2010-03-01
Ok I followed the setup for postfix on the linke you post [http://www.howtoforge.com/perfect-server-opensuse11-p4](http://www.howtoforge.com/perfect-server-opensuse11-p4)

I use it's using courier instead of dovecot, is courier better to use then dovecot, you also mentioned something about webmin I didn't see anything on that link about webmin.

---

### Post by Gone fishing on 2010-03-01
Sorry yes I'm using courier, however, if it's not receiving but now sending your dovecot is probably OK. is the port open? are the mail relay options allowing postfix to get the mail from the outside?. Here's Howtoforge for ubuntu [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p5](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p5)

Webmin isn't use in the howto I've just found it a very handy tool for all sorts of things, it's probably in the repositories although its can be download from the webmin site [http://www.webmin.com/](http://www.webmin.com/)

screanshot

---

### Post by Sargalus on 2010-03-01
That howto did nothing different from what I did but they installed ISPConfig which I never did. How do I check my mail relays to make sure postfix is accepting the ports are open I ran nmap and it shows port 25 and 143 open. Im going to install webmin see if that can help me any

Edit:

I install webmin, it's a pretty nice application. the bad thing is I don't know enough about postfix to know if something was messed up or not. Im going to check google to see if I can find answers, please let me know if you have any ideas

Edit:
I found [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3) Im going to remove postfix, squirrelmail, and dovecot and following this step by step and see what happens.

---

### Post by Sargalus on 2010-03-01
Ok I removed squirrelmail, postfix, dovecot, etc. and followed this guide [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p3)

now after completing this guide, im back at square one unable to log into squirrelmail all together I look at the /var/log/mail.log and get the following

Mar  1 15:30:02 requiem postfix/smtpd[21638]: disconnect from localhost[127.0.0.1]
Mar  1 15:30:02 requiem imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  1 15:30:02 requiem imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Mar  1 15:30:02 requiem pop3d: Connection, ip=[::ffff:127.0.0.1]
Mar  1 15:30:02 requiem pop3d: Disconnected, ip=[::ffff:127.0.0.1

looks like it's trying to connect from the wrong ip and what not

Anyone that has any suggestions please help.

---

### Post by Gone fishing on 2010-03-02
OK I've sent you my postfix config (/etc/postfix/main.cf) my setup is slightly different I relay through a mail external mail sever but all local area users have mail account and can use squirrel mail to send both internally and externally.

As you've got webmin if you open read user mail can you send from one account internally to another? If you can postfix is probably basically working your problem is with imap etc. I didn't look carefully at the Ubuntu howto on sourceforge, but if it's basically the same as the Opensuse one I didn't use ispconfig either.

Oddly had a similar problem yesterday with the server at the prep school - got badly bust and we fixed by setting up a new box and copying the config files over from the old system. Every thing worked but sending mail turned out to be procmail was not installed (so make sure you've installed everything when I did this I got stuck for a day because I didn't install amavis and the mail is relayed through this AV in the Opensuse setup)

 I'll ask the prep school techie to look at this thread.

---

### Post by Gone fishing on 2010-03-02
```
#
# -----------------------------------------------------------------------
# NOTE: Many parameters have already been added to the end of this file
#       by SuSEconfig.postfix. So take care that you don't uncomment
#       and set a parameter without checking whether it has been added
#       to the end of this file.
# -----------------------------------------------------------------------
#
# Global Postfix configuration file. This file lists only a subset
# of all parameters. For the syntax, and for a complete parameter
# list, see the postconf(5) manual page (command: "man 5 postconf").
#
# For common configuration examples, see BASIC_CONFIGURATION_README
# and STANDARD_CONFIGURATION_README. To find these documents, use
# the command "postconf html_directory readme_directory", or go to
# http://www.postfix.org/.
#
# For best results, change no more than 2-3 parameters at a time,
# and test if Postfix still works after every change.
# SOFT BOUNCE
#
# The soft_bounce parameter provides a limited safety net for
# testing.  When soft_bounce is enabled, mail will remain queued that
# would otherwise bounce. This parameter disables locally-generated
# bounces, and prevents the SMTP server from rejecting mail permanently
# (by changing 5xx replies into 4xx replies). However, soft_bounce
# is no cure for address rewriting mistakes or mail routing mistakes.
#
#soft_bounce = no
# LOCAL PATHNAME INFORMATION
#
# The queue_directory specifies the location of the Postfix queue.
# This is also the root directory of Postfix daemons that run chrooted.
# See the files in examples/chroot-setup for setting up Postfix chroot
# environments on different UNIX systems.

# The command_directory parameter specifies the location of all
# postXXX commands.
command_directory=/usr/sbin
# The daemon_directory parameter specifies the location of all Postfix
# daemon programs (i.e. programs listed in the master.cf file). This
# directory must be owned by root.
daemon_directory=/usr/lib/postfix
# The data_directory parameter specifies the location of Postfix-writable
# data files (caches, random numbers). This directory must be owned
# by the mail_owner account (see below).
data_directory=/var/lib/postfix
# QUEUE AND PROCESS OWNERSHIP
#
# The mail_owner parameter specifies the owner of the Postfix queue
# and of most Postfix daemon processes.  Specify the name of a user
# account THAT DOES NOT SHARE ITS USER OR GROUP ID WITH OTHER ACCOUNTS
# AND THAT OWNS NO OTHER FILES OR PROCESSES ON THE SYSTEM.  In
# particular, don't specify nobody or daemon. PLEASE USE A DEDICATED
# USER.
#
# The default_privs parameter specifies the default rights used by
# the local delivery agent for delivery to external file or command.
# These rights are used in the absence of a recipient user context.
# DO NOT SPECIFY A PRIVILEGED USER OR THE POSTFIX OWNER.
#
#default_privs = nobody
# INTERNET HOST AND DOMAIN NAMES
# 
# The myhostname parameter specifies the internet hostname of this
# mail system. The default is to use the fully-qualified domain name
# from gethostname(). $myhostname is used as a default value for many
# other configuration parameters.
#
#myhostname = host.domain.tld
#myhostname = virtual.domain.tld
# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
#
#mydomain = domain.tld
# SENDING MAIL
# 
# The myorigin parameter specifies the domain that locally-posted
# mail appears to come from. The default is to append $myhostname,
# which is fine for small sites.  If you run a domain with multiple
# machines, you should (1) change this to $mydomain and (2) set up
# a domain-wide alias database that aliases each user to
# user@that.users.mailhost.
#
# For the sake of consistency between sender and recipient addresses,
# myorigin also specifies the default domain name that is appended
# to recipient addresses that have no @domain part.
#
#myorigin = $myhostname
#myorigin = $mydomain
# RECEIVING MAIL
# The inet_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on.  By default,
# the software claims all active interfaces on the machine. The
# parameter also controls delivery of mail to user@[ip.address].
#
# See also the proxy_interfaces parameter, for network addresses that
# are forwarded to us via a proxy or network address translator.
#
# Note: you need to stop/start Postfix when this parameter changes.
#
#inet_interfaces = all
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost
# The proxy_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on by way of a
# proxy or network address translation unit. This setting extends
# the address list specified with the inet_interfaces parameter.
#
# You must specify your proxy/NAT addresses when your system is a
# backup MX host for other domains, otherwise mail delivery loops
# will happen when the primary MX host is down.
#
#proxy_interfaces =
#proxy_interfaces = 1.2.3.4
# The mydestination parameter specifies the list of domains that this
# machine considers itself the final destination for.
#
# These domains are routed to the delivery agent specified with the
# local_transport parameter setting. By default, that is the UNIX
# compatible delivery agent that lookups all recipients in /etc/passwd
# and /etc/aliases or their equivalent.
#
# The default is $myhostname + localhost.$mydomain.  On a mail domain
# gateway, you should also include $mydomain.
#
# Do not specify the names of virtual domains - those domains are
# specified elsewhere (see VIRTUAL_README).
#
# Do not specify the names of domains that this machine is backup MX
# host for. Specify those names via the relay_domains settings for
# the SMTP server, or use permit_mx_backup if you are lazy (see
# STANDARD_CONFIGURATION_README).
#
# The local machine is always the final destination for mail addressed
# to user@[the.net.work.address] of an interface that the mail system
# receives mail on (see the inet_interfaces parameter).
#
# Specify a list of host or domain names, /file/name or type:table
# patterns, separated by commas and/or whitespace. A /file/name
# pattern is replaced by its contents; a type:table is matched when
# a name matches a lookup key (the right-hand side is ignored).
# Continue long lines by starting the next line with whitespace.
#
# See also below, section "REJECTING MAIL FOR UNKNOWN LOCAL USERS".
#
#mydestination = $myhostname, localhost.$mydomain, localhost
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain,
#	mail.$mydomain, www.$mydomain, ftp.$mydomain
# REJECTING MAIL FOR UNKNOWN LOCAL USERS
#
# The local_recipient_maps parameter specifies optional lookup tables
# with all names or addresses of users that are local with respect
# to $mydestination, $inet_interfaces or $proxy_interfaces.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown local users. This parameter is defined by default.
#
# To turn off local recipient checking in the SMTP server, specify
# local_recipient_maps = (i.e. empty).
#
# The default setting assumes that you use the default Postfix local
# delivery agent for local delivery. You need to update the
# local_recipient_maps setting if:
#
# - You define $mydestination domain recipients in files other than
#   /etc/passwd, /etc/aliases, or the $virtual_alias_maps files.
#   For example, you define $mydestination domain recipients in    
#   the $virtual_mailbox_maps files.
#
# - You redefine the local delivery agent in master.cf.
#
# - You redefine the "local_transport" setting in main.cf.
#
# - You use the "luser_relay", "mailbox_transport", or "fallback_transport"
#   feature of the Postfix local delivery agent (see local(8)).
#
# Details are described in the LOCAL_RECIPIENT_README file.
#
# Beware: if the Postfix SMTP server runs chrooted, you probably have
# to access the passwd file via the proxymap service, in order to
# overcome chroot restrictions. The alternative, having a copy of
# the system passwd file in the chroot jail is just not practical.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify a bare username, an @domain.tld
# wild-card, or specify a user@domain.tld address.
# 
#local_recipient_maps = unix:passwd.byname $alias_maps
#local_recipient_maps = proxy:unix:passwd.byname $alias_maps
#local_recipient_maps =
# The unknown_local_recipient_reject_code specifies the SMTP server
# response code when a recipient domain matches $mydestination or
# ${proxy,inet}_interfaces, while $local_recipient_maps is non-empty
# and the recipient address or address local-part is not found.
#
# The default setting is 550 (reject mail) but it is safer to start
# with 450 (try again later) until you are certain that your
# local_recipient_maps settings are OK.
#
# TRUST AND RELAY CONTROL
# The mynetworks parameter specifies the list of "trusted" SMTP
# clients that have more privileges than "strangers".
#
# In particular, "trusted" SMTP clients are allowed to relay mail
# through Postfix.  See the smtpd_recipient_restrictions parameter
# in postconf(5).
#
# You can specify the list of "trusted" network addresses by hand
# or you can let Postfix do it for you (which is the default).
#
# By default (mynetworks_style = subnet), Postfix "trusts" SMTP
# clients in the same IP subnetworks as the local machine.
# On Linux, this does works correctly only with interfaces specified
# with the "ifconfig" command.
# 
# Specify "mynetworks_style = class" when Postfix should "trust" SMTP
# clients in the same IP class A/B/C networks as the local machine.
# Don't do this with a dialup site - it would cause Postfix to "trust"
# your entire provider's network.  Instead, specify an explicit
# mynetworks list by hand, as described below.
#  
# Specify "mynetworks_style = host" when Postfix should "trust"
# only the local machine.
# 
#mynetworks_style = class
#mynetworks_style = subnet
#mynetworks_style = host
# Alternatively, you can specify the mynetworks list by hand, in
# which case Postfix ignores the mynetworks_style setting.
#
# Specify an explicit list of network/netmask patterns, where the
# mask specifies the number of bits in the network part of a host
# address.
#
# You can also specify the absolute pathname of a pattern file instead
# of listing the patterns here. Specify type:table for table-based lookups
# (the value on the table right-hand side is not used).
#
#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table
# The relay_domains parameter restricts what destinations this system will
# relay mail to.  See the smtpd_recipient_restrictions description in
# postconf(5) for detailed information.
#
# By default, Postfix relays mail
# - from "trusted" clients (IP address matches $mynetworks) to any destination,
# - from "untrusted" clients to destinations that match $relay_domains or
#   subdomains thereof, except addresses with sender-specified routing.
# The default relay_domains value is $mydestination.
# 
# In addition to the above, the Postfix SMTP server by default accepts mail
# that Postfix is final destination for:
# - destinations that match $inet_interfaces or $proxy_interfaces,
# - destinations that match $mydestination
# - destinations that match $virtual_alias_domains,
# - destinations that match $virtual_mailbox_domains.
# These destinations do not need to be listed in $relay_domains.
# 
# Specify a list of hosts or domains, /file/name patterns or type:name
# lookup tables, separated by commas and/or whitespace.  Continue
# long lines by starting the next line with whitespace. A file name
# is replaced by its contents; a type:name table is matched when a
# (parent) domain appears as lookup key.
#
# NOTE: Postfix will not automatically forward mail for domains that
# list this system as their primary or backup MX host. See the
# permit_mx_backup restriction description in postconf(5).
#
#relay_domains = $mydestination
# INTERNET OR INTRANET
# The relayhost parameter specifies the default host to send mail to
# when no entry is matched in the optional transport(5) table. When
# no relayhost is given, mail is routed directly to the destination.
#
# On an intranet, specify the organizational domain name. If your
# internal DNS uses no MX records, specify the name of the intranet
# gateway host instead.
#
# In the case of SMTP, specify a domain, host, host:port, [host]:port,
# [address] or [address]:port; the form [host] turns off MX lookups.
#
# If you're connected via UUCP, see also the default_transport parameter.
#
#relayhost = $mydomain
#relayhost = [gateway.my.domain]
#relayhost = [mailserver.isp.tld]
#relayhost = uucphost
#relayhost = [an.ip.add.ress]
# REJECTING UNKNOWN RELAY USERS
#
# The relay_recipient_maps parameter specifies optional lookup tables
# with all addresses in the domains that match $relay_domains.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown relay users. This feature is off by default.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify an @domain.tld wild-card, or specify
# a user@domain.tld address.
# 
#relay_recipient_maps = hash:/etc/postfix/relay_recipients
# INPUT RATE CONTROL
#
# The in_flow_delay configuration parameter implements mail input
# flow control. This feature is turned on by default, although it
# still needs further development (it's disabled on SCO UNIX due
# to an SCO bug).
# 
# A Postfix process will pause for $in_flow_delay seconds before
# accepting a new message, when the message arrival rate exceeds the
# message delivery rate. With the default 100 SMTP server process
# limit, this limits the mail inflow to 100 messages a second more
# than the number of messages delivered per second.
# 
# Specify 0 to disable the feature. Valid delays are 0..10.
# 
#in_flow_delay = 1s
# ADDRESS REWRITING
#
# The ADDRESS_REWRITING_README document gives information about
# address masquerading or other forms of address rewriting including
# username->Firstname.Lastname mapping.
# ADDRESS REDIRECTION (VIRTUAL DOMAIN)
#
# The VIRTUAL_README document gives information about the many forms
# of domain hosting that Postfix supports.
# "USER HAS MOVED" BOUNCE MESSAGES
#
# See the discussion in the ADDRESS_REWRITING_README document.
# TRANSPORT MAP
#
# See the discussion in the ADDRESS_REWRITING_README document.
# ALIAS DATABASE
#
# The alias_maps parameter specifies the list of alias databases used
# by the local delivery agent. The default list is system dependent.
#
# On systems with NIS, the default is to search the local alias
# database, then the NIS alias database. See aliases(5) for syntax
# details.
# 
# If you change the alias database, run "postalias /etc/aliases" (or
# wherever your system stores the mail alias file), or simply run
# "newaliases" to build the necessary DBM or DB file.
#
# It will take a minute or so before changes become visible.  Use
# "postfix reload" to eliminate the delay.
#
#alias_maps = dbm:/etc/aliases
#alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases
# The alias_database parameter specifies the alias database(s) that
# are built with "newaliases" or "sendmail -bi".  This is a separate
# configuration parameter, because alias_maps (see above) may specify
# tables that are not necessarily all under control by Postfix.
#
#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
#alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases
# ADDRESS EXTENSIONS (e.g., user+foo)
#
# The recipient_delimiter parameter specifies the separator between
# user names and address extensions (user+foo). See canonical(5),
# local(8), relocated(5) and virtual(5) for the effects this has on
# aliases, canonical, virtual, relocated and .forward file lookups.
# Basically, the software tries user+foo and .forward+foo before
# trying user and .forward.
#
#recipient_delimiter = +
# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
#
#home_mailbox = Mailbox
#home_mailbox = Maildir/
# The mail_spool_directory parameter specifies the directory where
# UNIX-style mailboxes are kept. The default setting depends on the
# system type.
#
#mail_spool_directory = /var/mail
#mail_spool_directory = /var/spool/mail
# The mailbox_command parameter specifies the optional external
# command to use instead of mailbox delivery. The command is run as
# the recipient with proper HOME, SHELL and LOGNAME environment settings.
# Exception:  delivery for root is done as $default_user.
#
# Other environment variables of interest: USER (recipient username),
# EXTENSION (address extension), DOMAIN (domain part of address),
# and LOCAL (the address localpart).
#
# Unlike other Postfix configuration parameters, the mailbox_command
# parameter is not subjected to $parameter substitutions. This is to
# make it easier to specify shell syntax (see example below).
#
# Avoid shell meta characters because they will force Postfix to run
# an expensive shell process. Procmail alone is expensive enough.
#
# IF YOU USE THIS TO DELIVER MAIL SYSTEM-WIDE, YOU MUST SET UP AN
# ALIAS THAT FORWARDS MAIL FOR ROOT TO A REAL USER.
#
#mailbox_command = /some/where/procmail
#mailbox_command = /some/where/procmail -a "$EXTENSION"
# The mailbox_transport specifies the optional transport in master.cf
# to use after processing aliases and .forward files. This parameter
# has precedence over the mailbox_command, fallback_transport and
# luser_relay parameters.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#mailbox_transport = lmtp:unix:/file/name
#mailbox_transport = cyrus
# The fallback_transport specifies the optional transport in master.cf
# to use for recipients that are not found in the UNIX passwd database.
# This parameter has precedence over the luser_relay parameter.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =
# The luser_relay parameter specifies an optional destination address
# for unknown recipients.  By default, mail for unknown@$mydestination,
# unknown@[$inet_interfaces] or unknown@[$proxy_interfaces] is returned
# as undeliverable.
#
# The following expansions are done on luser_relay: $user (recipient
# username), $shell (recipient shell), $home (recipient home directory),
# $recipient (full recipient address), $extension (recipient address
# extension), $domain (recipient domain), $local (entire recipient
# localpart), $recipient_delimiter. Specify ${name?value} or
# ${name:value} to expand value only when $name does (does not) exist.
#
# luser_relay works only for the default Postfix local delivery agent.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must specify "local_recipient_maps =" (i.e. empty) in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
unknown_local_recipient_reject_code=550   
# JUNK MAIL CONTROLS
# 
# The controls listed here are only a very small subset. The file
# SMTPD_ACCESS_README provides an overview.
# The header_checks parameter specifies an optional table with patterns
# that each logical message header is matched against, including
# headers that span multiple physical lines.
#
# By default, these patterns also apply to MIME headers and to the
# headers of attached messages. With older Postfix versions, MIME and
# attached message headers were treated as body text.
#
# For details, see "man header_checks".
#
#header_checks = regexp:/etc/postfix/header_checks
# FAST ETRN SERVICE
#
# Postfix maintains per-destination logfiles with information about
# deferred mail, so that mail can be flushed quickly with the SMTP
# "ETRN domain.tld" command, or by executing "sendmail -qRdomain.tld".
# See the ETRN_README document for a detailed description.
# 
# The fast_flush_domains parameter controls what destinations are
# eligible for this service. By default, they are all domains that
# this server is willing to relay mail to.
# 
#fast_flush_domains = $relay_domains
# SHOW SOFTWARE VERSION OR NOT
#
# The smtpd_banner parameter specifies the text that follows the 220
# code in the SMTP server's greeting banner. Some people like to see
# the mail version advertised. By default, Postfix shows no version.
#
# You MUST specify $myhostname at the start of the text. That is an
# RFC requirement. Postfix itself does not care.
#
#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)
# PARALLEL DELIVERY TO THE SAME DESTINATION
#
# How many parallel deliveries to the same user or domain? With local
# delivery, it does not make sense to do massively parallel delivery
# to the same user, because mailbox updates must happen sequentially,
# and expensive pipelines in .forward files can cause disasters when
# too many are run at the same time. With SMTP deliveries, 10
# simultaneous connections to the same domain could be sufficient to
# raise eyebrows.
# 
# Each message delivery transport has its XXX_destination_concurrency_limit
# parameter.  The default is $default_destination_concurrency_limit for
# most delivery transports. For the local delivery agent the default is 2.
#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20
# DEBUGGING CONTROL
#
# The debug_peer_level parameter specifies the increment in verbose
# logging level when an SMTP client or server host name or address
# matches a pattern in the debug_peer_list parameter.
debug_peer_level=2
# The debug_peer_list parameter specifies an optional list of domain
# or network patterns, /file/name patterns or type:name tables. When
# an SMTP client or server host name or address matches a pattern,
# increase the verbose logging level by the amount specified in the
# debug_peer_level parameter.
#
#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain
# The debugger_command specifies the external command that is executed
# when a Postfix daemon program is run with the -D option.
#
# Use "command .. & sleep 5" so that the debugger can attach before
# the process marches on. If you use an X-based debugger, be sure to
# set up your XAUTHORITY environment variable before starting Postfix.
debugger_command=PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin	 ddd $daemon_directory/$process_name $process_id & sleep 5
# If you can't use X, use this to capture the call stack when a
# daemon crashes. The result is in a file in the configuration
# directory, and is named after the process name and the process ID.
#
# debugger_command =
#	PATH=/bin:/usr/bin:/usr/local/bin; export PATH; (echo cont;
#	echo where) | gdb $daemon_directory/$process_name $process_id 2>&1
#	>$config_directory/$process_name.$process_id.log & sleep 5
#
# Another possibility is to run gdb under a detached screen session.
# To attach to the screen sesssion, su root and run "screen -r
# <id_string>" where <id_string> uniquely matches one of the detached
# sessions (from "screen -list").
#
# debugger_command =
#	PATH=/bin:/usr/bin:/sbin:/usr/sbin; export PATH; screen
#	-dmS $process_name gdb $daemon_directory/$process_name
#	$process_id & sleep 1
# INSTALL-TIME CONFIGURATION INFORMATION
#
# The following parameters are used when installing a new Postfix version.
# 
# sendmail_path: The full pathname of the Postfix sendmail command.
# This is the Sendmail-compatible mail posting interface.
# 
sendmail_path=/usr/sbin/sendmail
# newaliases_path: The full pathname of the Postfix newaliases command.
# This is the Sendmail-compatible command to build alias databases.
newaliases_path=/usr/bin/newaliases
# mailq_path: The full pathname of the Postfix mailq command.  This
# is the Sendmail-compatible mail queue listing command.
# 
mailq_path=/usr/bin/mailq
# setgid_group: The group for mail submission and queue management
# commands.  This must be a group name with a numerical group ID that
# is not shared with other accounts, not even with the Postfix account.
setgid_group=maildrop
# html_directory: The location of the Postfix HTML documentation.
html_directory=/usr/share/doc/packages/postfix-doc/html
# manpage_directory: The location of the Postfix on-line manual pages.
manpage_directory=/usr/share/man
# sample_directory: The location of the Postfix sample configuration files.
# This parameter is obsolete as of Postfix 2.1.
sample_directory=/usr/share/doc/packages/postfix-doc/samples
# readme_directory: The location of the Postfix README files.
readme_directory=/usr/share/doc/packages/postfix-doc/README_FILES
inet_protocols=all
biff=no
mydomain=machcoll.co.ls
myhostname=opensuse.$mydomain
mynetworks=127.0.0.0/8
smtpd_sasl_local_domain=
smtpd_sasl_auth_enable=yes
smtpd_sasl_security_options=noanonymous
broken_sasl_auth_clients=yes
smtpd_sasl_authenticated_header=yes
smtpd_recipient_restrictions=permit_sasl_authenticated,permit_mynetworks,check_relay_domains
alias_maps=hash:/etc/aliases
smtpd_tls_auth_only=no
smtp_use_tls=yes
smtpd_use_tls=yes
smtp_tls_note_starttls_offer=yes
smtpd_tls_key_file=/etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file=/etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile=/etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel=1
smtpd_tls_received_header=yes
smtpd_tls_session_cache_timeout=3600s
tls_random_source=dev:/dev/urandom
home_mailbox=Maildir/
mailbox_command=
mydestination=$myhostname, localhost.$mydomain, $mydomain
relayhost=196.202.240.148
```

Edit too long to send as a message so here's my main.cf

---

### Post by Sargalus on 2010-03-02
Cool I will check that out as soon as Im done re-setting up, I wiped ubuntu and went back to slackware 13 as ubunut was just too bloated, got tired of wanting to install one package and having to install 10000 others just to install that one or trying to remove one package and it saying it needs to remove 100packages you need so im going back to slackware and going to use it's default smtp/imap servers install squirrelmail and what nto and see how it works then. I will keep ya posted, thanks for all the help and support

---

### Post by Gone fishing on 2010-03-02
Well good luck - we did set this up(mail server postfix and squirrel mail) with Ubuntu but also used the box for nfs and ldap authentication and found that aspect a bit unstable. Subsequently changed to opensuse (more bloated) but its worked well and Yast might be a pain somethings but on others it makes thing easy.

I wonder how freeBSD would work?

---

### Post by Sargalus on 2010-03-02
I thought about trying out FreeBSD but I don't know crap about it, IMHO ubuntu makes a good desktop for a user whos using linux for a workstation other than that, I don't think it's that great and would rather go with a more reliable more stable distro like slackware.

---

