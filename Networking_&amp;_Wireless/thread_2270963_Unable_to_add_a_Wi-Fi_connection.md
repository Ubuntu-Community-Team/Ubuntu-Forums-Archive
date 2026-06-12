---
title: "Unable to add a Wi-Fi connection"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by balubeto on 2015-03-26
Hi

I have Lubuntu 14.04 32  bit.

Although I access through an administrative account and try to add a Wi-Fi connection via the "Network Connection" applet, I can not save it because the Save button is not active and tells me that I do not have the administrative permissions for activate it. How come? How should I do  add a Wi-Fi connection?

Thanks

Bye

---

### Post by kerry_s on 2015-03-26
you mean your logging in as root ?
log in as the user you created during install & set up the wifi from there. the setting is saved in that user account, i think ~/.gconf/nm-applet if i remember right.

---

### Post by JohnnyComeL8ly on 2015-03-26
Are you trying to use this? (nm-applet)
 [IMG]http://3.bp.blogspot.com/-qMK2vKZgVFk/U1E_SsnFAjI/AAAAAAAASXw/ZxrGeZaONTo/s1600/lubuntu-nmapplet-fix.png[/IMG]

Because if you aren't, I'd give that a try....  Also, it sounds like you are trying to use nm-connection-editor, not nm-applet: it works, but maybe you aren't filling in all that you need to for nm-connection-editor to make a Wi-Fi connection.

---

