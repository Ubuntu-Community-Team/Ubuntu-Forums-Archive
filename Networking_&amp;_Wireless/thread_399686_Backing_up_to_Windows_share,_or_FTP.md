---
title: "Backing up to Windows share, or FTP?"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by irish_flu on 2007-04-02
Hey folks,

This question is about your opinions, as much as anything.

I recently set up a box at my office running Ubuntu Dapper (desktop install).  On top of that, I installed Zimbra and Asterisk.

Just FYI:
Zimbra is a "Collaboration Suite" meant to offer similar functionality to Exchange.  It's a mail server with shared calendars and to-do lists and such.  The back end for the mail is Postfix, and the front end uses Ajax.  It's super-cool.

Asterisk is an Open-Source PBX phone system.  It can utilize VOIP and/or POTS to offer all the functionality one would expect from a business phone system, and it can also connect to various "softphones" (such as Ekiga which comes with Ubuntu).

OK on to the real post.   This is my first experience running Ubuntu in the enterprise environment (I've used Ubuntu as a desktop/workstation many times), and I don't have much experience with using Linux in the enterprise in general.

So, I need to back up my nice new server (made from cruddy old parts, lol).  Problem is, there's no tape drive in the box.

For my Windows 2000/2003 boxes, I use Veritas Backup Exec which writes everything to a centralized LTO tape autoloader (with lots of room).

So, it makes sense to me that I should back up my Ubuntu box over the network either to a Windows-shared drive, or to my (Windows-based) FTP server.

What would y'all recommend for this?  Should I just learn about Cron and schedule some kind of copy (I don't know jack about cron)?  Can anybody think of reasons why I should choose either FTP or the Windows Share?  Is there some nice GUI available that I've overlooked which might make this a simple process?

What else have I overlooked?  I'm mostly interested in getting my mailbox files, and my configuration files for Bind, Zimbra, and Asterisk; I can always rebuild the Ubuntu box if it dies.  I assume the thing to do is to tar the files up and then move them somehwere, using some kind of script to automatically repeat the process each day.  Is there anything else I should be thinking of?

Thanks in advance,
Irish_flu

---

### Post by irish_flu on 2007-04-02
Oh yeah, one more thing: backing up to Optical disk is not an option.  :)

---

