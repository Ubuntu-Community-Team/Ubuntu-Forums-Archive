---
title: "Text file won't open...encoding problem?"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-15
Hi,

Odd problem with ONE of my text files.

I have a text file that is being written to successfully...but I cannot open it with gedit like I can all the others. The backed up copy still opens just fine...just not the current new one that is being appended to.

Gedit says something about it cannot read the character encoding.

When I ran the command file myfile it says
"ASCII text with very long lines"

All the other files are fine and open normally.

I opened the file in question with gvim and it appears normal....meaning the contents look the same as the files that are opening as expected.

I tried opening the file with gvim, then saving it back with a new name but the new file has the same problem.

Been working on this for a day or two now and decided it was time to seek assistance.

Any idea why Gedit cannot open this file?

Thx for yours

---

### Post by Hippytaff on 2010-11-15
Can you cat it succesfully?

---

### Post by mistypotato on 2010-11-15
sudo cat myfile.txt myfile1.txt

"file not found"

But I'm not combining any files so why use cat ?

---

### Post by Hippytaff on 2010-11-15
Cat should output the contents of a file to the terminal
```

cat myfile.txt

```

---

### Post by mistypotato on 2010-11-15
Ah...

thx

Yes...it seems to display the contents just fine using cat.

I can also open it with GVIM....but not GEDIT

---

### Post by mistypotato on 2010-11-15
So I went one step further and opened the file with Bless Hex Editor and it  looks perfectly fine :confused:

I have no clue why gedit cannot open this file.

---

### Post by Hippytaff on 2010-11-15
Can Gedit open other files fine...this is odd :-)

---

### Post by mistypotato on 2010-11-15
> **Hippytaff said:**
> Can Gedit open other files fine...this is odd :-)

Right?

Yes, this is the ONLY file gedit cannot open....but I can't find a single reason for this behavior.

---

### Post by mcduck on 2010-11-15
Based on the what the "file" command said, the file either has extremely long lines or no line changes at all (or using some line terminators Gedit doesn't understand).

Many programs have limit to the max line length they can handle. And so does GtkTextView, which Gedit uses (about thousand characters per line, if I remember right).

Enabling text wrapping might help.

---

### Post by mistypotato on 2010-11-15
> **mcduck said:**
> Based on the what the "file" command said, the file either has extremely long lines or no line changes at all (or using some line terminators Gedit doesn't understand).

Many programs have limit to the max line length they can handle. And so does GtkTextView, which Gedit uses (about thousand characters per line, if I remember right).

Enabling text wrapping might help.

The odd thing is that it's an apache log....along with many others and not ANY other file has this error.  ALL other files can open normally.  I've been opening these files with gedit literally for years...maybe 5 or 5 ?  Not the SAME file of course....each time the logs rotate the old one is tarred and a new one created....but the current one is the one gedit cannot open?

I never opened the file in Windows or anything like that and unless there are hidden line terminators, it's the same as all the other files apache creates for logs.  I CAN open it with all the other text editors such as gvim....just not Gedit.

---

### Post by Hippytaff on 2010-11-15
maybe just copy the text to a new file...cat then copy and paste.

---

### Post by mistypotato on 2010-11-15
Here is the first byte from the ASCII file...each line start similarly...

36 36 2E 32 34 39 2E 37

and the plain text .....

66.249.

and here is the last byte of the line (each line ends the same)

2E 68 74 6D 6C 29 22 0A

and the plain text......

t.html)".



there are thousands of lines, but each starts the same.  I have opened MUCH larger files than this one with gedit.

---

### Post by Hippytaff on 2010-11-15
I can see your determined to get to the bottom of this :-)

I would have given up ages ago and copied the info to a new file :-)

---

### Post by mcduck on 2010-11-15
> **mistypotato said:**
> The odd thing is that it's an apache log....along with many others and not ANY other file has this error.  ALL other files can open normally.  I've been opening these files with gedit literally for years...maybe 5 or 5 ?  Not the SAME file of course....each time the logs rotate the old one is tarred and a new one created....but the current one is the one gedit cannot open?

I never opened the file in Windows or anything like that and unless there are hidden line terminators, it's the same as all the other files apache creates for logs.  I CAN open it with all the other text editors such as gvim....just not Gedit.

Well, maybe this time Apache just generated some very long error message, perhaps with some long URL. That could result in one very long line in the log.

It's pretty hard to say anything for sure without seeing the file. But everything really does point to the file having one or more very long lines, like the "file" output says, and if the line(s) are long enough that would be a problem to any text editor that uses GtkTextView. (vim of course doesn't use it, it's not a GTK application)

---

### Post by mistypotato on 2010-11-15
I'm trying to find the longest lines in a gvim file by enabling the bottom scrll bar then moving to the right side of the file but gvim refuses to stay put to the right and as soon as I move the mouse, shifts back over the the left.

Any way to get it to stop doing that so I can find the longest line ?

---

### Post by mistypotato on 2010-11-15
> **Hippytaff said:**
> I can see your determined to get to the bottom of this :-)

I would have given up ages ago and copied the info to a new file :-)

Well, they're very important files and in case it ever happens again I'd like to know what to do.

btw... I DID try copying the file and pasting the text into a new file and saved it but I got the same error.

So, I'm trying to see if McDuck is onto something and look for very long lines but as indicated, gvim isn't helping.

---

### Post by col48 on 2010-11-15
The file is clearly 1 byte per char.

Why not try splitting (_a copy of_) the file in two using either gvim (divide at the end of a line) or the Bless editor (divide after a 0A byte) and seeing whether it affects just one half?

On the assumption that it is just one line or a small set of neighbouring lines which is causing the problem you could isolate those lines by repeated division in this way and then have a closer look at them alone.

---

### Post by col48 on 2010-11-15
And a text editor isn't the only option.....

What about paste into OpenOffice Calc?  If the file does not have too many lines, you could paste into one column and use a the len function in an adjacent column on each line to find the length of each line.

---

### Post by mistypotato on 2010-11-15
thx.

Good suggestions :KS

---

### Post by AngusH on 2010-11-15
Hey, don't know if this will be of help but worth a shot, quick python script to tell you the length of the longest line:

```
top=0
x=raw_input()
try:
	while x:
		if len(x)>top:
			top=len(x)
		x=raw_input()
except EOFError:
	print top
	exit()
```
Copy that into a file called script.py (or whatever) then run ```
python script.py < file
``` where file is the path to the file causing the problem.

(Yes I know it's a rubbish script, but I'm not very good with python, just used it because it's easier for me than bash and is installed on Ubuntu by default)

---

### Post by mcduck on 2010-11-15
I just realized that there's actually a very simple way to check if a long line might be causing the problem; you can use "wc -L" to check the length of the longest line in a text document.

```
wc -L /path/to/somefile.txt
```

---

### Post by mistypotato on 2010-11-15
> **mcduck said:**
> I just realized that there's actually a very simple way to check if a long line might be causing the problem; you can use "wc -L" to check the length of the longest line in a text document.

```
wc -L /path/to/somefile.txt
```

Hmmmmm

It returned a line number but it definitely wasn't the longest line :confused:

---

### Post by mcduck on 2010-11-15
> **mistypotato said:**
> Hmmmmm

It returned a line number but it definitely wasn't the longest line :confused:

It doesn't return a line number, it returns the length of the longest line.

If you prefer, you can also use awk to print the length together with the text of the longest line:
```
awk ' { if ( length > L ) { L=length ;s=$0 } }END{ print L,"\""s"\"" }' /path/to/somefile.txt
```

---

### Post by mistypotato on 2010-11-15
ok.

That number was 973.

Do you think a line that is 973 chars long is choking gedit?

---

### Post by AngusH on 2010-11-16
> **mcduck said:**
> I just realized that there's actually a very simple way to check if a long line might be causing the problem; you can use "wc -L" to check the length of the longest line in a text document.
 
```
wc -L /path/to/somefile.txt
```
 ^^ Much better than my script :)
Angus

---

### Post by mcduck on 2010-11-16
> **mistypotato said:**
> ok.

That number was 973.

Do you think a line that is 973 chars long is choking gedit?

I just tested creating a text file with a 1000-character line, and it did open in Gedit, although with even a single line that long it did take a good while to load.

But anyway, that would mean that the line legth, at least alone, can't be the problem.

Sorry, but I really have no further ideas, as the long line(s) are actually the only information we have about the file in question. Hopefully somebody else comes up with some other idea.

---

### Post by migs73 on 2010-11-16
I have seen a similar problem in a completely unrelated system/software, where the extra length in the line was due to spaces. Does the command you tried count spaces? 
McDuck, did your 1000 character line have spaces?

The OP's example lines had a space about every third character.


EDIT; Just checked it myself, and the command does count space.....oh well worth a shot.

---

### Post by mcduck on 2010-11-16
no, I just used a simple script to generate the file so it had no spaces.

Of course I could test with spaces, or multiple long lines.

Anyway, even the single 1000-char line took a good 8 seconds to load in Gedit, so it definitely does have some issues with such long lines. Maybe if there are couple of such long lines, or if the file is otherwise large enough, that would result in the file not opening at all. But that's just guessing.

---

### Post by migs73 on 2010-11-16
Mcduck

Maybe you missed my edit, but the command does count spaces so it isn't that. You might be on to something with the multiple long lines.

FYI the case I was referring to was a text editor/compiler that would accept commands at any length, but when you download into a BASIC module in a PLC it would fall over as the lines were to long, even though the lines we added were not the longest. It seemed the compiler ignored spaces but the module 'counted' them (even though the file was downloaded from the module in the first place).
Very confusing. :confused:

---

### Post by mistypotato on 2010-11-18
It has nothing to do with spaces or line length....imo

Remember, the file is an apache log file.   I have literally hundreds of them and have never had this problem.  It is also the ONLY one gedit cannot open.  The only way I could see either of those being a problem is if someone maybe tried hacking and the entry went into the logs and had all kinds of garbage code in the line.  But the file is about 200MB now (it's growing as we speak) and finding a bad line is like looking for a needle in a haystack.  I may just rotate the log and let apache create a fresh one.   I do believe the cure is that simple, however, I would like to find a solution as this could possibly happen again and I like to use gedit to open the file occasionally and scan the entries for unusual activity.

The log still works, apache is still appending new entries to it and AWSTATS is apparently reading the info from it just fine as it updates every morning and I can see it's updating and looks accurate.

The error says that it is not "Encoded" properly, yet I cannot find any problem with the file.

I can open it with GVIM also with no problem...but I personally find gvim a bit tedious.

So at this point, my best guess is that it's a bug with gedit.

---

### Post by Kamilion on 2011-01-06
I ran into this today, trying to parse a serial capture of GPS data.

Turns out it had a bunch of NULs in it; 0x00.

My solution:

```
tr -d '\0' <gps-capture.log >gps-clean.log
```

After this, gedit opens it without issue.

How I figured this out:
Installed SciTE
```
sudo apt-get install scite
```
Opened the file, started scrolling, looking for black boxes.
Found 26 lines, removed all the others and saved to a bad.log file.
Installed GHex
```
sudo apt-get install ghex
```
Opened bad.log with GHex. Noted a bunch of 0x00s that should not have been there; and no other odd character codes.
Googled for a couple minutes, found [an old usenet message from april 2003]("http://unix.derkeiler.com/Newsgroups/comp.unix.questions/2003-04/0120.html") with the 'tr' command syntax.

Declared Success.

Hope this helps you; if you can identify the errant character code, tr -d '${character}' <infile >outfile should be able to strip it.

---

### Post by col48 on 2011-01-08
I think Kamilion has probably hit the button.  Perhaps the Apache log includes a report of some 'bad' characters it found - 'bad' in the sense of the NULs that Kamilion had.

All the non-printable character codes have to be handled by an editor, and some of them have special meanings (such as 'bell', 'end of line', 'line feed', 'tab', 'end of file'); some of these meanings may only be interpreted accurately by the program which wrote them.  The editor has to decide what to do with each one.  Perhaps gedit does not cope with (say) two nulls in a row.

Maybe the OP could report back his findings?

---

### Post by SlugSlug on 2011-02-18
am having this roblem with several txt files - gedit - maverik

---

