---
title: "Firefox--work off line checked"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by hosmer on 2009-03-24
After connecting to the net, I start firefox and the "work off line box" is always checked, so i must uncheck it in order to use firefox on-line.
How can i make working on line the default?

---

### Post by kanikilu on 2009-03-24
What are the network connection settings in Firefox?

Edit > Preferences > Advanced > Connection > Settings

---

### Post by hosmer on 2009-03-24
> **kanikilu said:**
> What are the network connection settings in Firefox?

Edit > Preferences > Advanced > Connection > Settings

I can only go to Advanced --No option for Connection > Settings

I think I came across a post a while ago addressing this problem.
I haven't been able to find it.

The post said the problem is in the profile folder.
I'm to new to Linux to find this let alone fix it.

Thanks

---

### Post by kanikilu on 2009-03-24
A quick way to check that your profile has the correct permissions would be to:

Open a terminal with Applications > Accessories > Terminal.

Then type ```
ls -l ~/.mozilla
``` and copy and paste the output here.

---

### Post by hosmer on 2009-03-24
> **kanikilu said:**
> A quick way to check that your profile has the correct permissions would be to:

Open a terminal with Applications > Accessories > Terminal.

Then type ```
ls -l ~/.mozilla
``` and copy and paste the output here.

hear ya go

user1@user1-desktop:~$ ls -l ~/.mozilla
total 8
drwx------ 3 user1 user1 4096 2009-03-03 19:48 extensions
drwx------ 3 user1 user1 4096 2009-03-03 19:48 firefox
user1@user1-desktop:~$ 

Thanks for the help

---

### Post by kanikilu on 2009-03-24
That looks fine. I don't think it's permissions, but can you also post the output of:

```
ls -l ~/.mozilla/firefox/
```

Your profile is stored in the "firefox" directory...

---

### Post by hosmer on 2009-03-24
> **kanikilu said:**
> That looks fine. I don't think it's permissions, but can you also post the output of:

```
ls -l ~/.mozilla/firefox/
```

Your profile is stored in the "firefox" directory...

user1@user1-desktop:~$ ls -l ~/.mozilla/firefox/
total 8
drwx------ 7 user1 user1 4096 2009-03-24 16:32 dl2ypbkm.default
-rw-r--r-- 1 user1 user1   94 2009-03-03 19:48 profiles.ini
user1@user1-desktop:~$

---

### Post by kanikilu on 2009-03-24
Yeah that all looks fine. Hmm... :???:

I may be stumped...the only other thing I might try is to create a new Firefox profile: [http://support.mozilla.com/en-US/kb/Managing+Profiles#Starting_the_Profile_Manager](http://support.mozilla.com/en-US/kb/Managing+Profiles#Starting_the_Profile_Manager)

---

### Post by hosmer on 2009-03-24
> **kanikilu said:**
> Yeah that all looks fine. Hmm... :???:

I may be stumped...the only other thing I might try is to create a new Firefox profile: [http://support.mozilla.com/en-US/kb/Managing+Profiles#Starting_the_Profile_Manager](http://support.mozilla.com/en-US/kb/Managing+Profiles#Starting_the_Profile_Manager)

OK i'll give it a go thanks hosmer grunch

---

### Post by geofff on 2010-07-27
This has recently started happening to me. The solution was to right click on network manager icon and ensure that the "enable networking" box was ticked.

---

### Post by mikewhatever on 2010-07-27
I think there is a setting in Firefox's 'about : config' that you can change to prevent it from checking for network connection, and consequently going into offline mode.
Search for 'toolkit.networkmanager.disable'.
[http://kb.mozillazine.org/Toolkit.networkmanager.disable](http://kb.mozillazine.org/Toolkit.networkmanager.disable)

---

