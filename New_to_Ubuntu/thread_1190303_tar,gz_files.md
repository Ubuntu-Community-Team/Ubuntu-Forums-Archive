---
title: "tar,gz files"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by davellew69 on 2009-06-17
after 3 months of trying ,I just dont get it, how do I install the buggers

---

### Post by Bigtime_Scrub on 2009-06-17
It depends.

Is there something specific you are trying to install via tarball or just in general so that you know? I find using tarballs more trouble then they are worth. It is all about hunting down dependencies. If you do not have the prerequisites for a program it will not install.

---

### Post by LewRockwell on 2009-06-17
[http://www.justlinux.com/nhf/Software/Compiling_Software.html](http://www.justlinux.com/nhf/Software/Compiling_Software.html)

---

### Post by ddrichardson on 2009-06-17
tar.gz are compressed archives, it depends on what they contain.  Generally the first step is```
tar xvfz tarball.tar.gz
```where tarball.tar.gz is the filename.  This will expand a folder in which you will find a readme telling you what to do next.

This will either be a binary, which is executed by typing its name with a dotslash:```
./filename
```or a source file.

To build source you need to install the basics:```
sudo apt-get install build-essential
```Then run the configure script.  This will tell you if you are missing anything needed to build, then@```
make; sudo make install
```Be aware that this is not the preferred installation method as it does not provide automatic updates.

---

### Post by davellew69 on 2009-06-17
thanks all, I`m off to bed so i`ll try in the morning hope i get these licked soon,

---

### Post by aysiu on 2009-06-17
After four years of using Linux full-time, I have yet to find a need to install "the suckers."

What program do you think you need an .tar.gz for?

---

### Post by LewRockwell on 2009-06-17
> **aysiu said:**
> After four years of using Linux full-time, I have yet to find a need to install "the suckers."

What program do you think you need an .tar.gz for?

I was just working under the assumption that they wanted to learn how and successfully do it, regardless of the choices and preferences of others.

perhaps I was mistaken.

---

### Post by aysiu on 2009-06-17
If I see a post in Absolute Beginner that asks about .tar.gz files, I work under the assumption that the OP is not aware of [the convenience of package management.](http://www.psychocats.net/ubuntu/installingsoftware)

If people are just curious, the original post usually looks more like "So I know how to use the package manager to install stuff, but I just want to learn other ways of doing things, so can someone teach me how to compile form source?"

---

### Post by davellew69 on 2009-06-18
still confused, i`m trying to install 70324 dashboard tar.bz2

---

### Post by davellew69 on 2009-06-18
I take it you deal with tar.gz and bz2 files in the same way

---

### Post by ddrichardson on 2009-06-18
> **davellew69 said:**
> I take it you deal with tar.gz and bz2 files in the same way
Yes but the command is slightly different (its a different compression)```
tar xvfj tarball.tar.bz2
```

---

### Post by ddrichardson on 2009-06-18
> **davellew69 said:**
> still confused, i`m trying to install 70324 dashboard tar.bz2
Ah wait - the number at the beginning - is this a theme file from gnome-look.org?

---

### Post by goldblattster on 2009-06-18
If it is a theme file, then open the appearance setting window, drag the tar.gz into the theme selection part of the window and boom, your theme is installed. If it's not a them, then let us know. ;)

---

### Post by davellew69 on 2009-06-18
ok Ive dragged it into the screenlet menu, but the bugger wont launch

---

### Post by goldblattster on 2009-06-18
What's bugger? Is that the name of the theme?
Is it a theme at all?
If not, is it a source tarball?

---

### Post by davellew69 on 2009-06-18
it`s the dashboard widget  in the screenlets folder

---

### Post by goldblattster on 2009-06-18
Oh, sorry, I can't help with *that*. I thought it was a different tar.gz for a different use. I'm very sorry. :(

---

### Post by davellew69 on 2009-06-18
no worries mate, I`ll get there, thats how you learn

---

### Post by kndfs3001 on 2009-06-18
It depends.  Sometimes the .tar.gz files are simply packages containing the application, and sometimes they are theme packages, but sometimes they contain the source code, which you'll have to compile yourself.  It is kind of a pain, but you'll get used to it.  Here are instructions:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by ZackM on 2009-06-18
I started off on FreeBSD command line shells using tar.bz files. I haven't had to use any with personal use on Ubuntu, but it's good to learn just as a precautionary. Good ole IRCds came in handy after all. Lol

---

### Post by cubeist on 2009-06-18
For the OP, if you are using nautilus, right-click on the tar or gz and select extract here...

---

### Post by skyjacker on 2009-06-18
> **davellew69 said:**
> after 3 months of trying ,I just dont get it, how do I install the buggers Make that 2 of us... I gave up last month after trying dozens of procedures, internet sites, etc. I only use files I find in synaptic.

---

### Post by Amilo1718 on 2009-06-18
> **skyjacker said:**
> Make that 2 of us... I gave up last month after trying dozens of procedures, internet sites, etc. I only use files I find in synaptic.

is compiling the difficulty?
or just accessing the tar.gz?

---

### Post by aysiu on 2009-06-18
Can you link to the download file so we can see what it is (program, theme, screenlet)?

---

### Post by articwolf2012 on 2009-06-24
> **davellew69 said:**
> after 3 months of trying ,I just dont get it, how do I install the buggers

I still don't get it either man! I understand DEB and how to AUTORUN a damn program but a Tar.gz or ANY TAR is complicated as hell man! I am worse than u! You are going for 3 months when I have 5!:confused::confused::confused::confused::confused::confused::confused::confused::confused: Please reply back if u find anything new man....

---

### Post by decoherence on 2009-06-24
People who are having difficulty 'getting' tar.gz files.... they're equivalent to .zip files. You really have no idea what's in them before you 'unzip' them.

Generally the place you got the tar.gz file from will have instructions on what to do with them. Sometimes the instructions are contained within the .tar.gz, often with names like README or INSTALL.

As was previously mentioned, to unzip them you right click the file and select "Extract Here" or use the 'tar -xzvf filename.tar.gz' command in the terminal.

Some programs can read directly in to the tar.gz file, much like how some Windows programs can see what's inside a .zip without you unzipping it. Themes are one example of when .tar.gz files don't have to be 'unzipped' but there is no hard and fast rule for this.

So the simple answer for "what do I do with a .tar.gz?" is "you decompress it." Then follow whatever instructions accompany it, assuming instructions are needed (you could also tar.gz your holiday photos... no instruction needed there! It's JUST like .zip)

---

