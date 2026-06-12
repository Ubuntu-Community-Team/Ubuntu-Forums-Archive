---
title: "How to connect via FTPS - FTP over SSL/TLS"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Ted_Smith on 2007-06-15
I am trying to connect to an FTP server that uses Filezilla Server which itself uses FTPS which is FTP over SSL/TLS. But gFTP does not have any of it, even on port 990. I know my router is OK because I can connect fine using FileZilla from my Windows laptop. 

Anyone know how to connect to such a server from Linux under those circumstances?

Cheers

Ted

---

### Post by morningboat on 2007-06-16
[LIST]
[*]CrossFTP ([http://www.crossftp.com/](http://www.crossftp.com/)) GUI multi-tab FTP client for reliable transfers.
[*]lftp ([http://lftp.yar.ru/desc.html](http://lftp.yar.ru/desc.html)) "LFTP is sophisticated file transfer program with command line interface.
[*]TLSWrap ([http://freshmeat.net/projects/tlswrap/](http://freshmeat.net/projects/tlswrap/)) "TLSWrap is a TLS/SSL FTP wrapper/proxy for UNIX (including Linux, *BSD, and Solaris) and Windows, allowing you to use your favourite FTP client with any TLS/SSL-enabled FTP server.
[*]ftp-ssl ([http://packages.debian.org/stable/net/ftp-ssl](http://packages.debian.org/stable/net/ftp-ssl)) which is a SSL wraparound for the normal ftp client.
[/LIST]
I like GUI style of CrossFTP, and lftp is a good command line tool.

---

### Post by Ted_Smith on 2007-06-21
Thanks a lot for your response which is very useful. 

I have given CrossFTP a whirl (nice app) and also the beta Linux version of FileZilla. Neither are able to connect. I stress however that FileZilla on my Windows laptop can connect which goes via the same router (allbeit wirelessly). 

Very odd. I cannot work it out.

---

### Post by morningboat on 2007-06-21
FTP over SSL/TLS has three types: Implicit SSL, Explicit SSL (Auth SSL), and Explicit TLS (Auth TLS). You must make sure you have selected the correct one on your client.

Meanwhile, you can paste the log messages to help identifying the problem. You should be able to easily find the log messages on the log window in CrossFTP or FileZilla.

---

