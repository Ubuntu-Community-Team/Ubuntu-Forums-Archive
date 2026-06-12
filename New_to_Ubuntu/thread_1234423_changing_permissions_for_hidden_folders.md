---
title: "changing permissions for hidden folders"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by raziiq on 2009-08-07
Hi there.

Is there any way i can change the permissions for hidden folders (name starting with ".") with root being the owner of the file? I want write permissions on a hidden folder but my user does not have write permissions to that folder.

I know i can do sudo but is there any other solution to this?

---

### Post by philcamlin on 2009-08-07
to get permission 

sudo chown -R user:user /secret_path

to put back the permissions 

sudo chown -R root:root /secret_path

---

### Post by raziiq on 2009-08-07
thanks for the reply, i know about sudo but i dont wanna use that, is there any other way to do that?

---

### Post by y-lee on 2009-08-07
> **raziiq said:**
> thanks for the reply, i know about sudo but i dont wanna use that, is there any other way to do that?

Open a terminal and type
```
gksudo nautilus
```

Now do what you want in nautilus. BE CAREFUL nautilus is running as root.

---

### Post by raziiq on 2009-08-07
i think i can get the write permissions only using sudo or gksudo right?

---

### Post by y-lee on 2009-08-07
> **raziiq said:**
> i think i can get the write permissions only using sudo or gksudo right?


philcamlin above told you how to change permissions using sudo, my suggestion was to open nautilus as root using gksudo. I left unsaid the fact you need to show hidden files hit ctrl and H at the same time in nautilus. Now find the file whose permissions you wish to change and you should be able to change permissions by right clicking and choosing properties or something. (I am on a win machine right now so...)

---

