---
title: "completely new. i apologize in advance. need help with application install."
date: 2011-03-16
forum: New to Ubuntu
---

### Post by spaz33g on 2011-03-16
so i had this old laptop i was ready to get rid of, but today i decided to boot ubuntu on it to see what is all about. Anyway, I'm liking everything so far but it has become very clear that i have no idea what I'm doing. There are a few applications i want to install so i can get the ball rolling, but as a former windows user I'm used to double clicking and opening an installer. Today i downloaded a few linux apps and they al appear to be a different format. some are .zip some .7z or .tar.gz

i started looking up the methods for instalation but it would seem like most of the information was out of date or didnt make much sense to me. i would really appreciate it if someone could point me in the right direction or explain me how to get my applications installed.

---

### Post by amauk on 2011-03-16
What applications are you trying to install?

You don't usually download programs from websites (unlike in windows). The normal way to install software is from the repositories

Open up Applications > Ubuntu Software Center, and search for what you need

---

### Post by Grenage on 2011-03-16
While you can compile and install source code, new users will generally find it a lot easier using the package manager, or software centre.  You can find the software centre in the main menu, and synaptic package manager under *Administration*.

---

### Post by spaz33g on 2011-03-16
Ya i figured out how to use the native app browser,  the thing is i'm an avid android user and have been getting interested in making themes and such and the only way i have been able to find any of the programs i need is to download them from the browser.  Thank you for the quick replies btw.

---

### Post by Grenage on 2011-03-16
Well if you have source code from a website, you'll generally need to extract and compile it.  First you'll need to make sure that you have the usual dependencies installed:

```
sudo apt-get install build-essential
```
Alternatively, you can add it using Synaptic in the GUI.

Then you'll need to extract the (likely) tar file:

```
tar -xvzf *filename*
```
Alternatively, extract in via the GUI by clicking on it.

There will likely be a readme file which you should read; it will probably have exact instructions.  If it doesn't, then from the directory with the files, it's 'usually':

```
./configure
make
sudo make install
```

---

### Post by nothingspecial on 2011-03-16
Click the files and archive manager should offer to extract them for you

Inside the extracted folders should be a README or INSTALL file which should tell you what to do.

That being said, I'd spend a bit of time getting used to Ubuntu before you start compiling stuff on your own. There's plenty of stuff to mess about with.

---

### Post by spaz33g on 2011-03-16
alright i feel a little silly now. i took your advice and started looking through one of the zip files and found a read me file and some sort of file that had what looked like terminal command lines. i ended up running the stuff in the terminal, and foe now things are going swimmingly. i may have more questions, but thanks again for the replies.

---

