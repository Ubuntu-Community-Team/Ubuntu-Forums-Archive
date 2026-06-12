---
title: "database: I want one- KISS"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by penguinv on 2011-02-01
I'd like to use a database. I want to have a bunch of data (USDA Food info) and have it searchable by query. This isnt rocket science. I will use this project to learn what's up with databases these days and how to use one.

(I have programmed in rbase in the deep dark distant past.)

What do I use?  Why not keep it normal and Vanilla for now.
I will be starting with ASCII or better yet, a .mdb file.

Thanks..

PS I googled. I looked at 30 thread-headings. Nothings is anything like this question.

---

### Post by lavinog on 2011-02-01
MySQL and postgreSQL are pretty popular.

mongoDB is something that I recently heard about that looks interesting.

Where would you like to store the data (remotely or locally)
What kind of frontend do you want?
Many database systems use a server/client type model where the frontend and the database are different programs (unlike MS Access where the database and frontend can be stored in one file)

A web frontend can be quick to setup if you are not focusing on looks, and has the added benefit of not requiring extra software.

Go to [http://w3schools.com/](http://w3schools.com/) and look at the SQL and php training.  A book on MySql+PHP is also a good resource.

If you are looking for something smaller, you might be fine with using python and storing your data in a pickle file.

---

### Post by Zill on 2011-02-01
penguinv:  You might like to take a look at [OpenOffice.org Base]("http://www.openoffice.org/product/base.html") - it's in the repos:
```
sudo apt-get install openoffice.org-base
```

---

