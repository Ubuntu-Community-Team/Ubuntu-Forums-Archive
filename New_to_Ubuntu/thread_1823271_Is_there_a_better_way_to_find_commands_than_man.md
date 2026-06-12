---
title: "Is there a better way to find commands than man"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by imortalninja161 on 2011-08-11
oki so man is cool but ya have to know the command to look up the syntax and variables for that command 

I also enjoy enjoy comming on the forums and being part of the community but is there like a massive archive with nilly every command in it that i can just look up ;/ from time to time maybez :D

thanks
imortalninja161

---

### Post by haqking on 2011-08-11
> **imortalninja161 said:**
> oki so man is cool but ya have to know the command to look up the syntax and variables for that command 

I also enjoy enjoy comming on the forums and being part of the community but is there like a massive archive with nilly every command in it that i can just look up ;/ from time to time maybez :D

thanks
imortalninja161

yeah the man pages...LOL

man is your source for every command.

if you dont know what command you want then use

apropos <insert text here>

so for example:

apropos delete files

ths will then find all the commands you might be looking for to be able to delete

---

### Post by papibe on 2011-08-11
Have you tried [CLI Companion]("http://www.omgubuntu.co.uk/2010/12/cli-companion-helps-you-understand-terminal/")?

Regards.

---

### Post by sisco311 on 2011-08-11
+1 for `apropos' & `man'

If you don't read the man pages, you might end up writing redundant constructs, like the one from papibe's link: `[s]cat file1.txt file2.txt | sort | uniq > file3.txt[/s]' :evil:

---

### Post by Furball588 on 2011-08-11
outside of a man page...you'll catch me trying <command> --help just to see what comes up.  

Typically the results of that, if something exists, is intuitive enough to get me going...

---

### Post by The Cog on 2011-08-12
The man pages also always have a "See also" section at the bottom which can be very useful.

---

### Post by JKyleOKC on 2011-08-12
You can run "xman" which is a GUI viewer for man pages, and it includes an index listing all of the man pages that exist on your system. I've created a panel launcher for it so that I can immediately look up things without having to launch a separate terminal window. The command line I use for it is ```
xman -notopbox -pagesize 829x814-0-6
```

The -notopbox skips over its initial window, and the -pagesize option sets its window size and position to be at the righthand side of my display with full width for the man page and full height on my monitor.

---

### Post by CVGH on 2011-08-12
Nice!!!


> **jkyleokc said:**
> you can run "xman" which is a gui viewer for man pages, and it includes an index listing all of the man pages that exist on your system. I've created a panel launcher for it so that i can immediately look up things without having to launch a separate terminal window. The command line i use for it is ```
xman -notopbox -pagesize 829x814-0-6
```the -notopbox skips over its initial window, and the -pagesize option sets its window size and position to be at the righthand side of my display with full width for the man page and full height on my monitor.

---

### Post by bokgeneraal on 2011-08-12
Check out [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) if you have time. Great source to start you down the path of command line scripting . Also you can get the html files here [http://linuxcommand.org/script_library.php](http://linuxcommand.org/script_library.php) to browse offline:o

---

### Post by haqking on 2011-08-12
[http://linuxmanpages.com/](http://linuxmanpages.com/)

---

### Post by imortalninja161 on 2011-08-13
Thank you all for your suggestions and valuable information

Thanks
imortalninja161

---

### Post by amjjawad on 2011-08-13
> **JKyleOKC said:**
> You can run "xman" which is a GUI viewer for man pages, and it includes an index listing all of the man pages that exist on your system. 

Nice, will give that a look :)

---

