---
title: "Startdate for sessions in FreeRadius with MySql?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by bladan2000 on 2008-10-06
Hello!

We're using FreeRadius 1.1.7 along with MySql on an Ubuntu server. We have a web application to create users for FreeRadius and administrators can set the expire date for when a session should expire. This is achieved with the "Expiration" attribute in the table called RadCheck in the MySql database. However, a customer would like to be able to also set a "start"-date for when the session should become valid i.e. if I set 2008-10-06 it won't be possible to log in before that date.

I haven't found a way to do this in FreeRadius. Does anyone have a solution for this? I thought that it might exist an attribute for "Start" as well when there is one for "Expire" but I haven't found any. The only solution I can come up with is some kind of own customized que handling for this altough I would prefer a simple attribute.

Any thoughts?

Johan

---

