---
title: "install fonts"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by ave2 on 2009-03-18
is there an easy way to install fonts- I find a few tuts using the terminal, but I always get stuck, which is so frustrating!!

---

### Post by gn2 on 2009-03-18
You can use [Synaptic Package Manager]("https://help.ubuntu.com/community/SynapticHowto") or Add/Remove to install fonts.

If you are just looking for the Microsoft style fonts, copy and paste this command into a terminal:

```
sudo apt-get install msttcorefonts
```

---

### Post by ave2 on 2009-03-18
iv downloaded a free true type font from the net, and want to install that- can this also be done with add/remove or synaptic

---

### Post by stchman on 2009-03-18
> **ave2 said:**
> is there an easy way to install fonts- I find a few tuts using the terminal, but I always get stuck, which is so frustrating!!

I have a tutorial on installing fonts.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

### Post by Gilabuugs on 2009-03-18
> **ave2 said:**
> iv downloaded a free true type font from the net, and want to install that- can this also be done with add/remove or synaptic

if you open up a terminal this should do it

```

cd ~
mkdir .fonts
cp /path/to/yourfont.ttf ~/.fonts/

```
where /path/to/yourfont.ttf is where your font is and its name

then all you have to do is log out and log back in

---

### Post by D3ath on 2009-03-18
> **ave2 said:**
> iv downloaded a free true type font from the net, and want to install that- can this also be done with add/remove or synaptic


```
# Install the Tahoma fonts
cd ~

# get file
wget http://www.stchman.com/tools/MS_fonts/tahoma.zip

# extract .zip 
sudo unzip -d /usr/share/fonts/truetype/msttcorefonts ~/tahoma.zip

#Update Cache
sudo fc-cache -f -v

# remove the .zip file 
rm -r -f ~/tahoma.zip
```

That is how you would manually install a font...

---

### Post by jjgomera on 2009-03-18
for a noob maybe is easy graphically:

-open your file manager (nautilus, konqueror, pcmanfm...)
-ctrl+H to show hiden directories
-Find the directory /home/usuario/.fonts (if it dont exist, create it)
-copy rar, zip with the downloaded font
-extract there (right click and there is option in the menu)

---

### Post by ave2 on 2009-03-18
thanks stchman your tutorial makes sense- just one thing sudo fc-cache -f -v
 could someone give me more detail on this one-im trying to get away from just repeating commands eg what is the -f, the -v etc
thanks everyone for the help

---

### Post by D3ath on 2009-03-18
> **ave2 said:**
> thanks stchman your tutorial makes sense- just one thing sudo fc-cache -f -v
 could someone give me more detail on this one-im trying to get away from just repeating commands eg what is the -f, the -v etc
thanks everyone for the help

```

xxxxxxx@xxx-xxxxxxx:~$ fc-cache --help
usage: fc-cache [-frsvV?] [--force|--really-force] [--system-only] [--verbose] [--version] [--help] [dirs]
Build font information caches in [dirs]
(all directories in font configuration by default).

  -f, --force          scan directories with apparently valid caches
  -r, --really-force   erase all existing caches, then rescan
  -s, --system-only    scan system-wide directories only
  -v, --verbose        display status information while busy
  -V, --version        display font config version and exit
  -?, --help           display this help and exit

```

For any command just type --help after it to find out more info on that command.

---

### Post by ave2 on 2009-03-18
aaah simple- thanks d3ath

---

### Post by D3ath on 2009-03-18
> **ave2 said:**
> aaah simple- thanks d3ath

Not a problem...;)

---

### Post by Ozdemon on 2009-03-19
Or just open up your fonts folder by using the terminal:

**gksu nautilus /usr/share/fonts/truetype**

then open another window with the required fonts and drag across.

Job's done.

---

### Post by D3ath on 2009-03-19
Using a terminal is a good thing to get used to you have complete control of your system. Using the gui is awesome but the CLI is much faster.  FYI.

---

### Post by gn2 on 2009-03-19
> **D3ath said:**
> ~ the CLI is much faster.  FYI.

Only if you can remember the commands and are a fast and accurate typist.
It is also far easier to make a mistake which can wreck your system using the CLI.

---

### Post by D3ath on 2009-03-19
> **gn2 said:**
> Only if you can remember the commands and are a fast and accurate typist.
It is also far easier to make a mistake which can wreck your system using the CLI.
That's simple to over come. Don't Fail. Learn from the mistakes. Making scripts could also stop mistakes as well.

---

### Post by gn2 on 2009-03-20
> **D3ath said:**
> Making scripts could also stop mistakes as well.

Far easier to just click buttons with a GUI.

CLI is useful for "tweaking" but it's no use for a modern desktop operating system.

---

### Post by longtom on 2009-03-20
> **gn2 said:**
> Far easier to just click buttons with a GUI.

CLI is useful for "tweaking" but it's no use for a modern desktop operating system.

+1  case in point in this thread for sure.

Anybody can see quite clearly, that for the ..."average" user, the GUI solution is really simple.

"Average" as in "coming from Windows".

CLI is good and has it's place without a doubt.  Also it is good to learn it and use it wereever anybody feels comfortable to do so, it shouldn't be used where those "average" users get rather confused than helped.

Not saying that anybody is doing this in this thread - but I have seen it before...

regards

longtom

---

### Post by D3ath on 2009-03-20
> **gn2 said:**
> Only if you can remember the commands and are a fast and accurate typist.
It is also far easier to make a mistake which can wreck your system using the CLI.

I'm sure you know that you can use the tab key to stop mistakes!


> **gn2 said:**
> Far easier to just click buttons with a GUI.

CLI is useful for "tweaking" but it's no use for a modern desktop operating system.

I would beg to differ. For someone novice to use the CLI yes, i agree. But once mastered (which i am far from). You can write scripts and run them as commands to do things that would take a few extra steps using the GUI. I'm not downing anybody. But im a die hard linux user. You can use the CLI without the GUI. But the GUI would be nothing without the CLI.

---

### Post by oldos2er on 2009-03-20
> **gn2 said:**
> Only if you can remember the commands and are a fast and accurate typist.
It is also far easier to make a mistake which can wreck your system using the CLI.

 'Tab' and aliasing are your friends, and help you not to make mistakes. And it's just as easy to wreck your system by running Nautilus as root, imo.

---

### Post by D3ath on 2009-03-20
> **oldos2er said:**
> 'Tab' and aliasing are your friends, and help you not to make mistakes. And it's just as easy to wreck your system by running Nautilus as root, imo.
Thank you!

---

### Post by gn2 on 2009-03-20
> **oldos2er said:**
> And it's just as easy to wreck your system by running Nautilus as root, imo.

True enough, but the user would have to choose to do so and would require to know how.

An "Absolute Beginner" can easily and unwittingly hose their system by copying and pasting commands into a terminal.

Don't get me wrong, CLI has it's uses and it's great that it's available, but it is absolutely not the way forward for completing everyday tasks by the average personal computer user.

 <flame on> Nerdy geeks yes, normal people no. </flameoff>

---

### Post by oldos2er on 2009-03-20
> **gn2 said:**
> True enough, but the user would have to choose to do so and would require to know how.

An "Absolute Beginner" can easily and unwittingly hose their system by copying and pasting commands into a terminal.

Don't get me wrong, CLI has it's uses and it's great that it's available, but it is absolutely not the way forward for completing everyday tasks by the average personal computer user.

 <flame on> Nerdy geeks yes, normal people no. </flameoff>

 I have to confess, I really don't understand the xenophobia; seems much more productive to let the "average personal computer user" decide for him/herself--and it's not as if it's an either/or proposition.

---

