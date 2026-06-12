---
title: "&quot;invisible files&quot;"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-01
Is there any way in ubuntu to make files be there, yet not visible?  It seems like that, As there is stuff in my /home I can't see- the files don't appear.  The reason I ask is that there is a lot of config program files in my /home, and they just clutter it up.  Don't say I should move them- If I do then the program can't see them.

---

### Post by sisco311 on 2009-04-01
never mind

---

### Post by Cypher on 2009-04-01
The normal way of making a file or directory be "invisible" to normal "ls" is to put a "." in front of it. Adding the "." means that you have to use "ls -a" to see the file/directory.

However, you can't simply prepend the "." to make a file hidden since the application that uses a file should know the new name..

Apart from that, there really isn't a way of hiding the files. Traditionally though, programs usually put their configuration files in hidden directories in your home directory, they don't/shouldn't put them directly in your home directory and clutter things up..

---

### Post by DarkReaper79 on 2009-04-01
> **qwertyuiop96 said:**
> Is there any way in ubuntu to make files be there, yet not visible?  It seems like that, As there is stuff in my /home I can't see- the files don't appear.  The reason I ask is that there is a lot of config program files in my /home, and they just clutter it up.  Don't say I should move them- If I do then the program can't see them.
Are they hidden files that are visible, or no? You can do ctrl H and if they are already hidden they willnot be seen. If not, you can always rename them with a . before the name. But if they are config files, you may screw up stuff. Unless you correct the path that the program lists for those files. Hope it makes sense

edit:Im too slow

---

### Post by drs305 on 2009-04-01
There is actually a trick that will hide files and folders *in nautilus*. Since you are using ubuntu, you are in luck.

Make a file called .hidden  Open it up with a text editor and type in the name of any files and subfolders you want hidden. Save the file. Now elect to hide "." files in nautilus with CTRL-H. Any file or folder listed in .hidden in the same directory will not be displayed in nautilus. The files will still be seen in command line operations and by applications.

---

### Post by qwertyuiop96 on 2009-04-01
Yeah, If I do the . prefix thing the file is hidden, but then the program can't find the stupid file.  Oh well.  I'm just a bit mad at the programs that are like that.

---

### Post by Cypher on 2009-04-01
In Linux/Unix, the files "test" and ".test" are entirely different, so though the latter makes a file hidden, the application which was using "test" will not automatically look for ".test".

Which programs are you using that is putting files in your home directory and cluttering things up?

I don't believe I've come across any progarm that does that. My home directory is cluttered up largely because I get lazy sometimes..:)

---

### Post by qwertyuiop96 on 2009-04-01
> **drs305 said:**
> There is actually a trick that will hide files and folders *in nautilus*. Since you are using ubuntu, you are in luck.

Make a file called .hidden  Open it up with a text editor and type in the name of any files and subfolders you want hidden. Save the file. Now elect to hide "." files in nautilus with CTRL-H. Any file or folder listed in .hidden in the same directory will not be displayed in nautilus. The files will still be seen in command line operations and by applications.

Thanks drs305- this forum continues to provide solutions within 3 minutes!:p

---

### Post by egalvan on 2009-04-01
I've been running Hardy 8.04.2 since it came out (april-08 )
and have installed many packages... 2,306 as of one minute ago.
98% using Synaptic, the rest using apt-get.

I went to my home directory, turned off 'hidden files',
and it shows exactly seven files...
of which three are mine. That is fairly neat.


Showing all files, give 29 files.... a little messier...

---

### Post by aeiah on 2009-04-01
i use the .hidden file to hide those annoying windows folders that get created (system volume information etc). 

i also use it to hide all the subtitle files that are in my movie folder. i have a startup script for conky and other stuff and ive added this, so it adds any new files to the .hidden each time i start up my pc:

```

cd /media/giantpeach/film/;
ls *.ifo *.idx *.sub *.srt | tee .hidden;

```

makes the folder look much nicer

---

### Post by llamabr on 2009-04-01
What is this program that puts files in your home dir?

---

### Post by qwertyuiop96 on 2009-04-02
well, it is fixed now, but one is Foldit, one is Sweethome 3d, one is Golly, and Rythmbox sticks my music archives there.  But I was succesful l in making those files dissapear.

---

