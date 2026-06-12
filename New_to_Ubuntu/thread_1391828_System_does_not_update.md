---
title: "System does not update"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Shubhank on 2010-01-27
When I update using " Update Manager "
IT Shows Following ERROR
"[SIZE=3][COLOR=Red]Could not download all repository indexes[/COLOR][/SIZE]

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct. "

how to cope up ?????
and my software centre  shows all packages but is not able to install any............
                     
Thanks in Advance

---

### Post by jd65pl on 2010-01-27
Its possible you have an incorrect repository in your sources list, or that the repository is not currently available.

Can you post the contents of /etc/apt/sources.lst

```
cat /etc/apt/sources.list
```

---

### Post by warfacegod on 2010-01-27
> **Shubhank said:**
> 
and my software centre  shows all packages but is not able to install any............
                     
Thanks in Advance

Right click you Applications, Places, System menu> select Edit Menus> Highlight Ubuntu Software Center> click Properties to the right> change Command from:

/usr/bin/software-center

To:

gksudo software-center (note the space)

---

