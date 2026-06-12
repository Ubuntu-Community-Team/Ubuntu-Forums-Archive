---
title: "Scheduled Database Backups"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by TimReal on 2009-11-24
I run an ecommerce site and I'd like to schedule hourly database backups of the live site from a dedicated local box. 

More specifically, I'd like to grab only certain details from certain tables (namely new orders) and back them up to my local machine. Then, I'd like to add these new details into my local machine's local web server.

This would then give us an almost live view of the website locally in an automated way and without resorting to a full database backup every hour - just the new bits. It's really in case of live server failure or connectivity failure.

BTW, we have a managed dedicated server so we could more or less do anything needed on that server if needed.

My questions are:

1. Can this be done using Linux?
2. Fully automated with no input from me once it's set up?
3. Is it implementable by a total noob with Linux, though I'm a web developer/computer science graduate?

Many thanks in advance.

---

### Post by kidders on 2009-11-25
Hi there,

What you're looking for seems more like replication than backup, really. If that's true, there's no need to settle for an *almost* live copy of your database ... it might as well be fully replicated, so you can fail over to the other server on a whim. What DBMS are you using?

Since this is (presumably) a commercial server, it should be noted that the kind of mirroring your thinking of is not adequate to protect you from *everything* that might befall your data though. You still need to perform regular full backups (eg once every couple of days).

> **TimReal said:**
> 1. Can this be done using Linux?Yes. How to do it depends on a few things though. For example ...[LIST]
[*]You could go for standard replication ... something most DBMSs support in some form. Most/all of the SQL executed on your live server would be automatically executed on the replica at the same time (or at least *relatively* immediately). Assuming all your SQL is properly transactionalised, this would effectively guarantee you a consistent copy of your data that you could fail over to in seconds, with no (or very minimal) data loss.
[*]Partial replication would be another reasonable option. You could do the above, but only with one or two tables (eg your orders table). Obviously you couldn't fail over to the replica, but it might still be useful to you in other ways.
[*]Alternatively, you could schedule execution of a script to SELECT new data from one database and INSERT it into the replica manually ... let's say once every 10 minutes. This kind of approach is fraught with weird little issues though, so it would have to be carefully done.
[/LIST]

> **TimReal said:**
> 2. Fully automated with no input from me once it's set up?Naturally! Having to trigger the replication yourself would sort of defeat the purpose, I suppose. That said, this kind of automation is one of the reasons backups are so important. For example, suppose your live server were compromised, or did something crazy with your data for some other reason (eg a bug). Any garbage that got into the live database would automatically propagate to the replica. Given how bad things'd have to be before you'd even consider doing so, the ability to revert to a full backup you *know* is clean (albeit a day or two old) is pretty essential, imo.

> **TimReal said:**
> 3. Is it implementable by a total noob with Linux, though I'm a web developer/computer science graduate?Hehe... you're no noob, in that case :-P I suppose it depends on the DBMS. MySQL would be a walk in the park, but Oracle might be a different story.

By the way, what's the approximate size of your database? A rough guesstimate to the nearest few thousand table rows and/or hundred megabytes would do. Also, how busy is your site? (For example, would you measure activity in purchases per minute or per hour?) I'm just wondering how feasible it would be to lock entire tables.

---

