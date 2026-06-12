---
title: "Command line: to show what programs are installed"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Segofam on 2011-01-09
Hi all,
Can someone let me know what to put in the command line to display all the programs I have installed?
Kind regards,
Scott

---

### Post by TeoBigusGeekus on 2011-01-09
I think it's
```
dpkg -l
```

---

### Post by JCollierDavis on 2011-01-09
> **TeoBigusGeekus said:**
> I think it's
```
dpkg -l
```
 
dpkg -l will spit out a huge list of every package installed in the system, including all dependencies. The default ubuntu desktop has about 1300 so it's a long list. You might try one of the following to make it a bit easier on your self:
 
```
 
dpkg -l | less
dpkg -l | more

```
These will let you scroll through the output as it's going instead of having to use the mouse wheel to roll all the way back up to the top. That | is a pipe probably on your keyboard just above the [enter] key.
 
```
 
dpkg -l | grep package

```
Replace 'package' above with a search term to narrow down the list some more as well. Depending on which terminal you use, it might highlight your search term.
 
```
 
dpkg -l >> all_my_packages.txt

```
Use this to route dkpg's output into the text file 'all_my_packages' so you can look at it with a text editor or something other program you might have. You can paste the column of packages into a spreadsheet. At a later time compare this list to another list to see what's different.

---

### Post by oldos2er on 2011-01-09
aptitude, toggle down to Installed Packages.

---

### Post by Segofam on 2011-01-09
Thanks for the response folks, much appreciated :)

Scott.

---

