---
title: "Evolution"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Someone uk on 2010-09-28
after evolution has been working seemlessly for ages i get the message "Error while Generating message list.

database disk image is malformed"

when i try ```
evolution
```
the output is 

** (evolution:2422): DEBUG: mailto URL command: evolution %s
** (evolution:2422): DEBUG: mailto URL program: evolution
Making error

anyone have any idea what's wrong or why i have this problem?

---

### Post by chaanakya_chiraag on 2010-09-28
Hmmm...seems like your database got corrupted...can you try moving /home/$USER/.evolution to /home/$USER/.evolution.bak and then try starting Evolution?

---

### Post by Someone uk on 2010-09-28
is there anything i can do the possibly recover some of the emails, how are they stored in evolution?
i just realised my hotmail deletes the emails once i fetch them via pop :/

---

### Post by chaanakya_chiraag on 2010-09-29
Ouch...I'm not on my Ubuntu comp right now, but I'm pretty sure Evolution caches them somewhere...especially if you're using pop...I'll take a look later and let you know...

---

### Post by Someone uk on 2010-09-29
a little experiment that seems to fix things..
i rename .evolution (whist evolution is closed) something like .evolution.backup
then i open evolution, delete the new .evolution, rename the .evolution.backup back to .evolution and apart from it will mark some of my read emails as unread it works fine

so i assume it's a corruption in a file it reads on startup but not when i press "send/receive"

anyhow i know now to make a backup of my emails, if evo doesn't already do it...

---

### Post by chaanakya_chiraag on 2010-09-29
If you can find where evolution stores the emails (it should be somewhere inside .evolution), you can create a copy of that folder, which should work to save your emails.  To restore, you should be able to simple copy the folder back.  However, I have never done this and do NOT know the ramifications.  Try at your own risk!!!

---

### Post by chaanakya_chiraag on 2010-09-29
Oh, and btw, don't use hotmail!!!  Use gmail or yahoo mail! ;)

---

### Post by philinux on 2010-09-29
> **chaanakya_chiraag said:**
> Ouch...I'm not on my Ubuntu comp right now, but I'm pretty sure Evolution caches them somewhere...especially if you're using pop...I'll take a look later and let you know...

Close evolution then delete this file.

```
/home/YourUserName/.evolution/mail/local/folder.db
```

Restart evolution and it will rebuild it's database.

---

### Post by chaanakya_chiraag on 2010-09-29
> **philinux said:**
> Close evolution then delete this file.

```
/home/YourUserName/.evolution/mail/local/folder.db
```

Restart evolution and it will rebuild it's database.
Right...but where does Evolution store the actual emails themselves?

---

### Post by chaanakya_chiraag on 2010-09-29
> **chaanakya_chiraag said:**
> Right...but where does Evolution store the actual emails themselves?
Also...love your pic philinux! :)

---

### Post by philinux on 2010-09-29
> **chaanakya_chiraag said:**
> Right...but where does Evolution store the actual emails themselves?

.evolution/mail/local is one place.

---

### Post by chaanakya_chiraag on 2010-09-29
> **philinux said:**
> .evolution/mail/local is one place.
For the OP, wouldn't it be ```
.evolution/mail/pop
```?  Also, would backing up this folder guarantee that all emails are saved?

---

### Post by Seaban on 2010-09-29
Hi,

I am a bit new to all this so please excuse any "inappropriates".  I am using 10.10 but am having a problem with duplicates being automatically downloaded into my inbox in evolution.  This has not happened under 10.04 with the same settings.  Can anyone suggest a way to rid my inbox of the dupes?

Many thanks,

S

---

### Post by chaanakya_chiraag on 2010-09-30
> **Seaban said:**
> Hi,

I am a bit new to all this so please excuse any "inappropriates".  I am using 10.10 but am having a problem with duplicates being automatically downloaded into my inbox in evolution.  This has not happened under 10.04 with the same settings.  Can anyone suggest a way to rid my inbox of the dupes?

Many thanks,

S
You should probably post this in the Maverick Testing Category as you will probably get more help there.

---

### Post by philinux on 2010-09-30
> **chaanakya_chiraag said:**
> For the OP, wouldn't it be ```
.evolution/mail/pop
```?  Also, would backing up this folder guarantee that all emails are saved?

pop folder contains the pop settings. Backing up is always good. :P

---

### Post by philinux on 2010-09-30
> **chaanakya_chiraag said:**
> You should probably post this in the Maverick Testing Category as you will probably get more help there.

Not necessary OP is running 10.04, and it's a generic support request.

---

### Post by Someone uk on 2010-10-01
works, thanks :)

---

### Post by chaanakya_chiraag on 2010-10-01
That was for Seaban, who IS running Maverick (as I read the post - please correct me if I'm wrong Seaban).

---

### Post by jakell on 2010-10-08
I know it says 'solved, above, but I'm having problems exporting mail and  from Lucid (evolution 2.28 ) to Maverick (evolution 2.30 ).

 I retained my home folder when installing Maverick, but the mail was invisible. (email accounts were ok). Also I have done an export file from the old evolution (2.28 ), and even though the file seems to load ok into 2.20, the emails are still invisible. 

 I've tried fiddling with display settings in evolution, but to no avail.

---

### Post by jakell on 2010-10-08
Have sorted this now. A non-intuitive part of evolution's display properties confused me.

---

