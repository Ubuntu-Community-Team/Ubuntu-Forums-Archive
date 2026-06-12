---
title: "curl( or wget) DNS requests not reading /etc/hosts file"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by thaniyarasu-gmail on 2015-04-20
[FONT=Arial]Hi All,[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]it seems like , curl DNS requests are performed based on the proxy dns server,  not /etc/hosts file[/FONT][FONT=Arial]even chrome browser also acting same as curl.

[/FONT]
[FONT=Arial]how to configure curl to use system /etc/hosts file  ?[/FONT]
[FONT=Arial]or [/FONT]
[FONT=Arial]how to configure curl to use /etc/hosts file for all "*.[myhost.com]("http://myhost.com/")" ?[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]i am using docker to create deployment instances(dev/test/prod) in my local system.[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]my env :=============
Ubuntu 14.10 64 bit

curl --version
curl 7.37.1 (x86_64-pc-linux-gnu) libcurl/7.37.1 OpenSSL/1.0.1f zlib/1.2.8 libidn/1.28 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp smtp smtps telnet tftp 
Features: AsynchDNS GSS-Negotiate IDN IPv6 Largefile NTLM NTLM_WB SSL libz TLS-SRP 


Google Chrome 42.0.2311.90



i am behind corporate proxy ([proxy.com:8080]("http://proxy.com:8080/")).
/etc/hosts content is


user@ubuntu:~$ cat /etc/hosts 

127.0.0.1 localhost
127.0.1.1 ubuntu
172.17.0.1 [dev.myhost.com]("http://dev.myhost.com/")
172.17.0.2 [test.myhost.com]("http://test.myhost.com/")
172.17.0.3 [myhost.com]("http://myhost.com/")


# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
============



when i ping "172.17.0.1, 172.17.0.2, 172.17.0.3, [dev.myhost.com]("http://dev.myhost.com/") ,etc" from terminal, then i got success.
but when i curl url (172.17.0.1 , 172.17.0.2,172.17.0.3, [dev.myhost.com]("http://dev.myhost.com/") ,etc) 
[/FONT]
[FONT=Arial]it always searching on proxy dns or somewhere else.[/FONT]
[FONT=Arial]curl is not reading my /etc/hosts file.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Any idea or help appreciated[/FONT]
[FONT=Arial]Thanks[/FONT]

---

### Post by The Cog on 2015-04-20
try adding the option ```
--noproxy '*'
``` and see if that fixed it.

or remove the proxy from the environment first:
```
proxy=
curl <blah>

```

---

### Post by thaniyarasu-gmail on 2015-04-20
Thanks for your help,

already i have defined no_proxy at /etc/environment file
user@ubuntu:~$ echo $no_proxy  
localhost,127.0.0.0/8,::1

but

user@ubuntu:~$ curl 127.0.0.1 --noproxy '*'   
is working fine

"127.0.0.0/8"  is not working 
did i miss anything ?

---

### Post by thaniyarasu-gmail on 2015-04-20
thank you for your help .
now i can able to curl 172.17.0.1

but chrome with url [http://172.17.0.1](http://172.17.0.1) is not working. 
still chrome searching on dns service. chrome is not reading /etc/hosts file .

---

### Post by The Cog on 2015-04-20
I think chrome always uses the "system settings" for the proxy, though I can't be sure as I don't have it installed. And I think it is desktop dependent too. Firefox is much better in that regard. However, there are proxy-changing extensions that you can get for chrome - I use one occasionally (forget which) on my work windows box.

---

