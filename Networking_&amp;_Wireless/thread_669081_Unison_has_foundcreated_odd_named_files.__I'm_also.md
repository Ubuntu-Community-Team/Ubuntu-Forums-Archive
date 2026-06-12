---
title: "Unison has found/created odd named files.  I'm also after basic syncing advice."
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-16
**What I'm trying to do is:**

I have two Laptops and a Desktop. 

I want both of the laptops  to have the same Documents, Pictures, and Installs (where I keep windows and linux programs) folders as the Desktop.

Normally I would just mount an SMB share, but that's no good if I decide to go somewhere   I may find a good excuse to show off some pictures or install AVG Free on someone's XP installation.

I've set Unison up to sync Laptop 1 with the Desktop, then Laptop 2 with the Desktop.  Then it will sync Laptop 1 again, then Laptop 2 again.  That way changes made on Laptop 2 go to Laptop 1 and visa versa.

**The Problems:**

I have discovers odd named folders such as "GMS4HZ-Q" on the laptops and those folders do not exist on the desktop, even after syncing.  The extra fascinating thing is that the folders with the odd names have contents that match the proper named folder.  (For example a folder named "Junk" contains "Doc1" and "Doc2" a folder named "PASYEA-Q" will exist alongside the folder names "Junk" and contain the same "Doc1" and "Doc2"  

What if my pops decides to check his email on Laptop 1 at 12:00 and downloads the e-mails off the server and into the Thunderbird inbox.  Then at 4:00 he checks on Laptop 2 or even the Desktop.  When the syncing is complete the e-mails he downloaded at the 12:00 check will be gone.

Any thoughts?  

Any suggestions how I may better accomplish what I am trying to do?





[B]
*I just thought of a potential idea while typing this:*[/B]

I should try creating multiple SMB shares on the desktop and mount those in the home folder (ex the ~/Documents folder on my desktop would be mounted to ~/Documents on the laptops home folder.  Same with pictures..etc.) then I can have it copy or r..(rsync? r something or other.  It's a program like unison.. what was it..) to another place on the HD so I can have access to the files while away.  

The problem then comes when updating Thunderbird and other programs that access the Documents directory for the files is different home vs away (Thunderbird e-mails and Banshee database are in the documents folder).  And all the virtual links (to abook.mab for example) would be messed up too.

---

### Post by kevdog on 2008-01-16
This question would probably be better addressed specifically in the Yahoo unison forum.  Yes I know the response will not be as rapid, but that is where the unison developers respond.

---

### Post by Mysticle31 on 2008-01-16
Ah ha..  Thanks for the tip I'll go check it out.

---

