---
title: "Shared folder"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-25
I'm trying to setup a shared folder between my *ubuntu* box and my *mac*.
 
On *ubuntu* I created a folder on my desktop and set up the permissions and users with samba (the system-config-samba GUI). 

Well I can access the folder on my *mac*,  and anything I put in there I'm able to see from *ubuntu*, "but" on *ubuntu* theres a little locked symbol above all the files and documents that I put in there from the *mac*.

I basically only have read-only access to everything in there.. so I tried to delete the files from my *mac* and I get an error saying I dont have permission to do that.. 

So it seems whatever I put in there neither computer owns anymore. The only way i could remove the files is to unshare the folder and then through the terminal using the rm -rf command.

Anyone got an idea what I've done wrong?

---

### Post by shadow120 on 2009-10-25
on ubuntu go to the folder permissions change others folder access to create and delete files change file access to read and write then apply permissions to enclosed files
i think this will fix it on the mac side but not 100% sure so let me know if it works

---

### Post by Loki57701 on 2009-10-25
I tried that and it didnt seem to work. Instead I changed the permissions on the folder I was dropping into the shared drive from my mac to (everyone:read-write/ apply to enclosed). That fixed the problem on the ubuntu side but on my mac once I drop that folder into the shared drive I no longer have write permission from my mac.. The shared folder on ubuntu has the permissions set to: 

owner: myusername
folder access: create and delete foles
file access: read-write

group: sambashare 
folder access: create and delete files
file access: read-write

others
folder access: create and delete files
file access: read-write

Under group the only groups I can set are: sambashare, adm, admin, dialout, cdrom, ipadmin, plugdev and myusername. So I'm guessing sambashare would be the correct one?

---

### Post by shadow120 on 2009-10-25
i dont know much about macs but i thought i would give it a shot i'll let someone else take it from here

---

### Post by Loki57701 on 2009-10-25
lol me either, thanks though.

---

### Post by Loki57701 on 2009-10-25
fixed it

---

