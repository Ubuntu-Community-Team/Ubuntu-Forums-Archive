---
title: "Apache2 won't start due to SSL cert not existing when it does"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by qwensdai on 2018-01-25
Hi everyone,

I've been running a file server using owncloud for a while and it was working swimmingly. Then I stopped using the server for a while and today I found I can no longer connect to the server. After looking into it (by connecting to it through ssh) I found out that Apache2 wasn't running and when I tried to start apache I got this error
"AH00526: Syntax error on line 35 of /etc/apache2/sites-enabled/default-ssl.conf:
SSLCertificateKeyFile: file '/etc/ssl/private/apache-seflsigned.key' does not exist or is empty"
When I looked in the specified directory I found that the cert DID exist and it wasn't empty (no surprise to me as I hadn't changed anything since I last connected) I did some searching online and have found basically bumpkiss. I did try changing permissions to see if that was the issue but even when i gave the folder 777 it didn't work. Has anyone else had an issue similar to this and any suggestions?

OS: Ubuntu 14.04.4 LTS (GNU/Linux 4.2.0-42-generic x86_64)

Thanks in advance!

EDIT: Just realised this is in the wrong forum. Could a mod lock it?

---

### Post by wildmanne39 on 2018-01-25
Closed as requested! In the future please use the report button in the lower left hand corner of your post to communicate with the staff and please do not create a new thread just ask and we can move it for you.

Thanks

---

