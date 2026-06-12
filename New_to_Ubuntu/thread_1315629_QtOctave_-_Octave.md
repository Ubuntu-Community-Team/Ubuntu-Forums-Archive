---
title: "QtOctave - Octave"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by lauriehurman on 2009-11-05
Hi
I have Ubuntu 9.10
I've loaded Octave 3.0
I've loaded QtOctave, both from the System>Administration>Synaptic Package Manager
In QtOctave, Config>general configuration>general menu>Octave I have to put a pathway so that Qt can find Octave.
How do I find out what to put in here?
I've tried /usr/share/octave/packages/3.0/octave_packages
and I've tried /home/laurie/octave-core
but neither works.

Can you help or direct me to where I can find out?
Thakns
Laurie

---

### Post by Mornedhel on 2009-11-05
Hi,

The path they are referring to may be the path to the Octave executable (the actual program).

You may find this path using the which command, as in (in a terminal):

```
which octave
```

This returns "/usr/bin/octave" on my system.

---

### Post by lauriehurman on 2009-11-09
Thank you
That worked. it was /usr/bin/octave

Very greatful for your help. May I ask, how did you know to do that and where can I read about it? I've read all the obvious stuff but there seems to me to be a layer of information that I don't have.

Thanks

Laurie

---

### Post by Mornedhel on 2009-11-09
> **lauriehurman said:**
> Thank you
That worked. it was /usr/bin/octave

Very greatful for your help. May I ask, how did you know to do that and where can I read about it? I've read all the obvious stuff but there seems to me to be a layer of information that I don't have.

Thanks

Laurie

You're welcome.

Mostly I learned by trial and error. I haven't read any books, although I do have a copy of Bash from O'Reilly, which I still haven't entirely read, and which is mostly obsolete anyway. For `which' in particular, I knew about the `who' and `whoami' commands; one day when tab-completing (1) on "wh" I noticed the commands `whatis', `whereis' and `which'. Out of pure curiosity I read the manual pages (2) for them.

Many GUI frontends will ask for the location of the command-line executable, in case it's somewhere unusual, for instance if you compiled it yourself or if you haven't installed it system-wide. This is somewhat usual, so any veteran or even semi-experienced user would immediately understand what is asked.

If you have further questions (on octave or another topic), you can reply to this thread or PM me.

On a somewhat unrelated note, I use octave daily, but haven't tried QtOctave yet. Is it any good ? Different from MATLAB ? What does it bring in comparison to using the command-line version ?

(1) In case you haven't noticed yet, if you find yourself in the terminal, in many cases you can ask it to expand filenames or commands for you by pressing TAB, for instance:
```
$ apr<TAB>
```
would complete to `apropos'. Several commands start with "wh", so the terminal displays potential matches, among which `which': just type a few characters more and press TAB again.

(2) Man pages contain most of the information you will need when dealing with the terminal. You can read the documentation of a command by typing `man <command>'. If you're not sure what command to use, you can use `apropos <keyword>' to display a list of man pages dealing with the keyword.

---

### Post by lauriehurman on 2009-11-10
Hi Mornedhel

Thanks for that. Appreciate your patience.

I'm a total newcomer to Linux but I'm used to using Matlab. Hence the command line is impossible for me whereas the QtOctave screen is fairly close to a normal Matlab screen. There is no tutorial available for Qt but like you say; sit there and try things and see what works.

When I first Opened Octave is was completely baffled. I'm used to writing discrete functions as M files and stringing them together in a "batch" program in order to produce and answer to a problem. But that is absolutely all I know about programming so ...

I had a light bulb moment the other day when I was using Qt and I was using what amounts to a "browse" to get from my "home" folder to a file on a USB stick. Each time I clicked I saw the command in the command line of the workspace. I learned more from that than days of reading.

I've been reading the "Python-vs-Octave" debate on the forum and I wondered whether if you have any views on whether it would be worth leaning python. I'm conscious that every hour spent leaning to use the tool is an hour not spent solving the problem you wanted the tool for but I would welcome your comments.

Laurie

---

### Post by Mornedhel on 2009-11-10
> **lauriehurman said:**
> I'm a total newcomer to Linux but I'm used to using Matlab. Hence the command line is impossible for me whereas the QtOctave screen is fairly close to a normal Matlab screen. There is no tutorial available for Qt but like you say; sit there and try things and see what works.

When I first Opened Octave is was completely baffled. I'm used to writing discrete functions as M files and stringing them together in a "batch" program in order to produce and answer to a problem. But that is absolutely all I know about programming so ...

You should still be able to work in Octave with your knowledge of Matlab. I don't have any experience with recent Matlab versions, but the ones I did use only featured a browser to change the working directory and a basic built-in editor for .m scripts and functions (as well as, obviously, the main window where you call functions). I'm curious as to what other functionality I may have missed, though.

You can think of Octave as being the main window only. Personally I use a text editor separately to edit my .m files and switch back to the terminal running Octave to test my changes and run my scripts. The`cd' command in Octave works the same as in Matlab.

> **lauriehurman said:**
> I had a light bulb moment the other day when I was using Qt and I was using what amounts to a "browse" to get from my "home" folder to a file on a USB stick. Each time I clicked I saw the command in the command line of the workspace. I learned more from that than days of reading.

I'm not sure I understand completely, do you mean QtOctave ? "Qt" by itself refers to a graphical toolkit used to program graphical applications, particularly KDE applications (although they will run on other desktop environments as well). QtOctave is, therefore, a Qt-using graphical interface to Octave.

If I do understand, when you select a directory in QtOctave, the corresponding cd command is displayed in the main window ? This does sound like a good step in understanding how it works from experience.

On a somewhat unrelated note, what version of Octave do you use ? If you reuse a lot of code from your Matlab days, it may be worth to look into the more recent versions, as they have higher compatibility. For instance, the toolbox I use (BayesNetToolbox) doesn't work under Octave 2.x or 3.0, but does under 3.2. If everything already works, no need to upgrade: "don't fix it if it's not broken".

> **lauriehurman said:**
> I've been reading the "Python-vs-Octave" debate on the forum and I wondered whether if you have any views on whether it would be worth leaning python. I'm conscious that every hour spent leaning to use the tool is an hour not spent solving the problem you wanted the tool for but I would welcome your comments.

I was not aware of this debate. I don't code in Python but consider it a very good programming language. Personally, I don't think you have to pick one. Octave/Matlab is excellent as long as matrices are involved, and uses many tried and tested math libraries, so it's also decent at general math. I would strongly recommend against using it for general purpose programming, though. This is not the language's purpose.

Python on the other hand is well-suited to any task and its math libraries are, from what I hear, more than decent. I have little experience in Python and none in using it for math. It's worth learning (or another programming language), however, if you get into programming for other reasons.

I use Perl myself for quick and dirty scripts, to automate certain tasks; Octave for numerical calculations and Java for other purposes at work (I'm a CS grad student, just starting on my Ph.D thesis on Bayesian networks); and C++ for a side project that requires speed and memory management. Each language can do anything the others do, but this doesn't mean that it's well suited for anything. I wouldn't use Perl for applications that require speed or math, and I wouldn't use C++ or Octave for quick scripts.

Again, feel free to ask further questions.

---

### Post by lauriehurman on 2009-11-11
<<<"I don't have any experience with recent Matlab versions, but the ones I did use only featured a browser to change the working directory and a basic built-in editor for .m scripts and functions (as well as, obviously, the main window where you call functions). I'm curious as to what other functionality I may have missed, though.">>>

Yup. That's exactly how my MatLab is. What stumped me when I first opened Octave was that I didn't know how to open a new "M" file so that I could start writing functions (I tend to write everything as a function).

I spent the evening yesterday reproducing one of my old "batch" programs (i.e. a complicated algorithm involving a lot of functions called in a loop) and everything worked straight out of the box. So it looks like I've fallen on my feet. I hear there is a much better plotting add-on so I may go looking for that next.

Yea I meant QtOctave, sorry.
I'm using Octave 3.0. That was the latest one available at "synaptic package manager". I haven't got beyond that yet although I have read stuff on "Octave-forge" website which sounds like the place to go for any needed functions or algorithms.

I asked about Python because I have seen an engineering text book which is avaiable as a "MatLab" version or a "Python" version. At the time I had never heard of Python so I went looking. Then I read some stuff on this forum.
But as I say Octave is working well and I'm not going to spend my time learning a new tool if I don't need to. Best to concentrate on solving the problem that I started with.

Laurie

---

### Post by Mornedhel on 2009-11-11
> **lauriehurman said:**
> Yup. That's exactly how my MatLab is. What stumped me when I first opened Octave was that I didn't know how to open a new "M" file so that I could start writing functions (I tend to write everything as a function).

Well, normally you'd use any text editor available on your system, and save the files normally, as "filename.m". They're just text, after all. If you're running normal Ubuntu (not Kubuntu), you can use gedit, the default text editor in the Applications/Accessories menu, and select View/Highlight Mode/Scientific/Octave (at least that option exists on my system). I guess kwrite, the Kubuntu equivalent, also has that. This just does syntax highlighting so that you'll be more comfortable while coding; more features may be available in the QtOctave built-in editor (if there is one). Use what suits you best.

> **lauriehurman said:**
> I spent the evening yesterday reproducing one of my old "batch" programs (i.e. a complicated algorithm involving a lot of functions called in a loop) and everything worked straight out of the box. So it looks like I've fallen on my feet.

OK, glad to hear that! Matlab and Octave should be compatible enough for your purposes, unless you need to use a very specific toolbox, or compiled code.

> **lauriehurman said:**
> I hear there is a much better plotting add-on so I may go looking for that next.

I rely on the gnuplot interface to Octave. It isn't very pretty, but it does the job. If you do come across a good plotting tool for Octave, I'm interested.

> **lauriehurman said:**
> I'm using Octave 3.0. That was the latest one available at "synaptic package manager". I haven't got beyond that yet although I have read stuff on "Octave-forge" website which sounds like the place to go for any needed functions or algorithms.

Karmic Koala (Ubuntu 9.10) has Octave 3.2 in its repositories. This was my most important reason to switch to Karmic as soon as possible. Some dependencies are broken, though (octave plugins apparently require 3.0 instead of (3.0 or 3.2)). I filed a bug, but no one has commented on it yet.

As for octave-forge plugins, many are also available in the package manager. You should check in there before installing from the website; it's easier and updates are taken care of automatically. This is also valid for other applications.

> **lauriehurman said:**
> But as I say Octave is working well and I'm not going to spend my time learning a new tool if I don't need to. Best to concentrate on solving the problem that I started with.

All right then, I wish you good luck on your scientific endeavors!

---

