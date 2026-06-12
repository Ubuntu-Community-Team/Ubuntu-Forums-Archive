---
title: "Ubuntu Newbie"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-09-18
Hi guys..
M a beginner to ubuntu...
I would like to know if i install a package using

sudo apt-get install some-pckg

where do the files get stored

thanks

---

### Post by Cheezespread on 2009-09-18
I believe those are in 
```
/var/cache/apt/archives/
```

You would find the .deb packages there.

---

### Post by mapes12 on 2009-09-18
> sudo apt-get install some-pckg
Yes!

Or you could use the GUI: System>Administration>Synaptic Package Manager

---

### Post by Cheezespread on 2009-09-18
> **mapes12 said:**
> Yes!

Or you could use the GUI: System>Administration>Synaptic Package Manager

@mapes12 : I think he was asking where the deb files get stored !

---

### Post by mapes12 on 2009-09-18
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by muteXe on 2009-09-18
lol mapes :D

---

### Post by 3rdalbum on 2009-09-18
> **vipulkelkar said:**
> Hi guys..
M a beginner to ubuntu...
I would like to know if i install a package using

sudo apt-get install some-pckg

where do the files get stored

thanks

Why exactly do you need to know? If you can launch the program from the menu or from the command-line, then you don't need to know about what files have installed where; all you need to know is that they have installed.

If you haven't got an Applications menu item, then you can follow the screencast tutorial in my signature to add one. As you'll see when you follow it, most packages put files in all sorts of different places, so various parts of the system can find the files that they need.

A lot of people complain that packages put files in all sorts of different locations, but unless you're manually editing configuration files, you simply don't need to know where all the files have gone. It's the package manager's job to put them there, and it's the package manager's job to take them away again when you remove the package. The package manager will do this job so you don't have to.

---

### Post by Cheezespread on 2009-09-18
> **3rdalbum said:**
> Why exactly do you need to know? If you can launch the program from the menu or from the command-line, then you don't need to know about what files have installed where; all you need to know is that they have installed.

If you haven't got an Applications menu item, then you can follow the screencast tutorial in my signature to add one. As you'll see when you follow it, most packages put files in all sorts of different places, so various parts of the system can find the files that they need.

A lot of people complain that packages put files in all sorts of different locations, but unless you're manually editing configuration files, you simply don't need to know where all the files have gone. It's the package manager's job to put them there, and it's the package manager's job to take them away again when you remove the package. The package manager will do this job so you don't have to.

Sorry to say this. I found your responce a bit rude.

---

### Post by wojox on 2009-09-18
Alright after you install your package run:

```
sudo updatedb
``` 

To make sure our next command is up to date. Then:

```
locate <name of program>
```

To see where everything is. Ex.

```
locate firefox-3.5
```

---

### Post by 3rdalbum on 2009-09-18
> **Cheezespread said:**
> Sorry to say this. I found your responce a bit rude.

While I was writing my response I was thinking of some people previously who were being a bit silly about the whole thing; they complained that the package manager should put all the files in one location, so "it's easier for me to check that they get removed when I remove the package".

I apologise if my phrasing sounded rude, I didn't mean it to.

---

### Post by Cheezespread on 2009-09-18
> **3rdalbum said:**
> While I was writing my response I was thinking of some people previously who were being a bit silly about the whole thing; they complained that the package manager should put all the files in one location, so "it's easier for me to check that they get removed when I remove the package".

I apologise if my phrasing sounded rude, I didn't mean it to.


Cheers !.You can never judge anyone by their statements as you dont know what sort of a day they had till then .

---

