---
title: "UPDATE MANAGER no longer automatically checks for updates"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by wrtell on 2011-04-17
I am migrating from UBUNTU 9.10 server to Server 10.10

I run the 64 bit version under VirtualBOX using Vista as a host..

I have installed the GNOME Desktop in the server and I have enabled the  root ID ..

It appears that when I enabled the root password  the job,process or fiction that automatically check for updates on a periodic  basis stops working. Sever 9.10 exhibited the same behavior.

Any ideas on how to correct this or where to look( I assume  some CRON job?) would be greatly appreciated.

Thanks 

William

---

### Post by Hedgehog1 on 2011-04-17
The Update Notifier process is run at startup:

[IMG]http://img405.imageshack.us/img405/1935/startupapplications.png[/IMG]

Yours may be unchecked, or may even be missing (in which case you will need to add it).


***The Hedge***

:KS

---

### Post by wrtell on 2011-04-17
Thank you for your response.

I checked and the update manager button is checked.

I examined the entry in the startup applications and noticed it consists of the command update-manager.

 Nothing else.

I opened a terminal typed the command update-manager  in and yes the update manger started.

So given the box is checked. It doesn't work. Other items  do such as startup sounds..

The other issue is as I indicated in my initial post the update manager does not run automatically once day. I have it set to do so in the settings dialog for the it.

I think  that is related to logging in as root.


Once again thanks.

William

---

