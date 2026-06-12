---
title: "synching folders"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by DavidG24 on 2011-04-18
hi guys,

I recently installed Dropbox on my system (10.10 x64) and have it across three comps (2 Ubuntu , 1 Windows) all are working beautifully, however being the paranoid person I am, I would like to setup on my home pc a synchronised folder with the DropBox folder so that any time a change is made to any file in the DropBox it is automatically updated in the synchronised folder.

I did a bit of looking around and rsync seems to be good, but do I have to run it each time to update the folders, or can it be set to auto sync?

If not are their applications that do this? 

Cheers,

David

---

### Post by stoogiebuncho on 2011-04-18
You can use cron to run your rsync command automatically every day or hour or minute or whatever.  (Not sure if this is exactly what you're wanting, but maybe?)

I don't remember clearly enough to give you directions off the top of my head, but it's pretty simple to set up.  A few Google searches for 'cron' should get you well on your way.

---

### Post by mike555 on 2011-04-18
You might look into Lucky Backup , it will do what you want , but at a set time .

---

### Post by DavidG24 on 2011-04-18
> **stoogiebuncho said:**
> You can use cron to run your rsync command automatically every day or hour or minute or whatever. (Not sure if this is exactly what you're wanting, but maybe?)
 
I don't remember clearly enough to give you directions off the top of my head, but it's pretty simple to set up. A few Google searches for 'cron' should get you well on your way.
 
hey mate,
 
genius, never knew abut CRON - it was incredibly easy to setup, all I had to do was copy the command from the terminal to do the sync from rsync and set it up as a scheduled task in CRON - simple! I now have it syncing hourly :-)

Thanks again,

David

---

