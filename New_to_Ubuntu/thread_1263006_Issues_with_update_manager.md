---
title: "Issues with update manager"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by moving shadow on 2009-09-10
Fairly new to ubuntu, I got fed up with xp and installed Jaunty on an 'old' laptop and everything worked really well initially, including applications on Wine. Recently though the  update manager won't install the updates, it asks for the admin password which I enter, after which nothing happens. The same happens when I try accessing the synaptic package manager to see if I can change any settings. I can still install apps through Wine using the same password so I am a bit confused.

Not sure if I am missing something obvious, but I have done a decent amount of googling to no avail. 
Thanks in advance for any help!  

Yours

Ubuntu newb

---

### Post by mapes12 on 2009-09-10
What happens when you run the same application via the Terminal e.g.```
sudo apt-get update
``` what response do you get?

---

### Post by drs305 on 2009-09-10
Welcome to the Ubuntu forums.

Have you tried installing anything via the command line? Open a terminal with Applications, Accessories, Terminal. 
```

sudo apt-get update
sudo apt-get install <packagename>

```
Example: sudo apt-get install 2vcard
You will be asked for your password but won't see it entered as you type.

Please give us the error messages you get, if any.

If you have only used the GUI package tools, you also might try updating the following:
```

sudo update-apt-xapian-index
*if it says it is up-to-date:*
sudo apt-get --reinstall install apt-xapian-index

```

---

### Post by moving shadow on 2009-09-11
> **drs305 said:**
> Welcome to the Ubuntu forums.

Have you tried installing anything via the command line? Open a terminal with Applications, Accessories, Terminal. 
```

sudo apt-get update
sudo apt-get install <packagename>

```Example: sudo apt-get install 2vcard
You will be asked for your password but won't see it entered as you type.

Please give us the error messages you get, if any.

If you have only used the GUI package tools, you also might try updating the following:
```

sudo update-apt-xapian-index
*if it says it is up-to-date:*
sudo apt-get --reinstall install apt-xapian-index

```

Firstly thanks for all the quick responses,  when I try and do anything with the terminal, I enter the code as above I then get asked for my password, after i enter it it just returns to the first line of the terminal :~$ . 

No error messages.

I should say the password i set for the admin is just blank, but it worked fine up until recently.

---

