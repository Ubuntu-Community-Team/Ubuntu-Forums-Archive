---
title: "i have downed firefox 3.6 what do i do next ??"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by blake7 on 2010-01-20
or is there an easyer way to get it to run???

cheers

ps this wherre i got it from 

[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

---

### Post by Cheezespread on 2010-01-20
The downloaded file is a tar.bz2 file - meaning , its a bzipped tar ball. TO extract the contents please follow the below routine.

I hope you have downloaded into your Desktop. 

Open up terminal and "cd" into the directory where you have downloaded the file. For eg : I am taking Desktop as where you have downloaded it.

```
cd Desktop
```

Then to extract the file , feed this line into terminal :

```
tar -xvjf firefox-3.6rc2.tar.bz2
```

x = eXtract, this indicated an extraction ( c = create to create ) 
v = verbose 
j = bzip2-zipped 
f = from/to file ... (what is next after the f is the archive file)

---

### Post by danking12 on 2010-01-20
Sorry I had posted something but the above instructions are better.

---

### Post by lovinglinux on 2010-01-20
> **Cheezespread said:**
> Please correct me if i have gone wrong somewhere.

You was wrong when you started to compile, because that is not source code. The file the OP has downloaded is ready to run. Mozilla releases it's source code with the word **source** in the file name, like firefox-3.6rc2.**source**.tar.bz2. Besides, compiling firefox is not that simple. You need additional dependencies, special configuration files and other commands. So, you should not try to compile it, just extract and run it. 

**The correct method:**

Put that file on your Desktop and run this:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3.6rc2.tar.bz2 -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```

To revert to official version:

> [COLOR="Red"]**WARNING:**[/COLOR] be careful with **sudo rm -r** commands. If you put the wrong path in the command, you might delete ALL your files and make your machine unbootable.

```
sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox
```

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for further info on installation of development versions and compilation of Firefox.

---

### Post by rbscairns on 2010-01-20
Deleted.

---

### Post by Cheezespread on 2010-01-21
[QUOTE=lovinglinux;8699125]You was wrong when you started to compile, because that is not source code. The file the OP has downloaded is ready to run. Mozilla releases it's source code with the word **source** in the file name, like firefox-3.6rc2.**source**.tar.bz2. Besides, compiling firefox is not that simple. You need additional dependencies, special configuration files and other commands. So, you should not try to compile it, just extract and run it. 


QUOTE]

Apologies. I am on my windows machine and assumed it was the source code. Removed the wrong info as you mentioned. Thanks a lot :) .

---

### Post by lovinglinux on 2010-01-21
> **Cheezespread said:**
> Apologies. I am on my windows machine and assumed it was the source code. Removed the wrong info as you mentioned. Thanks a lot :) .

No problem. Thanks for deleting the commands. I have delete my note too, since is no longer needed.

---

