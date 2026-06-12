---
title: "Trouble logging in."
date: 2010-11-19
forum: New to Ubuntu
---

### Post by joegats916 on 2010-11-19
I have three accounts on my xubuntu system, one for myself, my wife and my son. Both my son's and my wife's work great when you put in the password on the login screen, but when I try to login, it just cycles through a black screen with writing thats gone too fast for me to read and back to the login screen. I was able to login for about two weeks since original install and this problem seems to have come from no where.

I tried changing the password via the sudo passwd command as was recommended to me by another site with no success.

---

### Post by sandyd on 2010-11-19
> **joegats916 said:**
> I have three accounts on my xubuntu system, one for myself, my wife and my son. Both my son's and my wife's work great when you put in the password on the login screen, but when I try to login, it just cycles through a black screen with writing thats gone too fast for me to read and back to the login screen. I was able to login for about two weeks since original install and this problem seems to have come from no where.

I tried changing the password via the sudo passwd command as was recommended to me by another site with no success.

whats your username.

go to one of the working accounts, and run this
```

sudo cp /home/**your_username_here**/.xsession-errors ~/Desktop/xsession-errors
gedit ~/Desktop/xsession-errors
```
copy and paste contents of file.

---

### Post by joegats916 on 2010-11-19
I was able to use the command by using the recovery console on the profile I'm having trouble with.  The file was created in the desktop directory.  However, when i run gedit, it says that it's not installed.  Furthermore, when I try to access the file using open office, it says access denied.

---

### Post by sandyd on 2010-11-22
> **joegats916 said:**
> I was able to use the command by using the recovery console on the profile I'm having trouble with.  The file was created in the desktop directory.  However, when i run gedit, it says that it's not installed.  Furthermore, when I try to access the file using open office, it says access denied.

run
```

apt-get install gedit
```

---

