---
title: "copy to new directory of the same name"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Heksie on 2009-02-05
Hello out there...

I have a number of sub-directories of similar name (Afr100, Afr101 etc) that contain a mix of files.  I need to copy files of type .cnv only and put them in a new directory of the same name as their origin (so ~Data/Afr121/*.cnv to /tmp/Data/Afr121 for example). I have about 80 of these sub-directories to go through.  Obviously I don't want to have to mkdir for all 80 folders and cp one at a time.  How simple is this to do?

---

### Post by carml on 2009-02-05
Haven't you got a graphical environment?

---

### Post by carml on 2009-02-05
If you can make use of a graphical environment you can arrange icons by type,then select them with the move and copy them into the folder you created in advance with the name you want.I think this way you'll be faster than with the shell. :)

---

### Post by Circus-Killer on 2009-02-05
> **carml said:**
> If you can make use of a graphical environment you can arrange icons by type,then select them with the move and copy them into the folder you created in advance with the name you want.I think this way you'll be faster than with the shell. :)

may the OP correct me if i'm wrong, but i think what he wants is to create a shell script to do it automagically.

i would help, but haven't gone into writing shell scripts just yet. any takers? ;)

---

### Post by carml on 2009-02-05
Mine was an attempt to help him,we can only make hypothesis on what he want to do,while he doesn't give us more scpecifications.Maybe your right,but me too I don't know how to write script.

---

### Post by Heksie on 2009-02-05
I guessed I would have to create a script, but was kinda hoping a few arguments with the cp or mkdir commands.  Automagically would be great!

---

### Post by carml on 2009-02-05
Do you have to do this action frequently?If so,yes you'll safe time with a script,look on the forum or in the web then.:)

---

### Post by hyper_ch on 2009-02-05
you'd have to use "find" to filter the files and then read-out the paths and create according new ones and then copy the file.

---

