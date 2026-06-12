---
title: "Managing users"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by MasterMind Karthik on 2010-07-10
Well guys,

I was trying to install Apache... According to the book that I am following, "Begining PHP6, Apache, MySQL Web development by Worx", it was mentioned to create a user dedicated to run the apache deamon. For that it was mentioned to type:
```

groupadd www-data
useradd -r -g www-data

```

But I cant get it working... I get an error message saying that my syntax is incorrect :o

---

### Post by Jean-Vivien on 2010-07-10
Hi,
 
 
you specify the initial group of the user (value after the -g parameter) and then after that you need to write the username/login, example :
```

useradd -r -g www-data www-data

```
 
For all commands, there is a manual page, example :
```

man useradd

```

---

### Post by stmiller on 2010-07-10
Wait!

You don't need to do this. On Ubuntu and Debian when you install apache2, it creates the correct users and groups automatically.

:)

---

