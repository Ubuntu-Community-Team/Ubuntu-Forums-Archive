---
title: "cd into a directory with a space in it"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by cfree220 on 2009-03-24
I'm trying to convert all of my .wav files into .flac for better tag support in my media players. I need to cd into directories such as ~/Music/Aine Minogue.

I tried to do the conversion as follows:
```

cd ~/Music
flac -8 --keep-foreign-metadata -f */*/*.wav
```

where
-8 indicates highest quality
--keep-foreign-metadata will try to preserve tags from original .wav
-f overwrites existing .flac files of same output name
and
*/ =>Artist
*/*/ =>Album
*/*/*.wav => .wav file

This only actually converted two Niel Young files...

What I need to know is:
a. how to cd into a directory that has a space in it and
b. Do I need to change the command if there are folders with spaces in it inside that directory?

---

### Post by cfree220 on 2009-03-24
Nevermind on the first question. I still need to know whether or not I can phrase */*/*.wav to ignore spaces...

---

### Post by RedSingularity on 2009-03-25
Put the name with the space in quotes.

---

### Post by cfree220 on 2009-03-25
Quotes didn't do anything for me... :-/

---

### Post by HermanAB on 2009-03-25
You have just learned a valuable lesson:

[INDENT]*Do not use file names with spaces or funny characters in them.*[/INDENT]

It is even more important with names: hostnames, domain names and the like, should never contain funny characters or upper case characters.

If you want to read up, google for 'POSIX Portable Names'.

Cheers,

Herman

---

### Post by cfree220 on 2009-03-25
:-/
Syntax can be really annoying when dealing with media libraries. My file hierarchy is, in large part, determined by the default rip settings of various media players...

Why they don't add a dash or an underscore in place of the space, I don't know.

---

### Post by RedSingularity on 2009-03-25
You did this?........~/Music/"Aine Minogue"

---

### Post by cfree220 on 2009-03-25
Ahhh! No, I thought I had to do

cd '~/Music/Aine Minogue' ...I wonder if that's the Windows syntax
When that didn't work, I tried:
cd ~/Music/Aine\ Minogue
Which worked.

Thanks for the tip! :)

---

### Post by logos34 on 2009-03-25
Since it appears you're going to be doing a lot of conversion, you might consider adding the verify option ("**[COLOR="Red"]-V[/COLOR]** --verify"). 

Just a tip...adds a little peace of mind.
> 
flac has a verify option -V that verifies the output while encoding. With this option, a decoder is run in parallel to the encoder and its output is compared against the original input. If a difference is found flac will stop with an error.

[http://flac.sourceforge.net/documentation_format_overview.html](http://flac.sourceforge.net/documentation_format_overview.html)


---

### Post by cfree220 on 2009-03-25
o.O

I saw that in the --help info and totally forgot to do that!

It's only 460 songs... I guess I should probably copy over the source from my server and convert them again with that command.

Thanks for the tip!

---

### Post by theozzlives on 2009-03-25
> **Shadow121 said:**
> You did this?........~/Music/"Aine Minogue"

Its:
```
~/Music/Aine\ Minogue
```

---

### Post by Peasantoid on 2009-03-25
Hey, just so you know, sticking the tilde (~) in quotes (single or double) causes the shell not to parse it. You'd need to use "cd /home/yournamehere/stuff" instead.

---

### Post by cfree220 on 2009-03-25
Yet another good tip! Thank you!

---

### Post by apmcd47 on 2009-03-25
> **cfree220 said:**
> Nevermind on the first question. I still need to know whether or not I can phrase */*/*.wav to ignore spaces...

How about [PHP]find . -name '*.wav' -print0 | xargs -0 cmd -args[/PHP]where _cmd -args_ is your original command. The *-print0* directive and the *-0* option to xargs will handle special chars (read: spaces) in the file path.

Andrew

---

