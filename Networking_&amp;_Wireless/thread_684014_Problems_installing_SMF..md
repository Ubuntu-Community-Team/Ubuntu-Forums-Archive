---
title: "Problems installing SMF."
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by lenswipe on 2008-01-31
When installing SMF I am getting errors due to incorrect permissions. It tells me to apply 777 to several files and a directory or to. I remember you told me to run a command, i have since forgotten that command so i thought i would make a thread to ask..


(hey maybe someone else out there knows the anwser too) 

ive a feeling the command to make certain folders writable for SMF installation was 

```
sudo chmod -R 777 <<name of file here>> 
```
but im not sure...

---

### Post by Dr Small on 2008-01-31
That should be:
```
sudo chmod 777 -R /path/to/directory/
```

Am I correct?

---

### Post by PriceChild on 2008-01-31
If you'll remember, chmod'ing the entire /var/www broke things last time.

Instead, just chmod the needed files and folders (non-recursively, ie no -R flag) which the installer lists for you.

sudo chmod 777 /var/www/nameoffile

---

### Post by lenswipe on 2008-02-01
> **PriceChild said:**
> If you'll remember, chmod'ing the entire /var/www broke things last time.

Instead, just chmod the needed files and folders (non-recursively, ie no -R flag) which the installer lists for you.

sudo chmod 777 /var/www/nameoffile



sure ok thanks....


also...

when setting SMF up when it asks for an address for the MYSQL server should i put localhost for that?

or do i just write the internet address of the forum for all the feilds such as [http://www.myfirstforum.com](http://www.myfirstforum.com)

Like that?

---

### Post by lenswipe on 2008-02-02
hello?

anyone?

---

### Post by lenswipe on 2008-02-02
> **PriceChild said:**
> If you'll remember, chmod'ing the entire /var/www broke things last time.


*shudder* dont remind me..

---

### Post by matthew on 2008-02-03
> **lenswipe said:**
> when setting SMF up when it asks for an address for the MYSQL server should i put localhost for that?Yes, put localhost.

---

