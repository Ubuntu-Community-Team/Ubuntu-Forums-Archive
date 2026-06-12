---
title: "[SOLVED] BIND and MyDNS Uninstall Problems"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by atjensen11 on 2007-10-12
I have been struggling to get a DNS server up and running on by Ubuntu server edition.  Mostly I have been struggling because of my lack of understanding of what to do.

But I accidently deleted some zone files for BIND after it was installed.  So I though I could uninstall and reinstall.  But I end up with a half uninstalled and half reinstalled system.

So then I tried to install MyDNS that uses a MySQL database.  I entered one wrong value (the MySQL hostname) in one of the GUI menu options and now I have a similar situation.  It won't uninstall.

Any help would be appreciated.

Thanks,
Tom

---

### Post by atjensen11 on 2007-10-16
I found that the reason I couldn't start or stop the server to uninstall is that a file was missing.  I just created a dummy file with the name it was looking for (as shown in my system logs) and then the uninstall was completed successfully so I could start over.

---

