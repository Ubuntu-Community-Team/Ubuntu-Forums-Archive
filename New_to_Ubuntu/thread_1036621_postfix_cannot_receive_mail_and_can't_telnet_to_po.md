---
title: "postfix cannot receive mail and can't telnet to port 25"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by EnterTheDarkSide on 2009-01-11
hi,

i installed postfix and was able to send and receive email within my network. i was also able to send email out to my gmail account but was unable to receive mail from it. I also tried doing
```
telnet mydomain.com 25
```
and go the following message:
```
Connection closed by foreign host.
```

does that mean my isp has blocked port 25? are there anything i should change in my postfix configuration?

---

### Post by Crafty Kisses on 2009-01-11
What are the results of this command?
```
netstat -tap
```
I'd also like to see if you manually restart Postfix if that does anything:
```
/etc/init.d/postfix restart
```
If you've restarted it and it's still not letting you telnet to that port, go into Terminal and type the following, remember post the results back here:
```
hostname
```
Then one more output I'd like to see:
```
hostname -f
```

---

### Post by EnterTheDarkSide on 2009-01-11
> **Codename said:**
> What are the results of this command?
```
netstat -tap
```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:www                   *:*                     LISTEN      -               
tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
tcp        0      0 localhost:postgresql    *:*                     LISTEN      -               
tcp        0      0 *:smtp                  *:*                     LISTEN      -               
tcp        0      0 yongsLinux.local:56087  222.186.13.104:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:52233  by1msg3275908.phx.:msnp ESTABLISHED 6099/pidgin     
tcp        0      0 yongsLinux.local:59481  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:36058  by2msg2263501.phx.:msnp TIME_WAIT   -               
tcp        0      0 yongsLinux.local:56092  222.186.13.104:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:56093  222.186.13.104:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:47664  222.173.188.35:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:40381  by1msg3082105.phx.:msnp ESTABLISHED 6099/pidgin     
tcp        1      0 yongsLinux.local:43148  s05.cache.bj1.aliyk:www CLOSE_WAIT  13153/npviewer.bin
tcp        0      0 yongsLinux.local:59478  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:56086  222.186.13.104:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:51569  p3.mm.vip.cnz.alima:www TIME_WAIT   -               
tcp        0      0 yongsLinux.local:51570  p3.mm.vip.cnz.alima:www TIME_WAIT   -               
tcp        0      0 yongsLinux.local:59483  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        1      0 yongsLinux.local:38512  feijoa.canonical.co:www CLOSE_WAIT  13153/npviewer.bin
tcp        1      0 yongsLinux.local:38393  p3.mm.vip.cnz.alima:www CLOSE_WAIT  13153/npviewer.bin
tcp        0      0 yongsLinux.local:50159  by2msg1231703.phx.:msnp ESTABLISHED 6099/pidgin     
tcp        0      0 yongsLinux.local:49274  feijoa.canonical.co:www TIME_WAIT   -               
tcp        0      0 yongsLinux.local:59479  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        1      0 yongsLinux.local:43135  s05.cache.bj1.aliyk:www CLOSE_WAIT  13153/npviewer.bin
tcp        0      0 yongsLinux.local:59480  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:56085  222.186.13.104:www      ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:36032  122.224.194.194:www     ESTABLISHED 6123/firefox    
tcp        0      0 yongsLinux.local:59482  ip073006.hkicable.c:www ESTABLISHED 6123/firefox    
tcp        1      0 yongsLinux.local:57229  s11.cache.cn3.yahoo:www CLOSE_WAIT  13153/npviewer.bin
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      -               
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      -               
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -               
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      -        

I'd also like to see if you manually restart Postfix if that does anything:
```
/etc/init.d/postfix restart
```

 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 

If you've restarted it and it's still not letting you telnet to that port, go into Terminal and type the following, remember post the results back here:
```
hostname
```
Then one more output I'd like to see:
```
hostname -f
```

hostname gave me: yongsLinux.

i can telnet into port 25 of my pc, but i cant telnet to port 25 of my domain (i'm behind a router). thanks for the reply.

---

