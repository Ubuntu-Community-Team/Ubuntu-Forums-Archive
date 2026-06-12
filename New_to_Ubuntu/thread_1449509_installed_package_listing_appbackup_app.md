---
title: "installed package listing app/backup app"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by lonewaster on 2010-04-07
i was bored and have recently been rebooting my setup quite alot, so i decided to make this.

this is a bash script + perl program that, together, get a list of installed packages and cleans up the list so that it is just all the package names separated by a space.
you can just open the output file (installed-packages.list) and copy+paste the output after 'sudo apt-get install' and ubuntu will re-install all the packages that were on the computer that ran the listing/backup script.
i plan to write a little tutorial to go with this, and most likely a restore script, too - just to make it easier for newer people.
but for now, here are the two files and a short example on how to use them.
enjoi !!  :guitar:

--- --- ---

okay, say your laptop went kaput and you had to reinstall ubuntu.
you are going to have to 'apt-get install <pack>' every package all over again, which in my case is a pain with all my programming/server/testing/debugging apps etc...
so, what if you could just run this script/program once a month, whatever (whenever you do a backup maybe?) and store the ouputted file somewhere safe?
then when you reformat your comp, you can just copy+paste the contents of the file after a 'sudo apt-get install <paste here>'  command and BOOM - all your packages install., hassle-free>? ( well, almost... i haven't tested this alot so there might be some package issues but i will get to that after some sleep =P )

anyway, there is TWO parts to this. 
packer.pl (perl program)   &   packup (bash script)

copy & paste the following (in its ENTIRETY) into a file and save it as 'packer.pl' WITHOUT THE QUOTES!
```

#!/usr/bin/perl
#######################################################################
#######################################################################
##          this perl script if for use by my 'packup' script        ##
##    and filters the output of the dpkg --get-selections command.   ##
##      feel free to modify/use this script for another purpose,     ##
##          but just leave these comments/credits intact, ok?         ##
## -->  this script requires to be placed in the same folder as  <-- ##
## -->  the aptly named 'packup' == which is a BASH program      <-- ##
## -->  used to link this program to the command line.           <-- ##
##  ((I KNOW, I KNOW...THIS COULD BE MORE COMPACT. BUT LESS FUN!!))  ##
##                                     ##
## version            v1.0                     ##
## createdBy            Darksider                 ##
## emailAddy            darksider@swedger.com             ##
## websiteUrl            www.swedger.com                 ##
## lastEdit            08/04/2010                 ##
## thanksTo            gedit   ^_^                 ##
#######################################################################
#######################################################################

print "loading 'installed-packages.list' for reading...\n";
if((-e 'installed-packages.list') and (-r 'installed-packages.list') and (-T 'installed-packages.list')) {
    open(packs,'<installed-packages.list');
    print "reading 'installed-packages.list' file...\n";
    while(<packs>) { # for each line in the installed-packages list file,
        $rawpack=$_; # save the line into a variable.
        @cutpacks=split(/\s/,$rawpack,2); # split() the line into two
        if($cutpacks[1] =~ /install/) { # IF the presently selected package is INSTALLED currently
            $cleanpacks=$cleanpacks." ".$cutpacks[0]; # then add the package name into our 'CLEAN' packlist variable
        }
        # otherwise it will be listed as DEINSTALL and is not installed/has been removed, hence we don't want/need to remember it !!
    } # after we've finished READING the file to deal with each package name, we want to clean it up. so...
    print "closing 'installed-packages.list'...\n"; # alert the user to what's happening at this moment in time (good practice)
    close(packs); # close the file for good practice
    print "cleaning up installed packages list...\n";
    print "loading 'installed-packages.list' for writing...\n";
    open(packs,'>installed-packages.list'); # re-open the file for rewriting with the chopped up and formatted list of installed packages,
    printf packs $cleanpacks; # re-write the file with the cleaned-up version of our package list
    close(packs); # and then close the file for good pactice
    print "'installed-packages.list' has been re-written in a nicer format =]\n"; # alert the user to the success...
}
else { # IF the list file doesn't exist, isn't readable OR isn't a text file, then alert the user. (this is incase the user edits the file
    # whether it be by accident or not. also useful if messing with the code >_<
    print "'installed-packages.list' file could not be read. please ensure that this program and 'packup' script are in the same directory, and that you haven't modified the 'installed-packages.list' file. The file must meet three qualifications for passing through this program's tidyup-\n+ It must EXIST\n+ It must be READABLE\n+ It must be a TEXT FILE\n\nIf you used 'packup' then there shouldn't be anything wrong. Make sure it is in a directory you have permission to read/write in, and if the problem persists then contact me for support-\ndarksider\@swedger.com\n\nThanks!!\n";
}
print "packer.pl program exiting...\n"; # print a little exiting message so the user knows the perl part is exiting
print "- - - - - - - - -\n"; # print a little line-break type thing to make it look nice in terminal

```then, copy and paste the following bit of code and save it, this time, into packup (no file extension, just call the file 'packup' without the quotes!!)
```

#!/bin/bash
#######################################################################
#######################################################################
##       this script packs up a list of all installed packages       ##
## and saves them in a file in a format readable by 'unpack' script. ##
##          you can also use the contents of the file to just         ##
##                        apt-get install <package-list>         ##
## -->  this script requires to be placed in the same folder as  <-- ##
## -->  the aptly named 'packer.pl' == which is a PERL program   <-- ##
## -->  used to edit the output of the dpkg command that lists   <-- ##
## -->  all installed programs on the machine running the script <-- ##
##                                     ##
## version            v1.0                     ##
## createdBy            Darksider                 ##
## emailAddy            darksider@swedger.com             ##
## websiteUrl            www.swedger.com                 ##
## lastEdit            08/04/2010                 ##
## thanksTo            gedit   ^_^                 ##
#######################################################################
#######################################################################

clear
echo "packup bash script v1.0"
echo "createdBy Darksider"
echo "websiteUrl www.swedger.com"
echo "this script utilises 'packer.pl', which was also created by me =]"
echo "- - - - - - - - -"
dpkg --get-selections > installed-packages.list
perl packer.pl
echo "thanks for using my code!!"
echo "--> darksider <--"
echo ""

```--- --- ---

now, when i fix up this post and give more info and possibly a TUTORIAL, i will show you how to make your own personal **bin** folder to put custom scripts and such into, so that they are easier to use and get to.
but for now, use the following command, replacing <directory tree here> with the directions to the directory where you have put your two new scripts.
```
cd <directory tree here>
```for instance, if you made** packer.pl** and **packup** on your desktop, then you would type-
```
cd /home/<your ubuntu username>/Desktop> 
```if you still don't get it, when I log into my ubuntu laptop, i click on my username which is **billy** and then i type my password.
so if i was running this command, i would type the following into my terminal-
```
cd /home/**billy**/Desktop
```so, now that you are in the directory, type the following and watch in amazement as my code works for your every whim! mwuahahahahaha.... *cough* sorry bout that...

```

chmod +x packup   [HIT ENTER]
packup                   [HIT ENTER]

```hope you liked this!!
please leave me lots of comments, whether they be good or bad. just ensure it is **constructive criticism**!!!!!!!!!

peace all, i will check back tomorrow.

-billy-
[lonewaster/darksider]

---

### Post by lonewaster on 2010-04-08
i have decided to write a set of utilities (bash,perl,maybe other languages) designed to make some tedious tasks easier under ubuntu.
i will make a new thread upon it being released [beta] and hopefully people will like and enjoy them!

<3 ubuntu <3

-billy-

---

### Post by dannyboy79 on 2010-04-08
> **lonewaster said:**
> i was bored and have recently been rebooting my setup quite alot, so i decided to make this.

this is a bash script + perl program that, together, get a list of installed packages and cleans up the list so that it is just all the package names separated by a space.
you can just open the output file (installed-packages.list) and copy+paste the output after 'sudo apt-get install' and ubuntu will re-install all the packages that were on the computer that ran the listing/backup script.
i plan to write a little tutorial to go with this, and most likely a restore script, too - just to make it easier for newer people.
but for now, here are the two files and a short example on how to use them.
enjoi !!  :guitar:

--- --- ---

okay, say your laptop went kaput and you had to reinstall ubuntu.
you are going to have to 'apt-get install <pack>' every package all over again, which in my case is a pain with all my programming/server/testing/debugging apps etc...
so, what if you could just run this script/program once a month, whatever (whenever you do a backup maybe?) and store the ouputted file somewhere safe?
then when you reformat your comp, you can just copy+paste the contents of the file after a 'sudo apt-get install <paste here>'  command and BOOM - all your packages install., hassle-free>? ( well, almost... i haven't tested this alot so there might be some package issues but i will get to that after some sleep =P )

anyway, there is TWO parts to this. 
packer.pl (perl program)   &   packup (bash script)

copy & paste the following (in its ENTIRETY) into a file and save it as 'packer.pl' WITHOUT THE QUOTES!
```

#!/usr/bin/perl
#######################################################################
#######################################################################
##          this perl script if for use by my 'packup' script        ##
##    and filters the output of the dpkg --get-selections command.   ##
##      feel free to modify/use this script for another purpose,     ##
##          but just leave these comments/credits intact, ok?         ##
## -->  this script requires to be placed in the same folder as  <-- ##
## -->  the aptly named 'packup' == which is a BASH program      <-- ##
## -->  used to link this program to the command line.           <-- ##
##  ((I KNOW, I KNOW...THIS COULD BE MORE COMPACT. BUT LESS FUN!!))  ##
##                                     ##
## version            v1.0                     ##
## createdBy            Darksider                 ##
## emailAddy            darksider@swedger.com             ##
## websiteUrl            www.swedger.com                 ##
## lastEdit            08/04/2010                 ##
## thanksTo            gedit   ^_^                 ##
#######################################################################
#######################################################################

print "loading 'installed-packages.list' for reading...\n";
if((-e 'installed-packages.list') and (-r 'installed-packages.list') and (-T 'installed-packages.list')) {
    open(packs,'<installed-packages.list');
    print "reading 'installed-packages.list' file...\n";
    while(<packs>) { # for each line in the installed-packages list file,
        $rawpack=$_; # save the line into a variable.
        @cutpacks=split(/\s/,$rawpack,2); # split() the line into two
        if($cutpacks[1] =~ /install/) { # IF the presently selected package is INSTALLED currently
            $cleanpacks=$cleanpacks." ".$cutpacks[0]; # then add the package name into our 'CLEAN' packlist variable
        }
        # otherwise it will be listed as DEINSTALL and is not installed/has been removed, hence we don't want/need to remember it !!
    } # after we've finished READING the file to deal with each package name, we want to clean it up. so...
    print "closing 'installed-packages.list'...\n"; # alert the user to what's happening at this moment in time (good practice)
    close(packs); # close the file for good practice
    print "cleaning up installed packages list...\n";
    print "loading 'installed-packages.list' for writing...\n";
    open(packs,'>installed-packages.list'); # re-open the file for rewriting with the chopped up and formatted list of installed packages,
    printf packs $cleanpacks; # re-write the file with the cleaned-up version of our package list
    close(packs); # and then close the file for good pactice
    print "'installed-packages.list' has been re-written in a nicer format =]\n"; # alert the user to the success...
}
else { # IF the list file doesn't exist, isn't readable OR isn't a text file, then alert the user. (this is incase the user edits the file
    # whether it be by accident or not. also useful if messing with the code >_<
    print "'installed-packages.list' file could not be read. please ensure that this program and 'packup' script are in the same directory, and that you haven't modified the 'installed-packages.list' file. The file must meet three qualifications for passing through this program's tidyup-\n+ It must EXIST\n+ It must be READABLE\n+ It must be a TEXT FILE\n\nIf you used 'packup' then there shouldn't be anything wrong. Make sure it is in a directory you have permission to read/write in, and if the problem persists then contact me for support-\ndarksider\@swedger.com\n\nThanks!!\n";
}
print "packer.pl program exiting...\n"; # print a little exiting message so the user knows the perl part is exiting
print "- - - - - - - - -\n"; # print a little line-break type thing to make it look nice in terminal

```then, copy and paste the following bit of code and save it, this time, into packup (no file extension, just call the file 'packup' without the quotes!!)
```

#!/bin/bash
#######################################################################
#######################################################################
##       this script packs up a list of all installed packages       ##
## and saves them in a file in a format readable by 'unpack' script. ##
##          you can also use the contents of the file to just         ##
##                        apt-get install <package-list>         ##
## -->  this script requires to be placed in the same folder as  <-- ##
## -->  the aptly named 'packer.pl' == which is a PERL program   <-- ##
## -->  used to edit the output of the dpkg command that lists   <-- ##
## -->  all installed programs on the machine running the script <-- ##
##                                     ##
## version            v1.0                     ##
## createdBy            Darksider                 ##
## emailAddy            darksider@swedger.com             ##
## websiteUrl            www.swedger.com                 ##
## lastEdit            08/04/2010                 ##
## thanksTo            gedit   ^_^                 ##
#######################################################################
#######################################################################

clear
echo "packup bash script v1.0"
echo "createdBy Darksider"
echo "websiteUrl www.swedger.com"
echo "this script utilises 'packer.pl', which was also created by me =]"
echo "- - - - - - - - -"
dpkg --get-selections > installed-packages.list
perl packer.pl
echo "thanks for using my code!!"
echo "--> darksider <--"
echo ""

```--- --- ---

now, when i fix up this post and give more info and possibly a TUTORIAL, i will show you how to make your own personal **bin** folder to put custom scripts and such into, so that they are easier to use and get to.
but for now, use the following command, replacing <directory tree here> with the directions to the directory where you have put your two new scripts.
```
cd <directory tree here>
```for instance, if you made** packer.pl** and **packup** on your desktop, then you would type-
```
cd /home/<your ubuntu username>/Desktop> 
```if you still don't get it, when I log into my ubuntu laptop, i click on my username which is **billy** and then i type my password.
so if i was running this command, i would type the following into my terminal-
```
cd /home/**billy**/Desktop
```so, now that you are in the directory, type the following and watch in amazement as my code works for your every whim! mwuahahahahaha.... *cough* sorry bout that...

```

chmod +x packup   [HIT ENTER]
packup                   [HIT ENTER]

```hope you liked this!!
please leave me lots of comments, whether they be good or bad. just ensure it is **constructive criticism**!!!!!!!!!

peace all, i will check back tomorrow.

-billy-
[lonewaster/darksider]
looks interesting. i ahe previously used aptoncd, which puts the list into an .iso file, then you can use aptoncd to restore that iso to a fresshly installed system. the thing I always want is an automated backup option for when a new version of ubuntu comes out and I would rather do a fresh install, tehn merely install all the apps I had in karmic into lucid and ALSO their respoective config files. BUT a diff would need to be run in case the package maintainers added new options within the configs. Example would be samba smb.conf or sshd_config etc etc. I know I can back up my /home/ foldfer and blindly restore that but that doesn't haev a lot of the changes made within /etc/ and possibly other places.

anyway, I noticed your script was last edited in August of 2010. Did you time travel into the future? just kidding. thanks for the scripts.

---

### Post by lonewaster on 2010-04-08
rofl
im from scotland, and over here we write the date day/month/year =P

thanks for the input, i will be sure and link you when my package comes out, as i hope to provide help for JUST that very purpose.
see, my new laptop doesn't seem to like linux nearly as much as me- crashing quite alot.
now that i upgraded to a fresh 64bit install with full 500.1GB partition, it only crashes once every now-and-then but still..
Acer Aspire 5732Z 4GB RAM, 500GB HD & Duo Core Intel Pentium T4400 2.4GHz.
anyways, i really appreciate the input and i will be sure to address any package configuration problems that arise from the use of my bashscript//perlapp

cheers!!

-billy-

---

### Post by pSYcl0Ne on 2011-05-24
```
lasher@mac-win-lin:~/Backup$ cd /home/lasher/Backup
lasher@mac-win-lin:~/Backup$ chmod +x packup
lasher@mac-win-lin:~/Backup$ packup
No command 'packup' found, did you mean:
 Command 'plackup' from package 'libplack-perl' (universe)
 Command 'backup' from package 'openafs-client' (universe)
packup: command not found
lasher@mac-win-lin:~/Backup$ 

```

This is what I get in Natty.

Is there a way I can get ```
aptitude search '?installed ?not(?automatic)'
``` to output to a txt file?

---

### Post by dannyboy79 on 2011-05-25
to get anything output into a text file you would use
```
>
```
so example would be
```
aptitude search '?installed ?not(?automatic)' > filename.txt
```

but, if you followed his directions all packup is is a bash script, if it's not in your "path" then you need to run it like this
```
./packup
```

+here's some info from a bash help sheet
Remember, a unix system will only only look for commands or scripts in the directories in your search path. So the system looks for the "packup" command in the directories /usr/bin and /bin, doesn't find it and returns the error message.
"command not found"
+Run the script with the command:
./packup
which means: run packup from the current directory

Hope this helped, good luck

---

### Post by zenon222 on 2011-12-03
Script worked great!

One suggestion for the future:  An analogous tool for installed sources!

I use a bunch of PPA's, so a two step "expedited install" process could clone the repositories, and then clone the installed applications!

---

### Post by dannyboy79 on 2011-12-05
haven't seen this thread in forever, is this guys script still supported? Curious, doesn't aptoncd do what this script does?

---

