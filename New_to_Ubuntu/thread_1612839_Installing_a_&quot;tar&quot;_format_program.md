---
title: "Installing a &quot;tar&quot; format program"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-11-03
I know it's here somewhere but can't find it.

Trying to do update/rebuild on my website using Kompozer and was given the recommendation at that forum to download and install the latest version, 0B8.3. Went to do that and it's in "tar" format.

Where are the instruction on how to download, save and install from "tar"?

Thanks.

---

### Post by ivarn on 2010-11-03
open the archive and see if it has a readme file.
The usual way to extract it and cd command to the folder with the terminal.
cd /home/username/Desktop/extracted_archive
now run 
```
./configure
``````
make
``````
sudo make install
```.
There you go.
EDIT: OH and to extract the archive, right click on it > extract here.

---

### Post by flyfishingphil on 2010-11-03
Don't see an "archive file" listed anywhere in the download. Is there something I need to open the "box" with to view that?  also, a little more explanation on your steps above. Like, open terminal, type in XXXX, hit enter, type in XXX. 

I'm here at absolute for a reason. Very slow learner with brain damage from a head injury!

---

### Post by ivarn on 2010-11-03
I thought you said the download file was a tar.gz file (which is an archive file).

---

### Post by flyfishingphil on 2010-11-03
Told you I was a slow learner!

Yes, I have the "container box" on my desktop. Clicked on that and opened the folder. Don't see a "read me" file in the long list that appears.

Tried using the steps you listed in the above. Terminal > entered the cd/home, etc. Get back "No such file found"

---

### Post by coffeecat on 2010-11-03
@flyfishingphil, if that's the 1:0.8~b3-2 version of Kompozer you want, you don't have to compile it from source. There's a PPA you can add to your sources for this. See:

[https://launchpad.net/~giuseppe-iuculano/+archive/ppa]("https://launchpad.net/%7Egiuseppe-iuculano/+archive/ppa")

Just do this is a terminal...

```
sudo add-apt-repository ppa:giuseppe-iuculano/ppa
```Then open Synaptic, do a reload and it should appear in the package list for installation, or upgrade if you have an earlier version already installed.

---

### Post by ivarn on 2010-11-03
ok right click the icon and you'll see it says "extract here".
Now you'll have the archive extracted on your desktop.
open the terminal and do the command directory.
cd /home/username/Desktop/the_new_folder
now follow my last post guide.

---

### Post by flyfishingphil on 2010-11-03
See if I'm entering this correct in Terminal:

flyfishingphil@ffpC-Rods:~$ cd/home/flyfishingphil/Desktop/kompozer
bash: cd/home/flyfishingphil/Desktop/kompozer: No such file or directory

---

### Post by ivarn on 2010-11-03
no, cd is the command so cd <space> location.
when you are in the folder, type in ./confugure, then make, followed by sudo make install.

---

### Post by flyfishingphil on 2010-11-03
Doesn't seem to matter how I enter the cd home, etc I still get back file not found

OK, Here are the results so far:

flyfishingphil@ffpC-Rods:~$ cd /home/flyfishingphil/Desktop/kompozer
flyfishingphil@ffpC-Rods:~/Desktop/kompozer$ ./configure
bash: ./configure: No such file or directory

Am I doing something else wrong?

---

### Post by coffeecat on 2010-11-03
@flyfishingphil, since you have ignored my earlier post I assume/hope you missed it. All I can say is: save yourself heartache and misery. Install from the PPA. It's so much simpler.

---

### Post by ivarn on 2010-11-03
OK here.
open the terminal and type paste this line in:
sudo apt-get install nautilus-open-terminal

This will install a right-click shortcut for the terminal.
Now you can open the terminal wherever you wish. That's easier. now you don't have to do the whole cd /location thing.
Now open the compozer folder and right click, click "open in terminal" and do the ./configure, make, sudo make install commands.
EDIT Or you can do what [coffeecat]("http://ubuntuforums.org/member.php?u=129087") said.

---

### Post by flyfishingphil on 2010-11-03
Didn't ignore Coffeecat, just tried doing it that way. The Komposer button is avaiable under Application > Internet or Applications > Programming. Click on either and get nothing. No Kompozer opens. Any thoughts on that?

Have tried everything I can think of. Uninstalled, shut down and restarted. Did a fresh download. Followed steps given by ivarn. Followed suggestions given by coffeecat. Doesn't seem to matter what I do Kompozer does not open when I click on the icon in either Applications > Internet or Applications > Programming.


When I go to Applications > Software Center and look up Kompozer it shows as installed. When I go to System > Synaptic Manager and check on Kompozer it shows as installed. No matter what I try it will not open. Suggestions on what may be wrong or how to correct the problem?

---

### Post by flyfishingphil on 2010-11-04
Hello! Anybody here? Any idea on how to get Komposer to actually work in Lucid Lynx?

Followed all of the instructions above but Komposer not opening. Any help greatly appreciated.

Another question. Would anybody have any idea on how I might install Serif WebPlus 10 in WINE? Tried that but didn't seem to be able to get it installed.

MORE INFO:

Still trying to get it to work properly but still won't respond when clicking on icon in Applications. However, in looking at other resources came across a suggestion and tried it. Went into KompoZer folder and clicked on kompozer page (5th down on right) and it offers option to open in terminal. Clicked that, terminal opened then kompozer opened with all of the pages I have worked on still in there. Is there something in KompoZer I need to set to get it to open clicking on the icon in Applications > Programming?

---

