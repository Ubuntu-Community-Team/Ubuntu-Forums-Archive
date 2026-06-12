---
title: "SSH setup with easydns fails"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by studiologe2 on 2014-04-15
Hi, I just signed up for easydns and I'm trying to set up my box to be a ssh-server, so I can access my home network from anywhere.
I'm using ddclient to update my IP with easyDNS.com and I'm getting my IP via checkip.dyndns.com because I'm not sure if easyDNS has a service for that...... Please somebody take a quick look at the following output and tell me what my errors are! THX

here is the (forum-safe) output from command ddclient -daemon=0 -debug -verbose -noquiet
```

# ddclient -daemon=0 -debug -verbose -noquiet
=== opt ====
opt{cache}                           : <undefined>
opt{cmd}                             : <undefined>
opt{cmd-skip}                        : <undefined>
opt{daemon}                          : 0
opt{debug}                           : 1
opt{exec}                            : <undefined>
opt{facility}                        : <undefined>
opt{file}                            : <undefined>
opt{force}                           : <undefined>
opt{fw}                              : <undefined>
opt{fw-login}                        : <undefined>
opt{fw-password}                     : <undefined>
opt{fw-skip}                         : <undefined>
opt{geturl}                          : <undefined>
opt{help}                            : <undefined>
opt{host}                            : <undefined>
opt{if}                              : <undefined>
opt{if-skip}                         : <undefined>
opt{ip}                              : <undefined>
opt{login}                           : <undefined>
opt{mail}                            : <undefined>
opt{mail-failure}                    : <undefined>
opt{max-interval}                    : 2592000
opt{min-error-interval}              : 300
opt{min-interval}                    : 30
opt{options}                         : <undefined>
opt{password}                        : <undefined>
opt{pid}                             : <undefined>
opt{postscript}                      : <undefined>
opt{priority}                        : <undefined>
opt{protocol}                        : <undefined>
opt{proxy}                           : <undefined>
opt{query}                           : <undefined>
opt{quiet}                           : 0
opt{retry}                           : <undefined>
opt{server}                          : <undefined>
opt{ssl}                             : <undefined>
opt{syslog}                          : <undefined>
opt{test}                            : <undefined>
opt{timeout}                         : <undefined>
opt{use}                             : <undefined>
opt{verbose}                         : 1
opt{web}                             : <undefined>
opt{web-skip}                        : <undefined>
=== globals ====
globals{daemon}                      : 60
globals{debug}                       : 1
globals{login}                       : "MyLogin"
globals{password}                    : "MyPassword"
globals{pid}                         : /var/run/ddclient.pid
globals{protocol}                    : easydns
globals{quiet}                       : 0
globals{server}                      : members.easydns.com
globals{ssl}                         : 1
globals{use}                         : web
globals{verbose}                     : 1
globals{web}                         : checkip.dyndns.com/
globals{web-skip}                    : IP Address
=== config ====
config{http://www."MyDomain.org"/}{atime} : 0
config{http://www."MyDomain.org"/}{backupmx} : 0
config{http://www."MyDomain.org"/}{cacheable} : ARRAY(0x90c4a44)
config{http://www."MyDomain.org"/}{cmd} : <undefined>
config{http://www."MyDomain.org"/}{cmd-skip} : 
config{http://www."MyDomain.org"/}{fw} : 
config{http://www."MyDomain.org"/}{fw-login} : <undefined>
config{http://www."MyDomain.org"/}{fw-password} : 
config{http://www."MyDomain.org"/}{fw-skip} : 
config{http://www."MyDomain.org"/}{host} : http://www."MyDomain.org"/
config{http://www."MyDomain.org"/}{if} : ppp0
config{http://www."MyDomain.org"/}{if-skip} : 
config{http://www."MyDomain.org"/}{ip} : <undefined>
config{http://www."MyDomain.org"/}{login} : "MyLogin"
config{http://www."MyDomain.org"/}{max-interval} : 2592000
config{http://www."MyDomain.org"/}{min-error-interval} : 300
config{http://www."MyDomain.org"/}{min-interval} : 300
config{http://www."MyDomain.org"/}{mtime} : 0
config{http://www."MyDomain.org"/}{mx} : 
config{http://www."MyDomain.org"/}{password} : "MyPassword"
config{http://www."MyDomain.org"/}{protocol} : easydns
config{http://www."MyDomain.org"/}{server} : members.easydns.com
config{http://www."MyDomain.org"/}{status} : 
config{http://www."MyDomain.org"/}{use} : web
config{http://www."MyDomain.org"/}{warned-min-error-interval} : 0
config{http://www."MyDomain.org"/}{warned-min-interval} : 0
config{http://www."MyDomain.org"/}{web} : checkip.dyndns.com/
config{http://www."MyDomain.org"/}{web-skip} : IP Address
config{http://www."MyDomain.org"/}{wildcard} : 0
config{http://www."MyDomain.org"/}{wtime} : 30
=== cache ====
cache{http://www."MyDomain.org"/}{atime} : 0
cache{http://www."MyDomain.org"/}{backupmx} : 0
cache{http://www."MyDomain.org"/}{host} : http://www."MyDomain.org"/
cache{http://www."MyDomain.org"/}{mtime} : 0
cache{http://www."MyDomain.org"/}{mx} : 
cache{http://www."MyDomain.org"/}{status} : noconnect
cache{http://www."MyDomain.org"/}{warned-min-error-interval} : 1397554568
cache{http://www."MyDomain.org"/}{warned-min-interval} : 0
cache{http://www."MyDomain.org"/}{wildcard} : 0
cache{http://www."MyDomain.org"/}{wtime} : 30
DEBUG:    proxy  = 
DEBUG:    url    = checkip.dyndns.com/
DEBUG:    server = checkip.dyndns.com
CONNECT:  checkip.dyndns.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.com
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Content-Type: text/html
RECEIVE:  Server: DynDNS-CheckIP/1.0
RECEIVE:  Connection: close
RECEIVE:  Cache-Control: no-cache
RECEIVE:  Pragma: no-cache
RECEIVE:  Content-Length: 106
RECEIVE:  
RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: 49.182.243.101</body></html>
DEBUG:    get_ip: using web, checkip.dyndns.com/ reports 49.182.243.101
DEBUG:    
DEBUG:     nic_easydns_update -------------------
INFO:     setting IP address to 49.182.243.101 for http://www."MyDomain.org"/
UPDATE:   updating http://www."MyDomain.org"/
DEBUG:    proxy  = 
DEBUG:    url    = http://members.easydns.com/dyn/dyndns.php?hostname=http://www."MyDomain.org"/&myip=49.182.243.101&wildcard=OFF
DEBUG:    server = members.easydns.com
CONNECT:  members.easydns.com
CONNECTED:  using SSL
SENDING:  GET /dyn/dyndns.php?hostname=http://www."MyDomain.org"/&myip=49.182.243.101&wildcard=OFF HTTP/1.0
SENDING:   Host: members.easydns.com
SENDING:   Authorization: Basic dhdsbybyibyjibberJABBERjibberJABBERYEPYEP
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 401 Unauthorized
RECEIVE:  Date: Tue, 15 Apr 2014 18:22:33 GMT
RECEIVE:  Server: Apache
RECEIVE:  WWW-authenticate: basic realm="easyDNS Member Access"
RECEIVE:  Vary: Accept-Encoding
RECEIVE:  Content-Length: 927
RECEIVE:  Connection: close
RECEIVE:  Content-Type: text/html
RECEIVE:  
RECEIVE:  <HTML>
RECEIVE:  <HEAD>
RECEIVE:  <TITLE>Lost Password?</TITLE>
RECEIVE:  <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
RECEIVE:  <link href="http://support.easydns.com/easydns.css" rel="stylesheet" type="text/css">
RECEIVE:  <SCRIPT LANGUAGE="Javascript1.1">
RECEIVE:  <!--
RECEIVE:  function quickHelp(which) {
RECEIVE:       file = 'http://support.easydns.com/quick-help.php3?' + which;
RECEIVE:       NewWin = window.open(file,'NewWin','toolbar=0,location=0,directories=0,status=0,menubar=0,scrollbars=1,resizable=1,width=500,height=250');
RECEIVE:  }
RECEIVE:  // -->
RECEIVE:  </SCRIPT>
RECEIVE:  
RECEIVE:  <link href="http://www.easydns.com/easydns.css" rel="stylesheet" type="text/css">
RECEIVE:  
RECEIVE:  </HEAD>
RECEIVE:  <BODY BGCOLOR=#FFFFFF TOPMARGIN=0 MARGINWIDTH=0 MARGINHEIGHT=0>
RECEIVE:  <P><B>IMPORTANT NOTICE:</B> For security reasons the lost password utility on the old members interface has been disabled. If you need to recover your old members interface password please <a href="https://web.easydns.com/contactus.php">contact our support team</a>.</P>
FAILED:   updating http://www."MyDomain.org"/: authorization failed (HTTP/1.1 401 Unauthorized
FAILED:    Date: Tue, 15 Apr 2014 18:22:33 GMT
FAILED:    Server: Apache
FAILED:    WWW-authenticate: basic realm="easyDNS Member Access"
FAILED:    Vary: Accept-Encoding
FAILED:    Content-Length: 927
FAILED:    Connection: close
FAILED:    Content-Type: text/html
FAILED:    
FAILED:    <HTML>
FAILED:    <HEAD>
FAILED:    <TITLE>Lost Password?</TITLE>
FAILED:    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
FAILED:    <link href="http://support.easydns.com/easydns.css" rel="stylesheet" type="text/css">
FAILED:    <SCRIPT LANGUAGE="Javascript1.1">
FAILED:    <!--
FAILED:    function quickHelp(which) {
FAILED:         file = 'http://support.easydns.com/quick-help.php3?' + which;
FAILED:         NewWin = window.open(file,'NewWin','toolbar=0,location=0,directories=0,status=0,menubar=0,scrollbars=1,resizable=1,width=500,height=250');
FAILED:    }
FAILED:    // -->
FAILED:    </SCRIPT>
FAILED:    
FAILED:    <link href="http://www.easydns.com/easydns.css" rel="stylesheet" type="text/css">
FAILED:    
FAILED:    </HEAD>
FAILED:    <BODY BGCOLOR=#FFFFFF TOPMARGIN=0 MARGINWIDTH=0 MARGINHEIGHT=0>
FAILED:    <P><B>IMPORTANT NOTICE:</B> For security reasons the lost password utility on the old members interface has been disabled. If you need to recover your old members interface password please <a href="https://web.easydns.com/contactus.php">contact our support team</a>.</P>
FAILED:    )

```


This is my (forum-safe) ssh_config
```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
    AllowGroups ssh_users
    PermitRootLogin no

```


And of course my (forum-safe) ddclient.conf
```

# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf
#
# Check the current IP address. Either check the eth0 port for its current IP address (can't be used on a LAN),
# or use the DynDNS IP checking service.
# Note: if this doesn't work, try changing web-skip to 'Current Address'

daemon=3600
pid=/var/run/ddclient.pid

protocol=easydns
ssl=yes
#use=if, if=eth0
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
#use=web, web=checkip.dyndns.com/, web-skip='Current Address'
server=members.easydns.com
login="MyLogin"
password='MyPassword'
http://www."MyDomain".org/

```

Can somebody explain to me, why this is failing? Or if I'm forgetting something??

---

### Post by ted_smith2 on 2014-04-15
Hello,  this is Ted from easyDNS support.  
If you would please provide me with the host name you are trying to update I'll look at the logs to see what is happening when you try to update.  The best way to do that would be to send an email to [email]support@easydns.com[/email] with attention Ted in the subject line, since you clearly don't want to post that here.  I don't see any obvious problems in what you have included above, but it can be hard to tell with things generalised to "mydomain" kinds of values instead of the specifics.  It will help a lot for me to look at the details of the update request being sent.
Thank you
Ted
easyDNS Support

---

### Post by studiologe2 on 2014-04-15
Hey Ted,
thanks for the reply! I'm glad to hear that the config so far seems to be good and free of error.
I sent you an email a little while ago and hope the info included is helpful in finding what the issue is.

Again thank you very much for your help!

---

### Post by studiologe2 on 2014-04-16
I'm still not able to remotely connect to my box via SSH.
Anything, anyone?
Ted, did you look into the logs?

---

### Post by Antony_Nikrooz on 2014-04-17
If you do an nslookup yourdomain.org, what do you get? Is it the correct external IP?
Is your ubuntu machine behind a home router (NATed - your IP address will likely be an internal, 192.168.x.x one)? If so, you'll need to log onto your router and forward port 22 to the correct internal address.

---

