---
title: "TrueCrypt"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-31
I downloaded the tar.gz file, but am not sure how to install it. Any help?

---

### Post by Krabby.Linux on 2010-07-31
1. extract the file (rightclick and extract here
2. go to your folder where truecrypt is located
3. give rights for the file : chmod +x filename.xx
4. sudo ./filename.xx to install

---

### Post by TimEnid on 2010-07-31
> **Krabby.Linux said:**
> 1. extract the file (rightclick and extract here
2. go to your folder where truecrypt is located
3. give rights for the file : chmod +x filename.xx
4. sudo ./filename.xx to install

thanks. but im lost between steps 2 and 3. go to my folder where truecrypt is located? where would that? and for part 3, do i type that in a terminal?

---

### Post by Krabby.Linux on 2010-07-31
Step 2 :

You can navigate with the Terminal :

If you type in (without quotes): 
"ls"  --> lists whatever is inside the folder
"cd .." --> goes back one step (previous folder, example: if you are in .../home/Timenid/ and you type cd .. you are in ../home/)
"cd foldername" --> goes into the named folder if it exists (you can see if it exists by typing in "ls"


And Yes, you should type that in. Do not forget to replace the text with the name of your file.

I am sorry my english is not that good I hope you understand .... I Have found a guide on how to install Truecrypt on Ubuntu this is a step by step guide, hope it helps. [http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

---

### Post by TimEnid on 2010-07-31
still totally lost. even after reading the thread in that link.

---

### Post by cjv8888 on 2010-07-31
> **TimEnid said:**
> I downloaded the tar.gz file, but am not sure how to install it. Any help?

After you extract the tar.gz file, you get a setup file.
All you need to do is to double click it and click run.

---

### Post by bodhi.zazen on 2010-08-01
First, what are you trying to install ? a tar.gz is an archive, like a zip file, it can contain anything.

Second, why are you not installing from the Ubuntu repos ?

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

WIth that in mind, archives (tar.gz) are generally source code, you then compile it

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

If you are trying to install truecrypt, why not use the .deb ?

[http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/](http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/)

Last, you understand there are alternates to truecrypt ? LUKS, ecryptfs, cryptkeeper ? all in the repos.

---

### Post by quinnten83 on 2010-08-01
> **bodhi.zazen said:**
> First, what are you trying to install ? a tar.gz is an archive, like a zip file, it can contain anything.

Second, why are you not installing from the Ubuntu repos ?

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

WIth that in mind, archives (tar.gz) are generally source code, you then compile it

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

If you are trying to install truecrypt, why not use the .deb ?

[http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/](http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/)

Last, you understand there are alternates to truecrypt ? LUKS, ecryptfs, cryptkeeper ? all in the repos.

the latest truecrypt is not i the repo's. Also If you want windows compatibility with the encrypted files on windows, there is a version of truecrypt for windows and they interoperate like a charm.

---

### Post by Krabby.Linux on 2010-08-01
Thats what I found out using google. Ubuntu wont find the Truecrypt version he needs.

---

### Post by gandaran on 2010-08-01
> **TimEnid said:**
> I downloaded the tar.gz file, but am not sure how to install it. Any help?
it's very easy if you can follow these instructions, download the tar file and extract the package, move the extracted file to your /home/user directory (very important this, the file must be on your user folder so that you have permission to execute the file) now open the terminal and type **sudo sh** plus space, then drag the file with the mouse and drop it in the terminal, this will complete the path to the file in the terminal, hit enter, type your password and enter again, when the truecrypt install window opens you can choose to install or extract the portable version.

---

### Post by bodhi.zazen on 2010-08-01
> **quinnten83 said:**
> the latest truecrypt is not i the repo's. Also If you want windows compatibility with the encrypted files on windows, there is a version of truecrypt for windows and they interoperate like a charm.

This is because of truecrypt's licensing.

You may use LUKS cross platform:

[http://www.freeotfe.org/](http://www.freeotfe.org/)

---

### Post by Primefalcon on 2010-08-01
right click extract files... make sure it's executable by right clicking->properties->permissions->tick execute box then just double click on the file and follow the prompts, simple

---

### Post by gandaran on 2010-08-01
> **Primefalcon said:**
> right click extract files... make sure it's executable by right clicking->properties->permissions->tick execute box then just double click on the file and follow the prompts, simple
well I have to ask you, did you try/test your method? 
can you explain how it works then because the only way I see is to run it from the terminal?

---

### Post by Primefalcon on 2010-08-01
> **gandaran said:**
> well I have to ask you, did you try/test your method? 
can you explain how it works then because the only way I see is to run it from the terminal?
after you extract and make executable and then double click on it, and it'll give you the option to run in terminal, say yes and it basically handles everything just answer a couple of prompts, that's it

---

### Post by Primefalcon on 2010-08-01
here's a quick youtube vid I just did even

[http://www.youtube.com/watch?v=MEeoVAxUpIE](http://www.youtube.com/watch?v=MEeoVAxUpIE)

---

### Post by gandaran on 2010-08-01
> **Primefalcon said:**
> after you extract and make executable and then double click on it, and it'll give you the option to run in terminal, say yes and it basically handles everything just answer a couple of prompts, that's it
no, it doesn't give any option, it just opens with gedit with an error message that it cont display the file, but I am going to try set it open in terminal if possible, will post back.

---

### Post by Primefalcon on 2010-08-01
> **gandaran said:**
> no, it doesn't give any option, it just opens with gedit with an error message that it cont display the file, but I am going to try set it open in terminal if possible, will post back.
Look at the vid

---

### Post by gandaran on 2010-08-01
> **Primefalcon said:**
> Look at the vid
that doesn't work in ubuntu!
unless you first set the file to open with the terminal in properties which is not set as default in ubuntu. you will have to do it or this method wont work

---

### Post by Primefalcon on 2010-08-01
> **gandaran said:**
> that doesn't work in ubuntu!
unless you first set the file to open with the terminal in properties which is not set as default in ubuntu. you will have to do it or this method wont work
I am running a stock standard install of Ubuntu...... And I did that video myself

if the file is executable you will get that option dialog box..... try it

---

### Post by gandaran on 2010-08-01
> **Primefalcon said:**
> I am running a stock standard install of Ubuntu...... And I did that video myself

if the file is executable you will get that option dialog box.....
well I did get it to work your way but after I added xterm to the list of applications to open the file, so I think the standard ubuntu installation doesn't have that option or is it only mine is different?
and yes I have to agree it's the easiest way to install but still people will run into the problem if they don't know how to add the xterm to the open applications list.

---

### Post by Primefalcon on 2010-08-01
> **gandaran said:**
> well I did get it to work your way but after I added gnome-terminal to the list of applications to open the file, so I think the standard ubuntu installation doesn't have that option or is it only mine is different?
and yes I have to agree it's the easiest way to install but still people will run into the problem if they don't know how to add the gnome-terminal to the open applications list.
All I know is if the file is executable and you open it you will get that option. I do a bit of c++ coding and a lot of web and shell coding so I see that a lot...

Oh it's great to have multiple ways of doing things, I just prefer to show new comers a graphical way if possible (99% of the time there is now, never used to be that way). And Ubuntu really is leading the way at making Linux easier

---

### Post by gandaran on 2010-08-01
> All I know is if the file is executable and you open it you will get that option. I do a bit of c++ coding and a lot of web and shell coding so I see that a lot...
the file was marked as executable, but still it doesn't work like you showed in the video, the video was to fast, I didn't get to see what you choose from the drop-down menu to open with, maybe you have something installed that I haven't.
the way I tried by adding gnome-terminal to the list worked very well and even more simpler that the video way, just selecting open in terminal opened the install window, that is one option I will keep enabled in the open list menu for future use now.

edit:
sorry it wasn't gnome-terminal but xterm, in fact it won't work with choosing gnome-terminal from the menu list but works nicely choosing xterm, duno why!

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> it's very easy if you can follow these instructions, download the tar file and extract the package, move the extracted file to your /home/user directory (very important this, the file must be on your user folder so that you have permission to execute the file) now open the terminal and type **sudo sh** plus space, then drag the file with the mouse and drop it in the terminal, this will complete the path to the file in the terminal, hit enter, type your password and enter again, when the truecrypt install window opens you can choose to install or extract the portable version.

tried this and got a Permission Denied message. I am trying the other options now.

---

### Post by TimEnid on 2010-08-01
> **Primefalcon said:**
> right click extract files... make sure it's executable by right clicking->properties->permissions->tick execute box then just double click on the file and follow the prompts, simple

this did not work.

---

### Post by TimEnid on 2010-08-01
> **Primefalcon said:**
> here's a quick youtube vid I just did even

[http://www.youtube.com/watch?v=MEeoVAxUpIE](http://www.youtube.com/watch?v=MEeoVAxUpIE)

followed the directions in your video, after it installs, i dont see it anywhere to be able to launch it. after i press enter after installation, the terminal exits and thats it.

---

### Post by gandaran on 2010-08-01
> **TimEnid said:**
> tried this and got a Permission Denied message. I am trying the other options now.
if you got the Permission Denied  message then you did not follow my instructions, you have to type **sudo sh** in the terminal first only then you drag the file in the terminal, there must be a space between sudo sh and the file.

please copy and post here the complete error message, only then I can tell what is the problem.

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> if you got the Permission Denied  message then you did not follow my instructions, you have to type **sudo sh** in the terminal first only then you drag the file in the terminal, there must be a space between sudo sh and the file.

please copy and post here the complete error message, only then I can tell what is the problem.

i followed the directions in the video. it seems to have installed, but i cant launch it. however, when i type "truecrypt" in a terminal, i get all its options.

> Usage: truecrypt [--auto-mount <str>] [--backup-headers] [--background-task] [-C] [-c] [--create-keyfile] [--delete-token-keyfiles] [-d] [--display-password] [--encryption <str>] [--explore] [--export-token-keyfile] [--filesystem <str>] [-f] [--fs-options <str>] [--hash <str>] [-h] [--import-token-keyfiles] [-k <str>] [-l] [--list-token-keyfiles] [--load-preferences] [--mount] [-m <str>] [--new-keyfiles <str>] [--new-password <str>] [--non-interactive] [-p <str>] [--protect-hidden <str>] [--protection-keyfiles <str>] [--protection-password <str>] [--random-source <str>] [--restore-headers] [--save-preferences] [--quick] [--size <str>] [--slot <str>] [--test] [-t] [--token-lib <str>] [-v] [--version] [--volume-properties] [--volume-type <str>] [Volume path] [Mount point]
  --auto-mount=<str>         	Auto mount device-hosted/favorite volumes
  --backup-headers           	Backup volume headers
  --background-task          	Start Background Task
  -C, --change               	Change password or keyfiles
  -c, --create               	Create new volume
  --create-keyfile           	Create new keyfile
  --delete-token-keyfiles    	Delete security token keyfiles
  -d, --dismount             	Dismount volume
  --display-password         	Display password while typing
  --encryption=<str>         	Encryption algorithm
  --explore                  	Open explorer window for mounted volume
  --export-token-keyfile     	Export keyfile from security token
  --filesystem=<str>         	Filesystem type
  -f, --force                	Force mount/dismount/overwrite
  --fs-options=<str>         	Filesystem mount options
  --hash=<str>               	Hash algorithm
  -h, --help                 	Display detailed command line help
  --import-token-keyfiles    	Import keyfiles to security token
  -k, --keyfiles=<str>       	Keyfiles
  -l, --list                 	List mounted volumes
  --list-token-keyfiles      	List security token keyfiles
  --load-preferences         	Load user preferences
  --mount                    	Mount volume interactively
  -m, --mount-options=<str>  	TrueCrypt volume mount options
  --new-keyfiles=<str>       	New keyfiles
  --new-password=<str>       	New password
  --non-interactive          	Do not interact with user
  -p, --password=<str>       	Password
  --protect-hidden=<str>     	Protect hidden volume
  --protection-keyfiles=<str>	Keyfiles for protected hidden volume
  --protection-password=<str>	Password for protected hidden volume
  --random-source=<str>      	Use file as source of random data
  --restore-headers          	Restore volume headers
  --save-preferences         	Save user preferences
  --quick                    	Enable quick format
  --size=<str>               	Size in bytes
  --slot=<str>               	Volume slot number
  --test                     	Test internal algorithms
  -t, --text                 	Use text user interface
  --token-lib=<str>          	Security token library
  -v, --verbose              	Enable verbose output
  --version                  	Display version information
  --volume-properties        	Display volume properties
  --volume-type=<str>        	Volume type


---

### Post by gandaran on 2010-08-01
look in applications » accessories » truecrypt

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> look in applications » accessories » truecrypt

no there. i checked everywhere

---

### Post by gandaran on 2010-08-01
TimEnid
I just curios, when you followed the video what option did you choose from the menu to open the file, was it just 'open' like in the video?
I ask because I don't have the 'open' option on the truecrypt file, what I have is 'open with gedit' and 'open with' which neither work unless I set to open with xterm, I wonder why my ubuntu is diferent?

---

### Post by gandaran on 2010-08-01
> **TimEnid said:**
> no there. i checked everywhere

I think you installed the command line version, go back and download the standard package.

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> TimEnid
I just curios, when you followed the video what option did you choose from the menu to open the file, was it just 'open' like in the video?
I ask because I don't have the 'open' option, what I have is 'open with gedit' and 'open with' which neither work unless I set to open with exterm, I wonder why my ubuntu is diferent?

yes, it was "open"

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> I think you installed the command line version, go back and download the standard package.

i downloaed the 64bit version found on this page
[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

edit: i see what u mean. downloading now

---

### Post by MCVenom on 2010-08-01
Uhh nevermind..

---

### Post by TimEnid on 2010-08-01
> **gandaran said:**
> I think you installed the command line version, go back and download the standard package.

> **TimEnid said:**
> i downloaed the 64bit version found on this page
[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

edit: i see what u mean. downloading now

got it. thanks for all the help. everyone.

---

### Post by TimEnid on 2010-08-01
> **BlackOtaku said:**
> I think bodhi.zazen solved this thread awhile ago :P

there is no .deb file.
i was downloading and running the wrong file.

---

### Post by MCVenom on 2010-08-01
> **TimEnid said:**
> there is no .deb file.
i was downloading and running the wrong file.
Yeah.. I noticed after I posted. Sorry bout that. :|

---

### Post by Primefalcon on 2010-08-01
yeah you need the standard version, the console version is command line only

---

### Post by gandaran on 2010-08-02
> **Primefalcon said:**
> yeah you need the standard version, the console version is command line only
Primefalcon
I found out why your method din't work for me, it was simple, because I dual boot windows I need to open .txt files in the windows partition so I changed the nautilus preferences to open files instead of asking what to do, reverting to the default settings works.
sorry for the misunderstanding.

---

