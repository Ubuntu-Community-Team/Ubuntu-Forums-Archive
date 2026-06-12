---
title: "http_proxy quirk"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by kyldere on 2006-08-03
Hello-

  I am behind a http proxy (and ftp, for that matter) in a corporate environment. I was able to reach the internet through one proxy (xxx.xxx.xxx.xx1:8080) when I set my machine up with Dapper, but that proxy has since been retired. I now am able to get to the internet (using FireFox) through a different proxy server (xxx.xxx.xxx.xx2:8080).
  Before I do an apt-get update, I usually export the second http_proxy, and I am able to complete updates. However, if I echo $http_proxy before exporting the new proxy server, the echo returns xxx.xxx.xxx.xx1:8080. So, I am lead to believe that this is stored somewhere in a conf file that I cannot seem to find.
  I have set the http proxy to xxx.xxx.xxx.xx2:8080 through the application launcher, and changed every setting that I could find to the second proxy. Please, could someone let me know where I can find where the original proxy server setting is stored that loads every time that I start a terminal? Thanks.

---

### Post by kyldere on 2006-09-26
Ok ... took me a while, but I have this figured out. While editing my .bashrc, I found that I had hard coded the proxy address. Changing these to the new address has resolved my problem. I am just posting here so that if anyone else has this problem, they can read about my solution.

---

