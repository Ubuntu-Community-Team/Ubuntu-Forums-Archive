---
title: "Trying to learn command line from book - on cd command"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-04-12
Hi,

Ok - I just know this is going to sound really, really pathetic, but I need a little help to get over the hump on something really simple.

I'm working through Ubuntu Unleashed 5th and am in the chapter "Command Line Quickstart." Right now, I'm trying to use the cd command to navigate my files. I thought the cd command allows you to navigate into a sub directory (sorry if I'm using windows terminology here). In other words a folder inside a folder inside a folder, etc (for example).

The example the book gives seemed pretty straight forward but when I tried this on my own system (using an actual folder/ folders on my system as my example) things really didn't work as I expected. Now, normally, I wouldn't come here and post on something I really think I should be able to figure out on my own but I've messed around with this for way too long now.

I Don't know what I'm missing here. I can get into my Desktop or any other main folder that is in my hone folder but I can't get past that (except once and the way that worked was odd and made me think there was something wrong with the system). I also know how to use the ls command to show me what is in the folder (no problems there). So I can type cd Desktop and get into my Desktop folder but that's where things break down. I've also chosen several different folders in the course of time to try to get to (sub folders I mean) but encounter the same obstacle.

Can someone please help me? Can someone correct my work or something? I've attached a document with my latest terminal session pasted in there so you can see what's going on and maybe help me understand what I'm doing wrong.

Thanks a whole bunch guys.

Sincerely,
Jake
:(

--------------------------------

PS: I did notice that I had not written out the file name correctly most of the way through this but If you look I did fix that in the very last line and still got an error.

Thanks

---

### Post by earthpigg on 2011-04-12
try doing it like this:

```
cd ./subdirectoryname
```

instead of:

```
cd /subdirectoryname
```

---

### Post by ClientAlive on 2011-04-12
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /Job Leads
bash: cd: /Job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./Job Leads
bash: cd: ./Job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$

------------------------------------------------------------------------

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /jobleads
bash: cd: /jobleads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./jobleads
bash: cd: ./jobleads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /job leads
bash: cd: /job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./job leads
bash: cd: ./job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd Desktop
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ ls
Job Leads                 Scratch.odt
MyNewResume.odt           TerminalSession_AttemptToUse_cd_Comnand.odt
Nero Linux 4.0.0.0 x86    Useful Information About Linux
ResumeLayout_Example.gif
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ 

See: "Job Leads" is a folder on my desktop. ls shows it there.

---

### Post by uRock on 2011-04-12
Try ```
cd ~/Desktop/Job\ Leads
``` You need "\" before the space in order to tell bash to ignore the space.

---

### Post by spillin_dylan on 2011-04-12
You definitely need to escape the 'space' character, as bash is looking at two different arguments there.  Try either:

```
cd ./Job\ Leads
```
or
```
cd ./"Job Leads"
```
or best yet,

```
cd ./Jo<tab key for autocompete!>
```

---

### Post by ClientAlive on 2011-04-12
Are you guys messing with me or something? I mean, I know this is pretty stupid to get stuck on, but I'm trying all the things you mention and getting nowhere. I mean, I'm just trying to learn Linux.

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./ Job Leads
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./"Job Leads"
bash: cd: ./Job Leads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./Job\ Leads
bash: cd: ./Job Leads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./JobLeads
bash: cd: ./JobLeads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd Desktop ./Job Leadsclientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ ls
Job Leads                 Scratch.odt
MyNewResume.odt           TerminalSession_AttemptToUse_cd_Comnand.odt
Nero Linux 4.0.0.0 x86    Useful Information About Linux
ResumeLayout_Example.gif
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$

---

### Post by 5149.5 on 2011-04-12
> **ClientAlive said:**
> clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /Job Leads
bash: cd: /Job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./Job Leads
bash: cd: ./Job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$

------------------------------------------------------------------------

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /jobleads
bash: cd: /jobleads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./jobleads
bash: cd: ./jobleads: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /job leads
bash: cd: /job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ./job leads
bash: cd: ./job: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd Desktop
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ ls
Job Leads                 Scratch.odt
MyNewResume.odt           TerminalSession_AttemptToUse_cd_Comnand.odt
Nero Linux 4.0.0.0 x86    Useful Information About Linux
ResumeLayout_Example.gif
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ 

See: "Job Leads" is a folder on my desktop. ls shows it there.


When a file name or directory has spaces in it, you need to put quotes around the name. Job Leads is interpreted as Job. 'Job Leads' is something different.

---

### Post by spillin_dylan on 2011-04-12
Okay, maybe I'm not in any shape to be giving Linux advice, but I have a few other suggestions:

```
cd "Job Leads"
```
```
cd Job\ Leads
```

I'm sure tab-completion should work for you, but if you haven't got to that chapter yet, then I won't spoil it for you!!  ;)

Edit:

And remember; Linux is Case Sensitive, so "job leads" is different from "Job Leads" which is different from "Job leads" which is different from "jOB lEAdS"

---

### Post by mastablasta on 2011-04-12
> **ClientAlive said:**
>  
[EMAIL="clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$"]clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$[/EMAIL] cd ./"Job Leads"
bash: cd: ./Job Leads: No such file or directory
[EMAIL="clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$"]clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$[/EMAIL] cd Desktop ./Job Leadsclientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop$ ls
Job Leads Scratch.odt

 
 
try 
 
cd /"Job Leads"

---

### Post by ClientAlive on 2011-04-12
Here is a quote from Ubuntu Unleashed 5th (p. 62). What I see is a cd followed by a space a forward slash then the file name (no space) another forward slash then the file name 

"Navigating Through the File System

Use the cd command to navigate the file system. This command is generally used with a
specific directory location or pathname, like this:
matthew@seymour:~$ cd /etc/apt/"

I've about had it with this stuff guys. This is insane. No offense - I do appreciate your help. Just I've been trying every possible combinations: Capitals in the names, no capitals, spaces, no spaces, slash at the end, no slash at the end, you name it! I've tried everything you both have mentioned and no luck. I've been pasting these things into my replies so if what I put in there is not correct it is obvious for anyone who knows to see.

I'm getting frustrated with this. I'm not pasting every time I go into terminal and try something but I am dong it. I tried the exact example in the book "cd /etc/apt/" and it seemed to take me there (I think). I don't understand then what the difference is between "cd /etc/apt/" and "cd /Desktop/Job Leads/" Same format, exactly the way the folders are named. If I can't get this I might as well just hang it up - right?

Jake

---

### Post by ClientAlive on 2011-04-12
Ok. Got it. Thanks a bunch.

So then, why doesn't the book show the quotation marks. Is it telling me incorrect information? Can I trust it to read another 600 pages and expect to learn anything?

Is there another way of doing it that is closer to what the book seems to be showing? A way that does not involve quotation marks?


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd  Desktop/"Job  Leads"clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop/Job  Leads$ ls
Administrative  Customer Service  Receptionist
Communications  Production        Technical
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop/Job Leads$ 
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop/Job Leads$ ls
Administrative  Customer Service  Receptionist
Communications  Production        Technical
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~/Desktop/Job Leads$ cd
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd Desktop

-----------------------------------

Ok. I'm getting the hang of it. It was me. I was not noticing certain, fine details. Like how you have to fist specify home using tilde (or, I imagine, any of the other ways to specify the home directory). I'm also learning that once you get part way down the directory you can just go to a next folder by just typing cd name of next folder. Now I need to learn to back up one level at at time and other stuff. I feel like an idiot with this stuff. This should be very easy to grasp. Back to the book I guess.

Thanks a lot for your help

---

### Post by earthpigg on 2011-04-12
linux is very cAsE sensitive and very s p a c e sensitive.

the book is not misleading you, it just didn't take into account that non-nerds (ie: normal people) sometimes put spaces in folder and file names.

if other things like this come up, don't spend more than 5 minutes with it -- as soon as you get frustrated, stop and make a thread on ubuntuforums.org. 

linux nerds generally make everything lowercase and not have spaces. it actually bothers me a little bit that my home folder in ubuntu has a "Downloads" folder instead of a "downloads" folder. why create an extra keystroke for me?!


edit: 

to maintain current directory-
```
cd .
```
to go back one level-
```
cd ..
```
to go back two levels-
```
cd ...
```

(unix/linux starts counting at zero, not at one. if you put an apple in front of unix, unix will tell you that you have exactly 0 apples and as far as it is concerned, it will be absolutely correct. if you put a pair of apples in front of it, it will tell you that you have 1 apples.)

---

### Post by ClientAlive on 2011-04-12
> **earthpigg said:**
> 
edit: 

to maintain current directory-
```
cd .
```to go back one level-
```
cd ..
```to go back two levels-
```
cd ...
```(unix/linux starts counting at zero, not at one. if  you put an apple in front of unix, unix will tell you that you have  exactly 0 apples and as far as it is concerned, it will be absolutely  correct. if you put a pair of apples in front of it, it will tell you  that you have 1 apples.)

Splendid!! I also found, through experimentation, that you can go back one level by typing out the whole string again less the folder you are in but that seems like the long hard way to do it.


> **earthpigg said:**
> 
linux nerds generally make everything lowercase and not have spaces. it  actually bothers me a little bit that my home folder in ubuntu has a  "Downloads" folder instead of a "downloads" folder. why create an extra  keystroke for me?!



Well if that's how everyone is doing it they must have figured something out about doing this stuff. I suppose I should get in the habit of using that as my naming convention too then.

Thanks.

Just past 2 am here. Gotta crash. Catch you on the flip side earthpigg.

Jake

-------------------------

So if a person uses all lower case and no spaces - if they need to use more than one word in the file name this could become hard to read/ understand. I can't think of a good example but it just seems like that could become an issue with a long file name that is something you came up with/ thought of. How do you deal with that? Just get used to it? What about using underscores to separate words? It wouldn't surprise me if the underscore meant something to linux too.

---

### Post by oldos2er on 2011-04-12
The Tab key is your friend. Type **cd J[Tab]** and let the shell do the dirty work for you. (Don't type the brackets in my example, just Tab.)

---

### Post by el_koraco on 2011-04-12
> **ClientAlive said:**
> What about using underscores to separate words? It wouldn't surprise me if the underscore meant something to linux too.

```
mreto@MrEto:~$ mkdir c_d
mreto@MrEto:~$ cd c_d
mreto@MrEto:~/c_d$ cd

```:D

---

### Post by safarin on 2011-04-12
> **oldos2er said:**
> The Tab key is your friend. Type **cd J[Tab]** and let the shell do the dirty work for you. (Don't type the brackets in my example, just Tab.)

Yes.. Tab can be your best friend for auto-completion of the folder or file.. So you can avoid typo error..

If there are more than one file/folder that share the same alphabet. 
Example: Jack.odt and John.odt,
J<Tab keystroke> , this tab will not auto-complete. You can check what been shared with this J by double "Tab" the keyboard. To complete this you can continue to type o and tab again.. Jo<Tab keystroke>.. then you will get auto-completion words.

---

### Post by idoitprone on 2011-04-12
remember, when naming files try to use only these characters:  letters, numbers, dashes, underscore,  or periods. So when you try to read a file, you dont need to backslash or quote it it. Ex. $ cd Program\ Files or use cd "Program Files"


Bash has so many special parameters and variables, it is best that you do accidentally do something
Do not follow windows way of naming things ok, less hassle on command line

---

### Post by ClientAlive on 2011-04-12
Holy cow guys!! Wow! That's some good stuff there. Like . . . fer sure!  :p

> **el_koraco said:**
> ```
mreto@MrEto:~$ mkdir c_d
mreto@MrEto:~$ cd c_d
mreto@MrEto:~/c_d$ cd

```:grin:

??

1) Making a directory named "c_d"
2) Going to that directory
3) going back home from that directory

But how would I delete that directory? Oh, well I guess i could go into my home folder and delete it the gui way. Never mind.

thx bud!

[SIZE=1]
[/SIZE]> Bash has so many special parameters and variables, it is best that you do accidentally do something
 Do not follow windows way of naming things ok, less hassle on command line

Do you mean "do accidentally" or don't accidentally?

     [SIZE=1][/SIZE]> **oldos2er said:**
> The Tab key is your friend. Type **cd J[Tab]** and let the shell do the dirty work for you. (Don't type the brackets in my example, just Tab.)

> **safarin said:**
> Yes.. Tab can be your best friend for  auto-completion of the folder or file.. So you can avoid typo error..

If there are more than one file/folder that share the same alphabet. 
Example: Jack.odt and John.odt,
J<Tab keystroke> , this tab will not auto-complete. You can check  what been shared with this J by double "Tab" the keyboard. To complete  this you can continue to type o and tab again.. Jo<Tab  keystroke>.. then you will get auto-completion words.


[SIZE=1] Neat! Saves a little time there.
[/SIZE]
[SIZE=1]I wanna learn all this stuff. I want to make sure I don't skip anything before jumping ahead though too. Great tips guys.

Thx
[/SIZE]

---

### Post by Vaphell on 2011-04-12
> Neat! Saves a little time there.
saves a lot of time when you know your way around your directories well and type these spells almost subconciously :) you can get anywhere in 3 seconds

to delete the directory use
```
rmdir <dir_name>
```


general advice: as a rule of thumb test each new command with **--help** parameter, more often than not it will spit out available options

---

### Post by earthpigg on 2011-04-12
> **ClientAlive said:**
> 
So if a person uses all lower case and no spaces - if they need to use more than one word in the file name this could become hard to read/ understand. I can't think of a good example but it just seems like that could become an issue with a long file name that is something you came up with/ thought of. How do you deal with that? Just get used to it? What about using underscores to separate words? It wouldn't surprise me if the underscore meant something to linux too.

in practice, i don't feel it has encumbered me any.

my movie and music collection, for example, have all sorts of spaces and upper case letters in file names... i also don't work with them from the command line, though, so it isn't problematic.

and if i am going to work with one of them from the command line, i generally rename it from "Complex Movie Title With Crazy Spaces.avi" to "input.avi", do whatever I am going to do with it, have the final product be "output.avi", and then rename both from "input.avi" and "output.avi" to "Complex Movie Title With Crazy Spaces.avi" and "Complex Movie Title With Crazy Spaces - Android Ready.avi" using GUI tools at the end. that is just my preference, though.

---

### Post by K_45 on 2011-04-12
Rather than that book, check here first:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Then use the commands whatis and whereis if you need a quick description of what a command does or where it is. Remember the man pages too. Just enter man ls for a detailed description of the command. Q to quit.

---

### Post by d3v1150m471c on 2011-04-12
checkout "Linux phrasebook" by scott granneman. short, sweet, powerful...and it fits in your pocket :)

---

### Post by el_koraco on 2011-04-12
> **ClientAlive said:**
> 
??

1) Making a directory named "c_d"
2) Going to that directory
3) going back home from that directory

But how would I delete that directory? Oh, well I guess i could go into my home folder and delete it the gui way. Never mind.

thx bud!

[SIZE=1]
[/SIZE]

no need for the gui really. 

```

mreto@MrEto:~$ mkdir c_d
mreto@MrEto:~$ ls
Audiobooks  Desktop    Downloads         Music     Podcasts  Templates   Videos
**c_d**         Documents  examples.desktop  Pictures  Public    Ubuntu One
mreto@MrEto:~$ rm c_d
rm: cannot remove `c_d': Is a directory
mreto@MrEto:~$ **rmdir c_d**
mreto@MrEto:~$ ls
Audiobooks  Documents  examples.desktop  Pictures  Public     Ubuntu One
Desktop     Downloads  Music             Podcasts  Templates  Videos
mreto@MrEto:~$ 

```but you can use it, for sure.

---

### Post by jtarin on 2011-04-12
Here's a quick reference to keep handy.Fullsize zipped. I used to use it as a wallpaper.

---

### Post by ClientAlive on 2011-04-12
> **K_45 said:**
> Rather than that book, check here first:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Then use the commands whatis and whereis if you need a quick description  of what a command does or where it is. Remember the man pages too. Just  enter man ls for a detailed description of the command. Q to  quit.



Wow!! Man pages rock! There's a book right in this thing and you know you can trust it! Betw. man pages, whatis is and whereis you're pretty well covered. I just pulled up man pages for every command I know of so far (even sudo - the super user). Omg I wish you guys could see the smile on my face right now. I mean there are tears in my eyes I'm so happy. I'm gonna love this ****!! Oh yeah!


> **el_koraco said:**
> no need for the gui really. 

```

mreto@MrEto:~$ mkdir c_d
mreto@MrEto:~$ ls
Audiobooks  Desktop    Downloads         Music     Podcasts  Templates   Videos
**c_d**         Documents  examples.desktop  Pictures  Public    Ubuntu One
mreto@MrEto:~$ rm c_d
rm: cannot remove `c_d': Is a directory
mreto@MrEto:~$ **rmdir c_d**
mreto@MrEto:~$ ls
Audiobooks  Documents  examples.desktop  Pictures  Public     Ubuntu One
Desktop     Downloads  Music             Podcasts  Templates  Videos
mreto@MrEto:~$ 

```but you can use it, for sure.

Awesome! So there's a difference between rm and rmdir. About dot com says its to "remove files or directories" but when you did it el_koraco t told you it wouldn't remove it because it was a directory. Hmm.

[http://linux.about.com/od/commands/l/blcmdl1_rm.htm](http://linux.about.com/od/commands/l/blcmdl1_rm.htm)

Time to go play w/ Linux again.

Jake

---------------------------------------------

Hmmm . . .  

Please correct if any of my assumptions/ concepts are wrong but I get the idea that the following things are the case with Linux:

One starts out in their home directory when they open the terminal. Apparently the home directory is not the highest level though. That's the only thing I could come up with to explain why I could go to cd /etc/apt/ (this was the example given in Ubuntu Unleashed) but not cd /Desktop/Job Leads/   I mean, I did figure out how to navigate to that folder but it didn't follow the format of the example.

So I got this idea that the home directory is one, among others, that are somewhere under root (how far under root I don't know) and that wherever /etc/apt/ is is in a separate line than the home directory. Does it make sense to try and use that word "line"? I don't know. Well so if this is right so far then I think that when you use mkdir you, by default, create a folder within the home dierectory (or maybe on a lower level if that's where you've gone to/ are, a folder or folders down into it but not above it). So, I'm sure you can do just about anything you want with Linux but I got to thinking about what it would mean to create a directory right under root (or another way or thinking of it - next to the home directory) and how that might happen. Maybe if one was logged in as root and they used mkdir that is what would happen. I don't know. I'm not saying I want to actually do it I'm just thinking about how the entire Linux might look in a diagram. You know?

Anyway, back to playin' round' with this thing. Just some thoughts I was having. Don't know if their right or not.

Jake

---

### Post by rosencrantz on 2011-04-12
Just to add some confusion again - you are approaching alarming levels of clarity:
rmdir works only with empty directories.
If there is something in it (any number of subfolders and files), you have to use rm -R <directoryname> (without <>, of course...)
The -R options stands for recursive.
On the whole, working through a book is probably not a bad idea. There is tons of help on the net, but lots of it is reference and not tutorials. I wouldn't know of a comprehensive online Ubuntu for Beginners. Also, you have to know what to look for.

---

### Post by earthpigg on 2011-04-12
> Apparently the home directory is not the highest level though.

correct. and, actually, you don't start in the home directory... you start in ***your*** home directory.

```
/home/ClientAlive
```
not
```
/home
```

/home/ClientAlive can also be expressed as ~. that is why it is mildly funny when some ubuntuforums.org users list their 'location' as '~' in their ubuntuforums.org profile (on the left, below the pig picture, were it says "location". if i changed it from California to ~, it would be good for a chuckle or two from someone in your shoes, just learning this stuff)

try it. go to some other crazy directory, and type

```
cd ~
```

for security reasons, stuff in ~ is the only stuff that ClientAlive can change or modify without invoking sudo. by default, additional users you create on that system will not be able to invoke sudo, limiting them to their own ~. handy for librarians, trying to prevent library-goers from accidentally damaging the computer. librarygoer can break the system for librarygoer, but not the system itself. all our librarian needs to do is invoke sudo to delete everything in /home/librarygoer/, and librarygoer's settings will be restored to default.

down the road (and trust me, this will happen), you will someday encounter some form of permissions problem. something in your ~ will be marked as owned by another user or even root. you will have to invoke sudo to clarify who owns that file or folder.


EDIT: also, this obligatory joke...

```
[chris: ~]$ man woman
No manual entry for woman
[chris: ~]$
```

"well, it looks like we're still screwed."

EDIT2: made some minor additions in body of post.

---

### Post by oldos2er on 2011-04-12
Everything starts at / which is called root.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Also, everything outside of your home folder requires admin privileges if you want to make alterations to it in any way.

---

### Post by akakingess on 2011-04-12
My favorite cli shortcut is the up arrow, it will retype out the last command that you entered, so if you entered everything correctly except the very end, you can just press the up arrow and start deleting/correcting from the end of the line ;)  Good Luck and Have Fun!!!

---

### Post by JKyleOKC on 2011-04-12
You're very much on the right track now.

When you type a path (such as /etc/apt) and it begins with a "/" then it's an "absolute path" but if it does not, it's a "relative path." The difference is that an absolute path begins at the very top, while a relative path begins in the current working directory -- which is wherever you happen to be when you issue the command.

All Linux file systems start with a "root" directory that's named simply "/" but you hardly ever do anything in that directory. It's primarily a container for a second level of directories, which include bin, etc, home, usr, and var among others. You can get the whole list by the command "ls /" and as you can see, it's a pretty short list. The names are pretty well standardized by convention. Not all of them are intuitive, though. The /etc directory holds most of the system-wide configuration files. Executables are in /bin but most of those installed by Ubuntu are in /usr/bin instead. System programs are in /sbin or /usr/sbin.

Home directories are in /home, and each user has his own home directory, named the same as the login ID. When you log in, that's where you land initially. You own that directory and most if not all of the files and subdirectories in it, but are not the owner of the other directories and files on the drive even though you own the system. Those other directories and files are for the most part owned by the super user, "root" by name, and you must use the sudo command to manipulate them.

Hope this helps you confirm your discoveries. The organization scheme is really quite simple, but amazingly powerful!

---

### Post by rosencrantz on 2011-04-12
Regarding your last question:
You got to the relative/absolute directory question.
The Linux tree looks more or less like this:
The top level is just a slash: /
It has lots of branching subdirectories, e.g.
/home
/usr
/etc
Your home directory is in /home/yourusername.
There are to ways to specify paths for mkdir (or any other command)
1) absolute, with a preceding slash:
mkdir /home/yourusername/new_directory
This works whichever directory you cd'ed into.
2 )relative to the directory you are in right now. So, if you start your terminal in home (~):
mkdir new_directory
produces the same directory. If you have cd'd into dir1 by now, you will get
/home/yourusername/dir1/new_directory
with the same command.
The tilde '~' is an abbreviation for the absolute path /home/yourusername
So, if you do mkdir ~/new_directory, it's equivalent to variant 1) and works from everywhere in the system.
If you are unsure where you are, use the pwd (print working directory) command to find out.

---

### Post by earthpigg on 2011-04-12
> librarygoer can break the system for librarygoer, but not the system itself. all our librarian needs to do is delete everything in /home/librarygoer/, and that user's settings will be restored to default.

quick addendum to that - if you ever mess up gnome in such a way that it will take more than an hour to trouble shoot and fix, there is a good chance your time would be better spent by

a) copying your personal files/data/bookmarks/etc off of ~, just in case you make a typo
b) delete all the dotfiles inside ~
c) log out, and back in

there, default gnome and default every app you have installed.

you can use intution and your brain to limit (b) so that you don't need to literally delete *every* dotfile.

but, yeah. check out dotfiles. those are fun.

put ssh on your "must explore" list, too.

:P

---

### Post by K_45 on 2011-04-12
GNOME should also be restored from this:

[http://library.gnome.org/admin/system-admin-guide/stable/gconf-28.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-28.html.en)

---

### Post by mikodo on 2011-04-12
Hi, 

I am beginning to study the Command Line also.

Here is a free e-book (a tutorial) I recommend: ***"The Linux Command Line"*** in PDF, by William E. Shotts:

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

His Website:

[http://linuxcommand.org/](http://linuxcommand.org/)

Good Luck!

:)

---

### Post by ClientAlive on 2011-04-12
This stuff you guys are saying is giving me all kinds of ideas! Wow! I'll come back in a bit here and share a few of them. Gotta break away and make a store fun for some munchies (read, chocolate).

:D

----------------------------------

Well I though I had some good ideas but then after I though about it for a while I realized that the one of them (I think) has already been done and even taken a step further. I think.

I'm sure the other one's been done too but that wouldn't stop me from using it.

Basically I was thinking about security. Computer security. With the one thing I though. If the names of those directories in Root are so standard, what would happen if someone changed the name of one of them to some arbitrary thing? Well it would probably screw the whole o/s up, the whole system. Then I though, yeah, but then what if that person wrote some simple program that went through the entire system and changed the all the occurrences of the name so it matched the new name? Almost like a find and replace kinda deal - so that all the programs and components that depend on that file being named what it was, now just looked for the new name. Why? Because if changing the file names makes things within the system not work then it would also make things outside the system not work - including people. People who may mean you harm. But if they don't know what the file names are when they expect it to be some standard name they're just stuck - right?  Don't they already do something like that though? On top of it they encrypt the file names?

Then I got to remembering how I read somewhere that Linux is very friendly to being split up onto different ;partitions and I though It might be good security (depending on the situation/ use/ environment of the machine) to put every different user on thier own partition and that separate from the rest of the o/s. Or maybe better than that, and more simple, to separate the rest of the o/s from the users and have the administrator on his own partition. Or, If it was a situation where security is a sensitive issue and there were groups who have different levels of clearance perhaps there should be a partition for each clearance level.

If these two were combined (partitioning and changing file names+encryption of those names) and all that on top of the regular security Linux has natively - one might think he'd have something almost impenetrable!

I don't know though. Probably just a bunch of garbage anyway. Guess it's nice to dream about things but there's still a need to buckle down and get some good foundational learning under my belt so I can understand the more lofty things. Just that reading your guy's posts makes me think about so much.

Thanks for listening to me ramble ya' all.

Jake

----------------------------------------------------------

Ok, probably getting too carried away with this post but I just learned something really, really cool and I'm too excited not to put this in here. Probably someone (or even a few people) told me this somewhere in this thread but I forgot it. So I open up my home folder through the gui to find some things to try and get to via cli. Messed around a bit with a couple things - no big deal. Then I see this thing called "File System" and I though - cool - I'll go after that one! Well, at first, I though it was just another folder in my home folder. Oh, I think I'm supposed to be calling those directories - no? So anyway, I thought is was the same as "Downloads" or "Music" or whatever else in there. Well, long story short - after some trial and error - I find out that "File System" is not even really a name you can use in the terminal (well maybe there's a way but I don't know it yet). So I find out that "/" is "File System" Now I remember several people telling me that "/" is root, so "File System" must be right under root (one of the main directories and somehow separate from my home directory, "~"). Now I think I'm seeing what was meant about absolute and relative paths. It makes sense.

---

### Post by JKyleOKC on 2011-04-13
> **ClientAlive said:**
> So I find out that "/" is "File System" Now I remember several people telling me that "/" is root, so "File System" must be right under root (one of the main directories and somehow separate from my home directory, "~").Close, but no cigar. "File System" **IS** "/" rather than a separate directory. Consider how puzzled you would be to find something called "/" in your "Places" window, and you'll understand why a more descriptive name was substituted there.

Linux, in all its versions, is based upon Unix, which was the property of AT&T and not available to the general public. Unix, in turn, was a sort of clone of an even older mainframe system called MULTICS that was developed at MIT by a joint effort of G-E and Bell Telephone Labs back in the mid-1960s. 

In those days, a 300-baud modem was considered to be high speed, and most i/o was done via clunky teletype machines. The whole emphasis was on cutting keystrokes to a minimum -- that's why the command is "ls" instead of "list," and "cd" instead of "change_directory." Thus the top-level directory became simply "/" instead of "root."

---

### Post by idoitprone on 2011-04-13
> **ClientAlive said:**
> 

Do you mean "do accidentally" or don't accidentally?

[/SIZE]

I;m an idoit. I fail on grammer. If you wanna learn to use a terminal, I will avocate for mistakes. Since ther more mistakes you make the more you learn about the operating system. I am not sure if I can say yhe same for windows

people who will try
```
 rm -r * 
```

will never do it again.

The star means everything in the directory and -r parameter is recursive.
There are many ways to srew up your system

Remember the this unix saying: "unix never say please"
[http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy)
If you are going to screw up your system, the computer do not care and lets you do it lol. It will never ask questions.

---

### Post by The Cog on 2011-04-13
The real power of the command line comes with knowing a few of the command-line tools, and particularly knowing how to chain them so that the output from one tool becomes the input of the next tool. But that can wait. 

I must pick up one error I saw earlier - "cd ..." doesn't take you up two directory levels (it did on Netware drives though). You need to use "cd ../.." to go up 2 levels, ../../.. for 3 levels etc.

And in case you missed it, just "cd" with no arguments takes you to your home directory.

---

### Post by earthpigg on 2011-04-13
> **The Cog said:**
> 
I must pick up one error I saw earlier - "cd ..." doesn't take you up two directory levels (it did on Netware drives though). You need to use "cd ../.." to go up 2 levels, ../../.. for 3 levels etc.


you are correct, my mistake. i've been known to mix up stuff in my own .bashrc with standard stuff.

```
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

```

---

### Post by rosencrantz on 2011-04-13
Regarding your security discourse:
That is pretty much how it's done.
It is very good practice to move your home directory (and everybody else's) to a separate partition and mount it as /home
Mostly not for security concerns, but to keep your personal settings unchanged when you re-install and as a partial safeguard against disk crashes.
In practice, this gives you also physical separation of permission areas, as everything outside your home partition should be read-only for you. (though, at some point you will probably encounter the password-protected sudo command, which gives you temporary root (superuser) permissions).
However, linux handles access permissions on a per file/per user or group basis, and it's pretty good at that - an intruder never has more permissions than the application/user session he is piggybacking on.

---

### Post by ClientAlive on 2011-04-13
> **JKyleOKC said:**
> Close, but no cigar. "File System" **IS**  "/" rather than a separate directory. Consider how puzzled you would be  to find something called "/" in your "Places" window, and you'll  understand why a more descriptive name was substituted there.



clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/$ ls
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var


Sure enough! There's my home directory under "/" ! Lol. I guess everything is under "/" then. That's my entire compter there!  :)  

Funny thing though - when I think of the term "File System" I can easily think of it as an action statement. Yet it really is more like a noun. It doesn't do anything except sit there and all the stuff (programming scripts or whatever) that makes it do anything is actually inside it or contained withing it. Hmm . . . getting too philosophical here I guess. I mean, its not a living thing right. It's just a piece of plastic and metal and whatever it does was created by someone and is just text in files. Lol.

So then is File System = to Root or is it under Root? I mean, Root must be a thing in an of itself or it could not exist in the system - unless they just chose to display the name differently in places and that's all it amounts to.


                                   Root                                   

                               File System

                            Everything Else


??  OR  ?? 


File System (which 'is' Root)

Everything Else

> **JKyleOKC said:**
> Linux, in all its versions, is based upon Unix, which was the property  of AT&T and not available to the general public. Unix, in turn, was a  sort of clone of an even older mainframe system called MULTICS that was  developed at MIT by a joint effort of G-E and Bell Telephone Labs back  in the mid-1960s. 

In those days, a 300-baud modem was considered to be high speed, and  most i/o was done via clunky teletype machines. The whole emphasis was  on cutting keystrokes to a minimum -- that's why the command is "ls"  instead of "list," and "cd" instead of "change_directory." Thus the  top-level directory became simply "/" instead of "root."



What a thrill to learn that!


> **idoitprone said:**
> IIf you wanna  learn to use a terminal, I will avocate for mistakes. Since ther more  mistakes you make the more you learn about the operating system. I am  not sure if I can say yhe same for windows

Makes sense. Great way to look at it.


> **idoitprone said:**
> people who will try
```
 rm -r * 
```will never do it again.

The star means everything in the directory and -r parameter is recursive.
There are many ways to srew up your system

Remember the this unix saying: "unix never say please"
[http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy)
If you are going to screw up your system, the computer do not care and lets you do it lol. It will never ask questions.



Anyone just learning Linux and reading this thread: Please don't actually run that code. I mean, you can if you want to - but understand what's going to happen if you do.

Sorry idiotprone - had to say that.  ;)


> **The Cog said:**
> I must pick up one error I saw earlier - "cd ..." doesn't take you up  two directory levels (it did on Netware drives though). You need to use  "cd ../.." to go up 2 levels, ../../.. for 3 levels etc.



+1  Yeah I tried "cd ..." and all it did was tell me 'no such file or directory\'


> **mikodo said:**
> Hi, 

I am beginning to study the Command Line also.

Here is a free e-book (a tutorial) I recommend: ***"The Linux Command Line"*** in PDF, by William E. Shotts:

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

His Website:

[http://linuxcommand.org/](http://linuxcommand.org/)

Good Luck!

:smile:



Got that book. Looks really good. Much more what I'm trying to get into right now than Ubuntu Unleashed. Suppose I'll work through that and kinda bounce back and forth between the two. Ubuntu Unleashed can still be a good springboard for me into more in depth study.

---

### Post by el_koraco on 2011-04-13
> **ClientAlive said:**
> 
Awesome! So there's a difference between rm and rmdir. About dot com says its to "remove files or directories" but when you did it el_koraco t told you it wouldn't remove it because it was a directory. Hmm.

[http://linux.about.com/od/commands/l/blcmdl1_rm.htm](http://linux.about.com/od/commands/l/blcmdl1_rm.htm)

Time to go play w/ Linux again.

Jake

---------------------------------------------


Anyway, back to playin' round' with this thing. Just some thoughts I was having. Don't know if their right or not.

Jake

Aah, well, you can't know everything from the get go, can you? rmdir, as was pointed out, only works with empty directories. If there are further files or directories , you have to add the -r option. That stands for "recursive", meaning the rm command will not delete both the files and subdirectories, as well as the directory itself. check it out: 

```
mreto@MrEto:~$ mkdir c_d
mreto@MrEto:~$ cd c_d
mreto@MrEto:~/c_d$ mkdir ab
mreto@MrEto:~/c_d$ ls
ab
mreto@MrEto:~/c_d$ cd
mreto@MrEto:~$ rm c_d
rm: cannot remove `c_d': Is a directory
mreto@MrEto:~$ rmdir c_d
rmdir: failed to remove `c_d': Directory not empty
mreto@MrEto:~$ rm -r c_d
mreto@MrEto:~$ ls
Audiobooks  Documents  examples.desktop  Pictures  Public     Ubuntu One
Desktop     Downloads  Music             Podcasts  Templates  Videos


```got it? nice. moving on. 

> Hmmm . . .  

Please correct if any of my assumptions/ concepts are wrong but I get  the idea that the following things are the case with Linux:

One starts out in their home directory when they open the terminal.  Apparently the home directory is not the highest level though. That's  the only thing I could come up with to explain why I could go to cd  /etc/apt/ (this was the example given in Ubuntu Unleashed) but not cd  /Desktop/Job Leads/   I mean, I did figure out how to navigate to that  folder but it didn't follow the format of the example.Again, as was pointed out, you don't start at /home, but at /home/ClientAlive. In your specific case, you wanted to go to the Desktop directory in / (root), which isn't there. Not to mention that you didn't put quotes on the directory name :D

> So I got this idea that the home directory is one, among others, that  are somewhere under root (how far under root I don't know) and that  wherever /etc/apt/ is is in a separate line than the home directory. Well, let's not think, let's check it out. 

```
mreto@MrEto:~$ cd /
mreto@MrEto:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  **home**  lib             mnt         root  srv      usr  vmlinuz.old 
```All of these directories are system directories. If you look them up in Nautilus, the file manager, they'll be listed under "File System", only then they're not called directories, but folder. It means the same thing, it's just legacy talk. Linux treats everything as a file, even the CD or USB stick you put in there. Basically, what you see, bin, dev, media, and so on, are directories, which contain subdirectories and files needed to get the OS to run.  

Now, to answer your question about creating directories. You either create further directories based on the one you're already in (like in the example above), or by specifying the path. 

```
mreto@MrEto:~$ mkdir ~/Documents/foo
mreto@MrEto:~$ cd ~/Documents/foo
mreto@MrEto:~/Documents/foo$ 
``````
mreto@MrEto:~$ cd Documents
mreto@MrEto:~/Documents$ mkdir foo
mreto@MrEto:~/Documents$ cd foo
mreto@MrEto:~/Documents/foo$ 
```Let's try to make a document in / (root)

```
mreto@MrEto:~$ cd /
mreto@MrEto:/$ mkdir foo
mkdir: cannot create directory `foo': Permission denied
```Not possible because you don't have the permission to do soo. In Unix terms, I, mreto, am not the owner of the / directory. So what can i do? In Ubuntu, i would use the sudo command. 

```
mreto@MrEto:$ cd /
mreto@MrEto:/$ sudo mkdir foo
[sudo] password for mreto: 
mreto@MrEto:/$ ls
bin    etc         initrd.img.old  mnt   sbin     tmp      vmlinuz.old
boot   foo         lib             opt   selinux  usr
cdrom  home        lost+found      proc  srv      var
dev    initrd.img  media           root  sys      vmlinuz
```Sudo is the command which gives an ordinary user the authority of another user, or the root user. How it can be done is specified in the file /etc/sudoers. By default, Ubuntu systems give the first user the sudo authority, and lock the root account. 

Beware when messing arround with sudo and system files, you can do a lot of damage. Do NOT make typos.

---

### Post by 5149.5 on 2011-04-13
Root is part of the file system. Think of the file system as an upside down tree. The root of the file system is at the top. Everything branches down from there.

---

### Post by K_45 on 2011-04-13
It also follows that a separate root, swap, and home partition is better than a single partition which contains everything. Easier to backup and salvage if one partition is damaged. If the whole disk is damaged, well you have backups don't you?

---

### Post by ClientAlive on 2011-04-13
> **el_koraco said:**
> Again, as was pointed out, you don't start at /home, but at  /home/ClientAlive. :grin:
 
 
Ahh! I see! I don't know why I got so confused about this. Well, I do  now, but it's really stupid on my part. People have been saying what you  did, el_koraco, over and over to me. Guess i had to go in a few  "circles" to get it through my head.


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /clientalive/Desktop/
bash: cd: /clientalive/Desktop/: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /clientalive/Desktop
bash: cd: /clientalive/Desktop: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ~/clientalive/Desktop/
bash: cd: /home/clientalive/clientalive/Desktop/: No such file or directory
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ~/clientalive/Desktop
bash: cd: /home/clientalive/clientalive/Desktop: No such file or directory

Here I thought I was going to find an absolute path to my Desktop. It's  not that one doesn't exist, it's just that I was mistaken about where I  was starting at when I launch the terminal. Again, very stupid on my  part - I've been told.

Besides, there's no practical purpose of using an absolute path to  something under the directory you are already in. What are you gonna do,  tell it to take you out and above where you are then back through where  you are and finally to where you want to go? Silly.


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates

So, as I've been 'repeatedly' told, I'm "in" "home" - that's why "home" does not show up in that list.

_Edit/ Correction:_ /home/clientalive/  not "home" (when the terminal is launched).


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /

I just went up the tree not down - as I had been mistakenly assuming before this.
--------------------------------------------------------------------------------------------------------------------------------

_Comment_: when I took a computer class before in college they told  us that the forward slash meant going down the tree and the back slash  meant going up it. That was Windows though. That mistake has caused me a  lot of grief trying to learn Linux now.
--------------------------------------------------------------------------------------------------------------------------------

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/$ ls
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var

This proves it as I can see that "home", where I was when I opened the terminal, is listed there.


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/$ cd home

Using a relative path I just went into my home folder. (So, really at  this point - I've gone out of home, going up the tree, and then back  into it.)


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/home$ ls
buildd  clientalive

There's clientalive. He's one of the users on this machine. (I gather  that it's possible for other user names to show up in this folder - if I  had created or if I do create other accounts on this computer. Those  user names will correspond to the home directory of each user  respectively - but I don't want to speculate).

--------------------------------------------------------------------------------------------------------------------------------

_Comment:_ Hmm . . . I wonder if "buildd" is where sudo lives? That doesn't make sense though. Or does it?

--------------------------------------------------------------------------------------------------------------------------------


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/home$ cd clientalive

Now I'm in _my_directory. I guess that even though they  call it your home directory "/home/" is still something else - its own  thing - and your home directory is actually _in_ _it_.

--------------------------------------------------------------------------------------------------------------------------------

_Comment:_ So it clientalive just another way of saying home  directory? I wonder if some of these terms are just terms people use  while others are terms the system uses?

--------------------------------------------------------------------------------------------------------------------------------


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates

See! I'm right back where I started. The place that the system puts you  when you open the terminal - and its not at "/" or, another way of  putting it. 'the beginning'. (What I had thought of as the beginning was  as a place not a point in time).


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ~/

I think I just told it to do something backwards. "~" is after "/" not  before. We read from left to right; and, apparently, so does the system.


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates

I guess it just ignored the "/". Maybe because I didn't really specify  the location to go to in a proper way, so it just read the first thing  and ignored the rest (again though, I don't want to speculate).


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ~
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates

compare

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd /
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/$ ls
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var

I was trying a couple things and comparing. Now, finally, it's beginning to sink in. Doh!


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:/$ cd
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ ls
Calibre Library  Documents  examples.desktop       Music     Public     Videos
Desktop          Downloads  Firefox_wallpaper.png  Pictures  Templates

Just another way to say it. I'm back in /home/clientalive/ . Yup! It's still there!  :smile:


clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ cd ~$
bash: cd: ~$: No such file or directory


Experimenting with something different. Asking the computer to tell me  something else about itself, really. If I read between the lines, the  answer it is giving me is: 'there's a difference between a command and a  location - dummy'

--------------------------------------------------------------------------------------------------------------------------------

_Comment:_ On second though, even thought that was my intuition at  first, I'm not sure that is right. Maybe what is right though is that  the $ is clientalive. I don't know.

--------------------------------------------------------------------------------------------------------------------------------



Ok, ok, get it out. Laugh. It's ok - I am. Fact is, as dense as I may  be, I still need to grasp these basic concepts. In fact, I would even go  a step further and say that grasping these basic concepts is critical  to everything else to come.

I'm starting to get it. I'm sure you were all worried about me for a bit there.  :smile:


**el_Koraco**:  I'm sorry buddy. I hadn't read through your entire  post before the lighbulb went off and I started doing that exercise in  the terminal. Then, I wanted to write the things down that I have up to  this point while they were fresh in my head. I left off reading right  where I quoted you at the beginning of this post.

> **el_koraco said:**
> Well, let's not think, let's check it out. 
 
 ```
mreto@MrEto:~$ cd /
 mreto@MrEto:/$ ls
 bin    dev   initrd.img      lost+found  opt   sbin     sys  var
 boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
 cdrom  **home**  lib             mnt         root  srv      usr   vmlinuz.old 
```
 
 
Then I came back and saw that. Home is right there under root in what  you posted (and on your machine too) but I just had to put myself  through all that hassle to figure it out.


> **el_koraco said:**
> Now, to answer your question about creating directories. You either  create further directories based on the one you're already in (like in  the example above), or by specifying the path. 
 
 ```
mreto@MrEto:~$ mkdir ~/Documents/foo
 mreto@MrEto:~$ cd ~/Documents/foo
 mreto@MrEto:~/Documents/foo$ 
``````
mreto@MrEto:~$ cd Documents
 mreto@MrEto:~/Documents$ mkdir foo
 mreto@MrEto:~/Documents$ cd foo
 mreto@MrEto:~/Documents/foo$ 
```
 
 

Finally, things are starting to come across simple and clear. My Linux eyes are beginning to come into focus and I can see.

Two ways to make a directory. Either make it right there where you are  (if that's where you happen to need it) or tell the thing where to make  it (If you don't have any other reason to navigate to where you want it  except to make a directory). Makes sense.


> **el_koraco said:**
> Let's try to make a document in / (root)
 
 ```
mreto@MrEto:~$ cd /
 mreto@MrEto:/$ mkdir foo
 mkdir: cannot create directory `foo': Permission denied
```Not  possible because you don't have the permission to do soo. In Unix terms,  I, mreto, am not the owner of the / directory. So what can i do? In  Ubuntu, i would use the sudo command. 
 
 ```
mreto@MrEto:$ cd /
 mreto@MrEto:/$ sudo mkdir foo
 [sudo] password for mreto: 
 mreto@MrEto:/$ ls
 bin    etc         initrd.img.old  mnt   sbin     tmp      vmlinuz.old
 boot   foo         lib             opt   selinux  usr
 cdrom  home        lost+found      proc  srv      var
 dev    initrd.img  media           root  sys      vmlinuz
```Sudo is  the command which gives an ordinary user the authority of another user,  or the root user. How it can be done is specified in the file  /etc/sudoers. By default, Ubuntu systems give the first user the sudo  authority, and lock the root account. 
 
 Beware when messing arround with sudo and system files, you can do a lot of damage. Do NOT make typos.
 
 
Got ya". As was told to me before, even though I own the system I still  don't automatically have permission to do whatever I want wherever I  want. I can ask for the permission and it'll be given to me, but it's  not just automatic.

You know, last night, I though I thought of a way to log into root. I  didn't want to try it out though since I wasn't sure if I needed to log  back out if it worked and I wouldn't know how to do that (maybe  "exit"?). So I thought that:  "sudo /' would ask me for my password and  then I'd be in root with super user permission and would be able just go  around doing whatever I want in root without typing sudo all the time.  Just a big fat guess though.


> **5149.5 said:**
> Root is part of the file system. Think of the  file system as an upside down tree. The root of the file system is at  the top. Everything branches down from there.
 
 
I think you're referring to


> **JKyleOKC said:**
> So then is File System = to Root or is it under Root? I mean, Root must  be a thing in an of itself or it could not exist in the system - unless  they just chose to display the name differently in places and that's all  it amounts to.
 
 
                                    Root                                   
 
                                File System
 
                             Everything Else
 
 
 ??  OR  ?? 
 
 
 File System (which 'is' Root)
 
 Everything Else
 
 


That


If so, what I guess I was getting at is whether they just played some  kind of computer trickery to make root appear/ be displayed as "File  System" when viewed in the Places pane in your home folder (through the  gui) - or whether there really is two separate things, "root" and "File  System". 

I was also thinking about how I would explain something like that. I  mean, root has to be an actual something on the computer. It isn't just a  concept is it? It's a very real errr directory? The directory of all  directories? The head cheese? And "File System" also has to be something  actual (if nothing more than the words "File System" when you look at  it in Places; and, that, through some fancy script that tells the o/s to  display root as File System when someone looks at it through the gui).  So either there's two actual somethings (root and File System) or root  is just being renamed in some places on the computer. If the latter is  the case then they even had to write some program or script to tell it  to display that way and that file is it's own thing stored on the system  somewhere - under root nonetheless.


Thanks so much for your incredible patience with me guys. I sure appreciate it.

Jake

---

### Post by K_45 on 2011-04-13
Root is the file system. Everything comes off it. You should also note pwd which is print working directory which will tell you where you exactly are. You can also use environment variables to change to some directories i.e. cd $HOME. Here is another useful link:

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

