---
title: "application/x-executable same as +x permission?"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by PrimroseGrange on 2011-07-13
Is the MIME type "application/x-executable" equivalent to the file permission "+x"?

Are they interchangeable? 

Does either or both allow a script (say) to be executed?

I ask because it is not obvious why Ubuntu is allowing some of my scripts to execute, but not others. They all have the same owner (me).

---

### Post by jtarin on 2011-07-13
**Execute permission.**
> In the case of a regular file, this means you can execute the file _as a program or a shell script_. 
On a directory, the execute permission (also called the "search bit") 
allows you to access files in the directory and enter it, with the 
cd command, for example. However, note that although the execute bit 
lets you enter the directory, you're not allowed to list its contents, 
unless you also have the read permissions to that directory.

 MIME type:[**application/x-executable**]("http://en.wikipedia.org/wiki/Internet_media_type#Type_x")

Where are you seeing application/x-executable?

---

### Post by dcsoldschool53 on 2011-07-13
> **PrimroseGrange said:**
> Is the MIME type "application/x-executable" equivalent to the file permission "+x"?

Are they interchangeable? 

Does either or both allow a script (say) to be executed?

I ask because it is not obvious why Ubuntu is allowing some of my scripts to execute, but not others. They all have the same owner (me).

Just because you have the same owner, does not mean you have permission to execute it. Do a```
ls -l `/directory-name
```to see if you have executable rights from a terminal. Only you know which directory your files are in, I am just saying directory name as an example.

---

### Post by dcsoldschool53 on 2011-07-13
I have a script called question.sh. I am the owner of it, but if you look at the permissions```
-rw-r--r--
``` I can not run it. It will say permission denied every time. I can read it and write to it, but I can not execute it.

@Jtarin This is a guess and I am only guessing because I am not him. When you right click on a file, you click properties > permissions > allow execution of this file, or something like that. I think that is what he was referring to. But I am not sure either.

---

### Post by PrimroseGrange on 2011-07-13
> **jtarin said:**
> **Execute permission.**
 
MIME type:[**application/x-executable**]("http://en.wikipedia.org/wiki/Internet_media_type#Type_x")
 
Where are you seeing application/x-executable?
 
Background: I have downloaded a very complex build tree and "make" is failing with permissions problems. There are hundreds of scripts and assorted check programs (it's a buildroot). It would take a long time to check them all, and because not all of them get used (due to conditional building), I don't even know which specific files to check. I have noticed that at least some of the scripts (typically <name>.sh) do not have the executable bit set, but do have a MIME type of application/x-executable. I wondered if the MIME type is used by Linux on an equivalent basis to +x permission. If so, that would explan why "make" gets at least part of the way through the build.

---

### Post by psusi on 2011-07-13
Where are you seeing this mime type?  Mime-type is not a property of files in a unix filesystem.  It is a hint that web servers and mime encoded email attachments provide to tell the web/mail client how it should handle the file.  application/x-executable is not a known mime type either.

---

### Post by mikejonesey on 2011-07-13
chmod 744 will change from;

-rw-r--r--
to
-rwxr--r--

(owner can execute)

the default for +x is to enable everyone to execute it... hmmm

---

### Post by PrimroseGrange on 2011-07-13
> **psusi said:**
> Where are you seeing this mime type? 
 
I'm seeing it in the file properties when I right click on the file in the Ubuntu file browser. If it's not a file property ... I'm confused. 
 
Linux man pages, "file" command, options:
**-i, --mime** Causes the file command to output mime type strings rather than the more traditional human readable ones. Thus it may say ''text/plain; charset=us-ascii'' rather than ''ASCII text'' ... 
All of these files came from a CD which in turn was burned from a .iso image which was created on a Linux system.

---

### Post by mikejonesey on 2011-07-13
> Is the MIME type "application/x-executable" equivalent to the file permission "+x"?
no both are totaly seperate things;

a mime type is a file extension mapping to a program

and a file permision -x tells the os if the user can run the file or not;

neither can be "interchanged", they have nothing in common;

for example;

i have test1.php and test2.php;

i run;

chmod +x test2.php

both are of mime type;

application/x-httpd-php

but only one has the file permission to run (+x)

... hope this helps...

---

### Post by PrimroseGrange on 2011-07-13
> **mikejonesey said:**
> no both are totaly seperate things...
 
Thanks, jonesey. That's the definitive response I was looking for.

---

