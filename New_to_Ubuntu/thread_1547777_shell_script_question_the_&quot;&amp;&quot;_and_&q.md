---
title: "shell script question: the &quot;&amp;&quot; and &quot;&amp;&amp;&quot; sign"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-07
Hi Community:

What do the "&" and "&&" signs mean in linux (unix) schell scripting? I forgot! :rolleyes:

What I'm trying to do is to is to 
[LIST=1]
[*]first remove an old copy of a directory "Bubba" in a location where I've backed up all of my files,
[*]then copy the current version of "Bubba" to the backup location
[/LIST]

(I've been using sbackup for this, and want to stop using it.) :-\"

In the past I've always done this manually, using:

[COLOR="Navy"][B]cd /home/philipsmith/WISDOM
rm -r /home/philipsmith/WISDOM/Bubba[/B][/COLOR]

followed by

[COLOR="Navy"]**cp -a /home/philipsmith/Bubba .**[/COLOR]

when the rm is completed.

I now want to put the whole thing in a shell script and execute it weekely with crontab.... :idea:

But think that I need to put "&" somewhere to make sure the rm completes before the cp starts with something like:

[COLOR="Navy"][B]cd /home/philipsmith/WISDOM
rm -r /home/philipsmith/WISDOM/Bubba[/B][/COLOR] [COLOR="Red"]**&**[/COLOR] [COLOR="Navy"]**cp -a /home/philipsmith/Bubba .**[/COLOR]

Am I using the "[COLOR="Red"]**&**[/COLOR]" sign correctly in this case, or should it be a "[COLOR="red"]**&&**[/COLOR]" sign?

I forgot! :confused:

Thanks!
Phil Smith
Duluth, GA

---

### Post by Bachstelze on 2010-08-07
[font=monospace]command &[/font] means "run [font=monospace]command[/font] in the background."

[font=monospace]command1 && command2[/font] means "run [font=monospace]command1[/font] and if it completes successfully, run [font=monospace]command2[/font] afterwards."

So you should probably use &&. You would use & if you want both commands to run simultaneously.

---

### Post by llamabr on 2010-08-07
Looks like you want &&

though in a script, just put them on seperate lines, and one will follow another.

---

### Post by Bachstelze on 2010-08-07
> **llamabr said:**
> 
though in a script, just put them on seperate lines, and one will follow another.

No, it is not the same thing. Read my message above.

---

### Post by Old Jimma on 2010-08-07
Thank you very much, Bachstelze!!

Phil Smith
Duluth, GA

---

