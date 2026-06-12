---
title: "2 part .rar how do I unpack them?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by RotorRick on 2011-04-26
Probably a boneheaded question, but I have a 2 part .rar file that I need to extract together as it's part of one .wmv video. I'm using the standard Ubuntu 10.04LTS 'archive manager' "File Roller 2.30.1.1."

How do I get it to combine the two while extracting?

Thanks!

---

### Post by u.rusty on 2011-04-26
Your question isn't boneheaded.

Try
Applications | Ubuntu Software Center | do a search for "rar"
Install the application, then try double clicking on your .rar file.

---

### Post by K_45 on 2011-04-26
```
sudo apt-get install unrar
```

```
cd *folder*
``` - where the file is

```
unrar x *file name*
``` where file name is the file name.

---

### Post by prshah on 2011-04-26
> **RotorRick said:**
> How do I get it to combine the two while extracting?

Just right click any part file, and choose "Extract Here". It will automatically detect a two part archive (if rar naming conventions have been followed) and load the corresponding archive sections automatically.

If you get an error (Eg, unrar not found) then please install unrar (rar handling routines) from the software center.

---

### Post by Mark Phelps on 2011-04-26
It depends on how the files are named ...

If they are part1.rar and part2.rar, then any unarchiver will combine the results.

If they are file.001 and file.002, unarchivers won't work on that.  You need to install hj_split to join the parts first.  that will result in a file like combined.rar.  Then you can use an unarchiver on that file.

---

### Post by RotorRick on 2011-04-26
Thanks for the help guys, but nothing seems to be working. Using the terminal for unrar doesn't seem to be getting me anywhere, same with the default FileRoller, and I couldn't find hj_split in the Software Center...has it been renamed or something?

Also, there seems to be no directions on how to work any of these little programs...any tips?

---

### Post by K_45 on 2011-04-26
What does unrar tell you when you try to extract?

---

### Post by RotorRick on 2011-04-27
> **K_45 said:**
> What does unrar tell you when you try to extract?

It says:  "Unexpected end of archive"

I have both .rar files in the same folder, side by side,

 ____.part1.rar

 ____.part2.rar

...and it doesn't seem to matter if I "select/highlight" both of them using the mouse, after extraction it tells me  "Unexpected end of archive". Whether I Right click on them or not. It's as if it doesn't recognize part 2 at all.

apparently I have unrar too, but I don't know how to select it for use, since it appears as installed in the Software Center, but doesn't show under "applications" or "System" pulldown menus. Is Unrar a command line program? Where would I find the commands lists?

---

### Post by K_45 on 2011-04-27
The command is above and here:

```
unrar x name of file 1.rar
```

with name of file 1 being the first file. That message seems to indicate there are more parts. Are you sure the file is only in 2 parts?

---

### Post by trollger on 2011-04-27
there might also be a part 3 that it is trying to find. Are you sure there are only 2 parts?

---

### Post by -kg- on 2011-04-27
"unrar" is shown as installed on my system, as well (I'm using Maverick on this computer, but I assume the same is the case on Lucid, as well).  I see no launcher in my menus either, so I assume it's a CLI/Service program.

For a list of commands, launch your Terminal and type or copy/paste the following:

```
man unrar
```

That will give you a list of options and switches available with the "unrar" command.

---

### Post by prshah on 2011-04-28
> **RotorRick said:**
> It says:  "Unexpected end of archive"

Either the archive is not completely downloaded, corrupted, or has a missing part. If you have unrar, then this is the only possibility.

You can also check if both filenames are the same (case matters!). It does not matter which file you select for extraction; in a multi-part archive, unrar will pick up the first and last files automatically, given any one part.

---

### Post by Tyler94 on 2011-04-28
I have alot of experience with this! I do it all the time! But I have only done this in a Windows enviroment. First off... go and install Wine. (A program that lets you run windows programs in linux). Now go and get your self a free trial version of Winrar [http://download.cnet.com/WinRAR-32-bit/3000-2250_4-10007677.html?tag=mncol;1](http://download.cnet.com/WinRAR-32-bit/3000-2250_4-10007677.html?tag=mncol;1). Install that on Windows if possible. if not try and use it in linux using wine. If it installs... GREAT! Now rename the 2 rar files to part1.rar and part2.rar. Place both of those files into the same folder. Now select both of the files so that they are highlighted. click once and than select "extract files here" If you correctly highlighted both files. They should be combined after extraction. Hope I helped.


Tyler

---

