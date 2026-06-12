---
title: "Failed to browse from the LAN through a proxy server"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by The Umanga on 2009-09-24
I have configured squid and it is now running, had errors with visible_hostname and port but I have managed. It is running without errors but PCs still cannot browse. I don't know what else to check that can show why these PCs can't browse. The server is Linux and the PCs are XP. I need help.

---

### Post by The Umanga on 2009-09-24
Hello, I've been trying a lot of things and I am now getting, " The requested URL could not be retrieved, while trying to retrieve the url: [http://www.google.com](http://www.google.com) , the following error was encountered, unable to determine the IP address from the host for [www.google.com]("http://www.google.com"), the dns server returned: refused: the name server refuses to perform the specific operation. This means that: this means that the cache was not able to resolve the presented url. check if the address is correct and the address is correct."

---

### Post by WolfRage on 2009-09-24
I think you are looking for SAMBA. Make sure it is installed and you want to set it up as a samba server. But I think really a client would be fine, as long as you add some share drives. Here are some links to help you out.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Screen cast: [http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)
 
By the way I have used the new samba 4 and it worked great, but it is experimental, plus it requires a lot of extra packages.

---

### Post by The Umanga on 2009-09-24
Samba is working fine. I have 6 user on the network right now and they are able to access the shares with no problems. The internet browsing is the problem right now.

---

### Post by WolfRage on 2009-09-24
So you are currently using Squid as a reverse proxy and an accelerator, right? If so I am sorry, but I have no experince in this area.
 
I imagine you already have this link, but just in case, here you go.
[http://wiki.squid-cache.org/ConfigExamples/Reverse/BasicAccelerator](http://wiki.squid-cache.org/ConfigExamples/Reverse/BasicAccelerator)

---

### Post by The Umanga on 2009-09-24
I checked out that site, thanks. The name in the /etc/hosts file the host name was wrong and I corrected it. I am close but need some help, when I run nslookup on the WinXP machines they are able to resolve but the cannot display the page in the browser, any ideas?

---

### Post by WolfRage on 2009-09-24
Have you rebooted the server since the change? Also you might want to reboot one of the XP's after the server to see if that helps.

---

### Post by The Umanga on 2009-09-24
I have been rebooting the after each config change just to be sure, still nothing.

---

### Post by The Umanga on 2009-09-25
Back with this problem this morning. Any help, will be thankful for it.

---

