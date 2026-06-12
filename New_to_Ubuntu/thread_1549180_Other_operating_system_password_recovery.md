---
title: "Other operating system password recovery"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by ruff4life on 2010-08-09
I was recently asked to help somebody to recover the files on a hard drive because they lost their login password on there pc. I used an ubuntu live disk to access the hdd an recover their files. Is there a way to recover their password also?

---

### Post by krishnandu.sarkar on 2010-08-09
Did he/she forgot the Login password only or both Root and Login password??

---

### Post by MorleyPotter on 2010-08-09
try this **ophcrack**.sourceforge.net/

---

### Post by ruff4life on 2010-08-09
I was recently asked to help somebody to recover the files on a hard drive because they lost their login password on there pc. I used an ubuntu live disk to access the hdd an recover their files. Is there a way to recover their password also?

---

### Post by endotherm on 2010-08-09
it's a pita to actually recover the password but it is trivial to reset it or blank it. 
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)


if you really want to recover the passwd, use the disk above to unlock the builtin administrator account and blank it;s passwrd. then from the admin account install 0phtcrach/L0phtcrack to recover the password for your friends account. with a strong password this recovery process can take several days of processing to achieve results. my passwords usually take about 4 days to recover.

---

### Post by CharlesA on 2010-08-09
The only hitch with blanking their password like that is that if there are encrypted files on the drive, they'll be inaccessible.

It would be easier to just try the administrator account with no password and see if it lets you login.

---

### Post by anewguy on 2010-08-09
If you are asking if you can use a linux based tool and basically "reset" a Windows users' password (like they forgot it and need to log in), the answer is yes.

I'm not sure on the forum rules for exact instructions for this, so I'll just leave my answer at that but add that a simple search on the web will turn up the free tool you would need.

Dave

---

### Post by Sef on 2010-08-09
Merged threads.

---

### Post by pricetech on 2010-08-09
We used a Linux based utility which we actually ran under bart's PE to blank the administrator's password when one came to us for service with such a thing requested.

Again a search using your favorite search engine should find you what you're looking for.

---

### Post by fslezak on 2010-08-09
Due to forum policy, I may not be allowed to give what you want, but I can give you this:

Password Suite

[COLOR=White]That file should have what you're looking for.[/COLOR]

---

