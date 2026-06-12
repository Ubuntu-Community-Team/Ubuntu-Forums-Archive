---
title: "desktop icons missing and broken file manager"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by greggy.gregory on 2010-02-13
i am pretty new to linux and have only been using it for a couple weeks now. i installed Picasa from google just now and since then my desktop icons have disapeared and if i open the file manager it closes within 5 seconds. i have tried rebooting the computer and have now completly removed picasa and the problem is still there.
any ideas what the problem might be and how i can fix it?

---

### Post by oldos2er on 2010-02-13
Which version of Ubuntu are you using? Can you open a terminal, (Applications, Accessories, Terminal), type in **nautilus**, and post the output here?

---

### Post by amsterdamharu on 2010-02-13
Did you install picasa form synaptic package manager? If so you should report the bug because that sounds like it has done some serous damage.

Can you create a new user and log in as that new user to see if this user has the same problems? If the new user doesn't have the same problems you might consider deleting settings files in your homedir (my guess .nautilus with rm -R .nautilus).

---

### Post by greggy.gregory on 2010-02-13
> **oldos2er said:**
> Which version of Ubuntu are you using? Can you open a terminal, (Applications, Accessories, Terminal), type in **nautilus**, and post the output here?

i am using ubuntu 9.10, i will post the terminal output once i reboot back into ubuntu. im in win 7 now cause i got fed up with it not working

---

### Post by greggy.gregory on 2010-02-13
> **amsterdamharu said:**
> Did you install picasa form synaptic package manager? If so you should report the bug because that sounds like it has done some serous damage.

Can you create a new user and log in as that new user to see if this user has the same problems? If the new user doesn't have the same problems you might consider deleting settings files in your homedir (my guess .nautilus with rm -R .nautilus).

yes i did install it from the package manager, after adding googles stable repository(not the beta one which they link to by defult if you go to the picasa page) how do i reprt a bug? will it have an option in the package manager?

---

### Post by greggy.gregory on 2010-02-13
terminal output when i enter the comand nautilus

```
greg@greg-ubuntu:~$ nautilus

(nautilus:4221): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:4221): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4221): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4221): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Segmentation fault
greg@greg-ubuntu:~$ 


```@**amsterdamharu**
i created and new user and the new user still has the same problems

also something i just noticed, i enabled the "automaticly remember running applications when logging out option" then decided i didnt want it so disabled it, yet it is still remembering what i last had open even though i have checked the option is not enabled any more

---

### Post by oldos2er on 2010-02-13
Some googling turned up a possible solution to Nautilus seg fault: ```
sudo rm ~/.local/share/gvfs-metadata/*
```

---

### Post by greggy.gregory on 2010-02-15
> **oldos2er said:**
> Some googling turned up a possible solution to Nautilus seg fault: ```
sudo rm ~/.local/share/gvfs-metadata/*
```

just tried this, problem still exists

---

### Post by greggy.gregory on 2010-02-25
does anyone have any more advice, my problem is not solved and i would rather not have to reinstall my entire OS

---

