---
title: "Can't run a program - Linux Noob.."
date: 2011-01-29
forum: New to Ubuntu
---

### Post by HexHeat on 2011-01-29
I am trying to install a program called "alternative transients program" in ubuntu.  It does not exist in any repositories, those who want to get it have to aquire a license from the organization (although it is free).  Anyway, the installation text says this:  

" [[INSTALL]] 
 (1) Copy atplinux.zip to a temporary directory, and    unarchive it.     
#  pkunzip atplinux.zip     

Move the following files to the install    directory of ATP.      
tpbig      
runtp      
atv      
atg      
armafit
listsize.big      
startup      
graphics      
graphics.aux 
and more .aux files     

If tpbig, armafit and runtp cannot run, set the attribute like as follows;      
chmod 0755 tpbig armafit runtp atv atg 

(2) Settings     
Write the following in .bashrc file.      GNUDIR=/home/atp/    <----- where you put startup, graphics                                 and graphics.aux     export GNUDIR     Add the directory where you put tpbig, armafit and runtp to PATH. 
"

 Ok first of all, I unzipped the files to a directory but I have no idea what step (2) is telling me.  I don't know what a .bashrc file is or how to edit one...  Supposedly when everything is setup properly, I can just type in "tpbig dc1.dat" into terminal and it will start working and give me some outputs.  

I didn't do anything with Step (2) yet but when I type in navigate to the directory that I have the program in and then type in:  "tpbig dc1.dat" it says "tpbig: command not found".  I have no idea what I'm doing.  On windows I just had to set up the installer and it 'worked'.  Anyone have any idea what's going on?  Espcially with installation step (2)??

---

### Post by nemilar on 2011-01-29
If you want to run a program from the current working directory, you need to preface is with "./" (dot slash).

So after you "cd" to that directory, instead of typing "tpbig dc1.dat" you'll want to type:

```
./tpbig dc1.dat
```

---

### Post by robsoles on 2011-01-29
Welcome to UF.

It sounds a bit like you didn't really complete step one and their instructions look pretty flaky to me. I have absolutely zero experience with ATP and just read a bit about it by Googling.

Try this:

Make a new folder in your home directory, let's use terminal coz we are going to land in it at some stage anyway;
```
md ~/atp
```so '~/' expands to whatever your home folder location is, mine is /home/rob so if I type it in my terminal it will create /home/rob/atp/.

Move or copy the files from where-ever you unpacked them already to this new folder - if you unpacked them in your downloads folder from a zip file named "pain-in-the-neck.zip", which unpacked into a subfolder with the zip's name, then the command to move them, in terminal, would be
```
mv -R ~/Downloads/pain-in-the-neck/* ~/atp
```The '-R' is telling the mv utility to take any subfolders in there in the move as well.

Finally Step 2:

We will open your .bashrc file in gedit using terminal
```
gedit ~/.bashrc
```Let's put their stuff right at the bottom, so we can add;
```
[COLOR=Black]GNUDIR=/home[/COLOR]/[COLOR=Red]*you*[/COLOR][COLOR=Black]/atp/[/COLOR]
export PATH=${PATH}:/home/[COLOR=Red]*you*[/COLOR]/atp
```right at the bottom. Don't put '[COLOR=Red]*you*[/COLOR]' for goodness sake - you must change that to whatever your username is for your home folder.

Log off and log back in again, or have a complete restart - open terminal and try to use it again.

How does that work out for you?

---

### Post by JKyleOKC on 2011-01-29
> **HexHeat said:**
> Anyone have any idea what's going on?  Espcially with installation step (2)??The ".bashrc" file is a hidden file in your home directory that sets up your profile each time you log in. The initial "." in its name makes it hidden from the file manager display unless you press CTRL-H, but you can edit it with any text editor. Do NOT try to use a word processor to change it, though, since they add control data to a file and that would royally mess up your ability to use the system!

The instruction to add the GNUDIR line is doing what Windows would do with a "SET" command in the autoexec.bat file. It creates an environment variable that tells the program in which directory it can find its support files. The instruction to add this directory to the PATH is meant to eliminate any need for the "./" prefix when attempting to run the program.

When you open the .bashrc file for the first time in a text editor, you can see all the commands that it executes behind the scenes. Any line that begins with "#" is a comment and will be ignored, as will empty lines. The rest of the lines are all commands that set up your environment, the prompt you will see, and certain convenient aliases (which are used to modify the action of some commands).

Before you can do Step 2 you'll have to know exactly where the program files are located. The instruction didn't tell you to create the /home/apt directory so presumably the install package does that for you -- but it may not, and in that case you might not be able to use the program at all!

---

### Post by HexHeat on 2011-01-29
Thanks everyone.  That made a lot more sense.  I was able to get the program working but now I'm having problems with the result but that has nothing to do with Ubuntu and everything to do with the software developers so I will contact them if I can.

I appreciate the help and I'll try to learn more so that some day I can help someone with a problem.

---

