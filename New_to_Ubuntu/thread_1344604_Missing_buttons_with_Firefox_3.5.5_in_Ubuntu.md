---
title: "Missing buttons with Firefox 3.5.5 in Ubuntu"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Clodia80 on 2009-12-03
Hi everyone, I'm totally new at ubuntu (karmic) and I'm not sure about how to solve this.
When entering at the PUBMED webpage, with firefox from windows I can see all the advance search buttons, but from Ubuntu they don't appear.
I contacted the PubMed helpdesk looking for some advice and their answer has been: "Perhaps the problem is with Firefox and Ubuntu.  Please use Firefox and Windows as it is working for you" which is a really advanced knowledge answer.
Is this a bug report that I must notify? Is it that I'm just missing any complement?
Many thanks for your help!

---

### Post by howefield on 2009-12-03
Can you post a link to the page ?

If I got the right one, it all looks fine (advanced search fields) using Ubuntu with both Firefox and Opera.

---

### Post by Clodia80 on 2009-12-03
Thanks for the quick reply!

This is the link: [http://www.ncbi.nlm.nih.gov/pubmed](http://www.ncbi.nlm.nih.gov/pubmed)
Just above from the search bar there should appear an advanced search and help options but from ubuntu they don't appear..

---

### Post by John Bean on 2009-12-03
> **Clodia80 said:**
> Just above from the search bar there should appear an advanced search and help options but from ubuntu they don't appear..

They do for me... with Windows, Jaunty and Karmic using Firefox 3.5.5.

---

### Post by Clodia80 on 2009-12-03
Thanks!
If this only happens to me, I must have touched something I shouldn't... Is there any diagnosis tool that can tell me what is wrong? Or should I use windows for pubmed search as suggested by the customer service?
Sorry to keep insisting...

---

### Post by mharrison on 2009-12-03
> **Clodia80 said:**
> Thanks!
If this only happens to me, I must have touched something I shouldn't... Is there any diagnosis tool that can tell me what is wrong? Or should I use windows for pubmed search as suggested by the customer service?
Sorry to keep insisting...

You could try backing up your Firefox profile and then letting FF create a new one to see if perhaps you tweaked something?  

Not sure if you know how, so I apologize if you already know how.

Open your home folder
Hit Ctrl + H to show hidden files
Copy the .mozilla directory to another location or simply rename it
Start Firefox

To restore your profile, delete the new .mozilla that was created and move back or rename your old .mozilla folder.

If the new profile allows you to see what you are missing, then I would suggest working on backing up what you want from your old profile and moving it to a new profile.  Personally, I would just back up my bookmarks and then just reinstall any add-ons one at a time, while checking to make sure none of them affect the PubMed page.

HTH

---

### Post by Clodia80 on 2009-12-03
No need to apologize, I'm a big disaster!
I've lost the .mozilla folder (I did CtrlC, but I couldn't copy it anywhere neither in the original folder), so I've reinstalled firefox (or at least this is what I was trying to do) with synaptic. Once the folder was back, I've renamed it (no way I was going to cut the folder again -  at least I try to learn from my mistakes), I've restarted firefox so a new folder has appeared. 
In the new firefox automatically Ad-block has been installed again (the only add-on I have). When I've gone to PubMed, the buttons keep missing. I've checked Ad-Block but it wasn't blocking anything.
While at synaptic, I've seen it says that the xulrunner 1.9.1.6 is obsolete (when I've done a firefox search). Also says libpurple0 is to be updated but it requests a file libzephyr3 which says is not installable. Could it be the problem?

---

### Post by pognonec on 2011-03-18
The post is a bit old, but I do have the same exact problem: no "Limit", "Advanced Search" nor "Help" links visible above the search field (Firefox 3.16.13, Ubuntu 10.10). Adblock on or off does not change it. On Chrome, the links are visible... Did you find a solution?

---

