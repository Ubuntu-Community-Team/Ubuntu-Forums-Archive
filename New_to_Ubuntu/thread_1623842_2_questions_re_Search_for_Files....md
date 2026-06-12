---
title: "2 questions re Search for Files..."
date: 2010-11-17
forum: New to Ubuntu
---

### Post by dkjMusic on 2010-11-17
1. When I run Search for Files... looking for mysqld.sock in File System, I get No files found. When I repeat the search in /var the file is found. I assumed the search is recursive thru subdirectories. Is this not the case?

2. Do I need to start some sort of indexing daemon to keep whatever index that Search for Files... uses up-to-date?

---

### Post by spikoley on 2010-11-19
It would help if you posted the command you are using.

One way to search for a file is the *locate* command.  Before running it you need to update the data base.

Update the DB:
```
sudo updatedb
```

Run locate:
```
locate filename
```

---

### Post by dkjMusic on 2010-11-20
> **spikoley said:**
> It would help if you posted the command you are using.

One way to search for a file is the *locate* command.  Before running it you need to update the data base.

Update the DB:
```
sudo updatedb
```

Run locate:
```
locate filename
```

I'm not using a command. I'm using (from the menu) Applications/Accessories/Search for Files...

---

### Post by spikoley on 2010-11-21
> **dkjMusic said:**
> I'm not using a command. I'm using (from the menu) Applications/Accessories/Search for Files...

I am not sure how the GUI works.  Maybe somebody else can answer your question.

---

### Post by beew on 2010-11-21
Go to Applications > System Tools> Configuration Editor. If you don't see the Configuration Editior you can make it visible by going to System > Preference > Main Menu and choose System Tools in the left panel, find "Configuration Editor" in the right panel and check the box and it will appear under  Applications > System Tools 

Now open the CE,  on the left panel choose apps > gnome search tool and you will see a range of option on the right panel. Check the box "disable quick search" and close the CE.
Now it will find your files. I don't know why, this seems to be counter intuitive but it works. I guess "quick search" relies on some kind of indexing scheme which needs to be activated or installed, and since it hasn't been searching for file is stuck.

---

### Post by dkjMusic on 2010-11-22
> **beew said:**
> Go to Applications > System Tools> Configuration Editor. If you don't see the Configuration Editior you can make it visible by going to System > Preference > Main Menu and choose System Tools in the left panel, find "Configuration Editor" in the right panel and check the box and it will appear under  Applications > System Tools 

Now open the CE,  on the left panel choose apps > gnome search tool and you will see a range of option on the right panel. Check the box "disable quick search" and close the CE.
Now it will find your files. I don't know why, this seems to be counter intuitive but it works. I guess "quick search" relies on some kind of indexing scheme which needs to be activated or installed, and since it hasn't been searching for file is stuck.

Thanks, that did the trick. The search is now, well, not quick.;)

---

### Post by SeijiSensei on 2010-11-22
locate really is the best choice; it will return the results immediately.  The database is updated nightly automatically by default as well.

---

### Post by dkjMusic on 2010-11-23
> **SeijiSensei said:**
> locate really is the best choice; it will return the results immediately.  The database is updated nightly automatically by default as well.

I just tried locate. It didn't find the file.

---

### Post by spikoley on 2010-11-23
> **dkjMusic said:**
> I just tried locate. It didn't find the file.

Did you run *sudo updatedb* first?

```
sudo updatedb
```
```
locate filename
```

---

### Post by dkjMusic on 2010-11-24
> **spikoley said:**
> Did you run *sudo updatedb* first?

```
sudo updatedb
```
```
locate filename
```

Yep.

---

### Post by spikoley on 2010-11-24
Is there a space in the name?  If so, put quotes around it.

---

### Post by dkjMusic on 2010-11-25
> **spikoley said:**
> Is there a space in the name?  If so, put quotes around it.

Nope. No spaces. The file name is mysqld.sock .

---

### Post by spikoley on 2010-11-25
> **dkjMusic said:**
> Nope. No spaces. The file name is mysqld.sock .

Try searching with just part of the name.

```
sudo updatedb
```
```
locate mysqld
```

Does it find the file that way?

---

### Post by dkjMusic on 2010-11-26
> **spikoley said:**
> Try searching with just part of the name.

```
sudo updatedb
```
```
locate mysqld
```

Does it find the file that way?

Still no. Man, I admire your persistence.

My file is /var/run/mysqld/mysqld.sock . I am not the owner, but the permissions for Others is "Access files" for the directories and "Read and write" for the file itself.

---

### Post by spikoley on 2010-11-26
> **dkjMusic said:**
> Still no. Man, I admire your persistence.

My file is /var/run/mysqld/mysqld.sock . I am not the owner, but the permissions for Others is "Access files" for the directories and "Read and write" for the file itself.

I have no idea what the issue is.  Try searching for another file and see if it finds it.

---

### Post by cmcanulty on 2010-11-26
is there a way to use locate from  the gui? then you can click a file to open it.

---

