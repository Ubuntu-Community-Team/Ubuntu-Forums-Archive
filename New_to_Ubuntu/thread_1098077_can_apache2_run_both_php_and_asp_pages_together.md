---
title: "can apache2 run both php and asp pages together?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by dcparham on 2009-03-16
Our firm intranet is dragging from the old server, some applications that would take too long to rewrite from ASP/msAccess to PHP/mySQL.  Is it possible also to host on Apache2, ASP/msAccess?

---

### Post by linuxisevolution on 2009-03-16
Yes it is. Install apache2 then install php5 ( sudo apt-get install php5 ). 

For asp you will need the mod, which resides somewhere on the intertubes...

---

### Post by dcparham on 2009-03-17
Evolution - thx for the "yes"; however, i do not know what the mod and intertubes references are, can you explain? remember, not knowing if i can use asp and php together in the first place, might clue you that i also do not know what mod and intertubes means.  i see some references in google regarding "customization" - nothing more. again, thx:)

---

### Post by dcparham on 2009-03-17
hmmm - just as i suspected: your references simply mean "customizations found by searching on the internet?" i found nothing definite there which is why i came here.  8?

---

### Post by finer recliner on 2009-03-17
first result googling "apache asp mod":

[http://weblogs.asp.net/israelio/archive/2005/09/11/424852.aspx](http://weblogs.asp.net/israelio/archive/2005/09/11/424852.aspx)


enjoy!

---

### Post by linuxisevolution on 2009-03-17
> **dcparham said:**
> Evolution - thx for the "yes"; however, i do not know what the mod and intertubes references are, can you explain? remember, not knowing if i can use asp and php together in the first place, might clue you that i also do not know what mod and intertubes means.  i see some references in google regarding "customization" - nothing more. again, thx:)

Intertubes = old name for Internet. [http://www.youtube.com/watch?v=EtOoQFa5ug8&feature=PlayList&p=4F6E51D4C823CFD3&index=0&playnext=1](http://www.youtube.com/watch?v=EtOoQFa5ug8&feature=PlayList&p=4F6E51D4C823CFD3&index=0&playnext=1)

The php mod is simply and addon to apache2 which lets it display .php content. Same goes for asp (look at finer recliner's post).

To get apache2 to display php content, install php5 from terminal, like so:

sudo apt-get install php5

and restart apache via: 

sudo /etc/init.d/apache2 restart


Good Luck! :)

---

### Post by dcparham on 2009-03-20
lEvolution - perhaps i should've earlier elaborated more on my lack of "LinuxPertise"!  i can tell your answer will get me close if not directly in the center of the bullseye. thanks very much!  the busyCoder rides again!

---

### Post by Panarchy on 2009-03-21
> **linuxisevolution said:**
> Intertubes = old name for Internet. [http://www.youtube.com/watch?v=EtOoQFa5ug8&feature=PlayList&p=4F6E51D4C823CFD3&index=0&playnext=1](http://www.youtube.com/watch?v=EtOoQFa5ug8&feature=PlayList&p=4F6E51D4C823CFD3&index=0&playnext=1)

The php mod is simply and addon to apache2 which lets it display .php content. Same goes for asp (look at finer recliner's post).

To get apache2 to display php content, install php5 from terminal, like so:

sudo apt-get install php5

and restart apache via: 

sudo /etc/init.d/apache2 restart


Good Luck! :)

LOL

A series of tubes!

---

### Post by dcparham on 2009-05-19
to wake a once-dormant topic, i have more presence of mind to now ask a more refined question: will the asp mod allow [1]classic vb-based ASP, and [2]an MS Access database working together on the Ubuntu, Apache2 server? sorry, but that was my real question:P.  Listen, thx for your time and help!

---

