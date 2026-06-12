---
title: "installing dev c++"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Sp1ck on 2009-01-29
i'm trying to install dev c++ on ubuntu 8.10
every time it says permission denied
i've tried sudo su - 
and it still doesn't work

the install readme tells me to go into root for the install but everything says thats a bad idea

i really need dev c++ for school i'm learning so the good compilers are useless to me

please if you got it installed without going into root your help will be appreciated

---

### Post by Binny88 on 2009-01-29
'su' wont work in ubuntu,Type 'sudo' & type the previous command.It will ask u to enter the password. just type the password u.Remember you wont see any asterisks but a blank space while u type, just keep on typin the password & then hit enter.

---

### Post by KIAaze on 2009-01-29
Are you talking about this DevC++?: [http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html)
It doesn't have a GNU/Linux version as far as I know.

Could you post a link to the software you're trying to install?

If you trust the package you downloaded, you can use root to install it if necessary.

---

### Post by mhh91 on 2009-01-29
or type "sudo bash" to become root in ubuntu :)

---

### Post by Sp1ck on 2009-01-29
i got it installed without going into root but now i get this 

./devcpp: error while loading shared libraries: libqtintf.so: cannot open shared object file: No such file or directory

there is a libqtintf.so in the same folder and it won't open for some reason.

---

### Post by KIAaze on 2009-01-29
If the library is in the same directory as the executable, just run this before running the executable:
```
export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
```

If it works, I recommend putting libqtintf.so into /usr/lib (default location where libraries are looked for).

But you haven't answered my question:
Is this the program you're trying to install?:
[http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=12148](http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=12148)

I didn't know they had a GNU/Linux port! It's not listed on the main website.

---

### Post by blissfulpenguin on 2009-08-04
> **KIAaze said:**
> Are you talking about this DevC++?: [http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html)
It doesn't have a GNU/Linux version as far as I know.

Could you post a link to the software you're trying to install?

If you trust the package you downloaded, you can use root to install it if necessary.

"Source code : Delphi 6 Source code of Dev-C++ is available for free under the GNU General Public License (GPL)" -- [http://bloodshed.net/devcpp.html]("http://bloodshed.net/devcpp.html")
:P

---

### Post by Simian Man on 2009-08-04
Dev-C++ is old, and out of date.  There are **much** better tools available nowadays.  Check out Code::Blocks instead.

---

