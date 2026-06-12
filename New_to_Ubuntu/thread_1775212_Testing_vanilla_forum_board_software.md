---
title: "Testing vanilla forum board software"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by rng on 2011-06-04
I need to create an online forum for my community. I have downloaded vanilla forum board software. The entire system of files and folders is to be put on server. 

How can I test it on my pc under ubuntu? I think I need to set up apache. Is it too difficult. Please help.

---

### Post by yeats on 2011-06-04
Can you be more specific about the problems you're encountering?

---

### Post by rng on 2011-06-04
I want to see how the forum will look like once it is put on server. I want to change and test some settings like the title, format etc. I want to try putting in messages and see how they appear. Can I do all these on my pc running ubuntu without putting the file system on server?

---

### Post by ExileAmongYou on 2011-06-04
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

LAMPP is a nice easy way to run an Apache server on your local machine.

---

### Post by rng on 2011-06-05
Thanks. I will try xampp and come back if there is any problem.

---

### Post by yeats on 2011-06-05
The easiest way to install lamp is to invoke tasksel from the command line:

```
sudo tasksel
```

Then arrow down to LAMP server and hit the spacebar to select, tab to OK and hit enter.  This will automatically install it for you.

Hope that helps!

---

### Post by rng on 2011-06-05
Thanks. I will try this and give you the feedback.

---

