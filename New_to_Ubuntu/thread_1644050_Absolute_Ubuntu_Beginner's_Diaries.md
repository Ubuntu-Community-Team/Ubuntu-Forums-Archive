---
title: "Absolute Ubuntu Beginner's Diaries"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Jugurtha on 2010-12-12
Hello everybody, 

I am Jugurtha, from Algiers, Algeria .. And I installed Ubuntu 10.10 today.

I have never used Linux before and I'm coming from Windows XP SP3. [I've been using Dos/Windows since I was a child, maybe  4 years old or less..  


I downloaded the Iso image, burned it into a CD, installed it ... And going by my Scortched Earth Approach .. Erase everything. Separate from any known territories. 

Without further ado, here is a little stuff I stumbled upon, witch an absolute begginer would probably do too...




Question- Opened [http://bit.ly](http://bit.ly) and it said I needed Flash plugin installed.

Answer- I went to Adobe site, I chose "APT for Ubuntu 9.04+", clicked on it.. It didn't do anything, so I chose ".tar.gz for Linux",I downloaded a file called "install_flash_player_10_linux.tar.gz"  

[Nb: It was "APT pour Ubuntu 9.04+", the page was in French, but I'm typing this in English so everyone can understand]

Google "Installing flash plugin tar.gz" clicked on mozilla.support -- Here's my link [http://bit.ly/installingflashplugintargz](http://bit.ly/installingflashplugintargz)  And followed instructions.. [Not really, at one point, they tell you to Quit Firefox.. How are you going to be able to read the instructions if you shut it ??]

cd Téléchargements               #I've installed the French version by mistake.

dir      #To see what's in there, I can't retain the hole name in my memory, so I list it to have it under my eyes..

tar -zxvf install_flash_player_10_linux.tar.gz  #Decompresses the archive

There's a file named "libflashplayer.so" 



sudo cp libflashplayer.so /usr/lib/mozilla/plugins   # Search sudo command online

# As they said in the instructions, however, I checked the very existence of such a path/directory before I do that :

After a little bit of trying {cd..,cd .., cd \ and stuff } , I did "cd /" and then "dir" and it showed "usr"

cd usr
dir

it showed "lib", I'm probably on the right track

Same process to check if the whole "usr/lib/mozilla/plugins" exists.. Once done, I went back to the "libflashplayer.so" in Téléchargments {Downloads} and did the command :

sudo cp libflashplayer.so /usr/lib/mozilla/plugins

It asked for authentification, I put the password.. And it works...

I will probably do a script to automate that kind of stuff, and name it targzinstaller or something like that .. Like the "bat" files I wrote sometimes in Dos..


I found that I could download the ".deb for Ubuntu 8.04+", because when I was going to download it it proposed to open it with "Logithèque Ubuntu" and it's in "Applications in the dashboard..

I'm going to give it a try and see what happens..

I clicked "Open" with "Logithèque Ubuntu" .. And it launched a pretty application that said it enters in conflict with the flash plugin ALREADY installed...So it would've done the same job, with less effort and in a "graphical" interface.. It installs and manages software.. [Don't hold things on me, I'm new]

So, next time ".deb" is the right file .. But I kind of know how to do install a tar.gz

I installed Thunderbird, it was proposed there .. I like Thunderbird.
---------------------------------------------------------------
I downloaded a rar file, clicked on it but it couldn't read it..

Question- Can't read RAR files.
Answer- Searched the internet for a quick fix : Install UNRAR.

How to ?  Terminal--> sudo apt-get install unrar

It works, you just double-click on the .rar file and it opens..
--------------------------------------------

Question- I'm writing this "Survival HandBook That You Read While Being Eaten" in Gedit, and I want to be able to automate "Question Answer How To", so I want to install XEmacs and put in a macro/script.. or try to {I don't know how, this is my first Ubuntu 10.10 day, but Emacs/XEmacs is a recurrent name, and it seems it does do lots of things}

Answer- I open a Terminal, type xemacs. It says Xemacs21 {It must be there but just not "installed", because how would it know that it's xemacs21.. } is not installed and tells me to "sudo apt-get install xemacs21".

How to ?  sudo apt-install xemacs21

Then xemacs21 and Voilà :)

I didn't like it. I couldn't even open this file with it... 

I got another one here : [http://ftp.gnu.org/pub/gnu/emacs/](http://ftp.gnu.org/pub/gnu/emacs/)

and got this one [http://ftp.gnu.org/pub/gnu/emacs/emacs-23.2.tar.gz](http://ftp.gnu.org/pub/gnu/emacs/emacs-23.2.tar.gz)

The file is 44.7 MB, so it will take about 8 or less minutes to download..

And I'll install it ..

Meanwhile, I typed help ... 

 
"history" lists all the things you've typed.

"history -c" clears that list..

Also "clear" works like "cls" in a Dos prompt..

All right, I decompressed the file.. And there is install-sh... It seems executable.. I opened it, but to view it before executing it .. It seems alot like the batch files, I guess "echo" does the same thing..


It's installed, I did "emacs" and it's different now .. It says it is in different packages.. I chose emacs23

sudo apt-get install emacs23

It went through a similar process...

Then 

emacs

And here you go ! A lot better ...

Close file and open it in Emacs.

In Emacs.

That's it for now...

Any proposition for doing things better than that, you're welcome...

English isn't my first language, I started using it very recently .. So any weird expression, it's not my intention to not write it well.

---

### Post by cchhrriiss121212 on 2010-12-12
To install things in Ubuntu is easy:
Go to the Software Center
Search for whatever you need, and click install

There is no need to compile from tar.gz files or debs from random websites. For the new user I recommend a package called ubuntu-restricted-extras, it has flash and rar and a bunch of proprietary codecs you will probably need at some point. Feel free to explore other methods though, it is just that Ubuntu is designed to be more of a point and click OS.

---

### Post by Quackers on 2010-12-12
Also in Synaptic search for and install ubuntu-restricted-extras. That will solve some problems for you.

---

### Post by Jugurtha on 2010-12-13
[FONT=Arial][SIZE=2]Hey, thanks a lot for the advice[/SIZE][/FONT] guys .. "ubuntu-restricted-extras" installed..

I'm really enjoying it, it's so clean and nice .. 

As for the Software Center [Logithèque] , I opened it before and actually found Eagle amongst other software .. But I didn't know it managed "plugins" as well, I thought they were in another "category".

Thank you.


~Jugurtha.

---

### Post by migs73 on 2010-12-13
There is a Firefox add-on called Flashaid, this should sort out any flash problems (there seem to be so many different ways of installing Flash/Flash alternatives). This should sort out any issues and is from a forum member (LovingLinux).

---

### Post by mastablasta on 2010-12-13
Jogurtha... is it the famous king himself :-)
 
anyway i would suggest to a newbie a bit of reading to learn more about the new system. perhaps the free Ubuntu pocket guide or Ubuntu manual (for a more up to date experience). just like when you were first introduced to DOS based system it's good that someone shows you the basics before you jump in. my opinion at least.
 
it makes it a lot easier to start and to see the possibilities of this system as well as to spot any troubles up ahead.
 
enjoy the experience.

---

### Post by prj44 on 2010-12-13
I have .rar files to combine.  I have installed unrar.  I run it, it says the files have been extracted.  But there is nothing there!  
This is incredibly frustrating, because I suspect that the answer is terribly simple.  (And I don't enjoy feeling incredibly dumb!)

Help please.

---

### Post by wojox on 2010-12-13
> **prj44 said:**
> I have .rar files to combine.  I have installed unrar.  I run it, it says the files have been extracted.  But there is nothing there!  
This is incredibly frustrating, because I suspect that the answer is terribly simple.  (And I don't enjoy feeling incredibly dumb!)

Help please.

Use 7-zip. Its really a good alternative. It should be in the repo's.

---

### Post by Jugurtha on 2010-12-13
> **mastablasta said:**
> Jogurtha... is it the famous king himself :-)
 
anyway i would suggest to a newbie a bit of reading to learn more about the new system. perhaps the free Ubuntu pocket guide or Ubuntu manual (for a more up to date experience). just like when you were first introduced to DOS based system it's good that someone shows you the basics before you jump in. my opinion at least.
 
it makes it a lot easier to start and to see the possibilities of this system as well as to spot any troubles up ahead.
 
enjoy the experience.

Hello, :)

Indeed, it is ! I've been named after him.. You realize you know something most people HERE in Algeria don't..

And I definitely am reading about things like you suggest.. I just like to try them "before" :D  {Thus the analogy of a survival handbook you read while in the belly of the beast} Or else, I would be just reading about it alot, and not doing it often to get better..

It's that I've got this habbit that, if something doesn't harm me.. I'm willing to make mistakes and learn from them and then getting assistance from someone more knowing.. Because at least, I've tried some things and I know they don't work ! It kind of reduces his work.

"enjoy the experience."

You bet I am ! Everytime I turn it on. It feels great. I'll navigate through the forum to check some stuff about sound...

My best ,

---

### Post by lindsay7 on 2010-12-13
Install "Ubunu Tweak" , you can use it to get other programs like google earth, etc that make the installation easy.  You can also clean up your computer from this and do a lot of other things that will make life easier.

---

### Post by low_rider on 2010-12-14
Quick note about .deb files.  Those come from the Debian repositories, which though very similar to Ubuntu may not always work.  So far I've failed to find anything that doesn't work, but they're different operating systems so you may run into a problem there.

---

### Post by waynefoutz on 2010-12-14
> **low_rider said:**
> Quick note about .deb files.  Those come from the Debian repositories, which though very similar to Ubuntu may not always work.  So far I've failed to find anything that doesn't work, but they're different operating systems so you may run into a problem there.

deb files from Debian will almost always work for Ubuntu, deb files for Ubuntu, not so good if you are using Debian.

---

### Post by owiknowi on 2010-12-14
> **low_rider said:**
> Quick note about .deb files.  Those come from the Debian repositories, which though very similar to Ubuntu may not always work.  So far I've failed to find anything that doesn't work, but they're different operating systems so you may run into a problem there.

don't get your point? what's the question?

ubuntu is based on debian but they made an effort to make several improvements or increasing the usability.

try them both and see the differences your self.

---

