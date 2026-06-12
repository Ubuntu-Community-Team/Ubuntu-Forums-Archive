---
title: "How do I install SBaGen (.tgz file, not in repositories as .deb)?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Shadow21 on 2009-10-31
I know you guys probably get a lot of these kinds of threads but I'm really confused and need help.

I'm trying to install a program called SBaGen (It's not in the software center) and it's in the .tgz format.

This is what I did:

I downloaded the program and I extracted it to the /usr/share folder because that's where I want to install it (or at least I think that's where I want to install it). After that I opened the "Read Me" file that was provided with the program. I went to the programs folder in the terminal and typed in "./mk" because that is what it said to do to install the program but I don't think that did anything. When I entered the command it waited for a few seconds and then a new command line came up.

I have no idea if that installed it so I'm hoping you guys could help.

And yes, I'm a newbie (You could probably tell lol :D)

---

### Post by mikewhatever on 2009-10-31
Hi Shadow21, and welcome to the forums. The readme says you need to run the mk script which is located in sbagen1.4.1/src. In other words,

cd /usr/share/sbagen1.4.1/src
sudo ./mk

By the way, I think /opt is probably a better place for it, since /usr/share has so much stuff, but it shouldn't matter.

---

### Post by cranecreek on 2009-10-31
[http://ubuntuforums.org/showthread.php?t=67628](http://ubuntuforums.org/showthread.php?t=67628)

---

### Post by Buuntu on 2009-10-31
The terminal might not output anything when you're running something like a script. That is normal and it doesn't mean that it didn't install.  You should only be concerned if you see any sort of error message.  
I'm pretty sure you installed it and now you can use it the way the program is meant to be used.  Read the text files inside the folder if you're unsure about how you use the program itself, but I'm quite certain you already installed it :)

---

### Post by Shadow21 on 2009-10-31
I'm guessing that SBaGen was installed on my computer because all it said to do was run the mk script.

Right now I'm just trying to learn how to open it and create new files for it.

These are the instructions that it gave to open it:

> 3: Invocation (all platforms)
-----------------------------
So, here we go.  The following example commands should be typed at the
shell prompt provided by your operating system, prepared as explained
above.

>> sbagen

This gives a brief usage information.
 
>> sbagen -h

This gives the full usage information, showing the version number and
the full list of options.  Check this for any new features.
 
>> sbagen prog-chakras-1.sbg

This runs the sequence in file 'prog-chakras-1.sbg', starting playing
whatever should be playing at the current moment, according to the
clock time.  The status-line at the bottom of the screen shows the
current time, and currently-playing tones/noise.  The two lines
immediately above show the period of the sequence which is being
played -- these lines scroll up the screen as one period moves into
the next.

Remember that you can stop the utility using Ctrl-C on all platforms:
Windows, Mac OS X and UNIX.  (Most UNIX users already know this, but
it seems that many Windows users don't know about this standard DOS
key combination).

>> sbagen -p drop 00ds+

This runs one of the built-in pre-defined sequences called "drop" with
the given parameters (see later for an explanation).

>> sbagen -m river1.ogg -p drop 00ds+ mix/99

This runs the same sequence, but mixes it with water sounds from the
loopable OGG file river1.ogg.

>> sbagen -m river2.ogg -p slide 200+10/1 mix/99

This runs another built-in pre-defined sequence and mixes it with
other river sounds.  This particular sequence keeps you in alpha for a
half-hour session whilst dropping the carrier right down to zero.

To test a sequence (without waiting the full 24 hours for it to play
through), run with the -q 'quick' option:

>> sbagen -q 120 prog-chakras-1.sbg

This example runs the sequence at 120 times the normal speed.  This is
quite useful to check that a new sequence is going to do what you
expect it to do.

To check that SBaGen has interpreted your sequence-file correctly, use
the -D option, which dumps a listing of the interpreted sequence
instead of playing it:

>> sbagen -D prog-chakras-1.sbg

To quickly test a particular tone-set continuously, use the -i
immediate option.  This is good for experimenting with different
ideas.  If your shell lets you recall the previous command with
up-arrow, you can quickly test and fine-tune a tone-set in this way
before putting it into a sequence:

>> sbagen -i pink/40 100+1.5/20 200-4/36 400+8/2

This incidentally, is an example of a complex brain-state built from
pink noise, to which is added three frequencies (1.5Hz, 4Hz and 8Hz)
each on an independant carrier (100, 200 and 400 Hz), at different
amplitudes (20, 36 and 2).  This combination is supposedly something
like "body-asleep, brain-awake", assuming I've reproduced it
correctly.

While you're at it, try the alternate 'spin' effect.  Not everyone
likes this, but in any case it's there if you want to use it:

>> sbagen -i spin:300+4.2/80

If you're having trouble with your soundcard or CPU usage on a very
old machine, use the -r or -b options to run at a lower output rate or
bit-width.  For example:

>> sbagen -r 8000 -i pink/40 100+1.5/20 200+6/30
>> sbagen -b 8 -i pink/40 100+1.5/20 200+6/30


For UNIX and Mac OS X, you'll find that there are a set of short
tone-set scripts (t-*) that you can run from the command-line.  For
example:

>> ls t-*
>> t-alpha

All these executable tone-set scripts (t-*) accept additional options
and pass them onto SBaGen, so you can use the same options (e.g. -r
and -b) with these as well.

Try out some of these scripts/batch files to get an idea of some of
the possibilities.


For all platforms (UNIX, Windows and Mac OS X), the sequence files
(prog-*) can be used in the same way:

>> sbagen prog-NSDWS-example.sbg

Have a play with these sequences.  Some of them are designed to run at
night, so you will hear nothing if you play them during the day.  You
get around this by playing them immediately using '-q 1', or '-S' (run
from start):

>> sbagen -q 1 prog-NSDWS-example.sbg
>> sbagen -S prog-NSDWS-example.sbg

On UNIX and Mac OS X, there are also a few Perl-scripts which you can
run (p-*).  These generate a sequence on the fly and then run it.  For
anyone familiar with Perl, this is a good way to generate sequences
that are slightly different each night in a random way.  For example:

>> p-nightly-sub-delta 7:30

This generates a night-time sequence in 'tmp-prog' with a wake-up time
of 7:30 and runs it.  Naturally you won't hear anything unless it is
already night time.How do I open the the shell thing?

---

### Post by metallicamike on 2009-12-03
I'm having the same problem. Running ./mk just makes it chill for a second and opens new command line. When you try to run something with sbagen it says command not found.

---

### Post by threecaster on 2012-08-20
This is still valid:

Sbagen 1.4.5

Ubuntu 11.04 Natty Narwhal

"./mk" appears to function (returns empty command line)

but "sbagen" returns "command not found" (or somesuch)

Some *explicit* instructions from some wise, compulsively elucidative unix sage would be lovely:

"Open terminal from your GUI by selecting 'Applications/accessories/Terminal' "
"type cd (and a space) followed by the path to the folder where you extracted your tar.gz"
"Install for Ubuntu 11.04 uses the ./mk-______ file for installation."
"Natty Narwhal should contain the GoblTgook Libraries which enable the ./mk-____ to work seamlessly..."
"when that does not perform as advertised, then invoke '_________' with the command '________________' to test your '_________' settings..."

If this type of talk strips the teeth from your gears in any sort of excruciating manner, or you feel it deprives the "black art" of it's mystique - then keep your fingers to yourself and let someone with some patience and understanding answer the question. 

With Love!

By the way , I got this working on my windows machine with about 8 clicks and no typing....*SLAP! SLAP!*

I would really love to have it working on my Narwhal!

---

### Post by wildmanne39 on 2012-08-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

