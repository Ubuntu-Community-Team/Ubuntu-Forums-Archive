---
title: "Where are my downloads?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by jaslin on 2009-02-16
Hi all,

I've used synaptic to download stuff like gstreamer for my movie player, my printer driver (foo2..) for hp printer, and ndiswrapper.  They don't register, they don't work, I can't find them.  There doesn't seem to be any kind of wizard or auto download.  What activates them?

I just don't get this stuff.  I'm not a Windows fan, but when I download on it, the stuff works and has a great graphical interface.  When I download on Ubuntu they seem to flat out disappear.

Bewildered,

Jaslin

---

### Post by SunnyRabbiera on 2009-02-16
Please dont make two topics on the subject unless its really needed, I try not to do it myself.
As for your issues, what kind of media are yopu trying to play?
I find gstreamer a little primitive at times, sometimes its just best to give in and use the win32codecs.
To get these codecs I suggest using medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu offers a lot that cannot be offered by ubuntu by default due to legal mumbo jumbo.


For your printer I am not sure, maybe a restart of both the printer and the OS might work but I am uncertain.

---

### Post by the_hardy_kid on 2009-02-16
Well, if you have downloaded them using synaptic, my guess is they're already installed.

Did you check Applications?
If they are not in there, run the name of the package in terminal.

---

### Post by Therion on 2009-02-16
Synaptic does more than download a file.  In Ubuntu, Synaptic not only downloads the install files, it also downloads any other files required for the first file to run properly.  So if you want file A, but it requires file B, file B is automatically downloaded along with file A.  Further, once all the required files are downloaded, Synaptic installs everything for you.  

You might have better luck if you post the details of the specific problems you're having so we can help you fix them.

---

### Post by jaslin on 2009-02-16
Thanks to those who responded to my question.  Sorry about posting twice, I couldn't find my previous and since no one was posting answers, I thought it might not have stayed on the board.

Anyway, two things were mentioned in response to my question: 1) that downloads might be in applications, if not use terminal, and 2) synaptic automatically downloads them.

Here's my problem.  They are not in applications, neither gstreamer (which apparently movie player needs), or ndiswrapper, or printer driver (hp laserjet 1000, foo2...).  Even if I find a file for these somewhere, I don't know what to do with it.  If they are present anywhere, they appear as text files and other formats.  There's nothing that makes them functional...you know, that kick starts them so they work.

Synaptic tells me they're installed, but if so, they're hiding.  They don't kick in when I need them. After downloading gstreamer, as prompted by movie player, I go to play movies and it prompts me for the same plugins.  The only thing I can do on my computer is internet.  I can't print, I can't watch movies...none of these apps, which my desktop says I have, do anything.

I would tell you more specifics, but I don't know what to say.  Synaptic says they're installed, but they seem to be lying dormant somewhere waiting for me to take another step that I don't know.  I've been up until 1 in the morning the last few nights, after hours of searching out answers and I still can't get anything out of ubuntu.  I don't expect it to be as simple as Windows, but I didn't think it would be a full-time job just getting my comp to do simple things like print or show a movie.

When I go onto forums and linux download sites, I can't get a straight answer.  When I was running windows, I would find a download I liked, click download, a wizard popped up, and the app showed up nicely on my desktop and was clearly in use.  In Ubuntu, which I desperately want to work, they are m.i.a.

Going to the terminal doesn't do me any good.  I'd have to spend weeks learning all the commands.  I tried doing the foo2... printer driver using line commands and nothing changed.  In fact I think I've probably downloaded the same driver for my printer about 9 times.

Sorry to rant, but I'm at a complete loss.  Ubuntu's help links don't have the answer and it's not like I can call someone or have a Linux person look at it.

Thanks again.

Jaslin

---

### Post by carml on 2009-02-16
First question->first answer: a)under the name Gstreamer there are any packages,maybe you have to add some one more to play that video,b) no Gstreamer isn't visible on the menù applications,but you can see if it's already installed by going on System->Administration-Synaptic package manager;by the way on Synaptic you'll find every package installed on your PC
c) ndiswrapper is showed under System->Administration and should be named Windows Wireless Driver.
Second question->second answer : people doesn't have all the same environment installed,maybe someone doesn't use a graphical one,so when someone suggests you to use the terminal he intends to be more general as he can or he intends to give a quicker solution,the use of a terminal can be more faster than use a graphical environment if you already know what you want to do(e.g. to install a package he already knows,execute a command usable only via terminal etc). :)

---

### Post by mcduck on 2009-02-16
Neither gstreamer nor ndiswrapper is even supposed to show in your menus. They are not that kind of programs you could run yourself.

You should thing of gstreamer as codecs, your media players will use gstreamer packages to decode and encode different media formats. THehose media applications that use gstreamer will detect available codecs as soon as you have them installed.

Then, ndiswrapper is used to run Windows drivers on Linux, and just like you don't actually start your drivers from the start menu in Windows, you're not going to do that in Linux either. I can't really help you more than this with ndiswraper as all my hardware has native Linux drivers so I haven't ever used ndiswrapper.

When you actually install desktop applications they will usually show automatically in the menus.

---

### Post by gn2 on 2009-02-16
For your HP printer, in a terminal run ```
sudo apt-get install hplip-gui
```

Then it will appear in System > Preferences > HPLIP Toolbox

You can use the toolbox to configure your printer.

---

### Post by durand on 2009-02-16
If you open the movie, the codec dialog should popup helping you to install the right packages. (well, it should automatically install them for you). If you get a bit bored, you can always try other movie players:

```

sudo aptitude install vlc mplayer
```

Then if you right click on the movie file, you will get an option to open with VLC or Mplayer, both of which are very good.

That said, I think the default movie player is good enough for most uses so you should probably try to get that to work first. If I recall correctly, you don't actually need to use synaptic to install anything. The movie player should do it automatically.

---

### Post by spcwingo on 2009-02-16
If you need a GUI for ndiswrapper install ndisgtk.

```
sudo apt-get install ndisgtk
```

---

### Post by Muffinabus on 2009-02-16
I second Durand's suggestion in trying out VLC, it is an excellent media player.

---

