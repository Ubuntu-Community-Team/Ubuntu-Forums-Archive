---
title: "How to restore startup programs in &quot;Sessions&quot; which I have accidentally deleted?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by kwokyinc on 2009-01-17
I have accidentally deleted two programs in the startup program list in "System" => "Preference" => "Sessions".

I don't know which two programs I have deleted. Can someone tell me how to restore that to the default setting?

I am using Ubuntu 8.10. Many thanks.

---

### Post by kukibird1 on 2009-01-17
The /etc/xdg/autostart folder has a list of default start applications.
Right clicking on the icons will give you the info you need to add the 
programs you deleted back into  System" => "Preference" => "Sessions.

 for a complete reset [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

---

### Post by kwokyinc on 2009-01-21
> **kukibird1 said:**
> The /etc/xdg/autostart folder has a 
[/URL]

Thanks Kukibird1.:D

I couldn't find what is missing from the /etc/xdg/autostart
so I guess what I have deleted is some extra startup program which was not in the default gnome setting.

I really think the startup program interface should include an "undo" button since it's so easy to accidentally delete things there.

Anyway I don't seem to have any actual problem booting / using the system even without the missing startup. So perhaps I will jsut leave it here.

---

### Post by nothingspecial on 2009-01-21
I once asked the question - Is it possible to undo a terminal command?

No, it`s not.

Hence my sig.

---

