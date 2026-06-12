---
title: "Delete multiple files recursively"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by farkle_one on 2011-02-20
I've been using Ubuntu for a few years now and have set up my first server using 10.04. The problem is that I have several itunes files (from my wife) that are no use to me in several sub folders under my Music share. The offending files are of the .mp4 and .m4v file extension. I want to delete these filles in the Music folder and all sub folders to save space but have had no success experimenting on my test computer. 

When I try:

```
sudo rm *.mp4
```I remove just the .mp4 files in the directory that I'm in and not any of the sub folders.

when I try:

```
sudo rm -R *.mp4
```I get the same results. 

and of course when I try:

```
sudo rm -R * 
```I delete the folder, all sub folders, and everything in them, which is not what I'm after. 

Can anyone tell me what I need to do to clean out the offending files from the Music folder and all of it's sub folders?

Thanks for any help.

---

### Post by 1clue on 2011-02-20
Maybe we need some more specific description of the problem.  You need to adequately specify each file, or a regular expression that shows the ones you want.

rm -r (or -R) is the right command, but does it say file not found or what?

Any filename with a space in it either needs to be quoted or the space needs to be escaped.  For example:

'my file.mp4'
or
my\ other\ file.mp4

---

### Post by idi0tf0wl on 2011-02-20
> **1clue said:**
> ...
rm -r (or -R) is the right command, but does it say file not found or what?
...
rm -r removes a **directory** recursively. rm -r *.mp4 will delete any folders in that directory that end with ".mp4" and all of the files inside of them. I doubt this is what you want to do.

Your best bet is to write a small script that does rm *.mp4 and then jumps into all of the folders within that folder and does the same, and so on until there are no more folders left into which you can navigate. Or, just do this:
```
$rm *.mp4
$rm */*.mp4
$rm */*/*.mp4
```
and so on until it tells you no such directory exists. If you're skittish about losing everything (rm * is devastating and irrevocable), use rm -i in place of rm to confirm the results of the regex with yourself before removing things permanently.

---

### Post by ksprasad on 2011-02-20
You can use find command.
 
```
 
$>find . -type f -name "*.mp4" -exec rm {} \;

``` 
hope, this helps.
 
Regards,
ksprasad

---

### Post by sisco311 on 2011-02-20
Welcome to the forums!

Assuming that you use bash4, you can do something like:
```
shopt -s globstar
cd /path/to/dir
rm -i -- **/*.mp4 **/*.mv4
```

See:
```
man bash | less +/globstar
```

If you don't fully understand what the commands do, then please feel free to ask for clarification.

---

### Post by sisco311 on 2011-02-20
> **ksprasad said:**
> You can use find command.
 
$find . -type f -name "*.mp4" -exec rm {} \;
 
hope, this helps.
 
Regards,
ksprasad

Instead of *-exec rm*, I would use find's -delete option. ;)

---

### Post by idi0tf0wl on 2011-02-20
sisco311 I just learned something! Slick! Thanks! Cheers!

*Ahem*, hopefully the OP learned something cool too.

---

### Post by Smart Viking on 2011-02-20
A one liner:

[HTML]for file in $(find . -name \*.mp4 -print); do rm $file; done[/HTML]
And just change the ".mp4" part.

---

### Post by sisco311 on 2011-02-20
> **ksprasad said:**
> You can use find command.
 
```
 
$>find . -type f -name "*.mp4" -exec rm {} \;

``` 
hope, this helps.
 
Regards,
ksprasad

If you don't mind, I have another suggestion (or two..., or more). :)

```
find . -name '*.mp4' -type f -delete
```

The -name test comes before the -type test  in  order  to  avoid having to call stat(2) on every file.

You should use single quotes in order to let find to interpret the arguments.

*rm* accepts one or more files as an argument, so, if you use -exec instead of -delete, you should use the *-exec command '{}' +* syntax.

```
find . -name '*.mp4' -type f -exec rm -i -- '{}' +
```

> **idi0tf0wl said:**
> sisco311 I just learned something! Slick! Thanks! Cheers!


You're welcome!

---

### Post by sisco311 on 2011-02-20
> **Smart Viking said:**
> A one liner:

[HTML]for file in $(find . -name \*.mp4 -print); do rm $file; done[/HTML]
And just change the ".mp4" part.

[s]Oh, boy! :)[/s]

Please check out:

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

---

### Post by Smart Viking on 2011-02-20
> **sisco311 said:**
> [s]Oh, boy! :)[/s]

Please check out:

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

Aha!

That makes sense. Spaces in file names is a nono though, would never have 'em on my system. :)

---

### Post by ksprasad on 2011-02-21
> **sisco311 said:**
> If you don't mind, I have another suggestion (or two..., or more). :)
 
```
find . -name '*.mp4' -type f -delete
```
 
The -name test comes before the -type test in order to avoid having to call stat(2) on every file.
 
You should use single quotes in order to let find to interpret the arguments.
 
*rm* accepts one or more files as an argument, so, if you use -exec instead of -delete, you should use the *-exec command '{}' +* syntax.
 
```
find . -name '*.mp4' -type f -exec rm -i -- '{}' +
```
 
 
 
 
Thanks for the info :)

---

