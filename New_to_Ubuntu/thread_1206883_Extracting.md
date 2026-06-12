---
title: "Extracting"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-07-07
This always stumps me when I'm setting up programs. i download a .tar.gz or a .deb file and never know where to extract them to. i usually get messages saying i don't have permission to extract to a location. currently i'm attempting Songbird Prime 95, and Adobe Flash files, where should they be extracted to if i can't use Add/Remove or SPM?

---

### Post by jonobr on 2009-07-07
Hello


if you use the terminal window for uncompressing, it will tell you a lot more about how the thing was archived.

When you uncompress it, 

eg
gunzip application.tar.gz
this will leave you with 
application.tar
to which you can do

tar -xvf application.tar

If you see the thing unpacking with something like
/file/location/here
then its placing the files its unpacking in a certain location for you.

If the package is unpacking relative to the current directory then you should see the directory structure created under your current directory

From what you say though it sounds as if your unpacking to a location not in your home, so it may rquire you to perform this with sudo

---

### Post by Sky Pixie on 2009-07-07
A .deb file is a type of archive.  I save .deb files to the Desktop because I have permission to save files to the Desktop.

To install a .deb file, change to the directory in which the file resides and use dpkg:
```
sudo dpkg -i file.deb
```
The -i option installs the file.  The installation will fail if there are unmet dependencies.  Those unmet dependencies will be listed.  After successful installation, a .deb file can be deleted.

A .tar.gz file is a type of archive.  I save .tar.gz files to my Desktop for the same reasons as .deb files.

Change to the directory in which the file resides and extract the file using tar:
```
tar -xzf file.tar.gz
```
The -x option extracts the file, the -z option tells tar the file is .gz, and -f tells tar it is extracting a file.  A tar file can be deleted after it has been extracted.

Learn more about tar [here](http://linux.die.net/man/1/tar).

Tar will not install the file.  There are installation instructions within the extracted directory, usually contained in a text file called INSTALL.  These instructions tell you how to configure and install the application.

At the very least you will need compilers:
```
sudo apt-get install build-essential
```

Generally, the install instructions are as follows.  From inside the directory:

Configure.
```
./configure
```

Make.
```
make -j#
```
where # is the number of CPU cores +1 (Handy for dual, tri, or quad cores).

Install.
```
sudo make install
```

Codecs will specify to where they must be installed.

Ask more questions if needed.

---

### Post by Messyhair42 on 2009-07-07
so i saved songbird_1.2.0-1146_linux-i686.tar.gz to my desktop and tried the terminal commands from sky pixie it just tells me it doesn't exist. but how do i change to my desktop? i remember something about that but not how.

---

### Post by VCoolio on 2009-07-07
You can install unp (stands for unpack) after which you can do "unp file.whatever" to unpack whatever archive, like .tar, .targz, .zip etc, so you don't need these -xzfwj options you never remember at the time you need them. At least I find unp easier to remember.

To navigate use cd, so navigating to your desktop requires cd Desktop since you start in /home/username and Desktop is a folder there. Remember it's all case sensitive. You can use <tab> to autocomplete so you don't have to remember the long songbird filename, just the beginning.

---

### Post by Messyhair42 on 2009-07-07
so i used unp to extract it, and it created the folder "songbird" on my desktop, and all the files in the archive now just have a location on my desktop, still not installed

---

### Post by philinux on 2009-07-07
You need to open a terminal and then

```
cd Desktop
```

follow the instructions from the songbird readme.

.deb files downloaded to your desktop only need a double click to install. No terminal needed there. ):P

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by Messyhair42 on 2009-07-07
i used the .deb to intstall it, but in general when i get a .tar.gz how (and where) do i extract it

---

### Post by philinux on 2009-07-07
I download tar files to my desktop. After that I double click it then select Desktop from the left pane to extract it to. Then click Extract bottom right. Think extract = unzip, simple.

---

### Post by DavidFourer on 2009-07-07
> **Messyhair42 said:**
> so i saved songbird_1.2.0-1146_linux-i686.tar.gz to my desktop and tried the terminal commands from sky pixie it just tells me it doesn't exist. but how do i change to my desktop? i remember something about that but not how.
Here's my not-an-expert approach, which seemed to get me quick results with Songbird.

First I went to Synaptic Package Manager and looked for Songbird.  It's not there, but if I really wanted a music player I'd do some reading and find out if there are popular music players that are in the Ubuntu repositories.  Those are a snap to install, and lots of people have tested them.

Then, assuming I really want Songbird, I went to their web site.  It offered no information except a download option for Linux.  I clicked download.  Then Ubuntu (Jaunty jackalope 9.04) opened a window for extracting the contents automatically.  By the way, the location of the download was /tmp (a directory in the root directory, for temporary files).

I clicked on "extract" and I was asked where to put the contents.  I selected a folder in my home directory called "download", where I put temporary stuff.  You could put it in your home folder, since it's going to make a Songbird folder.

I opened a Nautilus window and selected the "download" directory so I could see for myself that it's extracting. Nautilus is the file organizer that you probably use all the time in Ubuntu (Places>Home Folder in your top menu bar).  A folder named Songbird appeared in the download directory, and I opened it. 

Folder Songbird was loaded with stuff.  One file is simply called "songbird"  That often means it's where to start, so I clicked on it.  

Amazingly, the program started running.  A set-up wizzard sort of thing ran first.  Then I got the the main window.  

This kind of surprised me, because I didn't have to do a real install with synaptic package manager or dpkg.


I've been using Ubuntu on my home computer for several years and have not had to compile anything yet.  On the other hand, it has been indispensable to teach myself the basic shell commands, read an Introduction to Linux, and read the Ubuntu forums a lot.

---

### Post by VCoolio on 2009-07-07
In general on installing anything check [this]("http://www.psychocats.net/ubuntu/installingsoftware").
It tells you also how to compile applications, which is generally needed if you download a .tar.gz, but the better way to do this (instead with configure / make / make install) is using [checkinstall]("https://help.ubuntu.com/community/CheckInstall"), since that creates a .deb and installs that, after which your app is listed in synaptic and also deletable from there. And if it is added in the repos or you add a repo for it you can update is easily. But compiling apps is more for advanced users and generally not recommended. Try to find a [.deb]("http://www.getdeb.net/") or a [repository]("http://ppa-search.appspot.com/") for your application first.
It doesn't mention adding repositories, which generally is the best way of installing apps that are not in the default repositories (the ones you search via add/remove or synaptic), because it keeps you updated. On how to add repos read [this]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by DavidFourer on 2009-07-07
VCoolio--
That's a helpful set of links.  I'll keep that in my file of "things I don't want to forget".  Thanks.

---

### Post by Messyhair42 on 2009-07-08
the next program i have to install in Prime 95, which runs under Wine. I downloaded Prime95.zip. how do i install it from there, also making sure it gets installed to the right directory.

---

### Post by frunns on 2009-07-08
> **Messyhair42 said:**
> the next program i have to install in Prime 95, which runs under Wine. I downloaded Prime95.zip. how do i install it from there, also making sure it gets installed to the right directory.

This isn't any specific instruction, but I suppose you just extract the zip, and then run the file named setup.exe or similar, and then it should automatically be installed as configured in Wine (by default I think the "c:" drive is somewhere under ~/.wine).

---

### Post by ChaiTan on 2009-07-08
Any zip/tar.gz file can be extracted through the file browser by Right Click->Extract Here. Now go to the newly created folder and double click the exe file to execute it in wine.
Windows programs will get installed by default in /home/username/.wine/drive_c/Program Files/
If the program has no setup then you can just run it from the extracted directory.

---

