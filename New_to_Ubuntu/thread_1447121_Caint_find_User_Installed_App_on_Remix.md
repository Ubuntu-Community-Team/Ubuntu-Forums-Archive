---
title: "Caint find User Installed App on Remix"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by shaggy3131 on 2010-04-04
Hi guys wow i feel dumb, Just installed Ubuntu Mobile Remix, this is the first time ive used Linux. I used the software center to install 7ZIP but now i dont know where to find it so i can run it. Since the mobile remix does'nt have the applications menu like reg Ubuntu does (I lied i played with reg Ubuntu on a very old laptop for a couple days before making the switch on my netbook) Where do i find apps I have installed from the software center? The software center does show that 7zip is installed. How do i get the new installs in the menus on my desktop I.E. favorites, games, system, and so on. Is there a resource center specifically for remix?

P.S. Loving Ubuntu and caint wait till im good enough with it to switch the rest of our computers over!

---

### Post by 3rdalbum on 2010-04-05
7zip is a command-line program, not a GUI program. It provides the ability for File Roller (Archive Manager) to use the 7zip file compression format. So basically, use your normal Archive Manager program to compress and decompress 7zip files - it will call upon 7zip as a backend.

Command-line programs never appear in your Applications menu.

And no need to feel dumb, Linux is very different to Windows, and your question is quite common. So common, actually, that I made a screencast that explains "Where does my program go?".

---

### Post by shaggy3131 on 2010-04-05
Hmmm 7ZIP is installed i left click a file, select extract here, Alert : "Could not open "File_Name.rar" Archive type not supported"

---

### Post by 3rdalbum on 2010-04-05
> **shaggy3131 said:**
> Hmmm 7ZIP is installed i left click a file, select extract here, Alert : "Could not open "File_Name.rar" Archive type not supported"

7zip is completely different to RAR.

You need to install the 'unrar' package (RAR is a proprietary archiving format, which is why it isn't included by default).

```
sudo apt-get install unrar
```

---

### Post by shaggy3131 on 2010-04-05
Worked great! Thought rar was just another compression type and 7zip listed support for it. is there a brief explanation for the error in my logic?

---

### Post by 3rdalbum on 2010-04-05
> **shaggy3131 said:**
> Worked great! Thought rar was just another compression type and 7zip listed support for it. is there a brief explanation for the error in my logic?

On Windows, 7zip performs the same role as Ubuntu's File Roller - it compresses and decompresses many different formats, including the 7Zip format and RAR.

On Linux, 7zip is just a backend for the 7zip format, because there's already a program ('unrar') that can deal with RAR archives and will be called by any archive manager to deal with RARs. No need to duplicate effort.

That's the simplest explanation without talking about the Unix philosophy of "One program for a single task" :-)

---

