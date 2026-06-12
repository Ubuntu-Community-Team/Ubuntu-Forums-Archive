---
title: "trouble installing itunes in wine"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by bumpin240 on 2009-02-03
hey guys im pretty new to the ubuntu game but i love it so far, im trying to install itunes in wine and im having some trouble, first i have an error message saying that itunes needs windows 2000, xp or so on to install, i downloaded wine from winehq is there a newer wine that i should be downloading or can anyone help me figure out what i need to do with what i have i can post up a screen shot when i get home, on windows right now at work:(
 well thanks for the help in advance guys!

---

### Post by blazemore on 2009-02-03
Open a terminal
run the following commands (Copy and paste)
```

sudo su
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list && apt-get update && apt-get install wine -y --force-yes && apt-get upgrade -y --force-yes

```

That will install the latest Wine, and keep you updated in System updates.

---

### Post by bumpin240 on 2009-02-03
thanks for the fast response ill try that when i get home:D

---

### Post by jimv on 2009-02-03
Here's the Wine App DB entry for iTunes:

[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

---

### Post by blazemore on 2009-02-03
I'll explain what each bit does, so you learn a bit.
Each command is seperated by &&, it's the same as running each bit one after the other

1. ```
sudo su
```
This means that all commands run from now on will be run as the Super User (root), until you close the terminal window.


2.```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add
```
We download (wget) something called a "key" that verifies downloaded installation files. We install it. (apt-key add)


3. ```
echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list
```
echo just means display the next bit. The >> means append to the file /etc/apt/sources.list, which is a list of locations your computer uses to get software, when you ask it to.
In this case, we're using the official Wine repository, which has a more up-to-date version of Wine than the included Ubuntu repository.
We could just download the installation file from the Wine website, but the method I chose ensures Wine will be kept up-to-date.


4. ```
apt-get update
```
We refresh the list of repositories, making your computer aware of any new or updated packages


5. ```
apt-get install wine -y --force-yes
```
We install the package Wine (If it's not already installed). When the installer asks a question, we assume the answer is yes, even if yes is not the default option (You'll just have to trust me on this one!).


6. ```
apt-get upgrade -y --force-yes
```
If Wine was already installed, this command will update it to the version in the Wine repo, again, assuming Yes to all questions.

---

