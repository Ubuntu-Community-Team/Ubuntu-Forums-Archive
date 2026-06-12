---
title: "ubuntu hacked?"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by ldeveloperxl on 2008-09-21
Hi

while I was messing around with a folder's permissions today by right clicking on it then permissoins (within xampp htdocs folder), a message suddenly popped up randomly saying:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

was my computer hacked and someone trying to access my computer?

ps:
XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. ([http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) and I have run its security script '/opt/lampp/lampp security' and set the passwords)

:confused::confused::confused:

---

### Post by cariboo on 2008-09-21
No you haven't been hacked, you have a problem with your Samaba setup. I don't really like xampp as it is a non standard installation making it harder to diagnose problems. It also isn't available in the repositories, so every time there is an update you have to reinstall or even worse unless you keep track of the updates, you could after time be running an insecure system.

The default Lamp install ation is just a matter of a couple of clicks if you use Sysnaptic Package Manager, and is upadted constantly with security updates.

Jim

---

