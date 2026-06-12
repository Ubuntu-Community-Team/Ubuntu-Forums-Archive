---
title: "Renaming to hide?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Curtiee on 2009-10-06
Okay, so I know how files can be hidden by prefixing them with a . then press Ctrl + H to hide/show the hidden files.

What sort of shell script would I use to rename multiple files so that they're hidden?

I had something like this:

```
for f in /home/curtiee/desktop/*.txt;do mv $f .$f;done
```but when I run it, it tells me that "mv: cannot stat `/home/curtiee/desktop/*.txt': No such file or directory"

I am quite good at PHP, so I do have a "general understanding" of codes and the such, hence how I managed to modify some Shell to get the above...

Anyway, how would it be done? :$

All help is appreciated :3

*I'm also unsure if this is the correct forum, but it is basic help. I think :$*

---

### Post by drs305 on 2009-10-06
Curtiee, 

Welcome to Ubuntu and the Ubuntu forums.  :-)

I can't answer your question but will give you another option. 

If you want to hide files *in Nautilus*, without renaming them, you can create a file in the applicable folder called *.hidden*  Within this text file include the filename of any file you don't want displayed. 

If you elect to not view hidden files, any listed in the .hidden file will not be displayed in Nautilus.

---

### Post by CharlesA on 2009-10-06
Sidenote: linux hides anything with a "." before the filename. e.g., .vnc.

---

### Post by ibuclaw on 2009-10-06
May I also note that Desktop is spelt with a Capital 'D'

Also, feel free to get acquainted with the command **rename**.
It is based on Perl, so as a PHP developer, you may understand some of the syntax ... or not. :)
```
rename 's/^/./' /home/curtiee/Desktop/*.txt
```
and to change it back:
```
rename 's/^.//' /home/curtiee/Desktop/.*.txt
```

Regards
Iain

---

### Post by Curtiee on 2009-10-06
> **drs305 said:**
> Curtiee, 

Welcome to Ubuntu and the Ubuntu forums.  :-)

I can't answer your question but will give you another option. 

If you want to hide files *in Nautilus*, without renaming them, you can create a file in the applicable folder called *.hidden*  Within this text file include the filename of any file you don't want displayed. 

If you elect to not view hidden files, any listed in the .hidden file will not be displayed in Nautilus.
Thank you! (:

I was really just hoping to have some sort of Bash script to hide files in a certain directory. It's more to see how it's done, to further my knowledge of Bash, than the actual use of it, as I could do as you said (which I didn't know, so thank you), and also just put it in a hidden folder.

> **CharlesA said:**
> Sidenote: linux hides anything with a "." before the filename. e.g., .vnc.
I did know this already, but thanks for the help, nonetheless (:

My actual query is with the actual Bash-ing o.o

---

### Post by drs305 on 2009-10-06
> **Curtiee said:**
> 
I was really just hoping to have some sort of Bash script to hide files in a certain directory. It's more to see how it's done, to further my knowledge of Bash, than the actual use of it, as I could do as you said (which I didn't know, so thank you), and also just put it in a hidden folder.

I mentioned it because I think my preference would be to write a script to put the name in the .hidden folder rather than change the actual filename.  ;-)

---

### Post by Curtiee on 2009-10-07
> **tinivole said:**
> May I also note that Desktop is spelt with a Capital 'D'
Okay, I'll remember that, thanks. :3

> **tinivole said:**
> ```
rename 's/^/./' /home/curtiee/Desktop/*.txt
```and to change it back:
```
rename 's/^.//' /home/curtiee/Desktop/.*.txt
```
I'm not familiar with Perl... Yet.

I've tried running that (from the Terminal), but it just tells me [i]curtiee@Curtiee:~$ rename 's/^/./' /home/curtiee/Desktop/*.txt
Can't rename /home/curtiee/Desktop/atestingfile.txt ./home/curtiee/Desktop/atestingfile.txt: No such file or directory[/i]

I'm also not sure about the *'s/^/./'* bit, if I'm honest :$

---

### Post by kaibob on 2009-10-07
I tried the following, which failed:

```
for f in /home/kaibob/temp/*.txt ; do mv "$f" ".$f" ; done
```

I then changed the current directory to /home/kaibob/temp and ran the following, which did work:

```
for f in *.txt ; do mv "$f" ".$f" ; done
```

I don't know enough about filename expansion to explain why one worked and not the other. I'm sure a more knowledgeable forum member can explain.

---

### Post by Curtiee on 2009-10-07
> **kaibob said:**
> ```
for f in *.txt ; do mv "$f" ".$f" ; done
```I don't know enough about filename expansion to explain why one worked and not the other. I'm sure a more knowledgeable forum member can explain.
It worked! :D!

That's brilliant, thank you! :D

Edit: Okay, so I've now got this:

```
#!/bin/bash
cd /home/curtiee/Desktop/
for f in *.txt; 
do mv "$f" ".$f"; 
done
```

What file format do I save it as, so that I can double click to run? :$

---

### Post by DaithiF on 2009-10-07
Hi,
the problem with both the for loop and the rename approach above is that they are operating on the full path + filename, ie. trying to rename
```
path/to/file => .path/to/file

```
rather than
```
path/to/file => path/to/.file
```
the failure is because there is no directory .path and so the mv and rename commands both fail.

the easiest way around this is to cd into the directory first so that there are no leading directories to worry about.

---

### Post by issih on 2009-10-07
it works that way becuase you are prefixing the . at the front of the full path rather than at the front of the filename.

i.e.:
```

/home/bob/tweedledee/thing.txt
```

is renamed to:

```
./home/bob/tweedledee/thing.txt
```

rather than

```
/home/bob/tweedledee/.thing.txt
```

This happens because you use the full path in your initial query, so the system lists each "f" using its full path. Going the other way you are using relative paths, and just listing the filenames in the local directory, so that works.

You could look into using the commands dirname and basename to correct the behaviour if you want to 

Hope that helps

---

### Post by DaithiF on 2009-10-07
and just to add the (not-so-easy) alternative :)

you could manipulate the path + file to prepend the '.' character to the filename like this:
```
for f in tmp/testdir/*.txt; do echo mv "$f" "${f##/*}/.${f%%/*}" ; done
```

---

### Post by Curtiee on 2009-10-07
> **Curtiee said:**
> It worked! :D!

That's brilliant, thank you! :D

Edit: Okay, so I've now got this:

```
#!/bin/bash
cd /home/curtiee/Desktop/
for f in *.txt; 
do mv "$f" ".$f"; 
done
```What file format do I save it as, so that I can double click to run? :$

> **DaithiF said:**
> the easiest way around this is to cd into the directory first so that there are no leading directories to worry about.Hey!

I managed to do this, and my little mini-script now works! :3

The only question I have now is: > **Curtiee said:**
> What file format do I save it as, so that I can double click to run? :$

And here is the code incase someone missed it and is curious:
```
#!/bin/bash
cd /home/curtiee/Desktop/
for f in *.txt; 
do mv "$f" ".$f"; 
done
```

---

### Post by DaithiF on 2009-10-07
> What file format do I save it as, so that I can double click to run? :$
there is no particular file format to save it as, you have already told the system what command to use to run the file by the shebang #!/bin/bash in the first line.

the convention is sometimes to name shell scripts like this with a .sh extension, but its not required, you can basically name the file whatever you want.  The only requirement is that the file is marked as executable
```
chmod +x yourfile
```

---

### Post by kaibob on 2009-10-07
> **DaithiF said:**
> Hi,
the problem with both the for loop and the rename approach above is that they are operating on the full path + filename,... 
Thanks DaithiF. I was looking at an issue with filename expansion, while the answer was much simpler.

---

### Post by Curtiee on 2009-10-07
> **DaithiF said:**
>  The only requirement is that the file is marked as executable
```
chmod +x yourfile
```
Aha, that's what I was missing!

This works beautifully, just as I wanted it to. Thank youuu everyone! (L)

---

