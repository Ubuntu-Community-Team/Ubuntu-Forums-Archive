---
title: "Postfix/Dovecot install:"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by owemeacent on 2014-05-10
I've been trying to install a mailserver. I've tried a billion times and this is the closest time for me being succesful. My mail server name is "bone", while my client computers name is ShadyNet, and both users on them are omar, I've installed both postfix and dovecot. Here's my postfix/main.cf```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version




# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = yourdomain.com
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_security_options = noanonymous
readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = bone
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = bone, bone.bone, localhost.bone, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all






```

And here's my dovecot.conf

```

## Dovecot configuration file


# If you're in a hurry, see http://wiki2.dovecot.org/QuickConfiguration


# "doveconf -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting files when posting to the Dovecot mailing list.


# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "
protocols = pop3 imap
# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var
auth default2 {
mechanisms = plain login
passdb pam {
}
userdb passwd {
}
socket listen {
client {
path = /var/spool/postfix/private/auth
mode = 0660
user = postfix
group = postfix
}


}


}
# A comma separated list of IPs or hosts where to listen in for connections.
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
#listen = *, ::


# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/


# Name of this instance. In multi-instance setup doveadm and other commands
# can use -i <instance_name> to select which instance is used (an alternative
# to -c <config_path>). The instance name is also added to Dovecot processes
# in ps output.
#instance_name = dovecot


# Greeting message for clients.
#login_greeting = Dovecot ready.


# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =


# Sepace separated list of login access check sockets (e.g. tcpwrap)
#login_access_sockets =


# With proxy_maybe=yes if proxy destination matches any of these IPs, don't do
# proxying. This isn't necessary normally, but may be useful if the destination
# IP is e.g. a load balancer's IP.
#auth_proxy_self =


# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no


# Should all processes be killed when Dovecot master process shuts down.
# Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is e.g. because of a security fix).
#shutdown_clients = yes


# If non-zero, run mail commands via this many connections to doveadm server,
# instead of running them directly in the same process.
#doveadm_worker_count = 0
# UNIX socket or host:port used for connecting to doveadm server
#doveadm_socket_path = doveadm-server


# Space separated list of environment variables that are preserved on Dovecot
# startup and passed down to all of its child processes. You can also give
# key=value pairs to always set specific settings.
#import_environment = TZ


##
## Dictionary server settings
##


# Dictionary can be used to store key=value lists. This is used by several
# plugins. The dictionary can be accessed either directly or though a
# dictionary server. The following dict block maps dictionary names to URIs
# when the server is used. These can then be referenced using URIs in format
# "proxy::<name>".


dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-sql.conf.ext
  #expire = sqlite:/etc/dovecot/dovecot-dict-sql.conf.ext
}
# Most of the actual configuration gets included below. The filenames are
# first sorted by their ASCII value and parsed in that order. The 00-prefixes
# in filenames are intended to make it easier to understand the ordering.
!include conf.d/*.conf


# A config file can also tried to be included without giving an error if
# it's not found:
!include_try local.conf




```

and when I do ```
sendmail omar@ShadyNet
```, it doesn't send back an error, but when I ```
fetchmail bone
``` it gives back this

```
omar ~ $ fetchmail boneEnter password for omar@bone: 
fetchmail: Server certificate verification error: self signed certificate
fetchmail: Missing trust anchor certificate: /O=Dovecot mail server/OU=bone.bone/CN=bone.bone/emailAddress=root@bone.bone
fetchmail: This could mean that the root CA's signing certificate is not in the trusted CA certificate location, or that c_rehash needs to be run on the certificate directory. For details, please see the documentation of --sslcertpath and --sslcertfile in the manual page.
fetchmail: Warning: the connection is insecure, continuing anyways. (Better use --sslcertck!)
4 messages for omar at bone.
fetchmail: Connection errors for this poll:
name 0: connection to localhost:smtp [::1/25] failed: Connection refused.
name 1: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
fetchmail: SMTP connect to localhost failed
fetchmail: SMTP transaction error while fetching from omar@bone and delivering to SMTP host localhost
reading message omar@bone:1 of 4 (422 header octets)fetchmail: Query status=10 (SMTP)



```

I guess I have some ports that I need to open up or something. Or is there something else I forgot to do? Any help is greatly appreciated


PS: I also found this in my omar@bone mailbox

```

Message 2:
From MAILER-DAEMON  Sat May 10 09:56:57 2014
X-Original-To: root@bone
Date: Sat, 10 May 2014 09:56:57 -0700 (PDT)
From: MAILER-DAEMON@bone (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: root@bone
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="A186EE07E5.1399741017/bone"


This is a MIME-encapsulated message.


--A186EE07E5.1399741017/bone
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii


This is the mail system at host bone.


I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.


For further assistance, please send mail to postmaster.


If you do so, please include this problem report. You can
delete your own text from the attached returned message.


                   The mail system


<omar@ServShady>: Host or domain name not found. Name service error for
    name=ServShady type=AAAA: Host not found


--A186EE07E5.1399741017/bone
Content-Description: Delivery report
Content-Type: message/delivery-status


Reporting-MTA: dns; bone
X-Postfix-Queue-ID: A186EE07E5
X-Postfix-Sender: rfc822; root@bone
Arrival-Date: Sat, 10 May 2014 09:56:44 -0700 (PDT)


Final-Recipient: rfc822; omar@ServShady
Action: failed
Status: 5.4.4
Diagnostic-Code: X-Postfix; Host or domain name not found. Name service error
    for name=ServShady type=AAAA: Host not found


--A186EE07E5.1399741017/bone
Content-Description: Undelivered Message
Content-Type: message/rfc822


Return-Path: <root@bone>
Received: by bone (Postfix, from userid 0)
        id A186EE07E5; Sat, 10 May 2014 09:56:56 -0700 (PDT)
Message-Id: <20140510165656.A186EE07E5@bone>
Date: Sat, 10 May 2014 09:56:44 -0700 (PDT)
From: root@bone (root)


Hi
This is supposed to work


--A186EE07E5.1399741017/bone--

```
This means that the server cannot detect my client computer, but I can ping it from my server just fine

---

### Post by spynappels on 2014-05-11
You may get more answers posting this in the Servers forum.

The error does not appear to be ports related specifically, as the problem is that fetchmail cannot connect to the smtp daemon, even over localhost. You need to ensure smtp is actually running, and that it is configured to accept connections from localhost.

---

