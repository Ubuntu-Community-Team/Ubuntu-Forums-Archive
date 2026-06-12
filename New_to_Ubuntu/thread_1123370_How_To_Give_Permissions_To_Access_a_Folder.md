---
title: "How To Give Permissions To Access a Folder"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Sethalos on 2009-04-12
Hello, I'm trying to open up a file in Kubuntu /etc/mt-daapd.conf and change it. I'm getting permission errors and it won't allow me to copy/cut/paste into the folder or alter the file.

I'm not sure of the command to use to give myself permissions.

Thanks

---

### Post by Eisenwinter on 2009-04-12
Make sure to be a root user, when trying to modify files on the root filesystem.

Type the following, in the terminal:

```
sudo gedit /etc/mt-daapd.conf
```

EDIT:
I know, that didn't really answer the question, but it's safer to do it that way.

If you're looking to always be able to edit that file, you need to chmod it.

```
sudo chmod 770 /etc/mt-daapd.conf
```

This will give the root user, and you, access to read, write, and execute the file. Note that still, it's better if you just used sudo or **su** to give yourself temporary permission to edit the file, rather than having it open like that.

---

### Post by MrWES on 2009-04-12
> **Eisenwinter said:**
> Make sure to be a root user, when trying to modify files on the root filesystem.

Type the following, in the terminal:

```
sudo gedit /etc/mt-daapd.conf
```

EDIT:
I know, that didn't really answer the question, but it's safer to do it that way.

If you're looking to always be able to edit that file, you need to chmod it.

```
sudo chmod 770 /etc/mt-daapd.conf
```

This will give the root user, and you, access to read, write, and execute the file. Note that still, it's better if you just used sudo or **su** to give yourself temporary permission to edit the file, rather than having it open like that.

Really shouldn't mix command sudo with a graphical text editor, better to do a:

```
sudo vi /etc/mt-daapd
```
or
```
sudo nano /etc/mt-daapd
```
or
Alt + F2
then
```
gksu gedit /etc/mt-daapd
```

Bill

---

### Post by Paqman on 2009-04-12
> **MrWES said:**
> 
Alt + F2
then
```
gksu gedit /etc/mt-daapd
```


I'd lean strongly towards this option for the Absolute Beginners forum. Maybe nano. Definitely not vi.

---

### Post by Thedjatclubrock on 2009-04-12
You're using KDE, so you would:

```
kdesu kate /etc/mt-daapd
```

---

### Post by Paqman on 2009-04-12
> **Thedjatclubrock said:**
> You're using KDE, so you would:

```
kdesu kate /etc/mt-daapd
```

We have a winner! How did it take four of us to come up with the right command to edit a text file?

---

### Post by Sethalos on 2009-04-12
Excellent.  Thank you very much that did it.

Love this forum.

Have a great Easter.

Seth

---

### Post by MrWES on 2009-04-12
> **Paqman said:**
> We have a winner! How did it take four of us to come up with the right command to edit a text file?

I've actually done that more times than I care to take credit for; posting a GNOME command for a KDE user...duh!

~Bill

---

