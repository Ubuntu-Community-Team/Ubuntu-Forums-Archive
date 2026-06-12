---
title: "MySQL Administrator setup"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Urema on 2011-03-22
Hi,

I have everything set up for using MySQL on ubuntu.
When the main window opens and asks you to enter the connection details, I have provided localhost etc, and it fails, however the ping is successful.

Does anyone know what I am missing? I have went through several tutorials as well as other posts and they dont seem to work either.
Thanks greatly in advance,
U.

---

### Post by TeoBigusGeekus on 2011-03-22
Can you give us a screenshot of the administrator and the info you give it?

---

### Post by Urema on 2011-03-22
Atached.

Thanks,
U.

---

### Post by TeoBigusGeekus on 2011-03-22
Everything looks ok...
Are you sure you provided a root password while installing mysql?

---

### Post by r-senior on 2011-03-22
What's the error message you get?

---

### Post by Urema on 2011-03-22
Attached, error message,

Thanks,
U.

---

### Post by Urema on 2011-03-22
Im almost sure I would have provided it, generally when I set things up I use an initial default password, then I change it afterwards. I have not changed this password yet, whereabouts do you do this with MySQL?

U.

---

### Post by TeoBigusGeekus on 2011-03-22
Just one thought...
When you try to connect to the administrator, you're not already connected to mysql via command line, are you?

---

### Post by Urema on 2011-03-22
No currently not....however I had tried that as a part of pretty horrible tutorial!

U.

---

### Post by TeoBigusGeekus on 2011-03-22
After you installed mysql, have you restarted your pc?

---

### Post by Urema on 2011-03-22
Yes I did...

I had installed it through the synaptic package manager...I have removed this and tried installing it manually as well, it wouldnt work nor setup mysql at all doing it manually, keeps saying 'Access denied for user 'root '@' localhost' - even after I have set up root with a password etc.

Im confused as hell here.

U.

---

### Post by TeoBigusGeekus on 2011-03-22
One last thing to try is to reconfigure the package:
```
sudo dpkg-reconfigure mysql-server-5.0
```

---

### Post by Urema on 2011-03-22
Got it working now!!
I just reconfigured the user and password....I mustnt have set it up correctly!

Thanks greatly for all your help today!! Crisis avoided!!

U.

---

### Post by TeoBigusGeekus on 2011-03-22
Glad to hear that! Don't forget to mark the thread as solved.

---

