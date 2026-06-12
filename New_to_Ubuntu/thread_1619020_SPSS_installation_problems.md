---
title: "SPSS installation problems"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Willy07 on 2010-11-11
I managed to install SPSS. Then nothing happened. It did not appear under applications. Then I found that it was installed in the OPT folder. How should I fix this so it will appear in the application menu?

Should I delete the folder and re-install it and where then? Should I just copy the folder to other location? What do you recommend?

I use the 10.04.

Thanks!

---

### Post by mcduck on 2010-11-11
Changing the install location will change nothing if the program's installer doesn't create a menu entry for you.

Instead just create the menu launcher yourself. Right-click on the Applications menu and select "Edit Menus" to open the menu editor.

---

### Post by Willy07 on 2010-11-11
> **mcduck said:**
> Changing the install location will change nothing if the program's installer doesn't create a menu entry for you.

Instead just create the menu launcher yourself. Right-click on the Applications menu and select "Edit Menus" to open the menu editor.

Thanks for your help. I am unable to find the executable file. I have done a search but nothing seems to work. 

Could I reinstall the program into a new file instead of this OPT folder?

---

### Post by ayenack on 2010-11-11
You could try PSPP.

It's in the repo's in 10.04 and earlier I think.

**sudo apt-get install pspp**

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)

For a quick overview. It's Open Source also. ;-)

---

### Post by Willy07 on 2010-11-11
I already have PSPP installed. I am not sure if I can use that. Next week I will be attending a course in statistics. They are going to use SAP but also recommend SPSS. I doubt they are familiar with PSPP so I am not sure whether that is a good idea.

My alternative is to switch to Windows 7 tomorrow. I can get it for cheap through my University.

---

### Post by mcduck on 2010-11-11
> **Willy07 said:**
> Thanks for your help. I am unable to find the executable file. I have done a search but nothing seems to work. 

Could I reinstall the program into a new file instead of this OPT folder?

The executable should be where you installed it. :) I can't really help you finding it without being able to see the actual files or the installer, but if nothing else works try running "ls -l" in the program's directory and check which file is marked as executable. Or, better yet, check the documentation that came with the installer, I'm pretty sure it will tell you where the executable is and how to run the program...

Like I said, where a program is installed has nothing to do with menu entries. So if the program's installer didn't create a menu entry, installing it in different place won't create a menu entry either.

---

### Post by ayenack on 2010-11-11
Found this guide might be of some help to you. Only problem I can see is that you've already installed SPSS and may need to remove and re-install.

[http://ubuntu4students.wordpress.com/2009/03/05/installing-spss-16-linux-on-ubuntu-810/](http://ubuntu4students.wordpress.com/2009/03/05/installing-spss-16-linux-on-ubuntu-810/)

Guy says it works.

---

### Post by beew on 2010-11-11
> **ayenack said:**
> You could try PSPP.

It's in the repo's in 10.04 and earlier I think.

**sudo apt-get install pspp**

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)

For a quick overview. It's Open Source also. ;-)


No you can't if OP is doing anything more advanced than generating crosstabs and frequency tables, or perhaps simple regression. 

SPSS is not the greatest stat software around (R and Stata are both better and both run natively on Linux) but it has way more advanced functions than PSPP, which at the moment is basically only good for opening SPSS files and doing very simple spreadsheet type work, even gnumeric has more statistical functions than it does.

PSPP will make some real impact if it has logistic regression, many social science researchers use only that for their whole career! But at this moment if you tell anyone who does stat beyond a first semester course you can replace SPSS with PSPP you will be laughed off the stage and quite rightly.

P.S. The latest version of PSPP does have factor analysis. This is its only advanced function, but it doesn't have the options in SPSS, SAS, R or Stata.

---

### Post by ayenack on 2010-11-11
> **beew said:**
> No you can't if OP is doing anything more advanced than generating crosstabs and frequency tables, or perhaps simple regression. 

SPSS is not the greatest stat software around (R and Stata are both better and both run natively on Linux) but it has way more advanced functions than PSPP, which at the moment is basically only good for opening SPSS files and doing very simple spreadsheet type work, even gnumeric has more statistical functions than it does.

PSPP will make some real impact if it has logistic regression, many social science researchers use only that for their whole career! But at this moment if you tell anyone who does stat beyond a first semester course you can replace SPSS with PSPP you will be laughed off the stage and quite rightly.

P.S. The latest version of PSPP does have factor analysis. This is its only advanced function, but it doesn't have the options in SPSS, SAS, R or Stata.

The OP already has PSPP installed.

Not sure how you got from me suggesting that the OP "**could try PSPP**" to could replace SPSS with PSPP.

I was simply trying to offer some help.

---

### Post by llamabr on 2010-11-11
open a terminal, and type:

```
which spss
```

as you say, it is probably just in /opt/spss or something simple.

I'd think that will tell you where it's located.  You should also be able to run it right from the cli.

You'll be better off leaving where it is, but you can make a symlink to see it where you want to see it.  If you want it on the applications menu, right click and put it there should be self explanatory.

---

