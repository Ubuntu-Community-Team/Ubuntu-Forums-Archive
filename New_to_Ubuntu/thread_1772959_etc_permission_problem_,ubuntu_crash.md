---
title: "etc/ permission problem ,ubuntu crash"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by drathi on 2011-06-01
Hi,

I have changed permission for etc folder in ubuntu by mistake ,Now it lead to all ubuntu corrupted. Kindly suggest any solution to repair it.If I install ubuntu from start then how i can delete my old ubuntu files.

Looking for your support. Thanks.

---

### Post by Paddy Landau on 2011-06-01
Did you change permission only for the /etc folder, or for all files within it?
Did you change only the permissions or did you change the owner or group as well?

---

### Post by drathi on 2011-06-01
> **Paddy Landau said:**
> Did you change permission only for the /etc folder, or c?
Did you change only the permissions or did you change the owner or group as well?


I just changed permission for only folder /etc and all file within it.Then after when I started ubuntu,it was crashed..!

---

### Post by coffeecat on 2011-06-01
> **drathi said:**
> I just changed permission for only folder /etc and all file within it.Then after when I started ubuntu,it was crashed..!

If you changed the permissions for the /etc directory and every sub-directory and file within /etc (that is, a recursive permissions change) then it would be nearly impossible to undo the damage. But before we assume that to be the case, please post the *exact* command you used to change permissions, otherwise we are speculating.

---

### Post by drathi on 2011-06-01
> **coffeecat said:**
> If you changed the permissions for the /etc directory and every sub-directory and file within /etc (that is, a recursive permissions change) then it would be nearly impossible to undo the damage. But before we assume that to be the case, please post the *exact* command you used to change permissions, otherwise we are speculating.
 
 
Unfortunatly I used this below command:
 
sudo chmod 644 /etc

---

### Post by coffeecat on 2011-06-01
> **drathi said:**
> Unfortunatly I used this below command:
 
sudo chmod 644 /etc

If you are sure you did 'sudo chmod 644 /etc' then you have only changed permissions on your /etc folder amd none of the contents. Permissions for the /etc folder should be 755, so:

```
sudo chmod 755 /etc
```However, in an earlier post, you said that "I just changed permission for only folder /etc and all file within it." To do that you would have had to have run 'sudo chmod -R 644 /etc'. Note the -R option. If you did run chmod with the -R option, then all folders and files within /etc will now have permissions of 644 and your system will be beyond practical repair.

So - did you run chmod with or without the -R option?

---

### Post by drathi on 2011-06-02
> **coffeecat said:**
> If you are sure you did 'sudo chmod 644 /etc' then you have only changed permissions on your /etc folder amd none of the contents. Permissions for the /etc folder should be 755, so:

```
sudo chmod 755 /etc
```However, in an earlier post, you said that "I just changed permission for only folder /etc and all file within it." To do that you would have had to have run 'sudo chmod -R 644 /etc'. Note the -R option. If you did run chmod with the -R option, then all folders and files within /etc will now have permissions of 644 and your system will be beyond practical repair.

So - did you run chmod with or without the -R option?


Ok I got it.Now I want to remove all ubuntu files from my system and free hard disk space.Can I do it by using window 7.I also looking re-installation of ubuntu later.

---

### Post by Paddy Landau on 2011-06-02
If you want to completely remove Ubuntu, simply install Windows 7 over it. When you install, you probably will be given the option of where to install; just tell it to use the entire disk (assuming you have nothing else there you want to keep). It will overwrite Ubuntu.

**Warning:** Back up _all_ data first!

EDIT: I might have misunderstood. Do you have Windows 7 already installed on your machine?

---

