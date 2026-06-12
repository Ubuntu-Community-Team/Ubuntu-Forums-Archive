---
title: "Software Installation Problem in ubuntu 11.04?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by H A NAZIR on 2011-05-20
i am totally beginner to ubuntu and i insttall ubuntu few days ago but when i go to install any software through ubuntu software center it shows the following message " Package operation failed The Installation or removal of software package failed" Can you tell me what is meant by this problem and how to solve it?

---

### Post by Mr. Shannon on 2011-05-20
What package are you trying to install?  Say you were trying to install the Chromium web browser.  Open a terminal with **Ctrl+Alt+t** and type

```
sudo apt-get install chromium-browser
```

when asked for your password enter it and then copy and paste the output on this form.  Note: use any package you want as long as you know the right name.

If it installs with no errors then we know that the package management software is working and its only the software center itself.

**Edit:** I did not notice that you were not using Ubuntu.  The keyboard shortcut to get to the terminal may not work but you should be able to open up the terminal from the menu.

---

### Post by wildmanne39 on 2011-05-20
> **H A NAZIR said:**
> i am totally beginner to ubuntu and i insttall ubuntu few days ago but when i go to install any software through ubuntu software center it shows the following message " Package operation failed The Installation or removal of software package failed" Can you tell me what is meant by this problem and how to solve it?
Hi, it is best to use synaptic package manager, see if that works.

---

### Post by H A NAZIR on 2011-05-23
> **Mr. Shannon said:**
> What package are you trying to install?  Say you were trying to install the Chromium web browser.  Open a terminal with **Ctrl+Alt+t** and type

```
sudo apt-get install chromium-browser
```when asked for your password enter it and then copy and paste the output on this form.  Note: use any package you want as long as you know the right name.

If it installs with no errors then we know that the package management software is working and its only the software center itself.

**Edit:** I did not notice that you were not using Ubuntu.  The keyboard shortcut to get to the terminal may not work but you should be able to open up the terminal from the menu.

I write the same code in terminal but it shows following error "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."
and please tell me how to know the right name of any software?

---

### Post by oldos2er on 2011-05-23
Run this command in a terminal ```
sudo dpkg --configure -a
```

---

### Post by Mr. Shannon on 2011-05-23
I'm nearing the end of my knowledge so hofully some one else will step up soon with a solution.

Honestly, you should have never gotten that error.  So something may be wrong.  But, go ahead and run the command in the post above and see if it will install the package/s.  At least you will have a way to install software then.

You could run
```
sudo apt-get update
```
and see if it generates any errors.

As for knowing the corect package name, that can be found in the **Software Center**.  Go to a package click on **More Info** then scroll down to **Details** and under **Version** the package name will be listed in parethisis.  The other way to find the name of a package it through **Synaptic**.

---

### Post by H A NAZIR on 2011-05-23
> **oldos2er said:**
> Run this command in a terminal ```
sudo dpkg --configure -a
```
I run this command but it shows following message "dpkg: error: parsing file '/var/lib/dpkg/updates/0017' near line 0:
 newline in field name `#padding'  "

---

### Post by H A NAZIR on 2011-05-23
> **Mr. Shannon said:**
> I'm nearing the end of my knowledge so hofully some one else will step up soon with a solution.

Honestly, you should have never gotten that error.  So something may be wrong.  But, go ahead and run the command in the post above and see if it will install the package/s.  At least you will have a way to install software then.

You could run
```
sudo apt-get update
```and see if it generates any errors.

As for knowing the corect package name, that can be found in the **Software Center**.  Go to a package click on **More Info** then scroll down to **Details** and under **Version** the package name will be listed in parethisis.  The other way to find the name of a package it through **Synaptic**.
  After some processing this command shows the following error
" E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "
so what should i do?

---

