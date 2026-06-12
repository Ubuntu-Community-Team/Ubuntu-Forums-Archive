---
title: "Error when updating"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by newinubu on 2009-07-14
i get an error when typing the following:
sudo apt-get update.
the error is:
E: Type 'For' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
 also my synaptic manager also quote the same error when opening

---

### Post by unutbu on 2009-07-14
newinubu, open a terminal (Applications>Accessories>Terminal) and type
```

cd /etc/apt                            # change to /etc/apt directory
sudo cp sources.list sources.list.bak  # make a backup of sources.list
gksu gedit sources.list                # to edit sources.list with root privileges
```

Search for a line that contains the word "For". It should be on line 46.

You can make synaptic and apt-get ignore this line by placing a # symbol at the 
beginning of the line. For example, change
```

For ...

```
to
```

# For ...
```

This is called commenting-out since lines that begin with a # symbol are comments (meant for humans, but not the computer).

Save and exit gedit.
Then type
```

sudo apt-get update
```

If this does not solve your problem, please post the contents of sources.list here.
Using [code tags]("http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") would be appreciated.

---

### Post by drs305 on 2009-07-14
Hi newinubu, 

Welcome to the Ubuntu forums. You have found the Beginners Team forum. There is a "Absolute Beginners" forum where questions such as this are normally posted. If you click on the "Ubuntu Forums" link at the top left of the page you will see all the different sections. The "Absolute Beginners" is the one new users generally visit. You can take a look and see there is a "General" forum and forums devoted to specific topics.

I will send you a PM and we will get your problem fixed fairly quickly.

---

### Post by overdrank on 2009-07-14
Hi and welcome newinubu, I have moved your post an its response to its own thread.

---

