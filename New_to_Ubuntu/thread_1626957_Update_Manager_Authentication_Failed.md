---
title: "Update Manager Authentication Failed"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by slixz85 on 2010-11-20
Thanks for checkin this post. 
hang with me new to linux
when i try to update to meerkat 10.10 from 10.04 lts from the gui update manager i get an error message of authenticating the upgrade failed. there may be a problem with the network or with the server. i have tried to upgrade by wired and wifi connection and no difference my signal is strong so there is no problem with my connection. from surfin the net i have found post about restoring the default authentication key, saying click restore default. when i go to authentication tab under software sources there are no keys under trusted software providers. is this my problem if so. others restore default buttons said they solved problem but mine dont change anything.

---

### Post by Najand on 2010-11-20
> **slixz85 said:**
> Thanks for checkin this post. 
hang with me new to linux
when i try to update to meerkat 10.10 from 10.04 lts from the gui update manager i get an error message of authenticating the upgrade failed. there may be a problem with the network or with the server. i have tried to upgrade by wired and wifi connection and no difference my signal is strong so there is no problem with my connection. from surfin the net i have found post about restoring the default authentication key, saying click restore default. when i go to authentication tab under software sources there are no keys under trusted software providers. is this my problem if so. others restore default buttons said they solved problem but mine dont change anything.

Is it possible to write the exact error or take a screenshot from your display (using "Print Screen" button)?

---

### Post by slixz85 on 2010-11-21
when i click upgrade it just gives the above message no other error messages. i have all other updates done so none show in the update manager. when i click check though it pulls the below error message.
also for some reason my copy and paste dont work. i know how to use it but wont paste neither does control v

so i attached a screenshot.

i have tried reinstalling gpg again but no luck did it through synaptic i like installing stuff through the terminal just dont know all steps exactly

---

### Post by jaygo on 2011-04-29
you might need to fix the permissions in /etc/apt/ . Based on the permissions in another machine, I set all the files but secring.gpg to readable by all. That fixed it in my case.

---

