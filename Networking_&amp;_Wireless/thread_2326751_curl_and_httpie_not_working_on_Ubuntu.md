---
title: "curl and httpie not working on Ubuntu"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by alfredo12 on 2016-06-04
Hello,

I'm having a problem that I can't figure out.

Objective: I'm trying to upload a file using curl through a form POST. 
Problem: curl command is working fine on windows version but not on ubuntu. I tried with httpie on ubuntu and I got the same behaviour. The problem is that the command in Linux is never ending. I got a timeout after long long time. In windows is just working fine.
Where I tried: I tried with Ubuntu 12, 14 and raspbian wheezy. I have always the same problem. The command gets stuck after the HTTP/1.1 100 Continue message.
Where it works: The same command works fine on Windows 7!!!

Example in Linux :
```

curl -i -X POST -F file=@cat.jpg https://upload.pushbullet.com/upload-legacy/B5kt9mYS2KPQIIru8mLJ9AfuVvcFOeOT
HTTP/1.1 100 Continue
``` It get stuck here if the file is bigger than 2 KB.

Example in Windows (expected result is retrieved):
```
curl -i -X POST -F "file=@c:\cat.jpg" https://upload.pushbullet.com/upload-legacy/B5kt9mYS2KPQIIru8mLJ9AfuVvcFOeOT

HTTP/2 400
x-ratelimit-reset: 1465034946
content-type: application/json; charset=utf-8
x-ratelimit-limit: 16384
x-ratelimit-remaining: 16380
vary: Accept-Encoding
date: Sat, 04 Jun 2016 09:53:27 GMT
server: Google Frontend
cache-control: private
alt-svc: quic=":443"; ma=2592000; v="34,33,32,31,30,29,28,27,26,25"
accept-ranges: none


{"error":{"code":"invalid_request","type":"invalid_request","message":"That upload request does not exist.","cat":"&#960;àç&#960;àà&#960;àç"},"error_code":"invalid_request"}

```

I'm using the same curl version.
I guess that the problem is not with curl because I have the same behaviour with httpie. And in windows I tried with two tools and it is working for both. Because of this, I asume that the problem is somewhere else.

BTW, everything is workin fine with really small files. (100 bytes)

Can anyone help me?
Thanks!

---

### Post by Hadaka on 2016-06-04
Hi, To begin,I am not a curl expert, i have some script files i use for stock quotes.
here is a link..its about stock quotes and there is also a scrip file you can look at
for possible ideas.
[https://davidwalsh.name/stock-quotes-command-line](https://davidwalsh.name/stock-quotes-command-line)
try this in terminal..notice the single quote around the url
this is a working valid command, and gets the correct data..
```
 curl -s 'http://download.finance.yahoo.com/d/quotes.csv?s=AAPL&f=l1' 
```
it should return a value of..97.92
hope this gives you some ideas.
good luck

---

### Post by alfredo12 on 2016-06-05
> **Hadaka said:**
> 
try this in terminal..
```
 curl -s 'http://download.finance.yahoo.com/d/quotes.csv?s=AAPL&f=l1' 
```
it should return a value of..97.92


curl is working almost everywhere. With the exception of the POST method when sending files bigger than 1KB.
curl -X POST -F file=@test.jpg <serverurl>

I don't know what else to try. Of course that the problem could be on the server side ([COLOR=#000000][FONT=Ubuntu Mono]upload.pushbullet.com[/FONT][/COLOR]) but then my question is why it is working on Windows?!?!? cURL is sending the same headers in Linux and Windows so why it is working on Windows?

Thanks,
Alfredo.

---

### Post by alfredo12 on 2016-06-06
Hello,


Problem solved!!!
After doing a lot of tests I discovered that the problem was on the router. For some reason the server is trying to stablish a connection to the client or something like this. That's very strange for a POST but I noticed that If I set the DMZ to the client's IP then everything is working.
I still don't know why this is working on windows....
I discovered this when I run the Linux on a Window's virtual machine. Then it was working.... because it was using the Windows NW adaptor.


Anyway, it is working now...


Thanks,

---

