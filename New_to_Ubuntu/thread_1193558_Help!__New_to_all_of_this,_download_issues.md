---
title: "Help!  New to all of this, download issues"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by kiss67 on 2009-06-21
Please help, just got this computer yesterday, and took all day just to get connected to internet, there is a icon telling me there is 1127 updates available and when I try to download the updates, everything locks up, restart is inevitable.  Also tried to download Java, buth that does same thing.  Don't fully get the 'termanal' thing, but I am trying.

---

### Post by malangaman on 2009-06-21
You have to provide greater detail for help. What OS are you using? Some specs about your computer could help.

---

### Post by kiss67 on 2009-06-21
um.... where do i find that,  (sorry, just born today into ubuntu and linux)

---

### Post by Thelasko on 2009-06-21
[It's a little old, but still worth reading.]("http://www.psychocats.net/ubuntu/installingsoftware")

The fact that your machine locks up on update is strange.  It might be a graphics card issue.  Does it ask for your password when you update?

---

### Post by kiss67 on 2009-06-21
no, I see that I don't need all of the updates, 900 of them are for different languages.  I just managed to download java for linux, but to install it tells me to pick a program to run the application with, I have no clue!

---

### Post by -kg- on 2009-06-21
> **kiss67 said:**
> no, I see that I don't need all of the updates, 900 of them are for different languages.  I just managed to download java for linux, but to install it tells me to pick a program to run the application with, I have no clue!

Did you download Java from the Sun site?  That would be the only reason I can think of for it to ask you what program to run it with.

You should really install it from the repositories, either "Add/Remove Programs" under the "Applications" menu or "Synaptics Package Manager" under "System/Administration."  Search for "jre" or "Java" and you will find the Java Runtime files and plugins.  You can mark them for installation, and aptitude will install them and take care of any dependencies that they might have.

---

### Post by nothingspecial on 2009-06-22
Try doing your updates through the terminal and post any error messages.

Accessories > Terminal

type

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

You will have to type your password, you won`t see it.

---

