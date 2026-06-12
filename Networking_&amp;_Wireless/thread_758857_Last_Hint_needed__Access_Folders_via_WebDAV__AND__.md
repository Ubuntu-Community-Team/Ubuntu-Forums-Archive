---
title: "Last Hint needed:  Access Folders via WebDAV _AND_ Samba"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by tomcon on 2008-04-18
Hello,

Since this is my first post, hello to everyone :-)

I'm running an Ubuntu Server and use it for Filesharing with Samba.
I've setup Samba correctly and it works like a charm.

I've also some folders that I access via WebDAV.

What I'm missing now is to connect to a Folder (that I'm also accessing using Samba) via WebDAV.

Configuration:

I've a user USER1 and he is in the group GROUP1. I can access a directory called /home/groupfolder via Samba.
The attributes and user-rights of /home/groupfolder:

      drwxrwx--- root GROUP1   groupfolder

Question: Can I share a folder using WebDAV that doesn't belong to the www-Webserver-User.
Or what do I need to do in order to share a folder by WebDAV and SAMBA?

Any help would be great.

- Tom

---

### Post by tomcon on 2008-04-22
Thanks for the replies so far :(
Anyway... I found a solution myself by accident while browsing the Samba-Website (GUIs for Samba):

[davenport]("http://davenport.sourceforge.net/")

> Davenport is a servlet which provides a WebDAV gateway to SMB shared resources. Typical usage would be to provide web-based read and write access to Windows shared drives.

WebDAV clients, such as Windows' "Web Folders" can copy files to and from the shares over HTTP. Non-WebDAV-capable web browsers can also access the network, downloading files from shared folders in a seamless fashion.

Users access shared resources using their Windows domain username and password, so no account configuration is typically needed. When run over HTTPS, Davenport provides a secure means of accessing internal shared drives over the internet without requiring a VPN. 

Since davenport is java-based the following lines did the trick:

[LIST=1]
[*] ```
sudo apt-get install sun-java6-bin
```
[*] ```
wget http://dfn.dl.sourceforge.net/sourceforge/davenport/davenport-0.9.11.zip
```
[*] ```
unzip davenport-0.9.11.zip -d /opt/
```
[*] You may want to check the davenport-config file in /opt/davenport/webapps/root/WEB-INF/web.xml. But Davenport was working without any changes in my case.
[*] ```
cd /opt/davenport
```
[*] ```
java -jar start.jar
```
[*] You can now access your Samba Shares on [http://WEBSERVERNAME:8080/SAMBASERVERNAME](http://WEBSERVERNAME:8080/SAMBASERVERNAME)
[/LIST]

Even if Davenport is working you may want to check the davenport documentation.
Regarding Security you should tunnel your http-traffic with SSH or change to https. I'll try to update this information as soon as I get this working.

Problem: I can access my webserver via https on Port 443 (default) but since davenports runs on port 8080 you can _not_ access your samba-shares with

[https://WEBSERVER:8080/SAMBASERVERNAME](https://WEBSERVER:8080/SAMBASERVERNAME)

How were your experience with Davenport and Ubuntu? Any ideas or comments how to get https-secured-transfers?

- Tom

---

