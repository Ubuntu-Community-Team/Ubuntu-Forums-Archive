---
title: "searching for software using the command prompt"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by computerguts on 2010-02-04
Can you search for packages to install using the command prompt without using the ubuntu software center ?

---

### Post by morrcahn on 2010-02-04
You mean the terminal? Yes: 

sudo aptitude search PROGRAMNAME
or
sudo apt-get search PROGRAMNAME

And then use

sudo aptitude (or apt-get) install PROGRAMNAME

to install a program.

---

### Post by oldos2er on 2010-02-04
```
apt-cache search <search term>
```

Use a program or file name as search term. For details of a specific package, run ```
apt-cache show <package name>
```

For a CLI menu interface, run ```
sudo aptitude
```

---

### Post by thameera on 2010-02-04
Just to add to the reply by oldos2er. 

Suppose you need to install a twitter client. Then enter the following command:
```
apt-cache search twitter
```

Then the terminal will display a list of packages related to 'twitter'. Suppose you want to know additional information about a particular package in that list, say gwibber. Then type:
```
apt-cache show gwibber
```

If the package is satisfactory, install it using:
```
sudo apt-get install gwibber
```

---

