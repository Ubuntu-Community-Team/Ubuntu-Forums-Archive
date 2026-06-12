---
title: "command-line vlc and processes"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by redandgreen on 2009-03-23
So I'm trying to get myself into the habit of using the command line, and am taking it to quite silly lengths. I was wondering - it's easy enough to get music playing without the vlc interface (cvlc), but how do you pause it or change the volume etc while it's playing? 

(or is general impracticality precisely *why* they invented GUIs?)

Also, most programs are easily run from the command line, but unless I start suspending and restarting them, it doesn't seem possible to use the same shell do run multiple programs. But that doesn't sound right - isn't the whole system pretty much just a shell with pretty things stuck on top? And it's running dozens of processes...

*confused*

---

### Post by linuxguymarshall on 2009-03-23
If you want documentation for VLC from a command-line then ```
man vlc
```

But take my advice and just use the GUI

---

### Post by Mehall on 2009-03-23
When using cvlc you can type "help" (w/o quotes) to get a list of supported commands.

i know you can pause, and you can probably change volume.

---

### Post by AndrewTheArt on 2009-03-23
Yes, using VLC from the command line is ridiculous. [Debian Package of the Day]("http://debaday.debian.net/") lists a new Debian package every day (and it's very often a console-based package), so you might want to check that out. [Ubuntu Geek]("http://www.ubuntugeek.com/") also has some good console-based packages.[]("http://www.ubuntugeek.com/")

---

### Post by m_duck on 2009-03-23
If you're not desparate to use vlc, try moc (music on console). It's a good console based music player.```
sudo apt-get install moc
```Check the man page for details.```
man moc
```

---

### Post by karlr42 on 2009-03-23
> **redandgreen said:**
> Also, most programs are easily run from the command line, but unless I start suspending and restarting them, it doesn't seem possible to use the same shell do run multiple programs.
Use & to run a program in the background, for example, try
```
nautilus &
```
- the window will appear, but the terminal will return to the propmt, so you can keep using it

---

### Post by issih on 2009-03-23
Vlc actually has a rather nice ncurses interface.

```
vlc --extraintf ncurses
```

Thats command line enough surely :)

I used to use that so I could use my ds (running ds linux) as a remote control when watching movies.

---

### Post by redandgreen on 2009-03-23
Hmmm, maybe I'll stop being such a purist ;) thanks everyone!

---

### Post by clarenceweaver on 2013-04-28
I know this is an old thread but that doesn't mean folks don't access it currently so I want to rant.
I so don't like the way posters in forums stray from the original question. The OP wants to use cvlc, the command line version of vlc, and why shouldn't he? It's available and meant to be used by anyone. Suggesting he use your favorite music player instead of answering his question, is, at best, sub-optimal. I use a Raspberry Pi, headless, to stream audio from the internet using cvlc so, of course, your private solution won't help me. What will help is a direct answer. Millions of people, just within the last year, have purchased a Pi or two and are experimenting with Linux for the first time in their lives. The Pi runs Ubuntu or a version of it. Many will come to this forum to find answers to questions that are, to them, mysterious and difficult for them to get answers to. They should be encouraged to explorer the command line because of the massive power it gives over a GUI and should be given as much help as possible from the 'nix community. Real help, not alternate solutions for which they are not searching.</rant>

nohup cvlc --volume 50 [http://www.publicbroadcasting.net/mpbc/ppr/mainec24.pls](http://www.publicbroadcasting.net/mpbc/ppr/mainec24.pls) 0<&- &>/dev/null

will start an audio stream from the command line and give you back the command prompt. It will continue to play even if you log out. If you happen to be in a console, or, as in my case, in an ssh session to a remote headless box, you can run alsamixer to control your sound card volume before you log out or after you log back in.

The nohup prefix tells cvlc to ignore the hang-up signal it gets when you log out. 0<&- closes the STDIN file descriptor and &>/dev/null redirects STDOUT and STDERR to null. The final ampersand runs the whole process in the background. All four of these terms are required to properly daemonize a command so that you can log out and walk away while the daemon continues to run.

The volume can be any number you are comfortable with. Experiment.

I so hope that redandgreen was not discouraged from experimenting.

---

### Post by howefield on 2013-04-28
Old thread closed.

---

