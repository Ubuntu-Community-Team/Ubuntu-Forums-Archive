---
title: "How to untar.gz and bz2 files easily in terminal"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Mat11 on 2010-07-26
Hi i've spent hours trying to find out how to untar .gz and bz2 files using sudo in terminal and have had no end of error messages.I've read all the files that exist to no avail.I do remember updating sudo recently can anyone help.Have one Hp driver update gz , one game .gz and another game bz2 not mentioned in the software center or games mentioned in synaptic.
Where to i start as i have downloaded the tar files to my documents and need to get games and driver setup and working.
My laptop is an i386 using Ubuntu 9.10
Think i need someone with patience to talk me through.
Thanks Mat

---

### Post by RiceMonster on 2010-07-26
Do not use sudo. It will extract them with root ownership, and you will have to use chown to fix the issue.

You can extract either tar.gz or tar.bz2 with this command:

```
tar xvf filename
```

---

### Post by gandaran on 2010-07-26
> **Mat11 said:**
> Hi i've spent hours trying to find out how to untar .gz and bz2 files using sudo in terminal and have had no end of error messages.I've read all the files that exist to no avail.I do remember updating sudo recently can anyone help.Have one Hp driver update gz , one game .gz and another game bz2 not mentioned in the software center or games mentioned in synaptic.
Where to i start as i have downloaded the tar files to my documents and need to get games and driver setup and working.
My laptop is an i386 using Ubuntu 9.10
Think i need someone with patience to talk me through.
Thanks Mat
well, if you right click the file and choose the extract here option from the drop down menu, have you tried that?  why go to all the trouble using the terminal to unpack files?

---

### Post by Mat11 on 2010-07-26
Thanks for the reply Rice Monster the output of your command was cannot open:no such file or directory. Was trying to start up naev-0.4.2.tar.bz2 so i tried to open up the file on the main desktop and marked the file Game shows no such file .....
Have also unpacked it and tried the read me line in terminal which doesn't work.
Thanks for your help so far

---

### Post by RiceMonster on 2010-07-26
> **Mat11 said:**
> Thanks for the reply Rice Monster the output of your command was cannot open:no such file or directory. Was trying to start up naev-0.4.2.tar.bz2 so i tried to open up the file on the main desktop and marked the file Game shows no such file .....
Have also unpacked it and tried the read me line in terminal which doesn't work.
Thanks for help so far

That means you either aren't in the right directory or you mispelled the file name. Where is this file? If this file is on your desktop, you can do this:
```
tar xvf ~/Desktop/naev-0.4.2.tar.bz2
```

---

### Post by nmaster on 2010-07-26
"cd" into the location of the tar.gz/tar.bz2.  type "ls" to be sure that the you're in the right place. for a gzipped tar: "tar xvzf file.tar.gz" for a bzipped tar: "tar xvjf file.tar.bz2"

when in doubt, read the man page for tar.

---

### Post by Mat11 on 2010-07-26
> **RiceMonster said:**
> That means you either aren't in the right directory or you mispelled the file name. Where is this file? If this file is on your desktop, you can do this:
```
tar xvf ~/Desktop/naev-0.4.2.tar.bz2
```

Have tried the above exactly all i get is no such file or directory - why ?

---

### Post by Mat11 on 2010-07-26
> **neal.m.master said:**
> "cd" into the location of the tar.gz/tar.bz2.  type "ls" to be sure that the you're in the right place. for a gzipped tar: "tar xvzf file.tar.gz" for a bzipped tar: "tar xvjf file.tar.bz2"

when in doubt, read the man page for tar.

 I'm just trying to understand the whole thing what does cd into the location of the tar mean or what exactly should i do ?

---

### Post by RiceMonster on 2010-07-26
> **Mat11 said:**
> Have tried the above exactly all i get is no such file or directory - why ?

Because the file you typed doesn't exist, meaning that is not the right location or name of the file you're trying to extract. 

Follow these steps:
```
cd /path/to/the/directory/
ls
```

Now, do you see the file in the output of ls? If not, you're not in the right directroy, or maybe you renamed it to something different.

Now if you do see it, you're on the right track. I'm assuming the file is called naev-0.4.2.tar.bz2 because that's what you told me. So in that case, you can now type:
```
tar xvf naev-0.4.2.tar.bz2
```

---

### Post by Mat11 on 2010-07-26
> **RiceMonster said:**
> Because the file you typed doesn't exist, meaning that is not the right location or name of the file you're trying to extract. 

Follow these steps:
```
cd /path/to/the/directory/
ls
```Now, do you see the file in the output of ls? If not, you're not in the right directroy, or maybe you renamed it to something different.

Now if you do see it, you're on the right track. I'm assuming the file is called naev-0.4.2.tar.bz2 because that's what you told me. So in that case, you can now type:
```
tar xvf naev-0.4.2.tar.bz2
```


After i tried to input -- cd /path/to/the/directory/ exactly i get no such file or directory

---

### Post by nmaster on 2010-07-26
> **RiceMonster said:**
> Because the file you typed doesn't exist, meaning that is not the right location or name of the file you're trying to extract. 

Follow these steps:
```
cd /path/to/the/directory/
ls
```Now, do you see the file in the output of ls? If not, you're not in the right directroy, or maybe you renamed it to something different.

Now if you do see it, you're on the right track. I'm assuming the file is called naev-0.4.2.tar.bz2 because that's what you told me. So in that case, you can now type:
```
tar xvf naev-0.4.2.tar.bz2
```

this is *almost* exactly what i said.  the only difference is that you can untar and uncompress the file in one shot if you use this (instead of the last command)
```
tar xvjf naev-0.4.2.tar.bz2
```


EDIT:My 500th post! :)

---

### Post by RiceMonster on 2010-07-26
> **Mat11 said:**
> After i tried to input -- cd /path/to/the/directory/ exactly i get no such file or directory

replace /path/to/the/directory/ with the full path of the directory you saved the file you're trying to extract in.

> **neal.m.master said:**
> this is *almost* exactly what i said.  the only difference is that you can untar and uncompress the file in one shot if you use this (instead of the last command)
```
tar xvjf naev-0.4.2.tar.bz2
```


EDIT:My 500th post! :)

That command will give the exact same results as the one I supplied. The only difference is I didn't use the j flag, because you can extract without the j or z flag, and it will work regardless of whether it's .gz or .bz2. The OP also has to have the file in his working directory for it to work as well.

---

### Post by Mat11 on 2010-07-26
The new update for sudo mentioned something about super users access do you think i made a mistake updating it ?

---

### Post by RiceMonster on 2010-07-26
> **Mat11 said:**
> The new update for sudo mentioned something about super users access do you think i made a mistake updating it ?

That was just a security fix, and sudo is not needed to do this. It's fine.

---

### Post by Mat11 on 2010-07-26
> **neal.m.master said:**
> this is *almost* exactly what i said.  the only difference is that you can untar and uncompress the file in one shot if you use this (instead of the last command)
```
tar xvjf naev-0.4.2.tar.bz2
```
EDIT:My 500th post! :)

Thanks once again i tried what you said it says  f  needs an argument ????

---

### Post by WRDN on 2010-07-26
[http://ubuntuforums.org/showpost.php?p=5798678&postcount=7](http://ubuntuforums.org/showpost.php?p=5798678&postcount=7)

---

### Post by Mat11 on 2010-07-26
> **RiceMonster said:**
> replace /path/to/the/directory/ with the full path of the directory you saved the file you're trying to extract in.



That command will give the exact same results as the one I supplied. The only difference is I didn't use the j flag, because you can extract without the j or z flag, and it will work regardless of whether it's .gz or .bz2. The OP also has to have the file in his working directory for it to work as well.

Will post exact info copied from terminal :laptop:~$ tar xvjf naev-0.4.2.tar.bz2
tar: naev-0.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Thanks to all so far :(

---

### Post by Locke_99GS on 2010-07-26
It appears not that the untar command is bad, but that the OP doesn't know where he placed the file, doesn't understand linux directory structure, and doesn't understand how to navigate directories from the command line.

From a terminal, run this command to update the file index, which we will access in a moment:
```
sudo updatedb
```

Next, we will search the index for the file you have misplaced. Assuming that the file is indeed name "*naev-0.4.2.tar.bz2*" as you mentioned previously, do this:
```
locate naev-0.4.2.tar.bz2
```

This should have outputted one line to the terminal. If it did not, then the filename you provided is either wrong, or it doesn't exist.

Change to the directory that is listed (use everything EXCEPT for the file name)
An *example*: If the output was */home/mat11/Downloads/naev-0.4.2.tar.bz2*, then you would:
```
cd /home/mat11/Downloads
```

Now you should be in the proper directory, and you can untar it using methods mentioned previously.

---

### Post by bodhi.zazen on 2010-07-26
I use a function.

Add this to ~/.bashrc

```

# Extract files from any archive
# Usage: ex <archive_name>

function ex ()
{
  if [ -f "$1" ] ; then
    case "$1" in
      *.tar)                tar xvf $1        ;;
      *.tar.bz2 | *.tbz2 )  tar xjvf $1        ;;
      *.tar.gz | *.tgz )    tar xzvf $1     ;;
      *.bz2)                bunzip2 $1       ;;
      *.rar)                unrar x $1     ;;
      *.gz)                 gunzip $1     ;;
      *.zip)                unzip $1     ;;
      *.Z)                  uncompress $1  ;;
      *.7z)                 7z x $1    ;;
      *.xz)                 tar xJvf $1     ;;
      *)   echo ""${1}" cannot be extracted via extract()" ;;
     esac
   else
     echo ""${1}" is not a valid file"
   fi
}
# Modified by bodhi.zazen
# Thanks to rezza at Arch Linux
```You then extract an archive with

```
ex archive_name
```

You can use a different name if you do not want to use "ex"

---

### Post by Locke_99GS on 2010-07-26
Here's a oneliner that should find the file, change to its directory, and untar it. If it creates it's own folder (most do) you'll have to navigate to it on your own. (this is untested)

```
sudo updatedb && cd $(locate naev-0.4.2.tar.bz2 | xargs -l1 dirname) && tar xjvf naev-0.4.2.tar.bz2
```

---

### Post by Mat11 on 2010-07-26
> **Locke_99GS said:**
> It appears not that the untar command is bad, but that the OP doesn't know where he placed the file, doesn't understand linux directory structure, and doesn't understand how to navigate directories from the command line.

From a terminal, run this command to update the file index, which we will access in a moment:
```
sudo updatedb
```Next, we will search the index for the file you have misplaced. Assuming that the file is indeed name "*naev-0.4.2.tar.bz2*" as you mentioned previously, do this:
```
locate naev-0.4.2.tar.bz2
```This should have outputted one line to the terminal. If it did not, then the filename you provided is either wrong, or it doesn't exist.

Change to the directory that is listed (use everything EXCEPT for the file name)
An *example*: If the output was */home/mat11/Downloads/naev-0.4.2.tar.bz2*, then you would:
```
cd /home/mat11/Downloads
```Now you should be in the proper directory, and you can untar it using methods mentioned previously.



As you aware i am a beginner newbie that requires patience as first mentioned so i can get through this problem !!, you can critise the world but sometimes you need to take a close look at yourself !! The file naev is not misplaced because its in a folder named game on my desktop !! I also have a copy in Documents. Why does it have to be in my downloads anyway ??
Tried sudo updatedb then waited for a while and no info showed i just saw a flicker.
Tried locate naev-0.4.2.tar.bz2 and my cursor just dropped down showing no information further. The file exists as a tar size 618.2 in both documents and in a file in the desktop which has been extracted/opened.

---

### Post by nmaster on 2010-07-26
> **Mat11 said:**
> As you aware i am a beginner newbie that requires patience as first mentioned so i can get through this problem !!, you can critise the world but sometimes you need to take a close look at yourself !! The file naev is not misplaced because its in a folder named game on my desktop !! I also have a copy in Documents. Why does it have to be in my downloads anyway ??

it doesn't have to be. its just an example.  the Downloads directory would be a common place, so thats what people used as an example. there's no need to get defensive or upset.  after all, you're the one asking for help.

---

### Post by RiceMonster on 2010-07-26
> **Mat11 said:**
> As you aware i am a beginner newbie that requires patience as first mentioned so i can get through this problem !!, you can critise the world but sometimes you need to take a close look at yourself !! The file naev is not misplaced because its in a folder named game on my desktop !! I also have a copy in Documents. Why does it have to be in my downloads anyway ??

Locke_99GS was trying to help. No need to be hostile. It does not have to be in Downloads, that was just an example.

I'll try to explain again. When you are on the command line you have a "working directory" which is where the shell will look for the files you type. You have to switch to the directory the file is in so the shell can find it. Remember, it is case sensitive, so you have to get the capitalization right. You do this by using "cd". 

So the file is in Documents? Let's change to it:
```
cd ~/Documents
```

~ means your home directory, and Documents means the Documents directory.

Ok, so now we are in the "Documents" directory. Let's check to see if this file called "naev-0.4.2.tar.bz2" is there. Type this:
```
ls
```

You will get a list of files, which may be very big depending on how many files you have in the directory. Do you see the file you're looking for? If so, good.

Now if **did** see the file you are looking for, you can type the below command. If you did not see the file in the directory, the command will not work, because you are telling it to extract the file called "naev-0.4.2.tar.bz2" in your working directory.

```
tar xvjf naev-0.4.2.tar.bz2
```

---

### Post by Mat11 on 2010-07-26
> **neal.m.master said:**
> it doesn't have to be. its just an example.  the Downloads directory would be a common place, so thats what people used as an example. there's no need to get defensive or upset.  after all, you're the one asking for help.

I was'nt being defensive and i never get upset its just ive noticed sometimes people are just plain negative before thinking or reading !!

---

### Post by Locke_99GS on 2010-07-26
I apologize if I came across as tactless or captious. It was not my intent.

---

### Post by mc4man on 2010-07-26
> **bodhi.zazen said:**
> I use a function.

Add this to ~/.bashrc 
........ect. 

very cool - works great

@Mat11
if you didn't get this going try something very simple - 

open the folder containing the archive so you can see it and have room left on desktop.

Then open the terminal and type in the tar command, lets assume  

tar xvjf

Then hit the spacebar once , after that with your mouse drag and drop the archive onto the terminal - it will enter the path and filename for you.

Then click anywhere in the terminal to return focus and press enter on the keyboard.

---

### Post by gandaran on 2010-07-26
> The file naev is not misplaced because its in a folder named game on my desktop !!
in a way it wasn't misplaced but nearly, you are trying to cd and tar the naev file in desktop while all the time it was in the game folder, that's where you have to cd the terminal, to the game folder!

---

### Post by Mat11 on 2010-07-27
> **RiceMonster said:**
> Locke_99GS was trying to help. No need to be hostile. It does not have to be in Downloads, that was just an example.

I'll try to explain again. When you are on the command line you have a "working directory" which is where the shell will look for the files you type. You have to switch to the directory the file is in so the shell can find it. Remember, it is case sensitive, so you have to get the capitalization right. You do this by using "cd". 

So the file is in Documents? Let's change to it:
```
cd ~/Documents
```~ means your home directory, and Documents means the Documents directory.

Ok, so now we are in the "Documents" directory. Let's check to see if this file called "naev-0.4.2.tar.bz2" is there. Type this:
```
ls
```You will get a list of files, which may be very big depending on how many files you have in the directory. Do you see the file you're looking for? If so, good.

Now if **did** see the file you are looking for, you can type the below command. If you did not see the file in the directory, the command will not work, because you are telling it to extract the file called "naev-0.4.2.tar.bz2" in your working directory.

```
tar xvjf naev-0.4.2.tar.bz2
```

Thanks Monster heres the output copied :

laptop:~$ cd ~/game
bash: cd: /home/matt/game: No such file or directory
matt@matt-laptop:~$ cd ~/desktop/game
bash: cd: /home/matt/desktop/game: No such file or directory
matt@matt-laptop:~$ cd ~/documents
bash: cd: /home/matt/documents: No such file or directory
matt@matt-laptop:~$ ls
Desktop    Downloads         GNUstep  Pictures  Templates
Documents  examples.desktop  Music    Public    Videos

---

### Post by bance on 2010-07-27
As mentioned above the shell is case sensitive, that means you have to use capital letters.....

_D_ocuments not...

documents.


That simple;)

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> As mentioned above the shell is case sensitive, that means you have to use capital letters.....

_D_ocuments not...

documents.


That simple;)

Thanks Bance brill i found the naev folder then i tried tar .. heres what happened :


laptop:~$ cd ~/Desktop/naev-0.4.2
matt@matt-laptop:~/Desktop/naev-0.4.2$ 
matt@matt-laptop:~/Desktop/naev-0.4.2$ tar xvjf naev-0.4.2.tar.bz2
tar: naev-0.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
matt@matt-laptop:~/Desktop/naev-0.4.2$

I opened the file and tried to set the folder permissions what are the best settings,when i try to change file access to anything it goes back to (----) is that correct ?

---

### Post by bance on 2010-07-27
You've gone too far, you only want to be in the directory, not the file !

try this

```
cd ..
```

that should take you to the Documents directory.... the un-tar your file

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> You've gone too far, you only want to be in the directory, not the file !

try this

```
cd ..
```that should take you to the Documents directory.... the un-tar your file

Gave it a go:

matt@matt-laptop:~$ cd ~/Desktop
matt@matt-laptop:~/Desktop$ tar naev-0.4.2.tar.bz2
tar: Old option `b' requires an argument.
Try `tar --help' or `tar --usage' for more information.
matt@matt-laptop:~/Desktop$

 -

---

### Post by bance on 2010-07-27
Try it with the arguments.............


tar xvjf naev-0.4.2.tar.bz2

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> Try it with the arguments.............


tar xvjf naev-0.4.2.tar.bz2matt@matt-laptop:~$ cd ~/Desktop
matt@matt-laptop:~/Desktop$ tar naev-0.4.2.tar.bz2
tar: Old option `b' requires an argument.
Try `tar --help' or `tar --usage' for more information.
matt@matt-laptop:~/Desktop$ tar xvjf naev-0.4.2.tar.bz2
tar: naev-0.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
matt@matt-laptop:~/Desktop$

---

### Post by bance on 2010-07-27
OK, lets try to keep things very simple....

change to the directory that contains the file and type```
 ls
```

post the output, please.

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> OK, lets try to keep things very simple....

change to the directory that contains the file and type```
 ls
```post the output, please.


Thanks here it is :

matt@matt-laptop:~$ ls
Desktop    Downloads         GNUstep  Pictures  Templates
Documents  examples.desktop  Music    Public    Videos
matt@matt-laptop:~$

---

### Post by bance on 2010-07-27
I don't think you really want any help if you can't read the posts and do as they ask!

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> I don't think you really want any help if you can't read the posts and do as they ask!

Bance when i copied L(in lower case)  it shows up as l for ls in terminal differently from when it is copies over and pastes.


Have tried it twice and i'm not playing around ! I believe in logic and accuracy.
Also i appreciate your help so far. This in a way is a good test not just for me but for other beginners starting to use Ubuntu 9.10
I'm wondering whether my sudo update did **** up my terminal ? i know the printer (cups) one did and i had great difficulty in overcoming it. Despite these problems Ubuntu 9.10 seems to have great Apps and boots fast.

Matt

---

### Post by bance on 2010-07-27
OK _change _to the directory that contains the file (Documents or whatever) then type

```
cd /home/Documents
```

```
ls -l
```please post the output.

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> OK _change _to the directory that contains the file (Documents or whatever) then type

```
cd /home/Documents
``````
ls -l
```please post the output.


Hey here goes :
matt@matt-laptop:~$ cd /home/Documents
bash: cd: /home/Documents: No such file or directory
matt@matt-laptop:~$ ls -l
total 48
drwxr-xr-x   4 matt matt  4096 2010-07-27 09:56 Desktop
drwxr-xr-x 105 matt matt 12288 2010-07-27 02:16 Documents
drwxr-xr-x   2 matt matt  4096 2010-02-08 20:12 Downloads
-rw-r--r--   1 matt matt   167 2010-02-08 20:03 examples.desktop
drwxr-xr-x   4 matt matt  4096 2010-07-25 15:42 GNUstep
drwxr-xr-x  33 matt matt  4096 2010-02-10 01:09 Music
drwxr-xr-x  25 matt matt  4096 2010-07-24 08:43 Pictures
drwxr-xr-x   2 matt matt  4096 2010-02-08 20:12 Public
drwxr-xr-x   2 matt matt  4096 2010-02-08 20:12 Templates
drwxr-xr-x   2 matt matt  4096 2010-02-08 20:12 Videos
matt@matt-laptop:~$

---

### Post by bance on 2010-07-27
OK we still didn't get to the right place.... try

```
cd ~/Desktop
``````
ls -l
```and post the output please

---

### Post by Mat11 on 2010-07-27
> **bance said:**
> OK we still didn't get to the right place.... try

```
cd ~/Downloads
``````
ls -l
```and post the output please

New output :

matt@matt-laptop:~$ cd ~/Downloads
matt@matt-laptop:~/Downloads$ ls -l
total 0
matt@matt-laptop:~/Downloads$

---

### Post by Mat11 on 2010-07-27
Thought i might mention i use Bleach bit as root sometimes.
Have to leave my comp till this evening thanks for all so far.

Matt

---

### Post by ks07 on 2010-07-27
> **Mat11 said:**
> New output :

matt@matt-laptop:~$ cd ~/Downloads
matt@matt-laptop:~/Downloads$ ls -l
total 0
matt@matt-laptop:~/Downloads$
Sorry to but in, but...

Didn't you say earlier the archive was in a folder called 'game' on the desktop? If so, you'll want to go ```
cd ~/Desktop/game/
```and then use ls -l... Also, remember that while typing almost anything on the terminal **press tab to autocomplete** - The computer will look for files and programs that match what you've already typed. E.g. if you typed cd ~/Desk and pressed tab, the terminal would fill in the rest to give you Desktop. Good for long filenames like what you downloaded. :KS

Also, just a question, but why are we trying to use the terminal? I'm all for learning to use it, but if it's giving so much trouble then using the graphical way would be much easier. :p

---

### Post by mc4man on 2010-07-27
> laptop:~$ cd ~/Desktop/naev-0.4.2
matt@matt-laptop:~/Desktop/[COLOR="Blue"]naev-0.4.2[/COLOR]$ 

Sure looks like you already extracted the orig. tar.bz2, where the orig. archive is, if anywhere, well, only you would know....

---

### Post by Paqman on 2010-07-27
If you're running a graphical environment, sod using the terminal to untar. Right click > extract here. Couldn't be simpler.

---

### Post by Mat11 on 2010-07-28
> **Paqman said:**
> If you're running a graphical environment, sod using the terminal to untar. Right click > extract here. Couldn't be simpler.

I've extracted the tar using right click on Desktop but how to i run it in terminal and get it going so it shows up in application games.How do i run it ? I'm still unable to untar files in terminal.!! My files are set to custom in appearance and when i try to enable the access file to enable read and write the folder resets/reverts itself back to the double dash (--)
just want to get the game going then i'll try to update the hp driver.

---

### Post by Paqman on 2010-07-28
> **Mat11 said:**
> I've extracted the tar using right click on Desktop but how to i run it in terminal and get it going so it shows up in application games.How do i run it ?

Make sure the executable file is set to be executable. Right click > Properties > Permissions and check the box for "allow executing as a program". To add it to a menu go to System > Preferences > Main Menu and add an entry pointing to that executable.

---

### Post by Deiz on 2010-07-28
Heh. Funny coming across this (I'm one of NAEV's developers). If you got the tarball from the Google Code site, it's probably a source tarball - You'd have to compile it yourself.

If you're running 32-bit Ubuntu, you should download [this]("http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32") (the binary) and [the game data]("http://naev.googlecode.com/files/ndata-0.4.2").

By the way, NAEV is also packaged by PlayDeb - [see here]("http://www.playdeb.net/software/NAEV"). It should be easier to install for you. On their [main page]("http://www.playdeb.net/updates/ubuntu/10.04/") they also have instructions on installing their software.

---

### Post by Mat11 on 2010-07-28
> **Paqman said:**
> Make sure the executable file is set to be executable. Right click > Properties > Permissions and check the box for "allow executing as a program". To add it to a menu go to System > Preferences > Main Menu and add an entry pointing to that executable.

I wasn't aware i had to double click on the bottom bar as im new to linux have the tick now.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> Heh. Funny coming across this (I'm one of NAEV's developers). If you got the tarball from the Google Code site, it's probably a source tarball - You'd have to compile it yourself.

If you're running 32-bit Ubuntu, you should download [this]("http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32") (the binary) and [the game data]("http://naev.googlecode.com/files/ndata-0.4.2").

By the way, NAEV is also packaged by PlayDeb - [see here]("http://www.playdeb.net/software/NAEV"). It should be easier to install for you. On their [main page]("http://www.playdeb.net/updates/ubuntu/10.04/") they also have instructions on installing their software.

Diaz thanks for your info the Play Deb package thing nearly worked but my 32 bit comp said an apt file does not exist for the install.

---

### Post by ubun2warrior on 2010-07-28
Hi

can u plz tell how to add the code to ~/.bashrc and then save it. its slightly cofusing and i am afraid i might make a mistake....

regards

ubun2warrior

---

### Post by Deiz on 2010-07-28
> **Mat11 said:**
> Diaz thanks for your info the Play Deb package thing nearly worked but my 32 bit comp said an apt file does not exist for the install.

You need to install PlayDeb's package first - it sets up the repository ([here]("http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb")). Once you've done that, you can install anything from PlayDeb.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> You need to install PlayDeb's package first - it sets up the repository ([here]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb")). Once you've done that, you can install anything from PlayDeb.

Have set up repository then went back to what i did previously using play Deb's package from your here download and my comp said Naev file not found.

---

### Post by Mat11 on 2010-07-28
> **ubun2warrior said:**
> Hi

can u plz tell how to add the code to ~/.bashrc and then save it. its slightly cofusing and i am afraid i might make a mistake....

regards

ubun2warrior

I'm new to Ubuntu 9.10 and Linux myself hope someone can help you here.

---

### Post by Mat11 on 2010-07-28
> **ks07 said:**
> Sorry to but in, but...

Didn't you say earlier the archive was in a folder called 'game' on the desktop? If so, you'll want to go ```
cd ~/Desktop/game/
```and then use ls -l... Also, remember that while typing almost anything on the terminal **press tab to autocomplete** - The computer will look for files and programs that match what you've already typed. E.g. if you typed cd ~/Desk and pressed tab, the terminal would fill in the rest to give you Desktop. Good for long filenames like what you downloaded. :KS

Also, just a question, but why are we trying to use the terminal? I'm all for learning to use it, but if it's giving so much trouble then using the graphical way would be much easier. :p

I tried what you mentioned

 :matt@matt-laptop:~$ sudo -i
root@matt-laptop:~# cd ~/Desk
-bash: cd: /root/Desk: No such file or directory
root@matt-laptop:~# cd ~/Desktop/game
-bash: cd: /root/Desktop/game: No such file or directory
root@matt-laptop:~# 
matt@matt-laptop:~$ sudo -i
root@matt-laptop:~# cd ~/Desk
-bash: cd: /root/Desk: No such file or directory
root@matt-laptop:~# cd ~/Desktop/game
-bash: cd: /root/Desktop/game: No such file or directory
root@matt-laptop:~# ls -l
total 0
root@matt-laptop:~# 

Could i have damaged my terminal by using Bleach Bit or do you think my last sudo update has gone wrong ? My game is clearly opened in a new file next to my tarball on my desktop ! Have recently deleted a program called tweek which i think started causing problems with terminal.
How do you fix terminal or check its OK ?

---

### Post by Deiz on 2010-07-28
> **Mat11 said:**
> Have set up repository then went back to what i did previously using play Deb's package from your here download and my comp said Naev file not found.

When you visit [http://www.playdeb.net/install/naev](http://www.playdeb.net/install/naev) what happens? It should give you a prompt from Firefox. After that, a package update should run, and NAEV will be downloaded and installed.

If it still tells you the package can't be found, make *sure* you've installed this: [http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb) and then try the first link again.

Once it's installed it show up in Applications -> Games -> naev

If you still can't get it installed, run:

```
cat /etc/apt/sources.list.d/playdeb.list
```

and a) see if the file is there, b) if it is, paste the output.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> When you visit [http://www.playdeb.net/install/naev](http://www.playdeb.net/install/naev) what happens? It should give you a prompt from Firefox. After that, a package update should run, and NAEV will be downloaded and installed.

If it still tells you the package can't be found, make *sure* you've installed this: [http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb") and then try the first link again.

Once it's installed it show up in Applications -> Games -> naev

If you still can't get it installed, run:

```
cat /etc/apt/sources.list.d/playdeb.list
```and a) see if the file is there, b) if it is, paste the output.

Thanks for your help heres the output which is not underlined in grey at all in my terminal :

matt@matt-laptop:~$ sudo cat /etc/apt/sources.list.d/playdeb.list
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
matt@matt-laptop:~$


Just checked my janitor it says playdeb unused then a tick just after it which i left alone.
Have been using Tweek of which i deleted recently which was not part of the software center downloads and im wondering if i've damaged my file system recognition but lets see if it is still possible to get the game working if thats OK to carry on ?

---

### Post by Deiz on 2010-07-28
> **Mat11 said:**
> Thanks for your help heres the output which is not underlined in grey at all in my terminal :

matt@matt-laptop:~$ sudo cat /etc/apt/sources.list.d/playdeb.list
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
matt@matt-laptop:~$
So, the repository is enabled and you've presumably installed the package. Is the shortcut present in Applications -> Games?

What happens if you try and run this?

```
naev
```

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> So, the repository is enabled and you've presumably installed the package. Is the shortcut present in Applications -> Games?

What happens if you try and run this?

```
naev
```

Have no shortcut in apps games menu and heres the output :

matt@matt-laptop:~$ naev
naev: command not found
matt@matt-laptop:~$ sudo naev
[sudo] password for matt: 
sudo: naev: command not found
matt@matt-laptop:~$

---

### Post by Deiz on 2010-07-28
So you haven't installed it, then.

Run:

```
sudo apt-get install naev naev-data
```

... and the game, along with the shortcut, will be installed.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> So you haven't installed it, then.

Run:

```
sudo apt-get install naev naev-data
```... and the game, along with the shortcut, will be installed.

Hi i witnessed the dependance tree doing its thing heres output :

matt@matt-laptop:~$ sudo apt-get install naev naev-data
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package naev
matt@matt-laptop:~$

---

### Post by Deiz on 2010-07-28
Your repos are likely out of date. Run:

```
sudo apt-get update && sudo apt-get install naev naev-data
```

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> Your repos are likely out of date. Run:

```
sudo apt-get update && sudo apt-get install naev naev-data
```

Here goes :

matt@matt-laptop:~$ sudo apt-get update && sudo apt-get install naev naev-data
[sudo] password for matt: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release.gpg                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Translation-en_GB  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_GB
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package naev
matt@matt-laptop:~$

---

### Post by Deiz on 2010-07-28
Ugh, okay.

I just fired up a VM. Getdeb's repo for 9.10 is missing packages, the 10.04 one isn't but I'm doubting packages from it would run on 9.10.

So, here's what we'll do:

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```

That will create a directory on your desktop named "NAEV", and will start the game when it's finished downloading. When you want to start the game again later, you can just open the NAEV directory and double-click on naev-0.4.2-linux-x86-32.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> Ugh, okay.

I just fired up a VM. Getdeb's repo for 9.10 is missing packages, the 10.04 one isn't but I'm doubting packages from it would run on 9.10.

So, here's what we'll do:

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```That will create a directory on your desktop named "NAEV", and will start the game when it's finished downloading. When you want to start the game again later, you can just open the NAEV directory and double-click on naev-0.4.2-linux-x86-32.

Will try this option but could i say now i've just done an update and picked up something called device kit disks update so i afterwards went back to terminal and inputted once again :

ls -l
total 8
drwxr-xr-x 2 matt matt 4096 2010-07-27 09:56 Game
drwxr-xr-x 6 matt matt 4096 2010-02-01 16:03 naev-0.4.2
matt@matt-laptop:~/Desktop$ 

The only update i had not allowed was Firefox 3.5
Now i have my Desktop info back why has that happened ?

---

### Post by Mat11 on 2010-07-28
Have to go out for a bit thanks very much back later.

---

### Post by Deiz on 2010-07-28
I'm assuming you closed the terminal and opened another. By default, the terminal starts in ~/ (one directory above the desktop). To get back to the NAEV directory, you need to cd ~/Desktop/NAEV/

You may also need to install some dependencies:

```
sudo apt-get install libopenal1 libmikmod2 llibsdl-mixer1.2 libsdl-image1.2 libsmpeg0
```

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> I'm assuming you closed the terminal and opened another. By default, the terminal starts in ~/ (one directory above the desktop). To get back to the NAEV directory, you need to cd ~/Desktop/NAEV/

You may also need to install some dependencies:

```
sudo apt-get install libopenal1 libmikmod2 llibsdl-mixer1.2 libsdl-image1.2 libsmpeg0
```

Hi no joy output here :

matt@matt-laptop:~$ cd ~/Desktop/NAEV/
bash: cd: /home/matt/Desktop/NAEV/: No such file or directory
matt@matt-laptop:~$ sudo cd ~/Desktop/NAEV?
sudo: cd: command not found
matt@matt-laptop:~$ 
:(

---

### Post by Deiz on 2010-07-28
Did you run

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```

or not? If you haven't, the directory won't exist.

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> Did you run

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```or not? If you haven't, the directory won't exist.

Nearly heres what happened :

matt@matt-laptop:~$ sudo mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget [http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32](http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32) && wget [http://naev.googlecode.com/files/ndata-0.4.2](http://naev.googlecode.com/files/ndata-0.4.2) && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
[sudo] password for matt: 
--2010-07-28 19:26:34--  [http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32](http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32)
Resolving naev.googlecode.com... 209.85.229.82
Connecting to naev.googlecode.com|209.85.229.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2961835 (2.8M) [application/octet-stream]
naev-0.4.2-linux-x86-32: Permission denied

Cannot write to `naev-0.4.2-linux-x86-32' (Permission denied).
matt@matt-laptop:~/Desktop/NAEV$

I'm a bit concerned theres a padlock on my computer saying this folder does not belong to me when that is untrue.Half of it is greyed mentioning root. One of the main reasons i decided to use Ubuntu was because its open source.!
I have already enabled the executable permissions many moons ago .

---

### Post by Deiz on 2010-07-28
Don't prepend sudo. You caused the directory to be created by root, and consequently lack write access to it.

Now you need to do:

```
sudo rm -r ~/Desktop/NAEV
```

and re-run:

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```

---

### Post by Mat11 on 2010-07-28
> **Deiz said:**
> Don't prepend sudo. You caused the directory to be created by root, and consequently lack write access to it.

Now you need to do:

```
sudo rm -r ~/Desktop/NAEV
```and re-run:

```
mkdir -p ~/Desktop/NAEV && cd ~/Desktop/NAEV && wget http://naev.googlecode.com/files/naev-0.4.2-linux-x86-32 && wget http://naev.googlecode.com/files/ndata-0.4.2  && chmod +x naev-0.4.2-linux-x86-32 && ./naev-0.4.2-linux-x86-32
```

It worked its brilliant worth the wait . Have another file called NAEV folder on my desktop with no short cut from app games how exactly should i sort that out ?:)

---

### Post by oldos2er on 2010-07-28
> **Mat11 said:**
> I'm a bit concerned theres a padlock on my computer saying this folder does not belong to me when that is untrue.Half of it is greyed mentioning root. One of the main reasons i decided to use Ubuntu was because its open source.!


"Open source" doesn't mean what you think it means. [http://en.wikipedia.org/wiki/Open_source_software](http://en.wikipedia.org/wiki/Open_source_software)

Understanding "sudo": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mat11 on 2010-07-28
> **oldos2er said:**
> "Open source" doesn't mean what you think it means. [http://en.wikipedia.org/wiki/Open_source_software](http://en.wikipedia.org/wiki/Open_source_software)

Understanding "sudo": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the info 
Matt

---

### Post by Mat11 on 2010-07-28
[QUOTE=Mat11;9649097]It worked its brilliant worth the wait . Have another file called NAEV folder on my desktop. 
Thanks for all your help and time much appreciated.
How do i get it to execute as its not in the game folder ?

---

### Post by jtarin on 2010-07-28
The story of Alice's fall down the rabbit-hole is packed with intriguing problems. When Alice is puzzled — which is very frequently — you should be too. Enjoy your trip!:popcorn:

---

### Post by arpanaut on 2010-07-28
> **Mat11 said:**
> [QUOTE=Mat11;9649097].
How do i get it to execute as its not in the game folder ?

As per Diez in post #65
When you want to start the game again later, you can just open the NAEV directory and double-click on naev-0.4.2-linux-x86-32.


A search will find how to make a launcher in your menu.

---

### Post by Mat11 on 2010-07-28
> **arpanaut said:**
> [QUOTE=Mat11;9649245]

As per Diez in post #65
When you want to start the game again later, you can just open the NAEV directory and double-click on naev-0.4.2-linux-x86-32.


A search will find how to make a launcher in your menu.

Thanks, it works from the file you mentioned will give the search a go.

---

### Post by Speedsmack on 2010-08-18
Hello everyone.  I chose to post in this thread as my problem is very similar, but has a second part to it.. so please don't redirect me QQ.

I play Shaiya and the graphics suck to the point it's unplayable.. and I was given the tip to run Wine version 1.0.1 instead of the version that Ubuntu offers in the Software Center which is newer, so..

I ended up with wine-1.0.1.tar.bz2 file that I saved to Home folder.

I used the information I gathered from the first page of this thread on unzipping it and it worked like a charm.

Now can anyone tell me the terminal command to actually "install" wine 1.0.1 to where it's listed under Applications and is able to be ran?

I'm still quite new to Ubuntu and I'm dead set on installing this version of Wine.

---

### Post by jtarin on 2010-08-19
Get the .deb file [here]("https://launchpad.net/ubuntu/intrepid/i386/wine/1.0.1-0ubuntu1") and right-click on it to install with the debi installer.

---

### Post by Locke_99GS on 2010-08-21
@Speedsmack, it would be easiest for your to install from the pre-compiled deb linked in the previous post. The tarball you downloaded is most likely a source package, which you would have to compile prior to installing. For Wine, this can be pretty time consuming.

---

### Post by jtarin on 2010-08-21
And the topic of the first post was "How to untar.gz and bz2 files easily in terminal".Gonna be here awhile.:popcorn::popcorn::popcorn::popcorn:

---

