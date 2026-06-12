---
title: "Unable to run sites from subdirectories in LAMP"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by clockwork189 on 2011-04-24
Hey Forum,
So I am pretty new to Linux, spent the last few days learning terminals commands and familiarizing myself with Ubuntu. Lately I installed LAMP and I got everything working fine. Thats is when I go on [http://localhost](http://localhost)  I get the welcome screen and all.

Now here is where my problem comes. Basically, I have like 9 website that I have been working on, each in a folder, that I imported into my www directory. They are basically in a folder sites, which is in the www directory. For eg: one site (say site1) is in var/www/sites/site1, another site (say site2) is in var/www/sites/site2, and so on.

Now when I try running localhost/sites/site1/index.html it gives me the 403 Forbidden Error with: You don't have permission to access /sites/site1 on this server.

Any help would be greatly appreciated.

THanks
CD

---

### Post by frup on 2011-04-24
It probably is a simple permissions error, either the files or the folders have the wrong permissions.

Have you changed any of the ownership or permissions of the /var/www directory? 

I think you'll want to make sure everything is chmod 755.

---

### Post by clockwork189 on 2011-04-24
Thanks mate, that solved the problem. Quick question, is there a way to chmod 755 all the sub directories and sub sub directories, etc. because Right now I am finding myself going through each directory and chmod 755 all files there, then going sub directory and same thing again. 

Thanks again,

Nvm: figured it out. The command is 

chmod -R 755 sites

Thanks for your help :D

---

