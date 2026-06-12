---
title: "Finding a file"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-09
I am trying to find a file. It is named Rowester (the owner of a computer that I am using remotely).

The command I have used (and it works) is:

ssh -X Rowester. (-X is for graphics)

As I said it works. Now someone else wants to use it and I cannot find it. I need to so I can give it to him. The search for files command does not seem to work. I use Rowester everyday to log onto this remote computer - I know it is there - somewhere. I need what is in it such as network addresses and so on. I do not want to look up those values again - once is enough. 

I am out of tricks. I echoed $PATH and looked in each one and it was not there. 

So what is another command to find it?

Any help appreciated.


newport_j

---

### Post by philinux on 2010-02-09
```
sudo updatedb

then

locate filename
```

---

### Post by Paddy Landau on 2010-02-09
I confess that I find myself a little mystified. [FONT=Courier New]ssh[/FONT] is used to connect to a remote computer, not to find files.

You can try the following:
```
find / -name Rowester 2>/dev/null
```(You may need to use sudo.) This will find all files with the name Rowester on the entire drive. If you're unsure of capitalisation, then use [FONT=Courier New]-iname[/FONT] instead of [FONT=Courier New]-name[/FONT]. If the file has extra characters, e.g. an extension, then use this:
```
find / -iname 'Rowester*' 2>/dev/null
```Remember to put in the quotes as indicated.

---

### Post by newport_j on 2010-02-09
Yes, I said that it is used to connect to remote computers. It has for me a lot of info about network addresses. I want to give a copy to someone so that they can use the same computer remotely.

I do not offhand know these network addresses, but I am sure this files has them. If I can only find it.

Newport)j

---

### Post by Paddy Landau on 2010-02-09
> **newport_j said:**
> ... If I can only find it.
Did you try what philinux or I suggested?

---

### Post by falconindy on 2010-02-09
What you're looking for isn't a file. Do this:

```
host Rowester
```
Give them the IP address that is resolved by the name.

---

### Post by talonmies on 2010-02-09
try /etc/hosts

What you are providing to ssh is a host name, not a file name. The IP address of the host name is either coming from an external DNS server look up, or your local /etc/hosts file. I am going to guess the latter.

---

