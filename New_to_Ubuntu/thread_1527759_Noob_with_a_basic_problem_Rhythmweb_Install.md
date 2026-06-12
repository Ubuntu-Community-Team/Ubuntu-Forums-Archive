---
title: "Noob with a basic problem: Rhythmweb Install"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2010-07-09
Hi there,

Well my Mum says I'm smart - turns out she was lying.

I'm trying to install This: [http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote) but I'm stuck at the basics (I've been a windows user since forever..). The instructions say: 

*To install, unzip and copy the 'rhythmweb' directory to ~/.gnome2/rhythmbox/plugins, start Rhythmbox, go to the Edit > Plugins... menu and check the Enabled checkbox for Rhythmweb.*

I'm stuck at word 5. COPY the directory to this address. How the heck do I do that? I've copied the file (right click) but where do I paste it to? I can't find the "* ~/.gnome2" *let alone the "[I]/rhythmbox/plugins" bit.

[/I]Please, somebody...:popcorn:

---

### Post by SKhan on 2010-07-09
> **Moriarty123456 said:**
> Hi there,

Well my Mum says I'm smart - turns out she was lying.

I'm trying to install This: [http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote) but I'm stuck at the basics (I've been a windows user since forever..). The instructions say: 

*To install, unzip and copy the 'rhythmweb' directory to ~/.gnome2/rhythmbox/plugins, start Rhythmbox, go to the Edit > Plugins... menu and check the Enabled checkbox for Rhythmweb.*

I'm stuck at word 5. COPY the directory to this address. How the heck do I do that? I've copied the file (right click) but where do I paste it to? I can't find the "* ~/.gnome2" *let alone the "[I]/rhythmbox/plugins" bit.

[/I]Please, somebody...:popcorn:
welcome to ubuntu forums. i am also new linux user, so i can understand you problem and frustration very well. wait a couple of minutes until my next post.

---

### Post by Moriarty123456 on 2010-07-09
Glad I'm not the only one...!:D

---

### Post by SKhan on 2010-07-09
~ means your home directory. it's equivalent to "my documents" in microsoft windows.
to go to your home directory. you should click "places" at top right of the screen. then choose home.

any file with . before it's name is a hidden file. to view hidden files click view menu in nautilus then select "show hidden files."
keyboard shortcut for showing/hiding hidden files is Ctrl+H

~/.gnome2/rhythmbox/plugins  IS SAME AS /home/YOUR-UBUNDU-USER-ACCOUNT-NAME/.gnome2/rhythmbox/plugins

using ~ instead of the path to home folder has it's own benefits, which you will learn later if you are really smart enough.

my reply is slow because currently i can't connect to internet via ubuntu. so i have to reboot with windows in order to post reply, then reboot to ubuntu in order to type the reply. :)

---

### Post by themusicalduck on 2010-07-09
Like Skhan said ~ is your home directory and can be found under places.

Any folder or file with a . before it is hidden though, so once the file manager is up you need to press ctrl+h to show the hidden files.

---

### Post by feelshift on 2010-07-09
The files that start with a dot (".") are hidden files. Press Ctrl-H in Nautilus to show hidden files and you should be able to find .gnome2

---

### Post by ov3rcl0ck on 2010-07-09
In a year you'll have your head under the hood and know shell as a second nature.

---

### Post by Moriarty123456 on 2010-07-09
Thanks Kahn,

There's home/robert (my name) and a /home/robert/rhythmweb-iphone where I've dowloaded the file. Do they mean I have to CREATE a new directory called /.gnome2/rhythmbox/plugins?

I got the impression the .../rhythmbox/plugins would already be there and I'd have to just paste into it?

Thanks for your help..

---

### Post by Moriarty123456 on 2010-07-09
Hey! There she is! 

Thanks everybody! Why do they have to hide the good stuff?

:-)

Ok. We're rolling.

---

### Post by SoFl W on 2010-07-09
You should already have a 
/home/robert/.gnome2/rhythmbox/plugins
That is where the plug in needs to go.

---

### Post by SKhan on 2010-07-09
please again view my post number 4. i have updated it. i was slow for some reason.

---

### Post by Moriarty123456 on 2010-07-09
Opps! Actually I spoke to soon. Thought I had it.  Another problem.

I DON'T have a /.gnome2/rhythmbox/plugins folder. Which is strange as I use rhythmbox everyday.

There's Accels, eog, etc by no rhythumbox...

Could it be in a different location? I'm using 9.10

Yours, Confused.

---

### Post by SKhan on 2010-07-09
> **Moriarty123456 said:**
> Hey! There she is! 

Thanks everybody! Why do they have to hide the good stuff?

:-)

Ok. We're rolling.
just as hidden files are hidden in windows too.

---

### Post by Moriarty123456 on 2010-07-09
Thanks Kahn I do appreciate it.:P

---

### Post by SKhan on 2010-07-09
> **Moriarty123456 said:**
> Opps! Actually I spoke to soon. Thought I had it.  Another problem.

I DON'T have a /.gnome2/rhythmbox/plugins folder. Which is strange as I use rhythmbox everyday.

There's Accels, eog, etc by no rhythumbox...

Could it be in a different location? I'm using 9.10

Yours, Confused.
you went to wrong path.
it should NOT be /.gnome2/rhythmbox/plugins
it should be /home/robert/.gnome2/rhythmbox/plugins

---

### Post by Moriarty123456 on 2010-07-09
If it's a help I've found a /home/robert/.local/share/rhythmbox but that doesn't have a /plugins folder...

Hmmm..

---

### Post by Moriarty123456 on 2010-07-09
Thanks Kahn. I went to /home/robert/.gnome2/

There is no Rhythmbox folder there at all... Very strange. 

??

---

### Post by SKhan on 2010-07-09
open nautilus
press ctrl+L in order to show "address bar"
then type this path /home/robert/.gnome2/rhythmbox/plugins

one more thing. In order to show hidden files, you will have to press ctrl+h each time you launch nautilus.
I noted that we can't set nautilus to permanently "show hidden files".

---

### Post by Moriarty123456 on 2010-07-09
The only folders there are:
accels
eog
evince
file-roller
gedit
gnome-pilot
home-sudoku
keyrings
nautilus-scripts
panel2.d

No Rhythmbox... Maybe another glass of wine might help...!

---

### Post by SKhan on 2010-07-09
i don't have solution for your post 16 and 17.
i too am a new linux user.
i don't use rhythmbox, i use VLC instead.
i am using ubuntu 10.04, it's being my first linux installation ever. So i can't say anyting about older ubuntu versions.

---

### Post by Moriarty123456 on 2010-07-09
Thanks again Kahn,

But still no luck. Message is: File not found, check spelling (which I did).

Anyway of cheking on the rhythmbox program itself where it stores its plugins?

Thanks.

---

### Post by WRDN on 2010-07-09
If the folder doesn't exist, you can just create it:

```
mkdir --parents ~/.gnome2/rhythmbox/plugins
```

Though it is not often used, the "--parents" switch here is used to create any parent directory that does not exist, before the one you want. So, for example, if I wanted to create the folder "~/my_folder1/my_folder2/my_folder3" and my_folder1 did not exist, then it would create that, then my_folder2 and finally my_folder3.
If you excluse "--parents", mkdir will return an error, telling you it cannot create the directory as my_folder1 does not exist yet (nor my_folder2 after that).

---

### Post by SKhan on 2010-07-09
no rhythmbox directory in my ubuntu 10.04 as well. although rhythmbox is preinstalled in ubuntu.
but as WRDN said, you can just create it.
if you find it difficult to create directories using command line, you can create it just as we create it in windows.
that's right click and choose new folder or new directory, whatever.

---

### Post by Moriarty123456 on 2010-07-09
Thanks WRDN! Progress! Exciting! made the directory, Rhythmbox recognized it, but now the iPhone is saying it cant open location as it is a local file..! I suppose this is now an iPhone issue rather than a RB one..

Thanks very much. I'll keep trying. Any other tricks, or people that have done this install please shout out...!
:p

---

### Post by SKhan on 2010-07-09
> **WRDN said:**
> If the folder doesn't exist, you can just create it:

```
mkdir --parents ~/.gnome2/rhythmbox/plugins
```

Though it is not often used, the "--parents" switch here is used to create any parent directory that does not exist, before the one you want. So, for example, if I wanted to create the folder "~/my_folder1/my_folder2/my_folder3" and my_folder1 did not exist, then it would create that, then my_folder2 and finally my_folder3.
If you excluse "--parents", mkdir will return an error, telling you it cannot create the directory as my_folder1 does not exist yet (nor my_folder2 after that).

hey guys! why do you always come up with a command line method even in "Absolute Beginner Talk". :p
Do you know what does absolute mean? do you know what does bigenner mean? ](*,)
and that too Absolute Beginners who just switched to Linux from ms windows. They are usually used to easy GUI, and they may be terrified of command line #-o
and that too using terminal which is different from cmd. [-o<
average windows user is usually terrified of cmd.exe let alone terminal. [-o<
At this time i love using terminal, but yes i was terrified when i was new to linux.

---

### Post by Moriarty123456 on 2010-07-09
Just If anyone else is interested The Rhythmweb page says one should enter  " http://your-machine-name.local:8000" into safari on the iPhone, but I'm stuck at another noob question !!! - how do i find my machine's name...!

:D

---

### Post by SKhan on 2010-07-09
> **Moriarty123456 said:**
> Just If anyone else is interested The Rhythmweb page says one should enter  " http://your-machine-name.local:8000" into safari on the iPhone, but I'm stuck at another noob question !!! - how do i find my machine's name...!

:D

i think by default it should be robert-computer. but i am not sure. i am interested if someone else could answer.

---

### Post by joedoe47 on 2010-07-09
> **Moriarty123456 said:**
> Hi there,

Well my Mum says I'm smart - turns out she was lying.

I'm trying to install This: [http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote) but I'm stuck at the basics (I've been a windows user since forever..). The instructions say: 

*To install, unzip and copy the 'rhythmweb' directory to ~/.gnome2/rhythmbox/plugins, start Rhythmbox, go to the Edit > Plugins... menu and check the Enabled checkbox for Rhythmweb.*

I'm stuck at word 5. COPY the directory to this address. How the heck do I do that? I've copied the file (right click) but where do I paste it to? I can't find the "* ~/.gnome2" *let alone the "[I]/rhythmbox/plugins" bit.

[/I]Please, somebody...:popcorn:

that ~ symbol is the way that programs/scripts in ubuntu refers to your home directory.

so if your user name is joedoe47 you just replace the ~ with your username so you can type in a terminal "cd ~/.gnome2..." and ubuntu will automatically replace that symbol with your username and move into that folder.

after you download the plug in open your home folder and in nautilus press the "CRTL+H" (the letter H; this lets you see hidden folders with configurations for ubuntu and some of your programs) then just look for ".gnome2" in your home directory.

---

### Post by joedoe47 on 2010-07-09
> **Moriarty123456 said:**
> Just If anyone else is interested The Rhythmweb page says one should enter  " http://your-machine-name.local:8000" into safari on the iPhone, but I'm stuck at another noob question !!! - how do i find my machine's name...!

:D

press "ALT+F2" and type "gnome-system-monitor" then under "System" the name in bold is your machine name

---

### Post by Moriarty123456 on 2010-07-09
Thanks Kahn!

I tried robert-laptop and it came up! True - I can;t make it work but the interface is there! This is progress!

Thanks again.

---

### Post by Moriarty123456 on 2010-07-09
WHOOOOOOP! Whhhooooop!

It's playing! It's missing functionality like you have to start the playlist at the laptop, but once it's going you can control it. Also the playlist isn;t on the iphone screen. But it goes!

Currently listening to The Doors - Riders on the Storm...:-)

Thanks All, for all your help.!

---

### Post by SKhan on 2010-07-10
> **Moriarty123456 said:**
> Thanks Kahn!

I tried robert-laptop and it came up! True - I can;t make it work but the interface is there! This is progress!

Thanks again.

joedoe47 told you a method of how to know you computer name.
there is another method as well. just launch terminal. the first line that appears in terminal contains your computer name after the @ sign.
for example sk@sk-desktop
sk before @ is my user ID
and sk-desktop after @ is my computer name.

---

### Post by SKhan on 2010-07-10
> **Moriarty123456 said:**
> WHOOOOOOP! Whhhooooop!

It's playing! It's missing functionality like you have to start the playlist at the laptop, but once it's going you can control it. Also the playlist isn;t on the iphone screen. But it goes!

Currently listening to The Doors - Riders on the Storm...:-)

Thanks All, for all your help.!
i think you should also post your problem at [http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote)
may be someone might be of help. It seems that now it's either an iphone issue, or rhythmote lack the functionality you desire.

also scroll down [http://www.joaomak.net/projetos/rhythmote](http://www.joaomak.net/projetos/rhythmote)
and read the comments.

---

### Post by keithspg on 2011-01-25
If you want functionality, try this one:
[https://bitbucket.org/jimcerberus/rhythmweb/wiki/Home](https://bitbucket.org/jimcerberus/rhythmweb/wiki/Home)

---

