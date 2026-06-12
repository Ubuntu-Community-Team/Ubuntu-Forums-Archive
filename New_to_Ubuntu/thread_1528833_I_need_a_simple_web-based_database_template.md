---
title: "I need a simple web-based database template"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by harry003 on 2010-07-11
I am a moderately knowledgeable computer user who has used databases but never written one. I am involved in starting a small construction company and I will be the de facto "IT Guy" whether I like it or not.

We need to create a simple database to track leads, prospects, and customers. In the first year, that might be a few hundred leads and a few dozen customers, handled by something under a dozen salespeople and manager-type employees who will need varying levels of access to reading and writing sales tracking and work progress information.

Actual construction progress/timeline information and all accounting of money will NOT be a part of this scenario. Anything can change, of course, but at present it is our intention to keep Sales, Operations, and Accounting as completely separate and unblended entities (in the computer files, that is).

For now, the Sales database is what I need, and we would dearly love for it to be accessible over the web, for obvious reasons. We can't afford or support a server of our own, and our needs will be very modest.

Microsoft Access 2010 has a great template "Sales Pipeline" that I could easily modify to do what we need, and I could probably run it out of Hotmail/Live if I really worked at it.

But I would really prefer a FOSS application and something that is accessible on Google Docs/Apps would be perfect, but paying a reasonable monthly fee would not be a deal-killer. I have looked at Base a bit, and found no decent Templates. I tried to access Glom, but clicking on their Template list crashed it and I could not even get it to start. People seem to like Glom but that looks like a kludge of the highest order.

I feel like these needs are straightforward and exactly what 2/3 of the small businesses in the world would need, why is this so hard?

ps - please don't tell me to cobble something together using a spreadsheet, one thing I do know is that I need a REAL database, even if it is a basic one, because I need to make a variety of queries for several types of information.

thank you for your help.

---

### Post by new_tolinux on 2010-07-11
If you'll want your database to be accessible over the web you should be able to access the MS Access database with PHP.
Since you're looking for FOSS, MySQL should be the thing you want to use, which is also easily accessible with PHP.

The only problem is that you will need a computer to run it. Either at your company or at a (cheap) webhost.
It should be not too much of a hassle to import the MS Access database into MySQL.
The other thing to keep in mind is that MySQL won't come with any examples/templates. Creating a database and the corresponding tables should not that big of a problem when you're able to use PHPmyadmin.

The last thing is that MySQL is a database server, so you'll have to write the proper PHP-files yourself, as I guess having all visitors browsing in PHPmyadmin isn't a real nice idea.

---

