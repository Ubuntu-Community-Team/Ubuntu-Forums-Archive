---
title: "About to give up on my server"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by IslayMist on 2009-03-08
Ok... in /var/www there is a file called index.php... everthing works just fine with that... Now, I want to use folders in my default site to keep it nice and tidy. For example, /var/www/icons and /var/www/images and so on. It's just that... when I refer to icons or images in these folders, I just get broken links all the time... WHY ? I going bananas here... been checking configuration files for days, trying to understand what I'm doing wrong... nothing. Even reinstalled my server, just to make sure... Any idea ?

---

### Post by Nepherte on 2009-03-08
Make sure the url is right (perhaps try relative urls to refer to it) and check the permissions of the subfolders. They should be the same as the permissions for /var/www.

---

### Post by IslayMist on 2009-03-08
I checked and rechecked the permissions on the folders and they are identical to /var/www. I also tried different url's to find a way out, but no luck.

---

### Post by Nepherte on 2009-03-08
What's the exact error apache gives?

---

### Post by DGortze380 on 2009-03-08
/var/www is the root folder for your website...

so to link to a graphic in /var/www/icons

<a href="icons/myIcon.gif">myicon</a>

---

### Post by scottuss on 2009-03-08
That's your problem, you are using backslashes in the URL. Use forward slashes.

<a href="icons\myIcon.gif">myicon</a> should be <a href="/icons/myIcon.gif">myicon</a>

---

### Post by DGortze380 on 2009-03-08
> **scottuss said:**
> That's your problem, you are using backslashes in the URL. Use forward slashes.

<a href="icons\myIcon.gif">myicon</a> should be <a href="/icons/myIcon.gif">myicon</a>

I'm not the OP, sorry for the typo though.. ](*,)

---

### Post by scottuss on 2009-03-08
> **DGortze380 said:**
> I'm not the OP, sorry for the typo though.. ](*,)


Haha, sorry mate I didn't realise! I should re-read what I type before I hit Submit! :D

---

### Post by IslayMist on 2009-03-08
Well, the server never presents an error, nor a warning.
I am actually using a line like the this:
<img src="/icons/myicon.png" />

Should work out fine, or maybe this is wrong ?

---

### Post by hyper_ch on 2009-03-08
furthermore I think the apache default config has an alias for "icons". So you can't really use that (check the /etc/apache2/apache2.conf for it).

---

### Post by IslayMist on 2009-03-08
Thats it ! Finally :D Thank you so much for your help hyper !!

---

