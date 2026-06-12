---
title: "installing lamp stack unmet dependencies"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by mvalviar on 2010-09-26
I have this ```
Linux mac-mac 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
```

I'm trying to install LAMP with this ```
sudo apt-get install lamp-server^
```

but I get this ```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2: Depends: apache2.2-common (= 2.2.14-4ubuntu1) but 2.2.14-5ubuntu8.2 is to be installed
  apache2-mpm-prefork: Depends: apache2.2-common (= 2.2.14-4ubuntu1) but 2.2.14-5ubuntu8.2 is to be installed
                       Depends: apache2.2-bin (= 2.2.14-4ubuntu1) but 2.2.14-5ubuntu8.2 is to be installed

```

I tried to google for an answer but it's turning up old how-to's without a note on this.

How do I get around this? I ran apt-get update before installing.

---

### Post by louis--taylor on 2010-09-26
Have you tried:
```
sudo apt-get update 
```before trying to install?

EDIT: I didn't read the last line of your post! It appears that the repositories you are using have some conflicts, are you using the default ubuntu ones or do you have some PPAs or other repositories which might have the 2.2.14-5ubuntu8.2 version in them?

---

### Post by mvalviar on 2010-09-26
I haven't made any changes to sources.list. I did change the repository by doing "select best server". I'll try to change to another repo and try again.

---

