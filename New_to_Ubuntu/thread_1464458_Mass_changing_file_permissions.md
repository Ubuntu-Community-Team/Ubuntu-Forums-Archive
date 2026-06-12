---
title: "Mass changing file permissions"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by evil_urna on 2010-04-28
I reformatted today and I used a partition to back up data while I wiped and reinstalled. My problem is that when I copied the files back into my home folder I had to do it via gksudo nautilus and now my file permissions are all wonky now.

I can go back and gksudo nautilus and change the permissions on all the files and folders one by one but there has to be another way to do like a whole folder at once. Is this possible? TIA

---

### Post by jvc26 on 2010-04-28
chown is poss the command you're looking for:

```
sudo chown -R <user>:<group> folder/
```

Would recursively change the user and group to the values you want.

```
man chown
```

Will give you more information.

J

---

### Post by evil_urna on 2010-04-28
> **jvc26 said:**
> chown is poss the command you're looking for:

```
sudo chown -R <user>:<group> folder/
```

Would recursively change the user and group to the values you want.

```
man chown
```

Will give you more information.

J

I am pretty sure I love you but let me check.
the syntax I am looking for would be like so?

```

sudo chown -R <scott>:<scott> Pictures

```

to mass change the permissions on my Pictures folder whilst having my terminal in the home folder?

---

### Post by jvc26 on 2010-04-28
> **evil_urna said:**
> 
```

sudo chown -R <scott>:<scott> Pictures

```


Close, you'd want:

```
sudo chown -R scott:scott Pictures/
``` 

(assuming you're running from the directory above Pictures.

J

---

### Post by Zafrusteria on 2010-04-28
chmod has a recurse switch '-R' so you could use 

```
chmod -R 744 *
```

which would put the the permissions of all files and in all sub-directories to 744. Probably a good start but not what you want though.

You can make this better by using pattens eg *txt *doc *mpg *png as these will only need to be readable and in some cases writable.

You can further refine the changes by using find and using its options for -type and adding a -exec chmod 755 {} \; to find directories, as in 

```
find ./ -type d -exec chmod 755 {} \;
```

That will change the permissions on directories only.

With chmod also look at setting the permissions with letters rather than the octal version. Using the letters allows you to add or remove permissions to owner, group or world.

Take a look at the man pages for chmod and find. 

If you need to reset the owner and group of the files and those in sub directories use chown -R user:user *.

Hope that helps :)

---

### Post by Drenriza on 2010-04-28
[[SIZE=2][COLOR=#000000]Zafrusteria[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=237012") 
 
clever command.

---

### Post by evil_urna on 2010-04-28
> **jvc26 said:**
> Close, you'd want:

```
sudo chown -R scott:scott Pictures/
``` 

(assuming you're running from the directory above Pictures.

J

ok my problem was being straight stupid lol.

ps I love you.

It worked perfectly

---

