---
title: "Another .tar install question"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by cactusgal on 2010-02-01
My apologies for another .tar install question but I've been searching for 2 days now to answer this. I'm currently using Ubuntu Studio 9.04 and am trying to install EnergyXT, a program that will allow me to record and mix music tracks through the USB interface from my husband's Behringer mixing board. I've gotten as far as I can following what my searches have dug up so far but am now truly stumped and need some help. It went as follows in the terminal: 

susan@ubuntuhome:~$ mkdir /home/susan/src/
susan@ubuntuhome:~$ cd /home/susan/src/energyXT
susan@ubuntuhome:~/src/energyXT$ ls
clips  energyXT2  eula.txt  libaam.so  presets  projects
susan@ubuntuhome:~/src/energyXT$ su make install
Unknown id: make
susan@ubuntuhome:~/src/energyXT$ ./configure
bash: ./configure: No such file or directory
susan@ubuntuhome:~/src/energyXT$ su install
Unknown id: install

So now what do I do? I've discovered, I think, that libaam.so is the installation file and is already compiled(?) but what command line should I use to install this?

Thanks from a newbie,
cactusgal

---

### Post by kayvortex on 2010-02-01
Wow, that's a pretty unhelpful tar.gz file. By the looks of it, you just need to run the "energyXT2" binary.

In the directory which you extracted (by the looks of it, "/home/susan/src/energyXT"), just enter:
```
./energyXT2
```

If that starts the program up OK, then just move the whole thing to /opt and create a link to the binary in a directory that is in your PATH.
First, move the energyXT directory to /opt:
```
sudo mv -iv /home/susan/src/energyXT /opt
```

Then, create a link to the binary:
```
sudo ln -sv /opt/energyXT/energyXT2 /usr/local/bin
```

Hopefully, all you need to start the program now is enter:
```
energyXT2
```
anywhere in a terminal.

---

### Post by cactusgal on 2010-02-01
Thanks for the quick reply. Ya, this file came from Behringer to use with their hardware. Wish it could've been a .deb, so easy for a beginner but kinda neat that they actually have something for Linux. My other hardware mixing device (Creative Labs E-mu) is for Windows only and the mixing board will also connect through it but I thought it would be neat to be able to do this on my Ubuntu system as well.

Anyways, this is what I got when I tried what you said: 

susan@ubuntuhome:~/src/energyXT$ ./energyXT2
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  140 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  1750
  Current serial number in output stream:  1752
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x3200305
  Serial number of failed request:  1751
  Current serial number in output stream:  1752

So no success there. I was hoping it might be as simple as entering the correct syntax for libaam.so(?)

Regards,
cactusgal

---

### Post by kayvortex on 2010-02-01
Well, libaam.so is just a shared library -- it's not supposed to be called directly, but rather a binary file would execute parts of it as needed. Quite why they built a shared library when they've designed the installer like this I don't know, but still.

The error looks like a bug in the program, or at least something not being configured correctly. You could try asking in a Behringer or EnergyXT forum (if they exist) since they'll probably be more knowledgeable about the program itself. Just for the record, though, what system are you running: 32-bit or 64-bit? And did you do anything unusual to/with your system? 

Also, you say you got the program from Behringer, couldn't you just download the program from EnergyXT themselves? That is, have Behringer modified the program in order to work with their hardware? The link is [here]("http://www.energy-xt.com/index.php?id=0200"): give that a go and post back what happens.

---

### Post by cactusgal on 2010-02-02
I'm using a 32 bit system and haven't done anything to it other than add a few programs and updates and remove a couple of things.

The difference here is that the version from Behringer is the compact version and even at that they required to email me a key file (to insert into the program folder) and a serial number. The full version has to be purchased. I downloaded the full version from the EnergyXT website (just to compare) and the only difference I see when opening the folder after extraction is that it contains EnergyXT.ini (with a .3 MB larger size) whereas the compact version doesn't.

Another thing I've noticed since I first tried to install this 2 days ago is that I no longer have any sound on my computer. I must confess that what I did in my frustration (and probably shouldn't have) was to click directly on EnergyXT (exactly the sort of thing I would do and have done many times in Windows, being a power user). Nothing seemed to happen but perhaps it did and I just couldn't tell? Maybe a coincidence or maybe not?

I'll be joining the EnergyXT forum and ask over there but please do add any more input you may have, especially if you have any insights into my sound loss relative to this issue. Thanks very much for your help.

Regards,
cactusgal

---

### Post by da burger on 2010-02-02
I'm afraid I can't help with your problem but just so you know the command to use root privileges is ```
sudo command
``` not ```
su command
```
I believe there are ways to do it using su but most of the time sudo is what you want.

---

### Post by cactusgal on 2010-02-02
Well, thanks very much for trying. Actually, I've been using sudo but was reading via the Linux forum about installing .tar using a terminal and that's what it said there to use (su) but I guess that applies to other versions of Linux not Ubuntu.

Perhaps I should post on the Multimedia forum about my sound problem(?)

Regards,
cactusgal

---

### Post by dondiego2 on 2010-02-02
> **da burger said:**
> I'm afraid I can't help with your problem but just so you know the command to use root privileges is ```
sudo command
``` not ```
su command
```I believe there are ways to do it using su but most of the time sudo is what you want.


I thought 

sudo

gave you administrative privileges and

su

gives you all know all powerful everything privileges.  I know I have two different passwords for sudo and su.

---

### Post by Charlietje on 2010-02-02
Try this
```

sudo make

```

Then it's finished. Try

```

sudo make install

```

make sure you have build-essential installed
```
sudo apt-get install build-essential
```

---

### Post by kayvortex on 2010-02-02
Well, if you've paid for it then you can try phoning/emailing technical support. Apart from that, the only mildly useful thing I've found is [this link]("http://ubuntuforums.org/showthread.php?p=5118230"), which references [this link]("http://ubuntuforums.org/showthread.php?t=176636"); it's not strictly relevant, but may contain a solution to a common problem.

As for the sound issues, you've probably just set something off (double clicking on the energyXT2 file would just have done what you already tried, but in the background instead of in an open terminal). There are lots of better guides here for that than I could provide. Try [here]("http://ubuntuforums.org/showthread.php?t=789578") for a start. There's an older guide [here]("http://ubuntuforums.org/showthread.php?t=205449") that *might* still be useful (which looks identical to [this link]("https://help.ubuntu.com/community/SoundTroubleshooting"), but which may contain some useful resources). Finally, there's [this]("https://help.ubuntu.com/community/SoundTroubleshooting") and [this]("https://wiki.ubuntu.com/DebuggingSoundProblems"). It's a lot to look at, but a sound problem could be anything, and it's best to go things carefully. Also, you should open up a separate thread for your sound issue: it may have been caused by energyXT2, but there'll be a fix for it, and opening a separate thread will let more knowledgeable people look at it.

---

### Post by cactusgal on 2010-02-02
Thanks, kayvortex, for all your help. I think you're right about there being a bug in the program from Behringer (I've reported it to them). I downloaded the full version demo from the EnergyXT website and it installed fine as per your original instructions. I then inserted the key file for the compact version from Behringer which now gives me the fully functional compact version (so I can save and export projects, but only 6 tracks). I also installed Wine and then the Windows version, which also works fine but allows for more tracks to be saved and exported. I think my head's about ready to spin off trying to figure this all out! Sadly, I still have no sound. Tried a few things from the links you provided, no luck, so I'll be posting it to a separate thread (Multimedia, maybe?). Wondering if maybe I should upgrade to 9.10? Been holding off on that as when I first installed it a few months ago it didn't seem to offer the graphics card drivers I needed.

Regards,
cactusgal

---

### Post by kayvortex on 2010-02-02
Well, if the windows version works OK in wine, then that's something at least. See what the EnergyXT forum members come up with, and see if Behringer come up with a fix or solution from your bug report. Apart from that, there's probably not much else you can do -- like I said, at least you have something up and running!

Yeah, "Multimedia & Video" would probably be the best category to post the sound problem in. As for Ubuntu 9.10, what graphics card do you have? There may possibly have been a fix produced for your problem if your graphics work fine already in an older release. If you tell me what problem you had, I can take a look at it if you like. Generally, I find that newer releases do broadly get better (although there a few regressions sometimes), and the only time things don't go well is if your system's hardware already doesn't play particularly nicely with Linux. Did you have any other issues when you tried 9.10 before?

---

### Post by cactusgal on 2010-02-03
Yes, at least it's something. While I'm on this subject, if/when I install software from a .tar again will it always go in the /opt folder? And how do I put a shortcut for it in my start menu?

Well, it's an AGP card, ATI Radeon 9200 PRO (according to the Gnome Device Manager I just installed, have a few so can't always remember which). I build/rebuild/upgrade my own computers and always seem to have a few parts left over to build another computer with the addition of a part or two but this is my last and oldest working Athlon socket 'A' build (can't buy motherboards anymore). I started on this with Studio 9.04 but at that time there was a problem installing OpenOffice in it. I posted about it here but it was never resolved so I reformatted and installed 9.10 but there didn't seem to be any drivers for the card at that time so I reformatted again, installed 8.10, then OpenOffice and then upgraded to 9.04. Funny, when I first installed 8.10 there were proprietary drivers listed for it under System/Administration/Hardware Drivers but I checked yesterday and now it seems there aren't anymore. Would that be because this version now natively supports my card? Since something recently 'went' on my other working socket 'A' board (my Windows XP system). I now have another card, not sure if it's better or not, to put in here but it's also an ATI Radeon (9250). At any rate I'm thinking of upgrading to 9.10 (after I've rebuilt my XP system) but want to be sure there'll be no problems with my graphics card. Any advice/info you can give me would be appreciated. What I really appreciate about Ubuntu is that it's such a lean OS it runs pretty much as well on here (Athlon XP 2800+) as Windows 7 does on my newest/fastest system (Pentium core2duo 3.2 ghz., my husband's music studio). That and there's no registry to clog up and slow things down.

Regards,
cactusgal

---

### Post by kayvortex on 2010-02-03
OK, this might be a bit long, but...

No, normally stuff doesn't go in /opt: installing something in Linux usually just means putting the executable file in a PATH directory (usually /usr/bin or /usr/local/bin) and any libraries (.so files) in /usr/lib. Normally, however, the program will do this itself and not expect you to read up on where everything needs to be put. So, *normally*, most tar files contain a file called "Makefile" that will contain instructions on where to put everything. There's a program that's especially designed to read these "Makefiles" and run the commands in them called, unsurprisingly, "make".

So, *normally*, you type:
```
make install
```
and the "make" program will look for a Makefile in whatever directory you're in and look inside it for the section labelled "install" and will run all the commands in there that *should* detail where everything needs to go.

Makefiles are really flexible, and you can put anything in them in order to automate lots of different tasks. So, also, when you need to compile a program (as is often the case with tar files), there's also a section called "all" that will run the commands that will create your program. This is the default action, so you just need to type:
```
make
```
and "make" will build your program.

Sometimes, there's also a file called "configure" but I won't go into that. It'll be sufficient to say that if it exists, then you run it before the "make" commands. So, when you untar a file and see a file called "configure", then you normally run:
```
./configure
make
sudo make install
```
and if there's no "configure" file, but still a "Makefile", just
```
make
sudo make install
```
As always, though, decent programs will contain a file called "README" and/or "INSTALL" that will tell you exactly what to do.

This energyXT program, however, had no Makefile or even any README or INSTALL file, so I just ran the binary file "energyXT" to see what would happen. It ran OK, so I guessed that the directory contained everything that the program needed to run. In this case, you would want to put the directory in some place out of the way. Luckily, there's a special place for this: /opt. So, you just move everything to /opt. You could leave it at that, but in order to run it you'd have to "cd" into the /opt directory and then run it from there. So, to make things a little easier, you can just make a link to the binary file in /opt to a directory in your PATH variable and then just enter "energyXT" and the shell will know where the file is and run it for you.

That's a (not so quick!) intro into how things are installed in Linux.

=========================================================================

Start menu entries are contained in the directory /usr/share/applications. You can take a look at some of them to see what should go in there if you want to add a new one (not all of them get displayed because some of them have an entry called "NoDisplay=true"). As with all system directories in Linux, there's always a "local" one for stuff that you want to add, so to add your own entry, create a file called "energyXT.desktop" in /usr/**local**/share/applications. If you put this into that file:
> 
[Desktop Entry]
Name=EnergyXT
Comment=Start the EnergyXT music creator
Encoding=UTF-8
Exec=energyXT
Categories=AudioVideo;Audio;AudioVideoEditing;
Terminal=false
Type=Application

then I think that'll be enough for an entry in the Sound & Video section.

=========================================================================

I have an ATI card on my laptop, so I know the problems involved in getting some decent graphics support! Probably, the 
The ATI 9200/9250 are R200 generation cards, which are supposed to be well supported (see [here]("https://help.ubuntu.com/community/RadeonDriver#Full%203D%20support%20%28r100%20and%20r200%20series%29"), although a particular bug and its fix is noted [here]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI")). The open source drivers, which I find are getting pretty good and which are installed be default, *should* have worked OK. Did you do a clean install of 9.10, or an upgrade? Generally, it's only very new and really ancient cards that you'll have any real problems with -- older cards should be pretty well supported.

Probably, what I'd do is put a 9.10 LiveCD in and try booting the OS off the CD. If you don't get any graphics issues, then installing the OS for real *should* be OK. Also, if you don't mind doing clean installs (i.e. you don't mind copying your data to another HDD) then there's no real harm in giving a clean install a go, and seeing if you can carry out any fixes for any problems that occur.  Otherwise, it's probably better to stick with something that works rather than trying to get an ATI card to play nicely.

Anyway, boot off a LiveCD and see what happens. Let me know if you have any problems or any more questions.

---

### Post by cactusgal on 2010-02-05
My apologies for the delayed response. I want to thank you very much for your clear explanation of installing a tar. I've read similar information before but there was never any mention of 'why' particular commands are used. Your explanation, that it depends on what's in the tar file, makes complete sense. I'll definitely be referencing this information should I install one again. I think, to make things easy for myself, I'll download and untar on my desktop then cd to there from now on.

I have a couple more questions for you, just to clarify some details. Sorry to sound rather dense here but this is all quite new to me. When you said 'you can just make a link to the binary file in /opt to a directory in your PATH variable and then just enter "energyXT"' what exactly do you mean by path variable, whch directory, and how does one make a link.
And, when you said 'create a file called "energyXT.desktop' in /usr/local/share/applications', do you mean a text file? 
Please explain in more detail.

Strangely, my sound is back and I hadn't even gotten around to trying to do anything about it yet. I thought, yesterday, that I could very faintly hear something when an email arrived so this morning I went into sound and tested then opened sound control and raised the volume and it's all back to normal now.

As to the graphics card situation, I think I'm going to leave things as they are for now, at least till I get my Windows XP system rebuilt and running again (still waiting on the last of the parts to arrive in the mail). When I do there are several options I'm considering. First of all, is there a way to save all the programs besides just the data files (docs, pics, etc. which is what I assume you mean by saving my data to another hard drive, there are 3 in here plus others available via my eternal enclosure and my docking station) and restore them to a clean new install as there is for Windows? I rather like the idea of a clean install rather than an up-grade. I can try the live CD but, since Studio doesn't run from a CD I'll have to download and burn the regular Ubuntu 9.10 first. Another possibility is to save an image of this, try an up-grade and, if there's a problem (which I would try to resolve via this forum first), restore this from the image. A few possibilities but I'm not in a rush right now.

Again, thank-you very much for all your help, kayvortex.

Regards,
cactusgal

---

### Post by kayvortex on 2010-02-07
No need for the thanks: I'm happy to help!

No -- trust me -- you're not being dense: I thought I should've explained this PATH variable stuff more since it's under-the-hood stuff, but I didn't want to make the post too long.

The "PATH" variable is just a special shell variable that lists all the directories where the shell should look for executable files to run. (The shell is a special program that runs in a terminal, which is designed to interpret your input and run what you tell it to do. When you open a terminal, that blinking cursor is the shell waiting for you to tell it to do something.)

You can see what value is stored in "PATH" by echoing it:
```
echo "$PATH"
```
On my system, I get:
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
(the directories are separated by colons).

The reason for the "PATH" variable is that it lets you simply type the name of the program in a terminal and the shell will actually look for it in those directories and run it for you if it finds it. Why does it need to look for it? Well, because the actual program could be stored *anywhere* on the OS: it would have no idea where that file might be, otherwise.

Maybe some examples would help. First, let's confirm we can run a program OK:
```
apt-get moo
```
This should output an Easter Egg in the apt-get program. 

Now, let's change "PATH" to something else:
```
PATH=/home
```
We've now told the shell to look for any program we give it in /home (but *not* subdirectories of /home).
Now, let's try running what we did before again:
```
apt-get moo
```
On my system I now get:
> Command 'apt-get' is available in '/usr/bin/apt-get'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
[COLOR="Red"]apt-get: command not found[/COLOR]
What does this mean? Well, "Command 'apt-get' is available in '/usr/bin/apt-get'" is the shell telling me that it knows that there's a program called "apt-get" in /usr/bin; but since /usr/bin is no longer in the "PATH" variable, it cannot be sure that this is the apt-get you want to run -- remember, only those directories in "PATH" are the ones that the shell should look for programs in -- so, the shell simply concludes: "apt-get: command not found" since it found no program called "apt-get" in /home.
Try running more commands: the shell will just say the same thing, which is basically "I can't find X in /home (but there is, incidentally, a program called X in /usr/bin or /bin or whatever)".
The only way to run programs now is to explicitly tell the shell where it is:
```
/usr/bin/apt-get moo
```
Now, the shell runs apt-get fine again because there's no ambiguity: we told it exactly where the apt-get program we want to run is.
(There's no need to worry about breaking your system by having just changed "PATH" -- you can just close the terminal since any changes to shell variables like "PATH" only ever affect the terminal they are made in: they are never remembered or affect any terminals you subsequently open).

So, essentially, "PATH" just provides us with a very useful way of running programs since you can just enter the program name and the shell will know where to look for it without you needing to tell it.

Now, having placed energyXT in /opt, we can't just type:
```
energyXT
```
since the shell will look for a program called "energyXT" and fail to find it since it's in /opt which isn't in "PATH". The only way you'd be able to run it is by explicitly tell the shell where it is like this:
```
/opt/eneryXT/energyXT
```
There's nothing wrong with this, but it's just more useful to enter "energyXT" instead of "**/opt/energXT/**energyXT". So, how can we do this? By making a link to /opt/energyXT/energyXT in some directory listed in the "PATH" variable. You make links like this:
```
ln -s *ORIGINAL_FILE* *NEW_LINK_FILE*
```
So, we can do this:
```
sudo ln -s /opt/energyXT/energyXT /usr/local/bin
```
The above line will create a link in /usr/local/bin called "energyXT". Now, you can enter:
```
energyXT
```
and the shell will find a file called "energyXT" in a directory that is listed in the "PATH" variable (namely "/usr/local/bin") and will run that file. /usr/local/bin/energyXT is simply a link, so running /usr/local/bin/energyXT will just run /opt/energyXT/energyXT, which is what we wanted to do.

==========================================================================

> And, when you said 'create a file called "energyXT.desktop' in /usr/local/share/applications', do you mean a text file? 

Yes, sorry: it's just a text file. Run:
```
gksudo gedit /usr/local/applications/energyXT.desktop
```
A text editor will open, and just put:
> [Desktop Entry]
Name=EnergyXT
Comment=Start the EnergyXT music creator
Encoding=UTF-8
Exec=energyXT
Categories=AudioVideo;Audio;AudioVideoEditing;
Terminal=false
Type=Application 
in it. Save and close (and maybe re-login) and you should(!) see a "start-menu shortcut" in Applications -> Sound & Video.

==========================================================================

I'm glad that the sound problem has resolved itself: they can be nasty problems to solve! (Especially since Ubuntu recently changed to using pulseaudio, and they are apparently not doing a very good job integrating it into the OS.)

==========================================================================

Hmm, downloading a LiveCD and burning it for a version you're not going to install is a bit of a pain, but I can't think of an easier painless way of verifying that the OS's graphics will work. Then again, you sound competent enough to be able to make and restore partition images, so maybe that'll be your best bet (albeit one involving a bit of work!). As far as saving programs from a clean install goes, it can be tricky (just as with Windows): for most programs you'd also have to save any shared libraries used by the program and any configuration files too. I wouldn't recommend saving any programs downloaded from a repo (i.e. via apt-get/aptitude/synaptic) since these are easily re-installable. Do you have any specific program you want saved: it'll be easier if I run you through it specifically (rather than with a general guide) since it involves tracking files and libraries down and saving them in a way that'll remember where they're supposed to go when they're put back on your system after the clean install; and, suffice to say, it can be a complex task!

---

