---
title: "Ubuntu Firefox works with direct connection, not with ssh proxy"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Roy G Biv on 2006-11-12
Hello,
Firefox 2 works fine under Ubuntu 6.10 using "direct connection to the Internet," but if I change it to "manual proxy configuration," using 127.0.0.1, port 80 as the proxy for all protocals, and enter an URL, the status bar of Firefox shows "Done" within a few seconds and the browser window, itself, is blank. I use ssh and use it correctly, as far as I know, to connect to an anonymizing proxy.Code:
```
ssh -2 -v -L 80:cyberpass.net:80 cyberpass.net -l roygbiv
```
After entering my password, my bash shell announces a successful connection with cyberpass.net and netstat announces:

```
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:52547         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:110           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:80            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.2:34486       168.143.113.118:22      ESTABLISHED
tcp6       0      0 ::1:110                 :::*                    LISTEN     
tcp6       0      0 ::1:80                  :::*                    LISTEN     
tcp6       0      0 ::1:25                  :::*                    LISTEN     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          

```
Everything seems to work fine, except for the browser, itself. I had no problems with Ubuntu 5 or 6.06. Any ideas?
-Roy

---

