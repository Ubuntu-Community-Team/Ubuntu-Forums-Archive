---
title: "Granting user permissions to the /var/www folder"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by ajaykk on 2011-08-11
I am trying to grant a user read/write permissions to the /var/www folder. The owner for the folder is www-data. I tried usermod to add user to www-data and it adds the user(using members returns www-data and user), but i still don't have permissions to the folder.

---

### Post by ajaykk on 2011-08-11
Fixed it by changing the group from root to www-data. Earlier it was root.

```
sudo chown -R www-data:www-data /var/www
```

---

