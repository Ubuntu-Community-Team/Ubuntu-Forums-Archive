---
title: "Help Terminal!!!!!!"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by omnom on 2011-02-28
Well I am new to the Ubuntu and the Linux Oses so I need some help....

I open the Terminal and I have already made a script, but I can't run it!!!! I am in the directory the script is and I can't open it!!!! :(
that's what I wrote in the script:

#!bin/bash
cd Programmes 
mkdir OmNom

Then I save it and open the terminal. I find It at the directory I saved it BUT can't R U N it!!!!!:(

Please help me!!!!!!!!!:-?:cry:8-[:neutral:

---

### Post by Frogs Hair on 2011-02-28
There are other ways , but I learned from here. [http://linuxcommand.org/wss0010.php](http://linuxcommand.org/wss0010.php)

---

### Post by mikewhatever on 2011-02-28
Can't run is a vague statement, unless you actually tell why not.

---

### Post by lucasart on 2011-02-28
> **omnom said:**
> Well I am new to the Ubuntu and the Linux Oses so I need some help....

I open the Terminal and I have already made a script, but I can't run it!!!! I am in the directory the script is and I can't open it!!!! :(
that's what I wrote in the script:

#!bin/bash
cd Programmes 
mkdir OmNom

Then I save it and open the terminal. I find It at the directory I saved it BUT can't R U N it!!!!!:(

Please help me!!!!!!!!!:-?:cry:8-[:neutral:

chmod +x ./file.sh
./file.sh

if you're a linux beginner, then perhaps shell scripting isn't for you just yet. But once you understand more about the system (read the ubuntu manual), you should look at bash guides on internet.

---

### Post by sandyd on 2011-02-28
> **lucasart said:**
> 
```
chmod +x file.sh
**./**file.sh
```

but more generallt if you need to write bash scripts, you'll find bash a very powerful but somewhat more complex than DOS for example. Just google for a bash tutorial and start from there.
fixed.

---

### Post by The Linux Cynic on 2011-02-28
Try setting your script to be executable. You can do this through the nautilus gui (nautilus is the file explorer that Ubuntu comes with). Just right-click the file, select Properties, select the Permissions tab, and check the "Allow executing file as program" check box. Close this menu.

Now, when you double click the file, it should ask if you want to run it or display its contents. Also, in terminal, you can navigate to its location and type:

```
#> ./yourscriptname.sh
```

*NOTICE: As others have pointed out, you need the ./ before your script name. I suspect it might be too much to explain to you why this is right now, but once you learn a bit more about bash and terminal, it'll be obvious.*

---

### Post by omnom on 2011-03-01
thanx a lot

---

