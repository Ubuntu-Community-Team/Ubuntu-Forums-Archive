---
title: "A couple questions regarding Ubuntu Software Center"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2010-10-07
Hi, I just downloaded Ubuntu about a week ago; this is my first experience with Linux, and most of my previous computer experience has been with Windows XP.

Firstly, how do I determine the size of software I download via the Ubuntu Software Center? More Info would be the obvious choice, but there's nothing there, and I can't figure out a way to get *more* info.

Secondly, is there a simple way to determine the quality or popularity of a program within the Software Center? Another way to ask this: are the programs listed first the ones that are most frequently downloaded, so I could *assume* they're probably pretty adequate for what I'm looking for?

Okay, thanks people.

I also wanted to say (hopefully not sounding completely corny) that I'm pretty excited to be joining this community and culture.

---

### Post by Rinzwind on 2010-10-07
1. If it is there it should be shown on the page with the install button. For instance: moovida has a total size download and total size when installed. Same goes for frozen-bubble.
BUT! I am using Meerkat. Could be that your version does not have that yet.
 
2. Not via USC. 
The old version of USC had that and I think it might be comming back in a future release.
Currently all software is in alphabetical order.

---

### Post by NikoC on 2010-10-07
> **Rinzwind said:**
> 1. If it is there it should be shown on the page with the install button. For instance: moovida has a total size download and total size when installed. Same goes for frozen-bubble.
BUT! I am using Meerkat. Could be that your version does not have that yet.


The info is missing in Lucid (software center and synaptic). If you install it via command line e.g. 'sudo apt-get install moovida' it does tell you that 38.6MB additional disk space will be used.

---

### Post by mastablasta on 2010-10-07
Linux Mint has what you are looking for including reviews from users...

---

### Post by CommuneOfLoon on 2010-10-07
> **mastablasta said:**
> Linux Mint has what you are looking for including reviews from users...

Gotta be honest, wish you wouldn't have said that :) I was going back and forth between Ubuntu and Linux Mint, but now I don't feel like reformatting again.

> **NikoC said:**
> The info is missing in Lucid (software center and synaptic). If you install it via command line e.g. 'sudo apt-get install moovida' it does tell you that 38.6MB additional disk space will be used.

I haven't tried any CLI stuff yet. Would this command work for Ubuntu? Do I need to download any packages before hand, or will it simply recognize any program name I enter from the Software Center?

---

### Post by belkinsa on 2010-10-07
Yeah, it should.

---

### Post by Rubi1200 on 2010-10-07
Installing from the command line is easy and fun.

The command works like this:

```
sudo apt-get install <package_name>
```

---

### Post by oldos2er on 2010-10-07
Synaptic has always had this function; you just need to enable it. Settings, Preferences, Columns and Fonts, tic Installed Size and Download Size.

---

### Post by CommuneOfLoon on 2010-10-07
What is synaptic?

I'm gonna give the CLI install a try out of curiousity.

EDIT: so I tried the CLI install for VLC and it didn't work. I tried
    sudo apt-get install VLC media player
    sudo apt-get install VLC
    sudo apt-get install vlcmediaplayer

None of these worked (I tried them individually); response was:
    E: Couldn't find package <whichever variant I typed in>

EDIT 2: figured this out; I just had to use the parenthesized program name in the bottom right of the Software Center window.

---

### Post by oldos2er on 2010-10-07
Synaptic Package Manager. System, Administration, Synaptic.

---

### Post by CommuneOfLoon on 2010-10-07
> **oldos2er said:**
> Synaptic Package Manager. System, Administration, Synaptic.

Got it, thank you.

---

### Post by Rubi1200 on 2010-10-08
> **CommuneOfLoon said:**
> What is synaptic?

I'm gonna give the CLI install a try out of curiousity.

EDIT: so I tried the CLI install for VLC and it didn't work. I tried
    sudo apt-get install VLC media player
    sudo apt-get install VLC
    sudo apt-get install vlcmediaplayer

None of these worked (I tried them individually); response was:
    E: Couldn't find package <whichever variant I typed in>

EDIT 2: figured this out; I just had to use the parenthesized program name in the bottom right of the Software Center window.

Linux is case sensitive:

Therefore, the command would be ```
sudo apt-get install [COLOR=Red]vlc[/COLOR]
```

In most cases, the package name is quite simple; in other words, without any extra things like media player, browser, etc.

Hope this helps.

---

### Post by beew on 2010-10-08
> **NikoC said:**
> The info is missing in Lucid (software center and synaptic). If you install it via command line e.g. 'sudo apt-get install moovida' it does tell you that 38.6MB additional disk space will be used.

It is in Synaptic. After you check the software you want to install, you click "apply" and then it will tell you how many packages will be installed, the total size to download and total size of space needed , at this point you can choose to abort or continue, it is exactly like in the command line (where you choose y/n)  I don't know about the software center though, never really use it. Synaptic is much better IMO.

---

### Post by beew on 2010-10-08
> **Rubi1200 said:**
> Installing from the command line is easy and fun.

The command works like this:

```
sudo apt-get install <package_name>
```

If you are using the command line to install it is better to do ```
sudo aptitude install <package_name>
``` because it keeps track of packages that are installed simply as dependencies, so if you want to remove the program in the future these dependencies will be removed as well because they would serve no purpose (sudo aptitude remove <package_name>) whereas with apt-get these orphaned packages would be  left behind, only the program itself would be removed.

Apt-get is Synaptic without the GUI and I prefer to use Synaptic anyday because of the search function and you get imediate information about what other packages will be installed by simply highlighting, you can also browse programs at a glance. With cli you have to know exactly the name of the program and there is no browsing.  Using apt-get in the terminal to install has no advantage over Synaptic but has plenty of disadvantages (whereas aptitude does have the advantage of keeping track of dependencies as noted above)

---

### Post by NikoC on 2010-10-08
> **beew said:**
> It is in Synaptic. After you check the software you want to install, you click "apply" and then it will tell you how many packages will be installed, the total size to download and total size of space needed , at this point you can choose to abort or continue, it is exactly like in the command line (where you choose y/n)

True, I stopped a few steps earlier and only did a search in synaptic.

---

### Post by nothingspecial on 2010-10-08
> **beew said:**
> . With cli you have to know exactly the name of the program and there is no browsing.  Using apt-get in the terminal to install has no advantage over Synaptic but has plenty of disadvantages

```

$ apt-cache search "chess game"
convert-pgn - chess book format converter
dreamchess - a 3D chess game
fruit - chess engine, to calculate chess moves
gameclock - a simple chess clock to track time in real life games
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE
ggz-python-games - GGZ Gaming Zone: game clients collection for SDL and Python
gmchess - Chinese chess game (Xiangqi)
pgn-extract - Portable Game Notation (PGN) extractor
pgn2web - convert PGN chess game files into webpages
pouetchess - 3D chess game
pouetchess-data - Data files for the game pouetChess
scid - chess database with play and training functionality
texlive-games - TeX Live: Games typesetting
xboard - An X Window System Chess Board
3dchess - 3D chess for X11
$ apt-cache showpkg dreamchess
Package: dreamchess
Versions: 
0.2.0-2 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-amd64_Packages
                  MD5: 965b8ff10a4df08ab8647a9ffb51c127


Reverse Depends: 
Dependencies: 
0.2.0-2 - libc6 (2 2.4) libgl1-mesa-glx (16 (null)) libgl1 (0 (null)) libglu1-mesa (16 (null)) libglu1 (0 (null)) libmxml1 (0 (null)) libsdl-image1.2 (2 1.2.5) libsdl1.2debian (2 1.2.10-1) dreamchess-data (5 0.2.0-2) 
```

---

### Post by Rubi1200 on 2010-10-08
> **nothingspecial said:**
> ```

$ apt-cache search "chess game"
convert-pgn - chess book format converter
dreamchess - a 3D chess game
fruit - chess engine, to calculate chess moves
gameclock - a simple chess clock to track time in real life games
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE
ggz-python-games - GGZ Gaming Zone: game clients collection for SDL and Python
gmchess - Chinese chess game (Xiangqi)
pgn-extract - Portable Game Notation (PGN) extractor
pgn2web - convert PGN chess game files into webpages
pouetchess - 3D chess game
pouetchess-data - Data files for the game pouetChess
scid - chess database with play and training functionality
texlive-games - TeX Live: Games typesetting
xboard - An X Window System Chess Board
3dchess - 3D chess for X11
$ apt-cache showpkg dreamchess
Package: dreamchess
Versions: 
0.2.0-2 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-amd64_Packages
                  MD5: 965b8ff10a4df08ab8647a9ffb51c127


Reverse Depends: 
Dependencies: 
0.2.0-2 - libc6 (2 2.4) libgl1-mesa-glx (16 (null)) libgl1 (0 (null)) libglu1-mesa (16 (null)) libglu1 (0 (null)) libmxml1 (0 (null)) libsdl-image1.2 (2 1.2.5) libsdl1.2debian (2 1.2.10-1) dreamchess-data (5 0.2.0-2) 
```
+1

Moreover, Synaptic is a graphical front-end for APT, which is, itself, a front-end for dpkg.

[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
[http://en.wikipedia.org/wiki/Synaptic_Package_Manager](http://en.wikipedia.org/wiki/Synaptic_Package_Manager)
[http://en.wikipedia.org/wiki/Ubuntu_Software_Center](http://en.wikipedia.org/wiki/Ubuntu_Software_Center)
(The Ubuntu Software Center is also a graphical front-end for APT)

---

### Post by beew on 2010-10-08
Well how is that better than Synaptic where you can just browse and search without typing in the whole word? Moreover you told the OP to "sudo apt-get install" and "apt-cache search" would be yet another command. How many more command lines the poor OP would have to remember in order to get all the information that is displayed right before your eyes in Synaptic? :)

I know Synaptic is the GUI front end of apt and I said that in my original post, but that is exactly the point of a well written GUI, it provides a better, more intuitive way of organizing and displaying information (which you could get without the GUI).

---

### Post by oldos2er on 2010-10-08
> **beew said:**
> Well how is that better than Synaptic where you can just browse and search without typing in the whole word? Moreover you told the OP to "sudo apt-get install" and "apt-cache search" would be yet another command. How many more command lines the poor OP would have to remember in order to get all the information that is displayed right before your eyes in Synaptic? :)


No need to remember. Once commands are entered, they're in history. ;)

---

### Post by QLee on 2010-10-08
[QUOTE=beew]Well how is that better than Synaptic where you can just browse and search without typing in the whole word? Moreover you told the OP to "sudo apt-get install" and "apt-cache search" would be yet another command. How many more command lines the poor OP would have to remember in order to get all the information that is displayed right before your eyes in Synaptic? :)

I know Synaptic is the GUI front end of apt and I said that in my original post, but that is exactly the point of a well written GUI, it provides a better, more intuitive way of organizing and displaying information (which you could get without the GUI).[/QUOTE]
Well, as I have stated in a previous reply to one of your posts, helpers often choose CLI because they work regardless of what GUI's the OP's system has, people ask questions here about Kubuntu, Lubuntu, Ubuntu, etc. and, many times, they don't even mention which desktop environment or manager they are using. Not everyone has synaptic. Actually, not all systems even have an X server, so no GUI could run. But, the command line still functions. 

I agree that Synaptic is good and useful but how do you respond to a poster who replies I don't have synaptic and I don't want it. When we try to help people, we need to keep in mind that not all systems are configured as our own and that's fine, people can choose for themselves, we don't need to tell people they need to do things the way we choose. If the CLI gets someone back up and running faster than explaining how to use an unfamiliar GUI, then most people posting for help want that. Personally, I think everyone should learn the powerful command line and that this makes understanding the GUI's easier but I know that isn't the choice everyone makes.

---

### Post by beew on 2010-10-08
> **QLee said:**
> Well, as I have stated in a previous reply to one of your posts, helpers often choose CLI because they work regardless of what GUI's the OP's system has, people ask questions here about Kubuntu, Lubuntu, Ubuntu, etc. and, many times, they don't even mention which desktop environment or manager they are using. Not everyone has synaptic. Actually, not all systems even have an X server, so no GUI could run. But, the command line still functions. 


Well OP said he downloaded and installed Ubuntu one week ago, what is the chance that he/she is using Ubuntu 8.10 or a cli only system? :)(I don't know what features 8.10 supported, maybe Synaptic didn't exist then)

---

### Post by nothingspecial on 2010-10-08
```
/:$ apt-cache search -n byo
byobu - a set of useful profiles and a profile-switcher for GNU screen
/:$ apt-cache search -n guay
guayadeque - lightweight music player
/:$ echo 'alias acsn="apt-cache search -n"' | tee -a ~/.bashrc
alias acsn="apt-cache search -n"
/:$ . ~/.bashrc
/:$ acsn epiph
epiphany - clone of Boulder Dash game
epiphany-browser - Intuitive GNOME web browser
epiphany-browser-data - Data files for the GNOME web browser
epiphany-browser-dbg - Debugging symbols for the GNOME web browser
epiphany-browser-dev - Development files for the GNOME web browser
epiphany-data - required data files for epiphany game
epiphany-extension-gwget - Gwget extension for Epiphany web browser
epiphany-extensions - Extensions for Epiphany web browser
epiphany-extensions-more - Collection of third-party extensions for the Epiphany web browser
epiphany-gecko - Dummy, transitional package
epiphany-webkit - Dummy, transitional package
```

;)

---

### Post by CommuneOfLoon on 2010-10-08
I have Synaptic, and I plan to use it now based on the recommendation, but I definitely appreciate my first exposure to CLI as well. In other words, thanks all around :)

---

### Post by Rubi1200 on 2010-10-08
> **CommuneOfLoon said:**
> I have Synaptic, and I plan to use it now based on the recommendation, but I definitely appreciate my first exposure to CLI as well. In other words, thanks all around :)
At the end of the day, we use what works for us. Synaptic is a great tool as is the command line.

I hope you enjoy all your Ubuntu experiences! :)

---

### Post by CommuneOfLoon on 2010-10-08
> **oldos2er said:**
> No need to remember. Once commands are entered, they're in history. ;)

Tried to look for this history but couldn't find it; how do I access it?

> **Rubi1200 said:**
> I hope you enjoy all your Ubuntu experiences! :smile:

Thanks!

---

### Post by oldos2er on 2010-10-08
Type **history** into a terminal.

---

### Post by beew on 2010-10-08
> **oldos2er said:**
> Type **history** into a terminal.

Or you can keep hitting the up arrow until you find your command. It is not very efficient if you have a long command history, but if your list is short  it is quite convenient. :)

---

