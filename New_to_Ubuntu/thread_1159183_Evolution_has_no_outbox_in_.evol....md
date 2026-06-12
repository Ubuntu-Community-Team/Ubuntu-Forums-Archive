---
title: "Evolution has no outbox in ./evol..."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-05-14
Without ANY changes to Evolution or the OS, about 3 weeks ago, email quit sending. And Evol was very slow to close/quit.

Not being a 'puter guy, I uninstalled evol & re-installed. No difference and weird, outbox is still jammed and will not "deliver" mail.

I read these posts:

Re: email stuck in outbox ([http://ubuntuforums.org/showthread.php?t=785725](http://ubuntuforums.org/showthread.php?t=785725)) which says:

[B]I'm believe you can open your file manager and show hidden files (look under view).

evolution/mail/local/outbox
Locate the folder called "Evolution" in your home directory
Open Evolution folder then locate the "mail folder" and open it.
Locate "local" folder and open it.
Locate "Outbox" text file and double click on it.

This will open your text editor with the contents of you outbox.
select "edit" in the toolbar and "select all" then delete and save.
Close the text editor and check your evolution outbox.[/B]

Using gksudo nautilus, I looked in /.evolution/mail/local and to my surprise I have NO outbox. Is this standard or an anomaly? I love Ubuntu/Linux, but with each release, changes made make using "old" posts/solutions a problem for non-tech people such as myself.

---

### Post by Mark_in_Hollywood on 2009-06-10
I eventually recreated a folder with the name

outbox.sdb

and the same permission/attributes as the 

inbox.sdb

now Evol is sending emails. As of now I haven't sent an email with an attachment, and believe there should be no problem, anyway. This seems to be the result of a VIRUS that ClamAV found. It's name is:

/home/Virus found/**AF4Iw0MAAH+oSgNUtQBA+URzF7o**

I made the folder: Virus found to put this file into. If you know anything about this, please update me. It was listed as a "phising" virus. I don't do business over the 'net, so they lost here.

Thank you, community.

---

