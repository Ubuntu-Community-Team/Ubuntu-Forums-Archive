---
title: "Rename main (only) login user account?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by egalvan on 2009-08-08
Installed edubuntu 9.04 for a young lady on a used machine.

But I made the critical mistake of setting the login name wrong. :(
She's four years old, so these things are important;
it's *her* computer :)


I know that I can:

erase and start over (it's only been three days, so nothing major)
( and it's what the "owner" would prefer... it's *her* computer )

or

add the correct name ( as a  second user )
( and it's what I would prefer... less work )


But I'm curious...
is it *possible* to rename the user account?

Many thanks
ErnestG

As many fathers already know, it's difficult to say "No" to your four year old daughter.. :confused:

---

### Post by mprince on 2009-08-08
> add the correct name ( as a second user )
( and it's what I would prefer... less work )

I say go with the 'create a second account' method you mention.

----

There is another thread about this, but I'm unsure if it works for edubuntu. See here:

[http://ubuntuforums.org/showthread.php?t=64021](http://ubuntuforums.org/showthread.php?t=64021)

---

### Post by unutbu on 2009-08-08
Since the account is only 3 days old, you could try this:
```

sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWGROUP OLDGROUP
```

OLDNAME is the current login name
NEWNAME is the desired login name

On a default install,
OLDGROUP is the same as OLDNAME,
NEWGROUP is the same as NEWNAME.

The "usermod" command will change the login name and move the home directory from /home/OLDNAME to /home/NEWNAME

The "groupmod" command will rename the old group name to the new group name (for permissions).

There are a few things that might need fixing after issuing the above commands.
If she's set a background image at /home/OLDNAME/Pictures/background.jpg, then the background image will fail to display because the background is now at /home/NEWNAME/Pictures/background.jpg. The same story goes for any configuration file that names a file in /home/OLDNAME, or in any way refers to OLDNAME. So you may have to redo some configuration settings.

If you have setup wine, there is a bit of difficulty here too: wine creates a couple of symlinks with the name of the account "hard-coded" into the path of the symlink. You would have to delete these broken symlinks and reconstruct them with the appropriate paths.

---

### Post by colau on 2009-08-15
> **unutbu said:**
> Since the account is only 3 days old, you could try this:
```

sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWGROUP OLDGROUP
```

If the account is 5 years old, what would be the solution?

---

### Post by unutbu on 2009-08-15
[COLOR="Red"]If your OLDNAME is sufficently unique[/COLOR], you could follow up the "usermod"  and "groupmod" commands with this:
```

find /home/NEWNAME/ -type f -name '*' -exec sed -i 's/OLDNAME/NEWNAME/g' {} \;
```

This "find" command will loop through every single file in /home/NEWNAME and change every occurrence of OLDNAME *within* the contents of the file to NEWNAME. This is an attempt to correct any mention of OLDNAME in your hidden dot (configuration) files.

The reason why this command is dangerous is because your OLDNAME might be something short like "hank" *which is a substring of other words*. If you were trying to change username "hank" to "fred", do not use the above command because any document that contains the word "Thanks" would be changed to "Tfreds". Terrible damage can be done with the above command. Be careful. 

I wouldn't recommend trying the above command without backing-up first.

The other problem that sometimes occurs is that your .wine directory contains symlinks whose path contains the name OLDNAME.
(Things like this
/home/NENWAME/.wine/drive_c/windows/profiles/OLDNAME/Desktop
become broken symlinks).

I don't have a one-liner to fix the broken symlinks.
As far as I know there are not so many such symlinks however, so it is not hard to fix them manually.

---

### Post by colau on 2009-08-15
Thank you.
Creating a new user account and deleting the older account may be better.

---

### Post by unutbu on 2009-08-15
Yes, I definitely agree! :)

---

