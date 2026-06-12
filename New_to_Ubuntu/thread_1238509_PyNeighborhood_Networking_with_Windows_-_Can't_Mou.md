---
title: "PyNeighborhood Networking with Windows - Can't Mount?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-12
Objective: share files from my Win XP box with my Ubu box (and vice versa).

1. On Ubu I installed PyNeighborhood via Synaptic
2. I read on the forums that I should launch PyNeighborhood as root. So, I edited the menu launcher icon to "gksu PyNeighborhood"
3. Went to my XP box and ran the wizard to enable home/office networking
4. Once the wizard completed the machine restarted. I then went to the folder I want to share, right clicked and ticked the boxes to share the folder. A hand appears holding the folder confirming sharing enabled

5. Back to my Ubu box. I added a computer to my Group list then ran a scan
6. Found my XP box!
7. I want to open Dad's Documents so I double click it. "Failed to mount" error window pops up.
8. I right click it and select "Mount as SMB" - Fails!
9. I right click it and select "Mount as CIFS" - Fails!

Can anybody tell me where I'm going wrong please?

Mark

---

### Post by mapes12 on 2009-08-13
Very minor progress.

I have attached a screenshot of my XP machine showing that I have two folders with sharing enabled, namely Shared Documents and Dad's Documents. Before I ran the wizard (or whatever) on the XP machine to enable sharing the Shared Document folder was already there by default with the sharing hand around it. I had to configure sharing manually for Dad's Documents.

Back to my Ubu box and pyNeighbothood - I changed the mount location to /home/mark (me) because I read somewhere that would resolve any permission issues. I can browse the Shared Documents folder as can be seen by the mount confirmation in my other screen shot but I still can't access Dad's Documents. The same "Failed to Mount" window keeps popping up. But if I copy across the content from Dad's Documents to Shared Documents then I can access my files in Shared Documents.

But by doing this:

1. I am doubling up the space used on my HDD for the masses of stuff in the Dad's Documents folder
2. I'm having to manually copy stuff over every time there are any file changes.

There must be a way of accessing Dad's Documents without having to copy stuff across to the only folder I can access i.e. Shared Documents?

---

### Post by grj23 on 2009-08-17
Hi Mark

I guess you're doing this over an internal connection, rather than over the internet?

I'm sure there must be a way of linking straight to your dad's documents, but if you want a quick and dirty, Unison would provide a way to synchronise the documents in both directions -it is pretty straightforward to set up to synchronise two directories on the same machine!

G

---

### Post by mapes12 on 2009-08-17
After some days of head scratching I've finally resolved this problem. On the XP machine I have two accounts. Administrator with full admin permissions and Dad with limited permissions. I assumed that logging on as Administrator would be the best option so that I could access all the files on th system with admin permission. Although I could see and assign sharing to "Dad's Documents" I could not access the share from my Ubu box. I then had the idea that somehow the share was not being authorised by the account holder. So I logged in as Dad and to my amazement discovered that "Dad's Documents was not being shared when logged in as the account holder :mad: I then reconfigured "Dad's Documents" to be shared and hey presto! I can access it from my Ubu box :)

The problem was with XP, not Ubu.

---

