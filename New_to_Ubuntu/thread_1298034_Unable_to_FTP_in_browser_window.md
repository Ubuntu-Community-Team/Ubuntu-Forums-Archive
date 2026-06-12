---
title: "Unable to FTP in browser window"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by lcsfsr1 on 2009-10-22
Hello, 
Can anyone tell me why I am getting this error???
I have about 150 pcs with Windows XP Pro. These computers need to connect to the Windows Server 2003 FTP server through the squid proxy. It is not feasible to disable the proxy on each computer each time they need to ftp something.
 
All FTPing is done in **ACTIVE mode**.....not "passive".
 
Most users open a Internet Explorer Web Browser window and enter the FTP address in the browser address bar. (i.e. ftp.acme.net). Then they get a login box that pops up asking them to enter their user name and password. Once they press enter they are successfully logged into the ftp server.
Everything is fine as long as this proxy is not enabled on the client workstation.
 
The error below started occuring as soon as I setup this proxy server. I am not able to put all users on this proxy until this ftp problem is resolved.
 
I am using Ubuntu 9.04 Server / Squid 2.7 / and Dansguardian 2.9.9.7
 
[COLOR=red]**This is the error that I am getting:**[/COLOR]
 
ERROR
The requested URL could not be retrieved
 
--------------------------------------------------------------------------------
 
An FTP authentication failure occurred while trying to retrieve the URL: [ftp://ftp.acme.net/](ftp://ftp.acme.net/) 
 
Squid sent the following FTP command: 
 
PASS <yourpassword>and then received this reply 
Password not accepted.Your cache administrator is webmaster. 
 
 
 
--------------------------------------------------------------------------------
 
Generated Thu, 22 Oct 2009 15:54:59 GMT by bhproxy.xxxxxxxxxxxx.com (squid/2.7.STABLE3)

---

