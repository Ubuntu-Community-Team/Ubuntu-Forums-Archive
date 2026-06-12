---
title: "Getting UT3 to run on ubuntu 10.10"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by cryptoxic on 2011-01-04
_Dear friends,_
   I am new to Linux, only had it for 2 days. I am trying to install [COLOR="Red"]Unreal Tournament 3[/COLOR] windows application on my ubuntu and run it under Linux. So I got this wine thing and PlayOnLinux. It appeared to be self-explanatory at first, but there is no _script_ for UT3 in POL games tab. I looked for it online and actually found it. So the question: 
What do I do with it? Please be specific, as my Linux experience is **very** small.

---

### Post by earthpigg on 2011-01-04
can you link us to the script you found?

---

### Post by cryptoxic on 2011-01-04
> **earthpigg said:**
> can you link us to the script you found?

sure, here it is:
[http://www.playonlinux.com/en/topic-2591-script_Unreal_Tournament_3.html](http://www.playonlinux.com/en/topic-2591-script_Unreal_Tournament_3.html)

---

### Post by blind2314 on 2011-01-04
Well, there's no real guarantee this will work on Ubuntu, but here's how to give it a shot. Copy and paste that entire script into a new file, using your favorite text editor. Then go to a terminal and type the following:
 
```

cd <directory where you saved it>
chmod 777 <filename>
./<filename>

```
 
That will make the script fully readable/writeable/executable by everyone, and then run it. Like I said, I don't actually see that script working as intended, but who knows.

---

### Post by cryptoxic on 2011-01-04
> **blind2314 said:**
> Well, there's no real guarantee this will work on Ubuntu, but here's how to give it a shot. Copy and paste that entire script into a new file, using your favorite text editor. Then go to a terminal and type the following:
 
```

cd <directory where you saved it>
chmod 777 <filename>
./<filename>

```
 
That will make the script fully readable/writeable/executable by everyone, and then run it. Like I said, I don't actually see that script working as intended, but who knows.

Thanks for your reply. I wouldn't say that it didn't work... The terminal didn't complain about these commands. I have printed a part of my screen for you to see what happened. It is in the attachment. There you can see the terminal, the UT3 icon and a prompt window after clicking on UT3. What do I do next? Did it work? How do I "wine" it? Thanks.

---

### Post by earthpigg on 2011-01-04
what happens when you hit 'run'?

---

### Post by cryptoxic on 2011-01-05
> **earthpigg said:**
> what happens when you hit 'run'?

When I hit run, nothing happens. That prompt window just disappears. :confused:

When I hit run in terminal, some other window (probably the terminal) appears for a split second and then disappears.

---

