---
title: "Hardy Samba share issues (corrupted files, authentication failures)"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by RobinS on 2008-06-02
Hello,

I am a newby to Ubuntu, but have more or less successfully setup an Hardy desktop and server.
In my network, I have an (Raidsonic) NAS, and the hardy server, both with have samba shares on them.
With them, I have the following problems:

1) I can connect with my hardy desktop to my Raidsonic samba shares.
   When connected, reading files seems OK in the file browser, but when   reading word documents using openoffice they seem corrupted. If I copy the files onto my hardy desktop, I found out that I am able to open them.
   When using my Windows PC, I am able to read the documents without problems. 
   Is this an known issue ?

2) When writing files to the Raidsonic samba share, it either is very slow, writing fails, or the files get corrupted. 
   Again when using my windows PC, it all goes well.

3) When connecting to my samba shares located on my Hardy server, I am unable to logon. I get an logon screen, but when I enter my username and password, it keeps coming back. When I look at my samba user config with Webmin, everything seems to be configured OK.
  I have tried to troubleshoot this issue with the samba.log files, but I do not see anything about the configuration failures.
  And have no clue left how to troubleshoot this issue.

Can somebody please point me in the right direction, so I can resolve these problems ?

Thanks in advance,

Robin

---

### Post by superprash2003 on 2008-06-02
have you added samba users successfully to the smbusers file?

---

