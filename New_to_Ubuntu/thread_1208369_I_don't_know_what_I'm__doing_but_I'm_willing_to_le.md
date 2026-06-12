---
title: "I don't know what I'm  doing but I'm willing to learn. can anyone help?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-07-09
I just installed Ubuntu. I chose The first partitions option. I have absolutely nothing on Windows XP and was wondering if it would be wise to fully install Ubuntu. I tried using it but I don't know how  to dowload or install  drivers and all that.  I am  willing to learn.

---

### Post by nothingspecial on 2009-07-09
What drivers do you need. Most of them should already be there.

What is not working?

---

### Post by tacantara on 2009-07-09
A dual-boot setup might be good, as there are just some programs that don't have a Linux alternative and won't run optimally (or at all in some cases) under Wine.  If you have your Windows install disks, you can also install Ubuntu then download VirtualBox and set up Windows as a virtual machine.
 
As I understand Ubuntu, the drivers are part of the kernel.  This makes it fairly easy to set up on many computer systems.  However, if you need a driver, there are additional places on this forum that will give you further guidance.  I was fortunate in that Ubuntu worked right out of the box for me with the hardware on my laptop.
 
Good luck, and welcome to the world of Ubuntu :)

---

### Post by zeroseven0183 on 2009-07-09
So you mean you already installed Ubuntu on your computer? Is it a laptop or a desktop? Most of the drivers you need should be installed right away.

We suggest that you begin exploring Ubuntu with a guide. Check out this thread [**Free Beginners Guide**]("http://ubuntuforums.org/showthread.php?t=1052065") and download the PDF at [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

By the way, we know how you feel. I felt the same way too so keep on checking out stuffs in Ubuntu. You'll enjoy it.
And welcome to the Forums!

---

### Post by ibizatunes on 2009-07-09
Dual boot, only reason i have xp is if i want to play a game,
which version of ubuntu did you install 9.04?

once you have install go to application > accesiories > terminal > theh copy this code and hit enter
(this will allow you to play with restricted formats like flash)

```
sudo apt-get install ubuntu-restricted-extras
```

to play thing like avi you need to go to medibuntu url is below

[http://www.medibuntu.org/](http://www.medibuntu.org/)

go and add them to your repo's like restricted extras

welcome to the world of linux... at time it will be fustrating, just come on the formum and people will help you through your issues!! stick with it!! its worth it in the long run!!

---

### Post by 289531.EXE on 2009-07-09
Is this how to reply? I'll give it a shot:

Ok so, Ubuntu 9.04 comes with everything it needs. I don't know what drivers I will need,  yet. I  tried installing the security updates but apparently there is no room. My wireless internet card (I think that's what it's called [I'm not computer savvy if it's not apparent so  I hope I'm not being an annoying "noob". .  .sigh]) seems to be compatible since I  can  connect to the internet signal here.

I don't  know what I would really be missing out on without Windows XP. I did try to download flash player for youtube but it didn't seem to work. Other than that I don't know what else I would need. . . .

I hope you folks have patience, I know this can be quite annoying.

---

### Post by ibizatunes on 2009-07-09
289531.EXE run the command 
```
sudo apt-get install ubuntu-restricted-extras
```
will install flash for you!!

---

### Post by 289531.EXE on 2009-07-09
ok

---

### Post by 289531.EXE on 2009-07-09
I'm on XP hold on I have to switch.

---

### Post by ibizatunes on 2009-07-09
have you go the internet out of the box with ubuntu? via your wirless
top right there are 2 computer click them and see if you can 'see' your network.... then type your password to connect

---

### Post by nothingspecial on 2009-07-09
Before you try anything else can you open a terminal (in your menus accessories > terminal and type 
```
df -h
```

If you don`t have space for your updates there might be a problem.

All that command does is show your disk space.

---

### Post by 289531.EXE on 2009-07-09
I'm sorry, what?

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> My wireless internet card (I think that's what it's called [I'm not computer savvy if it's not apparent so  I hope I'm not being an annoying "noob". .  .sigh]) seems to be compatible since I  can  connect to the internet signal here.

Good to know that you have the wireless card working already.


>  I don't  know what I would really be missing out on without Windows XP. I did try to download flash player for youtube but it didn't seem to work.

How did you install [Adobe Flash Player]("http://get.adobe.com/flashplayer/")? Click the link and select .deb for Ubuntu 8.04+. It will automatically download the package. Restart your browser, or if you will, your computer and test it on YouTube. It worked for all computers I installed Ubuntu.


>  Other than that I don't know what else I would need. . . .

I hope you folks have patience, I know this can be quite annoying.

You have your OpenOffice.org applications for word processing, spreadsheet and presentations, etc. pre-installed with the OS. It's in Applications > Office.

---

### Post by nothingspecial on 2009-07-09
Go to the menu at the top of the screen.

Look in the accessories section and click terminal.

when it opens type ```
df -h
```

Then copy and paste what the terminal says into a reply here.

---

### Post by ibizatunes on 2009-07-09
go to the command line 
application > accessiores > terminal and copy this code in
```
df -h
```
and paste the results on the forum

---

### Post by 289531.EXE on 2009-07-09
Ok wait, what  will i ultimately be missing out on without Windows XP? I don't play video games or make  music or burn cd's (not yet at least).  I do need to scan and edit my art work and maybe load up pictures from my camera but other than that i really just use the computer for internet, aim, email, social network sites  and.  . . .and?. . .hm, I think thats it.

---

### Post by nothingspecial on 2009-07-09
Aslong as your scanner is compatible you will miss nothing.

---

### Post by 289531.EXE on 2009-07-09
you people type fast i'm trying to understand one person and i get  3 new responses when i'm done oy- 

I appreciate it : )

---

### Post by 289531.EXE on 2009-07-09
I have an 80  dollar scanner. . .  .(?) How do I know if it's compatible, rather how can I find out? Are there any programs that i can install to make it compatible if it isnt? By the way, im working with a laptop (Compaq  Presario V4000)

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> Ok wait, what  will i ultimately be missing out on without Windows XP? I don't play video games or make  music or burn cd's (not yet at least).  I do need to scan and edit my art work and maybe load up pictures from my camera but other than that i really just use the computer for internet, aim, email, social network sites  and.  . . .and?. . .hm, I think thats it.


Almost everything you need in Windows XP is available also in Ubuntu and have several alternative software that you can download for free.

As long as your scanner is detected then you have no problems with it. (Of course)

Downloading pictures from your camera is as easy as Copy and Paste option. See if you can do it now so we can guide you.

Internet, use may use Firefox (default)
Instant messaging, use may use Pidgin Instant Messenger (default)
Email, use may use Evolution

Social Network sites can be accessing using your web browser.

---

### Post by nothingspecial on 2009-07-09
If you haven`t got enough room for your updates then nothing is going to work. What does it say when you try to install your updates?

---

### Post by 289531.EXE on 2009-07-09
i  just finished kicking windows xp off my laptop. so what should i do now? oh let me check.. ..

---

### Post by 289531.EXE on 2009-07-09
i just put 
sudo apt-get install ubuntu-restricted-extras
 
in the terminal and  it said: E: Couldn't find package ubuntu-restricted-extras

---

### Post by WatchingThePain on 2009-07-09
No Room?, Make sure you're gonna have enough room. Security updates are required. Take time now to plan a good layout on disc or you will be sorry later.
There is a Wubi installer which installs Ubuntu inside XP (or Windows) if you're interested. This is usually easier.

---

### Post by nothingspecial on 2009-07-09
Go (in your menu) system > administration > software sources and make sure there is a tick next to universe and multiverse. (you`ll see what I mean when you get there).

Then type ```
sudo apt-get update
```

Then try again.

---

### Post by nothingspecial on 2009-07-09
> **289531.EXE said:**
> i  just finished kicking windows xp off my laptop. 

I may be wrong but I think the OP has just installed Ubuntu over his entire disk so the space may not be an issue any more.

---

### Post by 289531.EXE on 2009-07-09
ok im installing the updates. i saw the universe and multiverse if by "tick" you mean a check mark then yes, i see it. where do i type the code?

---

### Post by 289531.EXE on 2009-07-09
yes. i just installed ubuntu 9.04 and there is no more XP

---

### Post by nothingspecial on 2009-07-09
In applications > terminal

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> yes. i just installed ubuntu 9.04 and there is no more XP

Congratulations! You're now on your way to enjoying an IT life of freedom.

---

### Post by 289531.EXE on 2009-07-09
should i wait for updates to finish  loading before typing in codes?

---

### Post by 289531.EXE on 2009-07-09
Thank you. I never knew that something like this existed until my fri end turned me on to it last week. then i watched revolution os which was   a great film. i have a newly restored faith in technology since that dayand i just bought this laptop from another friend lastnight. i must say,  im quite excited to be part of such a radical technological movement even if it is justfor basic use.

---

### Post by zeroseven0183 on 2009-07-09
It depends on what code will you type in the Terminal. If it's related to Synaptics (installation of applications) or Update Manager and you're updating, then there will be conflict.

---

### Post by nothingspecial on 2009-07-09
Which wont work while your updates are downloading.

I suggest going [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") and following the tutorial. Just copy and paste all the commands relevant to your version of ubuntu. Ubuntu 9.04 jaunty jackolope I`m assuming.

This will install all the codecs and much much more. I use it every time I install

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> Thank you. I never knew that something like this existed until my friend turned me on to it last week. then i watched revolution os which was   a great film. i have a newly restored faith in technology since that dayand i just bought this laptop from another friend lastnight. i must say,  im quite excited to be part of such a radical technological movement even if it is justfor basic use.

Yes, thanks to your friend.

---

### Post by 289531.EXE on 2009-07-09
yes. i just pasted that code  in the terminal a  bunch of  jibberish scrolled down and said done. is that all there is to it? i  dont have to do anything else?

---

### Post by 289531.EXE on 2009-07-09
i just checked youtube and its still telling me i need to install flash

---

### Post by zeroseven0183 on 2009-07-09
I think so. Do another
```
sudo apt-get update
```

You just press the cursor UP to see the history of the commands you typed.

---

### Post by nothingspecial on 2009-07-09
Either try ```
sudo apt-get install ubuntu-restricted-extras
``` again or follow the tutorial in the link (pink here) I gave you earlier

---

### Post by random turnip on 2009-07-09
I would defiantly suggest doing a dual boot, which is really easy from the Live CD just in case.

After you've installed do all the updates and that should get most of the drivers, if there is still some missing then there is 90% of the time someone else with the exact same problem that has posted a guide on how to fix it, although they can be complex.

I was the same as you, i HATE Windows Vista, but my new laptop came with it, after i got the laptop the first thing i did was instal UBuntu a a dual boot and the wireless never worked, until 9.04 came out, now everything works perfectly, 9.04 improved hardware computability a hell of a lot, so make sure the disk you have is 9.04 as well.

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> i just checked youtube and its still telling me i need to install flash

You can also install it from [Adobe Flash Player website]("http://get.adobe.com/flashplayer/")? Click the link and select .deb for Ubuntu 8.04+. It will automatically download the package and click the button to Install it. Restart your browser, or if you will, your computer and test it on YouTube. It worked for all computers I installed Ubuntu.

---

### Post by 289531.EXE on 2009-07-09
what can i do about viruses or spyware, trojans etc etc?

---

### Post by nothingspecial on 2009-07-09
You don`t need to do anything. Unless you plan on sharing files with a windows computer.

---

### Post by 289531.EXE on 2009-07-09
hey, nothing special that code seemed to have worked. i can listen to the song on my myspace. thanks. i shouldnt  worry about the crazy random scrolling in the terminal box right? and, are there any codes anyof you folks suggest?

---

### Post by 289531.EXE on 2009-07-09
101010001010110101110010101010001010101011011011001111101010101

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> what can i do about viruses or spyware, trojans etc etc?

Nothing. You can almost ignore them. Ubuntu/Linux is designed in such a way that these malwares can almost impossibly infect your machine.

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> what can i do about viruses or spyware, trojans etc etc?

You don't really need a virus/malware/spyware scanner on Ubuntu, it's fairly impervious to such things. However, if you are going to be downloading stuff to Ubuntu and then copying it to a Windows PC, you might want to install ClamAV which will scan for Windows viruses (which don't affect Ubuntu).

I've skimmed the thread and I'm worried the advice you are receiving (installing via the Terminal) might be confusing you. If you go to Applications->Add/Remove you can install the most common applications through there. For example, to install Flash open Applications->Add/Remove, select "All available applications" from the drop down box, then search for "Restricted" and select the "Ubuntu restricted extras" package. 

If you can't find something there, take a look in System->Administration->Synaptic Package Manager which has more programs.

You might be used to searching for programs via the Internet on Windows, on Ubuntu you should instead look in these two applications first, before searching the Internet for an Ubuntu package (a file with a .deb extension).

---

### Post by nothingspecial on 2009-07-09
For torrents
```

sudo apt-get install deluge-torrent
```

Then look for deluge in your menu under internet.

Or you could use transmission which is there already.

For .rar 

```
sudo apt-get install unrar
```

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> what about .rar  or torrents?

There is a torrent application called Transmission installed by default. For rar files, search the Add/Remove program for "Rar".

---

### Post by zeroseven0183 on 2009-07-09
> **289531.EXE said:**
> what about .rar  or torrents?

RAR files can be opened with the default Archive Manager. Right-click on the file and open it with Archive Manager. Torrents, Ubuntu has a pre-installed application called Transmission BitTorrent Client and can be found in Applications > Internet.

I'm out of the forums for now. Good night and I'll check this thread tomorrow.

Happy to help you out today.

---

### Post by nothingspecial on 2009-07-09
> **Kazade said:**
> 

I've skimmed the thread and I'm worried the advice you are receiving (installing via the Terminal) might be confusing you. 

You are right. Read [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by random turnip on 2009-07-09
Viruses?
In Ubuntu?
I think you've got Windows fever, we're 100% virus free here, forget they even exist.

As for flash if you haven't got it working, go Applications --> Add/Remove --> search for "adobe" or "flash" and you will see the latest version of flash in there, click the ckeck box and "make changes", boom, you installed flash player.  Restart Firefox and YouTube will work just like it should.

---

### Post by 289531.EXE on 2009-07-09
sick! are there  any other useful and basic codes  for my peace of mind?

---

### Post by 289531.EXE on 2009-07-09
goodnite zeroseven thanks  alot iappreciate it. all of you too i appreciate it!

---

### Post by nothingspecial on 2009-07-09
And I am retiring to the gym. I have to maintain my heculean physique. (loose alot of weight) ;)

Good luck

---

### Post by random turnip on 2009-07-09
[http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/1004-ubuntuterminal](http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/1004-ubuntuterminal)
Look there.
There are also a few guides on these forums.

I avoided the terminal until the other day when i couldn't be bothered to search for something in Add/Remove, so i typed "sudo apt-get install" and it was so easy and quick.
I'm a total noob too btw.

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> sick! are there  any other useful and basic codes  for my peace of mind?

All the commands that have been mentioned in this thread can be done with the mouse by going to Add/Remove. However, I'll help you understand. There are 4 parts to the command which installs applications (packages) these are

1. sudo
2. apt-get
3. install
4. the package name

So, for example, to install unrar, you would use:

sudo apt-get install unrar

Each of the 4 parts does the following:

1. Tells Ubuntu to run this command as the super user (super user do). Only super users can install programs (part of the high security of Ubuntu).
2. apt-get. This is the program which installs/removes/updates packages (applications). 
3. install. Tells apt-get you want to install something
4. the package name. This is the name of what you want to install.

When you run the command, apt-get searches online servers (repositories) for the program you want. If it finds it, it downloads and installs it. If you run:

sudo apt-get update

This updates apt-get's local knowledge of the packages that are available on these servers. Whereas sudo apt-get upgrade will upgrade all the packages on your system to their latest available versions.

As I said, using Add/Remove or Synaptic programs will run these commands for you.

---

### Post by 289531.EXE on 2009-07-09
awesome! how do i access the "guts" of this os? is it possible to do that or do i get denied access?

---

### Post by 289531.EXE on 2009-07-09
> **Kazade said:**
> All the commands that have been mentioned in this thread can be done with the mouse by going to Add/Remove. However, I'll help you understand. There are 4 parts to the command which installs applications (packages) these are

1. sudo
2. apt-get
3. install
4. the package name

So, for example, to install unrar, you would use:

sudo apt-get install unrar

Each of the 4 parts does the following:

1. Tells Ubuntu to run this command as the super user (super user do). Only super users can install programs (part of the high security of Ubuntu).
2. apt-get. This is the program which installs/removes/updates packages (applications). 
3. install. Tells apt-get you want to install something
4. the package name. This is the name of what you want to install.

When you run the command, apt-get searches online servers (repositories) for the program you want. If it finds it, it downloads and installs it. If you run:

sudo apt-get update

This updates apt-get's local knowledge of the packages that are available on these servers. Whereas sudo apt-get upgrade will upgrade all the packages on your system to their latest available versions.

As I said, using Add/Remove or Synaptic programs will run these commands for you.












can  i do thatwithanything or does it need to be soecific or available files?

---

### Post by random turnip on 2009-07-09
You can do anything if you log in as a root user, but be aware, you can screw your OS up and you lose some security, so it isn't advised unless you need to do it.

You can also look at the source code of the OS if you want to by looking in the "System" option on the top bar.

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> awesome! how do i access the "guts" of this os? is it possible to do that or do i get denied access?

As the source code is open you can access/change any part of it :)

From a security point of view, you should understand that they only part of the filesystem you have write access to is your home directory (/home/yourname) and the temp directory (/tmp). To write anywhere else you need to run sudo but you shouldn't ever need to do that directly, you'll get that nice password dialog popup. It takes a while to get used to because, obviously, you can put stuff all over the C:\ in Windows, but it's better organized this way, and safer.

---

### Post by grappler on 2009-07-09
The command sudo effectively gives you root access for one command - you will be asked for your password.  

So when you type 

sudo apt-get install <package-name>

the sudo part tells you that you're root (ie Administrator) - but only for the remainder of the  command. 

If you want to know what processes are running just type

ps ax 

in a terminal.

There's a great program called htop which you can install in the usual way

sudo apt-get install htop

which when you run it - I think under Applications> System in gnome (I use kde these days so it's a bit different) or just by typing

htop & 

in the terminal will give you a list of processes in decreasing order of resource use.

Did you ever get flash working?

---

### Post by random turnip on 2009-07-09
> **289531.EXE said:**
> can  i do thatwithanything or does it need to be soecific or available files?

the "sudo apt-get" thing only works will programs, not things like spread sheets.
I think that's what you meant, lol.

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> can  i do thatwithanything or does it need to be soecific or available files?

You need to know the name of the package you are installing. If you don't know the name you can do:

apt-cache search flash

and it will search the packages for flash.

---

### Post by 289531.EXE on 2009-07-09
im trying to play a dvd  on the  latop (madagascar for testing purpose. . . .*of course*) .  but i keep getting an error message:

An error occure. can not open location;you may not have permission to open  the file,


is there a way to fix that?

---

### Post by random turnip on 2009-07-09
Instal VLC
```
sudo apt-get install vlc
```
Or search in Add/Remove for VLC, that's what i use, it plays virtualy any file format, and it's the same as the one you get in windows.

---

### Post by 289531.EXE on 2009-07-09
that didnt seem to work. i got  a bunch of error messages when i tried palying the dvd

---

### Post by 289531.EXE on 2009-07-09
nevermind i think the dvd i was using was just badly scratchedi tried another dvd and it worked

---

### Post by random turnip on 2009-07-09
Oh, lol, i'm afraid Ubuntu can't help with that.

---

### Post by 289531.EXE on 2009-07-09
something just crossed my mind, is there any kind of program i can download thats like limewire?

---

### Post by Kazade on 2009-07-09
try gtk-gnutella:

sudo apt-get install gtk-gnutella

---

### Post by 289531.EXE on 2009-07-09
where will that  appear? how do  i launch it?

---

### Post by 289531.EXE on 2009-07-09
are there codes designed to detect and remove useless or unecessary files and all that stuff to save space?

---

### Post by 289531.EXE on 2009-07-09
and i dont understand that gnutella. how do i uninstall it?

---

### Post by Kazade on 2009-07-09
You can either:

sudo apt-get remove gtk-gnutella

OR

go to System->Administration->Synaptic 

search for it and mark it for removal, then apply.

And to remove uneccessary files, try System->Administration->Computer Janitor.

---

### Post by 289531.EXE on 2009-07-09
is there a simpler program like lime wire that i can  use  to  download  music or videos documents or images?

---

### Post by Kazade on 2009-07-09
> **289531.EXE said:**
> is there a simpler program like lime wire that i can  use  to  download  music or videos documents or images?

I just realized, you can actually use limewire:

[http://www.limewire.com/download/?os=linux](http://www.limewire.com/download/?os=linux)

Just click "Open with GDebi" when it starts to download.

---

### Post by random turnip on 2009-07-09
```
sudo apt-get install wine
```
To install Wine, download the Limewire .exe like you usually would, right click, run with Wine, hope it works.

If not, then start torrenting, limewire is crap anyhow.

[edit]
I forgot Limewire has a Linux option >.<
Like said above, go to the Limewire website.

---

### Post by 289531.EXE on 2009-07-09
is there a grand theft auto for this os?

---

### Post by apostate on 2009-07-09
Hey,

LIMEWIRE
--------

Frostwire is the same thing, but better. Applications -> Add/Remove frostwire

TORRENTS
--------
You have transmission under your Internet menu. It will open torrents.

GTA
---

You need the Windows compatibility layer, called "Wine"

Applications -> Add/Remove  wine

Caveat: Some Windows apps work awesome, some work ok, some WILL NOT WORK. That is just the nature of the beast. Go to appdb.winehq.org if you want to run Windows games in Ubuntu, to see what is known to work or not work, or work with patches, etc.

---

### Post by 289531.EXE on 2009-07-12
ok so i just rebooted  my computer again (dont ask why, but i bet some one will) and i was trying to install flash with  all the codes here and nothing seems to work. any ideas?

---

### Post by 289531.EXE on 2009-07-12
sorry, seems like its fixed

---

