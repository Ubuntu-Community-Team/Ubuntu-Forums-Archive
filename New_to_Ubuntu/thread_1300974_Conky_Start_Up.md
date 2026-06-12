---
title: "Conky Start Up"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by pkjm17 on 2009-10-25
How do you get your Conky to start up, so it's there on your desktop when you turn on your computer? I have 2 conky files: conkyrc and conkyrc2. From a terminal I type conky which launches the first one, then I type conky -c .conkyrc2 which launches the second one. But I would like to have them automatically start up if possible. Any help is appreciated.

---

### Post by dv3500ea on 2009-10-25
Go to system->preferences->startup applications.
Add a new one called conky with the command ```
conky
```
Add another called conky2 with the command ```
conky -c .conkyrc2
```

---

### Post by pkjm17 on 2009-10-25
thanks that worked, however, when I restart or turn on the computer, there's something different with the conky background. For example, if I move an application like Firefox over to it, it appears underneath conky (see Screenshot.png). I'm wondering if there's something I can change in the conky files to prevent this from happening. Screenshot-1.png is how I want it to be.

---

### Post by pkjm17 on 2009-11-04
> **dv3500ea said:**
> Go to system->preferences->startup applications.
Add a new one called conky with the command ```
conky
```
Add another called conky2 with the command ```
conky -c .conkyrc2
```

that worked while I was using 9.04, but since I upgraded to Karmic 9.10, it doesn't work.

---

### Post by The Funkbomb on 2009-11-04
> **pkjm17 said:**
> thanks that worked, however, when I restart or turn on the computer, there's something different with the conky background. For example, if I move an application like Firefox over to it, it appears underneath conky (see Screenshot.png). I'm wondering if there's something I can change in the conky files to prevent this from happening. Screenshot-1.png is how I want it to be.

This is a conflict between conky and compiz.  When conky loads before compiz, that effect happens.

The easiest solution is a simple bash script.  Yours might look something like this:

```
#! /bin/bash/
sleep 12
conky && conky -c conkyrc2;
```

That simply tells your machine to wait 12 seconds and then load conky and conkyrc2.  That should be plenty of time for Compiz to load.

Save this as something simple like conkyscript.sh since it's a shell script.  Save it to your home folder.

Now, we need to make it executable.  Go into terminal and do this:

```
sudo chmod +x /home/[username]/conkyscript.sh
```

Replace [username] with your username of course.

Now, while you're in terminal, copy it over to your home folder.

Then simply rename it .conkyscript.sh so it's now a hidden file.

In startup applications, add the path to .conkyscript.sh

You can take out the other start up conky.

---

### Post by pkjm17 on 2009-11-09
> **The Funkbomb said:**
> This is a conflict between conky and compiz.  When conky loads before compiz, that effect happens.

The easiest solution is a simple bash script.  Yours might look something like this:

```
#! /bin/bash/
sleep 12
conky && conky -c conkyrc2;
```

That simply tells your machine to wait 12 seconds and then load conky and conkyrc2.  That should be plenty of time for Compiz to load.

Save this as something simple like conkyscript.sh since it's a shell script.  Save it to your home folder.

Now, we need to make it executable.  Go into terminal and do this:

```
sudo chmod +x /home/[username]/conkyscript.sh
```

Replace [username] with your username of course.

Now, while you're in terminal, copy it over to your home folder.

Then simply rename it .conkyscript.sh so it's now a hidden file.

In startup applications, add the path to .conkyscript.sh

You can take out the other start up conky.

Just to be clear...when I add my path (/home/pat/.conkyscript.sh/) in the Start Up Applications, this goes in the Command field?

---

### Post by The Funkbomb on 2009-11-09
Yes

---

### Post by Mi11z on 2010-09-25
Thanks for the extra info guys, i read somewhere else or maybe in a different thread that a delay of 30 seconds would definitely do the job and after trying everything it has and well you don't notice 30 seconds trust me in fact it seemed to load faster than that so cheers anyway and i hope my input will help someone else out there and lastly i'm running lucid by the way. :)

---

### Post by CMXILies on 2012-01-02
Conky is pretty exciting new stuff to get into. Thanks for the guide.

---

