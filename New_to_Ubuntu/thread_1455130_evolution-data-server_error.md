---
title: "evolution-data-server error??"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by leonardo_neo on 2010-04-15
I am running lucid 10.04. I have been trying to copy my evolution personal addressbook to couchdb ubuntu one addressbook, but not able to do so. I can't simply open ubuntu one address book. When I click on couchdb ubuntu one, I get the following message......

> Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Address Book does not exist

I searched in the forum got a clue that this could be evolution-data-server error, I am not sure though.

Someone asked me to force shutdown evolution and then start evolution-data-server from terminal and then try to access the couchdb addressbook again and copy paste the terminal output......so this is the terminal output.......

> impl_GNOME_Evolution_Addressbook_BookFactory_getBook
 + couchdb://127.0.0.1
 => 0x18834c0
impl_GNOME_Evolution_Addressbook_Book_open (0x18834c0)
in server_log_handler

** (process:5435): WARNING **: Could not get OAuth tokens from keyring: No matching results
in server_log_handler

** (process:5435): WARNING **: Could not create DesktopcouchSession object


I am not sure if this is a bug or my own setting error, so I am asking in the forum first.

Thank you all for your help.

---

### Post by Didius Falco on 2010-04-15
There is a bug report open on Launchpad for this bug:

[https://bugs.launchpad.net/ubuntu/+source/evolution-couchdb/+bug/559979](https://bugs.launchpad.net/ubuntu/+source/evolution-couchdb/+bug/559979)

You could subscribe to that bug report. Join Launchpad if you haven't already - it's useful to developers and end users alike. I use it to look for bugs like what you were asking about. AAMOF, I don't use either Evolution or Ubuntu One and I found it with a simple search.

Since Evolution is a standard part of Ubuntu and Ubuntu One is Canonicals  entry point into Cloud computing, you can be sure they'll pay close attention to this and resolve it ASAP. 

Also, for the next two weeks, until Lucid is released, you should post for help in the Lucid Lynx Testing and Discussion sub-forum:

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Moderators, could you move this thread please.

Regards,

Didius

---

### Post by leonardo_neo on 2010-04-15
Thanks Didius for your response.

---

### Post by Didius Falco on 2010-04-15
My pleasure - I just wish I could have pointed you at a fix, instead of a bug report. :)

---

