---
title: "Question re adding medibuntu repository"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by bep7987 on 2010-06-03
I have a question regarding adding the medibuntu repository using the following commands from the medibuntu help page:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get 
--quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install 
medibuntu-keyring && sudo apt-get --quiet update
```This is from the help page: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Why does the command include the switch "**--allow-unauthenticated install**"?

Why is this necessary?  :confused:

I have searched this forum, linuxquestions.org and googled for an answer without success.

Thank you.

---

### Post by yetiman64 on 2010-06-03
Just for your convenience really, otherwise the terminal output of apt-get will hang until you answer yes or no to installing medibuntu's keyring. I have always found the method from the documentation you're using to work ok.  If you want to see the difference just remove that switch and be prepared to manually answer "yes" to apt-get to complete the install.

---

### Post by bep7987 on 2010-06-04
But why does the install have to be unauthenticated?  When you add other repositories, don't you usually add a key for authentication purposes?

---

### Post by 3rdalbum on 2010-06-04
The package management system will give you a warning if you try to install software from a source that you haven't added the GPG key for. The GPG key prevents the software from being modified while in transit.

When you run the command, it first adds the Medibuntu repository, then retrieves the list of packages from Medibuntu, then attempts to install the 'medibuntu-keyring' package that contains the GPG key. In order to prevent the user from getting a warning message, the command tells the package manager to temporarily accept this package without an existing GPG key already being in the system.

The keyword is "temporarily" - it's only that once.

---

### Post by yetiman64 on 2010-06-04
> **bep7987 said:**
> But why does the install have to be unauthenticated?  When you add other repositories, don't you usually add a key for authentication purposes?

Yes, but in this case you are actually installing the key after you are adding the repo, so no authentication can be done as the key is not on your system yet. It's ok to do it this way and is why apt-get hangs and asks your permission if you leave out the switch you mention. No security issue with this switch if you're wondering, it just suits the situation and is for your convenience.

---

### Post by bep7987 on 2010-06-04
Ok. Thanks for the help!

---

