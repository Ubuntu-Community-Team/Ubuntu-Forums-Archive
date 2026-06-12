---
title: "creating a .hidden file"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by supermooshman on 2009-11-03
Hi all,

I read somewhere on the forum you can make a ".hidden" file in your directory, which will make the listed items hidden.

Can someone explain how to go about this?
at this time I have a file named ".hidden" and I have a file (for the sake of the argument) called "thisshouldnotbevisible" - making it /media/external/thisshouldnotbevisible


Anyone any help?
many thanks in advance

---

### Post by peculiar penguin on 2009-11-03
The dot at the beginning of a file/directory name causes various programs (e.g. ls without the -a switch, Nautilus with "Show hidden files" not set) to not show that specific file/directory by default. Simply rename your file/directory accordingly.

Please note that this isn't even "security by obscurity", because it's well known by anyone with even the slightest clue about Unix-like operating systems. This is more meant to reduce visual clutter in your home directory (so you don't have to sift through all those configuration files etc. to find the files you actually work with).

---

### Post by Tyke91 on 2009-11-03
+1 to peculiar penguin, most people looking for something would use a command like "ls -lah" anyway, so they would see your files.

but yeah. if you want to make a file hidden, put a period in front of it's name
```
~/hideme
```
becomes
```
~/.hideme
```

it's really only there to reduce clutter.

---

### Post by supermooshman on 2009-11-04
not to worry, I have no intention of hiding anything from prying eyes (just my own :)

but it is right to assume that
```
~/hideme
```is another file than
```
~/.hideme
```so my question would be; how does the method with the .hidden file work (**[which is explained here, from step 4]("http://www.ehow.com/how_5080631_hide-files-ubuntu.html")**)

Thanks

---

### Post by 3rdalbum on 2009-11-04
Create a file called .hidden. Inside this file, put the names of files in that directory that you want to be hidden within Nautilus. Put each filename on a different line.

Now they will not appear in Nautilus (unless you have the "Show hidden files" option turned on) but they are still available from the command-line or another file browser.

---

### Post by NickJones on 2009-11-04
If you want something to hide questionable files, download[ TrueCrypt ]("http://www.truecrypt.org/downloads")and you can sleep happily knowing that no one will find your....

---

### Post by jeffus_il on 2009-11-04
hidden files are not visible when using directory listing commands ```
ls
``` in a terminal.
or by display in a GUI file manager.

If you want privacy from other users to make sure the files are only accessible by logging in with your username and password, then look into file permissions. A file may for example may be rw (readable and writable) by the [COLOR="Red"]owner[/COLOR] for example but not by members of the same [COLOR="Red"]group[/COLOR] or by the rest of the [COLOR="Red"]world[/COLOR] . This may be what interests you more than hiding files.
As mentioned below encryption is also an option. this would be more appropriate for files sent by mail, or uploaded to the internet.

---

### Post by mcduck on 2009-11-04
> **supermooshman said:**
> Hi all,

I read somewhere on the forum you can make a ".hidden" file in your directory, which will make the listed items hidden.

Can someone explain how to go about this?
at this time I have a file named ".hidden" and I have a file (for the sake of the argument) called "thisshouldnotbevisible" - making it /media/external/thisshouldnotbevisible


Anyone any help?
many thanks in advance

The thing is that you can only hide files/directories from the same directory where the .hidden file is located. So no paths are supported.

In the case of the example file you mentioned you'd have to place the .hidden file in /media/external/.hidden, and then add "thisshouldnotbevisible" to the file.

Also note that hiding things this way only works in Nautilus and some other graphical file managers, the rest and the CLI will show the files anyway (unlike files hidden by adding a dot in their filenames). But it's still a nice trick when you want to hide something from your file manager without changing the name.

---

### Post by supermooshman on 2009-11-04
aaaah success! 
no idea why it did not work before.

> **NickJones said:**
> you can sleep happily knowing that no one will find your.... euhm no idea what you are getting at, but I am working on a 4 gb eee, so no leftover diskspace for images or videos of a certain nature :lolflag:

---

