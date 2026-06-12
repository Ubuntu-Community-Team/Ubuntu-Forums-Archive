---
title: "Getting Gmail SSL Working in Outlook 2003"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by zonerover on 2010-03-30
I've tried to use many of the open solutions in Ubuntu to handle my  email, calendar, tasks etc., but unfortunately given that I'm tied to  Outlook, there's no good way to sync all my data from it to any other  program. So I ended up getting Crossover and am trying to get Outlook  2003 to work with Gmail's SSL.

In short I've set up Stunnel and have set the right ports in Outlook.  When I send receive, I am not able to send or receive my email. Here are the instructions I followed for setting up Stunnel from a post  on codeweavers.com. The only bit I changed is the bit for connecting to IMAP in which I substituted for a POP connection.

> 1. Setup your Gmail Imap account in Outlook 2003 following  instructions  from this link: [http://mail.google.com/support/bin/answer.py?hl=en&answer=77661](http://mail.google.com/support/bin/answer.py?hl=en&answer=77661)   pr 220
2. However, in step 6, for "Server Information", enter 127.0.0.1 for   both IMAP and SMTP. 
3. Also for steps 9 and 10, More Settings - Advanced tab, do not check   "This server requires an encrypted connection (SSL)" for either IMAP or   SMTP.  In other words, use the default ports of 143 and 25,   respectively. 
4. Get stunnel: sudo apt-get install stunnel4 (or use synaptic package   manager) 
5. Go to the installed folder: $ cd /etc/stunnel 
6. create ssl certificate using: $ openssl req -new -x509 -days 3650   -nodes -out stunnel.pem -keyout stunnel.pem 
7. enter requested info which will create a stunnel.pem file in the   directory. 
8. Change permissions (not sure if needed, but read this somewhere): $   sudo chmod 600 /etc/stunnel/stunnel.pem 
9. Edit config file: $ sudo gedit /etc/stunnel/stunnel.conf 
10. Make sure to edit (uncomment) the following lines: 
    
cert = /etc/stunnel/stunnel.pem
debug = 7
output = /stunnel.log
client = yes
[pop3s]
accept = 127.0.0.1:110
connect = pop.gmail.com:995
[imaps]
accept = 127.0.0.1:143
connect = imap.gmail.com:993
[ssmtp]
accept = 127.0.0.1:25
connect = smtp.gmail.com:465
 
11. Run stunnel: $ sudo stunnel4 
12. If you send/receive with your new imap account in outlook 2003, it   should work fine (no error messages about unable to connect to servers).    If problems, you can test by: $ telnet 127.0.0.1 25 and $ telnet   127.0.0.1 143.  Telnet should be able to connect to gmail through   stunnel.And here is my stunnel.conf file...

> ; Sample stunnel configuration file by Michal Trojnara 2002-2009
; Some options used here may not be adequate for your particular  configuratipr 220on
; Please make sure you understand them (especially the effect of the  chroot jail)

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/stunnel/stunnel.pem
;key = /etc/ssl/certs/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on  Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside the chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = zlib

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[pop3s]
accept  = 127.0.0.1:11010
connect = pop.gmail.com:995

[imaps]
accept  = 127.0.0.1:143
connect = imap.gmail.com:993

[ssmtp]
accept  = 127.0.0.1:25
connect = smtp.gmail.com:465

;[https]
;accept  = 443
;connect = 80
;TIMEOUTclose = 0

; vim:ft=dosiniAlso the error message I'm getting for not receiving mail is 0x8004210A - The operation timed out waiting for a response from the receiving (POP) server. For not sending the mail, I'm getting 0x8004210B - The operation timed out waiting for a response from the receiving  (SMTP) server.

So can anyone explain if I'm doing anything  wrong?

---

### Post by zonerover on 2010-04-02
Still got the problem. Does anyone have any idea?

---

### Post by Jonners59 on 2011-05-17
> **zonerover said:**
> I've tried to use many of the open solutions in Ubuntu to handle my  email, calendar, tasks etc., but unfortunately given that I'm tied to  Outlook, there's no good way to sync all my data from it to any other  program. So I ended up getting Crossover and am trying to get Outlook  2003 to work with Gmail's SSL.

In short I've set up Stunnel and have set the right ports in Outlook.  When I send receive, I am not able to send or receive my email. Here are the instructions I followed for setting up Stunnel from a post  on codeweavers.com. The only bit I changed is the bit for connecting to IMAP in which I substituted for a POP connection.

And here is my stunnel.conf file...

Also the error message I'm getting for not receiving mail is 0x8004210A - The operation timed out waiting for a response from the receiving (POP) server. For not sending the mail, I'm getting 0x8004210B - The operation timed out waiting for a response from the receiving  (SMTP) server.

So can anyone explain if I'm doing anything  wrong?

Beautifully written up....  I have been trying Stunnel for the past year, buy that I mean trying to get it going.  Never have.  Not sure it actually works.  Did you eventually get it going?

---

