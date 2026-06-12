---
title: "Best way to give root access to certain folders"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-05-13
I did some searching about this, but I'm a little confused, as some of my searches recommends against logging into root.The problem is with Seamonkey. When I try to install extensions I get an error saying something like, the folder is locked, you need to log in as root and give access.

So I did the sudo thing and set my root password. Now...what would be the best, easiest, fastest, way to give root access to those folders?

Thank you for any and help.

---

### Post by Bodsda on 2009-05-13
Hi,

Logging in as root is discouraged because of the potential to destroy your system with as little as a single command. Therefore instead Ubuntu uses sudo which gives temporary root permissions allowing the normal user to access/write to files and folders that they would not normally be able to write to. 

Instead of changing the folder permissions I would suggest when you need to install extensions that you open seamonkey as root with gksudo

```
gksudo seamonkey
``` 

This will allow you to add extensions without creating as many security risks, however if you really want to change the permissions on the folder you will need to do
```
sudo chmod +w /path/to/folder
```

This will give your user write permissions to that folder

Hope this helps, regards,

Bodsda

---

### Post by h8uthemost on 2009-05-13
Thank you for the reply Bodsda. It's really appreciated.

Ok, so just to make sure I understand this...when I want to install an extension in Seamonkey, I first open Seamonkey in Terminal with the *gksudo seamonkey* command? And then just install the extension in Seamonkey as usual?

Thank you for the help. That sounds a lot easier and less riskier than logging in as root.

EDIT: Ha! That worked, and was extremely easy. Thank you so much for your help Bodsda!

---

### Post by Bodsda on 2009-05-13
> **h8uthemost said:**
> Thank you for the reply Bodsda. It's really appreciated.

Ok, so just to make sure I understand this...when I want to install an extension in Seamonkey, I first open Seamonkey in Terminal with the *gksudo seamonkey* command? And then just install the extension in Seamonkey as usual?

Thank you for the help. That sounds a lot easier and less riskier than logging in as root.

EDIT: Ha! That worked, and was extremely easy. Thank you so much for your help Bodsda!

Yep, thats all you do.

Glad this helped :)

If a graphical program ever moans about permissions when your trying to do this sort of thing, as long as you know what its installing opening it with gksudo will almost always fix the problem.

Anyway, your welcome,

Bodsda

---

