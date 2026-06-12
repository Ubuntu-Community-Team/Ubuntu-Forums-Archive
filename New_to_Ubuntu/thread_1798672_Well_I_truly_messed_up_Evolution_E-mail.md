---
title: "Well I truly messed up Evolution E-mail"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by dasgud on 2011-07-06
[SIZE=3][FONT=Arial]Hi all,

Today I was finally able to import old e-mails from Outlook but when I did I seem to have destroyed my Evolution e-mail database. So I saved each folder individually as .mbox folders and tried to remove Evolution with the idea to re-install it, but I can't remove it because... Well here's the output:
"   installArchives() failed: (Reading database ...  
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15%
(Reading database ... 20%
 (Reading database ... 25%
 (Reading database ... 30%
(Reading database ... 35%
 (Reading database ... 40%
 (Reading database ... 45%
 (Reading database ... 50%
 (Reading database ... 55%dpkg: unrecoverable fatal error, aborting: 
 files list file for package 'libbind9-60' is missing final newline 

"
After I tried that, I looked through these forums and I found where the database was stored and I moved and renamed it hoping that evolution would reset itself. After doing that and then restarting the computer I opened Evolution again but my folders and e-mails were still there. I still can't remove the application.
Any ideas?
I'm using Ubuntu 11.04 and Evolution 2.32.2
I am satisfied with Evolution and don't want to change clients. Even if I did want to, I still wish to remove Evolution but can't.
[/FONT][/SIZE]

---

### Post by perspectoff on 2011-07-06
Use Thunderbird.

---

### Post by Rex Bouwense on 2011-07-06
Welcome to the forums.
I am not sure of your question but if it is concerning the removal of Evolution, look here:
[https://help.ubuntu.com/community/Evolution](https://help.ubuntu.com/community/Evolution)

---

### Post by wolfgangmcq on 2011-07-06
perspectoff: did you read the last line? He *wants* to remove Evolution!
I encountered a similar problem with a different package, when I was messing around with something. It looks to me like your problem is that the files list file for package 'libbind9-60' is missing final newline (as it says.) I don't know much about the packaging system, so this one is beyond me. If you don't get help on this thread, try a new one titled "files list file for package 'libbind9-60' is missing final newline" or some such. (Sorry I can't help more.)

---

### Post by dasgud on 2011-07-06
[FONT=Arial][SIZE=3]Ok... So thunderbird might be preferable, I didn't try it yet. I don't want to install another e-mail client until I'm able to remove evolution. However I like evolution and don't mind using it if I can get it repaired. When I tried to remove it using the synaptic package manager as referenced in the link that wolfgang provided I still get an error and the removal fails.

@ wolfgang, I'm not sure I can explain better, but I'll try. I moved and renamed the folder for evolution from home/user/.evolution to /desktop/.evolution.bakup . so /.evolution is no longer there, but when I start evolution again, all of the e-mails are still there. From what I've read so far, they shouldn't be. I'm sure I can answer questions better than try to provide useful information without prompting. :( I'm not so good at 'splainin sometimes.
[/SIZE][/FONT]

---

### Post by dasgud on 2011-07-06
[SIZE=3][FONT=Arial]@ wolfgang: That's a huge help. Thanks! When I close this reply I'll search on your suggestion to see if anyone has posted about it already.[/FONT][/SIZE]

---

### Post by dasgud on 2011-07-06
I get the same error when I try to install Thunderbird. that file 'libbind9-60' seems to be pretty important.

---

### Post by dasgud on 2011-07-06
I get the subject error when I try to remove Evolution. :(

So I tried to import an old outlook .pst file into evolution. I've been using evolution for a long time already, so there were folders installed already and when I imported the .pst file today into new folders I corrupted something. I'm not sure what. Just that none of my e-mail totals show correct, I can't delete e-mails and can't purge the trash anymore.
Further... I can't remove Evolution either because the 'libbind9-60' is missing final newline. Whatever that means. I can't install Thunderbird either, for the same reason.

Does anyone out there have any idea what is causing this error and how I can fix it? I wish to keep evolution, but working e-mail is way more important.

Thank you :)

---

### Post by bapoumba on 2011-07-06
Threads merged.

---

### Post by dasgud on 2011-07-10
I finally gave up trying to fix the problem and restored all of Ubuntu from a recent back-up. I lost about 1 month of e-mails but nothing that will shatter my zen. I do wish I could have fixed it though. Now I will keep weekly back ups using the export utility bundled with Evolution.
Thank you all for trying to help. I think that if I was better at explaining I could have fixed this with your help. :)

---

