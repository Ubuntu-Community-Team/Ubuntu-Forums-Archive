---
title: "Launching Firefox - help please"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by staib on 2008-12-20
Hi all,

Every time Firefox updates itself my Menu launcher stops working. I'm sure it just because the launch address is too specific - in other words it says:

/usr/lib/firefox-3.0.4/firefox 

Rather than having to update it each time manually (for all user profiles), is there a way of writing this more generically, so Firefox will launch - regardless of the version?

Thanks.

---

### Post by cpetercarter on 2008-12-20
Mine is ```
firefox %u
```

---

### Post by pdtpatrick on 2008-12-20
firefox should be in your environment variables so just type firefox. I dont think you need to use the absolute path to bring it up.

---

### Post by staib on 2008-12-20
> **cpetercarter said:**
> Mine is ```
firefox %u
```

Just to be clear is that:

/usr/lib/firefox %u

Thanks

---

### Post by staib on 2008-12-20
Let's just try with 'firefox' then, I'll see what happens and report back.

---

### Post by staib on 2008-12-20
Nope I then get an error message:

Failed to execute child process "firefox" (No such file or directory)

---

### Post by staib on 2008-12-20
When I tried the following:

```
/usr/lib/firefox %u
```

I get this error message:

Failed to execute child process "/usr/lib/firefox" (Permission denied)

---

### Post by pdtpatrick on 2008-12-20
try running it with sudo ... did you change the permission of that path? do a ls -l on it and see what the current permissions are. 

In any case run sudo /usr/lib/firefox  ... see how that works out.

---

### Post by shalomhk on 2008-12-20
To change permission for all users to read and access the directory type the following command:

chmod 755 firefox                (while in the directory of firefox, and assuming there is a "firefox" file)

OR

chmod 755 [directory where firefox file is in] -R                    

you could change 755 for 666 too

chmod = change user permission
755 = all users may read and execute 
666 = all users may read, execute, write, change, delete... everything
-R = recursive (for all files within the folder to have their permission changed)

---

