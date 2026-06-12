---
title: "Package Manager error"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Chinedu on 2009-06-05
My package Manager reports an error each time i open it to install updates. the error is 
"An unresolvable error occured while reading the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Read error-read(5 input/output error), E: The package lists or status file could not be parsed or opened.'"
Please how do i rectify this problem because i cannot even install any software because of this error status.

---

### Post by porchrat on 2009-06-05
It could be that Ubuntu is trying fetch stuff from the CD instead of the respositories on the net.

An easy thing to try though (without mucking around with the system too much) is to run this command in the terminal:

```
sudo apt-get autoclean
```

Should remove any unneeded or partially installed/downloaded packages as this may be causing the problem.

Another thought is have you been editing the /etc/apt/sources.list file? Please post the contents of it.

In case you don't know how to do that you can use this command in the terminal:

```
cat /etc/apt/sources.list
```

Then copy and paste what you get into your next post.

EDIT: Actually you don't need to do that, just check to see if the line containing a reference to "cdrom" starts with a "#" character. If it doesn't, then add one, if it does, then perhaps try deselecting all the repositories through synaptic, saving and restarting.

---

### Post by jnw222 on 2009-06-05
try 
sudo apt-get -f 
         or was it
sudo apt-get install -f

---

### Post by porchrat on 2009-06-05
> **jnw222 said:**
> try 
sudo apt-get -f 
         or was it
sudo apt-get install -f

sudo apt-get install -f

---

