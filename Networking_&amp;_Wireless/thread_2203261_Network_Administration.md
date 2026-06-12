---
title: "Network Administration"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by jainabk on 2014-02-02
I have a wifi network with around 10 users. I want to be able to do the following :

1. Create username and password for each user.
2. Allocate a usage limit (in terms of GBs used)
3. Monitor web activity of every user.
4. block certain sites.

etc.

Please suggest which application would be best suited. Do I need to get any new hardware other than my computer?

TIA,
Abhishek

---

### Post by tfrue on 2014-02-02
You can set up rules within your router, whether that be a production or consumer router. You might also look into *iptables*, I don't know a lot about *iptables* but I know you can set up rules like you would in a router on Ubuntu.

I would suggest using Samba, or possibly LDAP as an Active Directory domain controller. I know you can set up Samba as a domain controller, but I haven't configured one so you would have to research that, but you can create users on the local level where they will have access to their /home directory with certain options that you configure. You may even be able to use the simple adduser command built into Linux to set up the users and set options there.

Here are some notes that I took while researching and I'm just copying and pasting so the format may be a little different:

-ULOG, watches for FW logs and logs to any specified file or Database.
-https://help.ubuntu.com/community/IptablesHowTo

---

