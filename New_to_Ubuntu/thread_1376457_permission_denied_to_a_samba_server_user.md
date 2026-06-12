---
title: "permission denied to a samba server user"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Ashishkhandelwal on 2010-01-09
I have configured samba server.My requirement was that the path which i have to share was /srv/www/htdocs.With this the shared path for developer user was /srv/www/htdocs/projects.So in the smb.conf file i made the entries as following:

[share]

path=/srv/www/htdocs
valid user = root
browseable = yes
writable = yes

[developer]

path = /srv/www/htdocs/projects
browseable = yes
writable = yes

After that root user was able login to both /srv/www/htdocs and also project folder and developer was only able to login to projects folder.That was according to my requirement but now the problem is that when developer is trying to edit any file in projects folder he is getting error that you dont have permissions to change this file.But developer should be able to edit any files.What changes i need to do now.

---

### Post by Muttley99 on 2010-01-09
Are you serving to a windows machine?

if not. Use NFS. 

If you are, what permissions are set for the developer files?

---

### Post by Ashishkhandelwal on 2010-01-09
Both server and local system are linux system.Developer files are stored in project folder and there are a lot of files in that folder.The root user is able to edit all the files but developer user is not able to edit.If i have to change the permissions of all the files in that folder then that would be a lot of problem for me so if there is any solution available by making any changes in smb.conf file then it would be great for me.

---

### Post by Muttley99 on 2010-01-09
If you plan to share more files in the future, consider changing to NFS; its easy to set-up and permissions stay relative.

for your smb.conf file try;

[HTML]force user = YOUR_USERNAME
force group = YOUR_USERNAME[/HTML]

..at the end of your developer section.

If this doesn't solve your problem; assuming you have a samba user developer and only developer and root need access!

[HTML]sudo chown -R developer:root /srv/www/htdocs/projects[/HTML]

---

