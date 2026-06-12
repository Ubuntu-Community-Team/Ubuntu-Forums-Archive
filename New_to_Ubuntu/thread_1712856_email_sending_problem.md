---
title: "email sending problem"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by vasan.85 on 2011-03-23
dear friends,

 i try to install  the mail transfer agent called postfix.i thought i successfully  installed in our server.but i am not able to send email.currently i  am using ubuntu natty version.


vasan@ProLiant-ML370-G3:~$ telnet localhost 25
[B][COLOR=#333333]Trying ::1...[/COLOR]
[COLOR=#333333]Connected to ProLiant-ML370-G3.[/COLOR]
 [COLOR=#333333]Escape character is '^]'.[/COLOR]
[COLOR=#333333]220 [info.thenetworkjob.com]("http://info.thenetworkjob.com/") ESMTP Postfix (Ubuntu)[/COLOR]
 [COLOR=#333333]ehlo [info.thenetworkjob.com]("http://info.thenetworkjob.com/")[/COLOR]
[COLOR=#333333][250-info.thenetworkjob.com]("http://250-info.thenetworkjob.com/")[/COLOR]
 [COLOR=#333333]250-PIPELINING[/COLOR]
[COLOR=#333333]250-SIZE 10240000[/COLOR]
[COLOR=#333333]250-VRFY[/COLOR]
 [COLOR=#333333]250-ETRN[/COLOR]
[COLOR=#333333]250-STARTTLS[/COLOR]
[COLOR=#333333]250-AUTH NTLM DIGEST-MD5 LOGIN PLAIN CRAM-MD5[/COLOR]
 [COLOR=#333333]250-AUTH=NTLM DIGEST-MD5 LOGIN PLAIN CRAM-MD5[/COLOR]
[COLOR=#333333]250-ENHANCEDSTATUSCODES[/COLOR]
 [COLOR=#333333]250-8BITMIME[/COLOR]
[COLOR=#333333]250 DSN[/COLOR][COLOR=#333333][/COLOR][COLOR=#333333][/COLOR]
 [COLOR=#333333]quit[/COLOR]
[COLOR=#333333]221 2.0.0 Bye[/COLOR]
[COLOR=#333333]Connection closed by foreign host.[/COLOR][/B]




   plz any one guide me to fix the issue.

                                        Advance thanks

---

### Post by cariboo on 2011-03-23
have you check to see if your isp is blocking port 25? Go to [canyouseeme]("http://www.canyouseeme.org/") to check.

---

