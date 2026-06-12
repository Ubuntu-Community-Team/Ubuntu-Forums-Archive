---
title: "Evolution Email Problem"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-11-25
When I click send/receive, every time, the same 2856 messages that are on the gmail and hotmail servers are sent to my inbox. Time was, those email were somehow marked as previously downloaded. Anyone know how to fix this?

---

### Post by Mark_in_Hollywood on 2009-11-30
Here is what has helped. So far as it as helped. This is from the FAQ for Evolution.

**Why does Evolution download duplicate emails?** How can I get rid of them? Why does Evolution reload old mails from server when "Leave a message on the pop server" is activated?

There are several possible reasons when this happens:

You have got several copies in your mailbox

The mail server supports the UIDL extension yet changes the message UIDs each session

The mail server does not support UIDL (which means Evolution has to generate UIDs using md5sums of the message headers) but the server changes the message headers after download (usually adding a Status: or X-Status: header - Evolution's md5sum ignores these, but Evolution may be missing other headers that this particular server munges)

**$HOME/.evolution/mail/pop/cache-* files are not writable**

I did alt-f2, gksudo nautilus. Found not a cache, but all the folders in pop were owned by root. I made them owned by user and group (i.e., user:user) by ME. That seems to have cleared up some of the problem.

There are 2 folders in ~/pop that are imap (gmail). Opening properties is not possible. Nautilus locks Nautilus. 

Solved. For now.

There is also a script to get rid of duplicates at [http://lists.ximian.com/archives/public/evolution/2005-January/041442.html](http://lists.ximian.com/archives/public/evolution/2005-January/041442.html) and an external plugin available at [http://www.gnome.org/~carlosg/stuff/evolution/](http://www.gnome.org/~carlosg/stuff/evolution/) which also works with Evolution 2.10 if you have installed the devel-packages for evolution (and evolution-plugin if your distro ships the plugins in a seperate package).


from:


[http://www.go-evolution.org/FAQ#Why_does_Evolution_download_duplicate_emails.3F_How_can_I_get_rid_of_them.3F_Why_does_Evolution_reload_old_mails_from_server_when_.22Leave_a_message_on_the_pop_server.22_is_activated.3F](http://www.go-evolution.org/FAQ#Why_does_Evolution_download_duplicate_emails.3F_How_can_I_get_rid_of_them.3F_Why_does_Evolution_reload_old_mails_from_server_when_.22Leave_a_message_on_the_pop_server.22_is_activated.3F)

---

