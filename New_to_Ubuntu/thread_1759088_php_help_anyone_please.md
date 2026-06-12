---
title: "php help anyone please"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Old-un on 2011-05-15
I am running Ubuntu 11.04 and i want to learn php so i installed php5 via Synaptic. But after creating a simple html page with a .php file extension i cannot view its contents? Keep getting: Server could not be found? Could someone please tell me where i must save the .php file?

---

### Post by KL_72_TR on 2011-05-15
Take a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) , [https://help.ubuntu.com/8.04/serverguide/C/php5.html](https://help.ubuntu.com/8.04/serverguide/C/php5.html)

---

### Post by NoNameWill on 2011-05-15
place/save your work in the /var/www/ folder. Then open it from there. 

You can get there through the interface. Computer>Filesystem>var/www/  
or
```
 cd /var/www/ 
```to run .php file 

```
 php filename.php 
```

---

### Post by NoNameWill on 2011-05-15
Bare with me. It's been a few months since I messed with this. I am no expert. 

To place files into /var/www you will need to 

```
sudo chmod a+w /var/www
``` This of course is unsecure to do to a live server. 

to run your scripts in your browser [http://localhost/yourfilename.php](http://localhost/yourfilename.php) 

Hope this helps.

---

