---
title: "remove extra period (.) from filename"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by skooter1121 on 2009-10-07
I've got a bunch of files that I want to remove the extra periods in the file name and replace with spaces. EX: Skooter.Art.Image.001.jpg to Skooter Art Image 001.jpg

Can this be easily done?

I'd like to use nautilus to  be able to highlight the file or files I'd like to rename.

There does not seem to be a script to do this.

Can anyone help?


-Skooter

---

### Post by mikeyphi on 2009-10-07
Right-click on file icon - select 'rename'....

don't know of a way to do all files at the same time.....unless you write a script!

---

### Post by orngjce223 on 2009-10-07
[http://www.unixguide.net/unix/bash/G6.shtml](http://www.unixguide.net/unix/bash/G6.shtml) is the basic template that should work I think.  That, or you can write a quick application-ette in some other language.  I don't know how to do that (as much a n00b as you are :D).

Basically, take something that looks vaguely like the example given above, and stick it into a text file, then right click it and set it executable.  Now you have an executable text file.  Stuff that into the right folder, and run it.  *trots off to learn some more shell syntax* xD

---

### Post by skooter1121 on 2009-10-07
Thanx for the replies:

I have found the RENAME on right click, would take forever on 1000 files,

Triied that template but it also removed the period before the file extention. File now lookslike Skooter Art Image 001 jpg.


Any other suggestions?

-Skooter

---

### Post by orngjce223 on 2009-10-07
Tweak the thing to add a period before the JPG, run it again, and you should be done.

---

### Post by DaithiF on 2009-10-07
using the terminal, you can use the rename command for this:
```
rename 's/\.(?!jpg$)/ /g' *.jpg
```
will replace all '.' characters with spaces, except for the last '.' before the jpg extension.

---

### Post by skooter1121 on 2009-10-07
Thanx DaithiF,

Yes this worked on all .jpg files in that folder, after I navigated to that folder in terminal. Seemed like a lot of steps.

(I tried to find the RENAME command line help file so I could see what this command was doing but rename -? --help did not work)

I guess I'm looking for a nautilus script to do this on selected files. Possibly for other file types also.

-Skooter

---

### Post by tom66 on 2009-10-07
*rename* takes a Perl-style regular expression and is very powerful if used properly. See the Perl docs on regular expressions ([http://perldoc.perl.org/perlre.html](http://perldoc.perl.org/perlre.html)) for more information.

To get help on any command, type 'man' before it. Example: *man rename* gives the manual/docs for *rename*.

---

### Post by atomizer on 2009-10-07
It is not recommended to use spaces in linux file names.

You could use an underscore "_" instead of a period

---

### Post by tom66 on 2009-10-07
Why isn't it recommended? Most Linux filesystems permit all characters but the directory seperator (usually '/') and NUL. If you're entering a file name with spaces put it in quotes or put a slash before each space.

---

### Post by skooter1121 on 2009-10-07
tom66

WOW. Now I'm really confused. Way too much input.


atomizer

Thes files are located on a NTSF formatted drive. Does LINUX care differently then? Ok, then I'd like to replace the extra (.) with underscores. 

There has to be an easy solution.

-Skooter

---

### Post by tom66 on 2009-10-07
Sorry if I confused you. I'm confused about what atomizer said.

NTFS will work with almost any character except "\", "/" and NULL (0). You don't really need to worry about NULL though, it has little use in file names.

In Windows, additionally you cannot enter a name with ":", "*", "?", double quote, "<", ">" or "|". You can access a file with all of these characters, but you can't use any Windows Explorer/Shell application to name them. In other words, you can access these files with odd names but you can't rename or create them such that they contain these characters. It's just a throwback from the old DOS days where these characters have special meaning.

---

### Post by sisco311 on 2009-10-07
You can try one of the GUI bulk renaming tools:
[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

---

### Post by skooter1121 on 2009-10-07
tom66

Thanks for clearing that up for me.

sisco311

I've already tried gprename, and was unable to exclude the extension. Looking at purr now. Like to stay with nautilus.

ALL:

All I want to do is rename files with extra (.) and (_) so my 86 year old dad can read the file names on his WebTV. He gets confused by all the extra stuff.

-Skooter

---

### Post by DaithiF on 2009-10-07
personally i would use the command line for things like this, but i took a look at gprename and you can use the regular expression i gave you earlier to achieve what you want.

In the Replace/Remove tab of gprename, check the 'Regular Expression' checkbox, and in the replace box put:
```
\.(?![A-Za-z]*$)

```and in the with box, put underscore, space, or whatever you wish.

the expression above is a generalized form that will work for most file extensions (which contain alphabetical chars only)

good luck

---

### Post by CaptainMark on 2009-10-07
atomizer i freaking love your signature, it just made me spit cider all over my keyboard because i was laughing so much

---

### Post by skooter1121 on 2009-10-07
DaithiF

when I used your expression in GPRename it also removed the (.) before the extension. As shown in the New Name column.

Where in that expression would I put (_) rather than the period to change that.

I appreciate your patience with me on this. I've just gotten this Netbook and Linux i brand new to me.

-Skooter

---

### Post by DaithiF on 2009-10-07
hmm, works for me, see screenshot.
can you double check that you entered the expression exactly:
\.(?![A-Za-z]*$)

---

### Post by sisco311 on 2009-10-07
gprename:
[img]http://www.upload3r.com/serve/071009/1254946797.png[/img]


thunar:
[img]http://www.upload3r.com/serve/071009/1254946807.png[/img]

---

### Post by skooter1121 on 2009-10-07
Here's my screen-shot.

works for .jpg but not .mp4 ?

Isn't a (.) a(.) anymore?

-Skooter

---

### Post by sisco311 on 2009-10-07
> **skooter1121 said:**
> Here's my screen-shot.

works for .jpg but not .mp4 ?

Isn't a (.) a(.) anymore?

-Skooter

try:
```
\.(?![A-Za-z0-9]*$)
```

---

### Post by skooter1121 on 2009-10-07
Yes, now I was able to get this to work.

Thank You all.

Can anyone tell me what this "Regular Expression" does in plain language. I had never heard of it before.


-THANX

-Skooter

SOLVED

---

### Post by niteshifter on 2009-10-07
> **skooter1121 said:**
> 
Can anyone tell me what this "Regular Expression" does in plain language. I had never heard of it before.


Regular Expression is pattern matching on sequences of characters. That's about as simple as I can put it - it's an arcane subject on which entire books have been written. Here's the wikipedia [page]("http://en.wikipedia.org/wiki/Regular_expression") on the subject.

---

