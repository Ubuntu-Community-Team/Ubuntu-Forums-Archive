---
title: "Modifying a script having trouble with adding a repository."
date: 2009-02-16
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-16
I am modifying a script to make a live cd  and not having to do any commands at all. I need to add some repositorys for certain programs like picasa and boxee. Boxee repository is deb [http://apt.boxee.tv](http://apt.boxee.tv) hardy main               Now I am trying to find out how to add this in the sources.list without going into a editor or anything at all for that matter cept a command that types it in and saves it to the sources.list with that one command anyone know of any?

---

### Post by snova on 2009-02-16
If the script is being run as root, add it to the end of /etc/apt/sources.list:

```
echo "deb http://apt.boxee.tv hardy main" >> /etc/apt/sources.list
```

Otherwise, as a normal user, sudo won't *quite* do it, as the shell (not sudo) handles the >> operator. Thus we would use the tee command with the -a option (for appending):

```
echo "deb http://apt.boxee.tv hardy main" | sudo tee -a /etc/apt/sources.list
```

Potentially undesirably, this will ask the user for their password. If it's meant to be graphical, use gksudo instead.

---

### Post by ericeclifford on 2009-02-17
ty it worked I beleive ill run the script and find out but I tried it and it does copy the url to the bottom of the list. Ty again

---

