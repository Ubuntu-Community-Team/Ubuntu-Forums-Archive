---
title: "Java Browser Plug inI ???"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by MetaMs on 2010-07-20
I'm trying to install the Java Browser Plug in by following these instructions:
[http://ubuntuforums.org/showthread.php?t=1517979](http://ubuntuforums.org/showthread.php?t=1517979)

The USS has been "In Progress" for over 45 minutes. Is this normal? If not, what should I do? Help!

---

### Post by msandoy on 2010-07-20
If you do not mind all the other non-free addons, just use synaptics, and install Ubuntu restricted extras. This gives you both Java and flash.

---

### Post by MetaMs on 2010-07-20
Is it OK to just close the USS? Won't it mess things up?

---

### Post by MetaMs on 2010-07-20
I closed USS. Now when I try to run Synaptic Package Manager I get the following error:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I really need help. I am a newB!

---

### Post by QIII on 2010-07-20
In the terminal (Applications | Accessories | Terminal) type
 
 ```
sudo dpkg --configure -a
```

You will be asked for you login password.  Type it.  You will not see  anything happen on the screen.  That is normal.  Press Enter.

For the next step, I need to know if you are running Lucid or if you are running an earlier version.

---

### Post by QIII on 2010-07-20
> **msandoy said:**
> If you do not mind all the other non-free addons, just use synaptics, and install Ubuntu restricted extras. This gives you both Java and flash.

Java is in the Partner repository and needs to be installed from there.

---

### Post by MetaMs on 2010-07-20
I'm running Lucid. 10.04 on an Eee PC netbook.

---

### Post by QIII on 2010-07-20
Did you run the command in the terminal?

---

### Post by MetaMs on 2010-07-20
yes. I now see a lot of other 'instructions'

---

### Post by QIII on 2010-07-20
Go on ...

I can't see your monitor ;)

Is it just a bunch of text scrolling by?

---

### Post by MetaMs on 2010-07-20
This is what it says after the password request (which I entered):

dpkg: unknown option --QIIIconfigure

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
michelle@michelle-laptop:~$

---

### Post by QIII on 2010-07-20
Did you actually type 

```
QIIIconfigure
```

?

---

### Post by MetaMs on 2010-07-20
Oh heck. I did NOT mean to type that. I'm still having problems with the sensitivity on this touchpad and sometimes things end up where I don't want them.

Should I start over? I'm so sorry!

---

### Post by QIII on 2010-07-20
Yes.  Start over.  Type carefully :)


I have to go catch a train before my wife beats me to within an inch of my life for being home so late.

If someone has not been along to help by the time I get home, I'll get back to you.

---

### Post by MetaMs on 2010-07-20
Oh gosh...I don't want you in trouble with Mrs. QII! Thanks.

---

### Post by MetaMs on 2010-07-20
I ran the command again (correctly) then, opened SPM.

I ran the "fix broken packages" and everything now seems to be OK! Thank you so much for starting me down the right road. I can even see the website with the Java camera on it. :o)

Hope you made it to the train on time!

---

### Post by Miljet on 2010-07-20
So you are all fixed up now? If so, please mark the thread solved.

Also please try to refrain from using abreviations when asking for help. I know that it takes a little longer to type out the full name, but it often helps avoid confusion.

---

