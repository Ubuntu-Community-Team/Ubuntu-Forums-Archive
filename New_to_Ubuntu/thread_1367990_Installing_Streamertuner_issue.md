---
title: "Installing Streamertuner issue"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by cozski on 2009-12-30
Hello

When I run the command in the terminal to extract the file streamertuner-0.99.99.tar.gz it returns this information:

cozski@cozski-laptop:~$ tar zxf steamertuner-0.99.99.tar.gz
tar: steamertuner-0.99.99.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
cozski@cozski-laptop:~$ 

Any ideas? Thanks.

---

### Post by kellemes on 2009-12-30
> **cozski said:**
> tar: steamertuner-0.99.99.tar.gz: Cannot open: No such file or directory


Is it there?
```
ls stream*
```

---

### Post by cozski on 2009-12-30
Its says 'no such file or directory' but I see it in my Dowloads folder.

---

### Post by arochester on 2009-12-30
I don't know about 9.10, but in 9.04 Streamtuner is in Repository so there is no need to compile.

See
1)"Installing Software in Ubuntu" on [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
2) "How to install ANYTHING in Ubuntu!" on [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

Have you navigated to the Directory where you uncompressed the .tar?

---

### Post by kellemes on 2009-12-30
> **cozski said:**
> Its says 'no such file or directory' but I see it in my Dowloads folder.

Make a little subfolder somewhere to unpack the tarball..
```
mkdir ~/Downloads/buildstreamtuner
```
Move the downloaded tarball to this folder..
```
mv ~/Downloads/steamertuner-0.99.99.tar.gz ~/Downloads/buildstreamtuner
```
Move yourself to this folder..
```
cd ~/Downloads/buildstreamtuner
```
Now.. unpack the thing..
```
tar -zxvf steamertuner-0.99.99.tar.gz
```

Edit: > I don't know about 9.10, but in 9.04 Streamtuner is in Repository so there is no need to compile. even better.

---

### Post by cozski on 2009-12-30
At the point of moving the file to the newly created folder it returns this message:

mv: cannot stat `/home/cozski/Downloads/steamertuner-0.99.99.tar.gz': No such file or directory

---

### Post by kellemes on 2009-12-30
> **cozski said:**
> At the point of moving the file to the newly created folder it returns this message:

mv: cannot stat `/home/cozski/Downloads/steamertuner-0.99.99.tar.gz': No such file or directory

Well.. in my case the Downloads-folder is at /home/<username>/Downloads..
Maybe it's somewhere else in your case..

You can find the file (and it's exact location) like so..
```
sudo updatedb
locate steamertuner-0.99.99.tar.gz
```

It will return the location of this file..

---

### Post by cozski on 2009-12-30
I extracted the file (Right click > extract here) in my Downloads folder and tried again but is still returning the same error message. The install file includes this info:

3. Instructions

    streamtuner uses the GNU build system. Hence, the following
    familiar sequence should satisfy most users:

        $ ./configure
        $ make
        <get root privileges, if needed>
        $ make install

    The ./configure script options are documented below. They are
    enabled by default and automatically disabled if a requirement
    is not met, so you probably do not need to use them.

Does that help? I also cant find it in my Repository...I thought that might be an easier way to install.

---

### Post by kellemes on 2009-12-30
> **cozski said:**
> I also cant find it in my Repository...I thought that might be an easier way to install.

```
sudo apt-get install streamtuner
```
from a terminal-window should work if you're using Karmic.

What version of Ubuntu are you using?

---

### Post by arochester on 2009-12-30
Alternatively go here: [http://allmyapps.com/search/ubuntu-9.10/all/1?q=streamtuner&cat=&sub=&rank=relevancy/desc&filters=](http://allmyapps.com/search/ubuntu-9.10/all/1?q=streamtuner&cat=&sub=&rank=relevancy/desc&filters=)

Click on the orange button that says Free - and Install when you roll over it.

---

### Post by cozski on 2009-12-30
> **kellemes said:**
> Well.. in my case the Downloads-folder is at /home/<username>/Downloads..
Maybe it's somewhere else in your case..

You can find the file (and it's exact location) like so..
```
sudo updatedb
locate steamertuner-0.99.99.tar.gz
```It will return the location of this file..

It tells me it's here:

/home/cozski/.local/share/Trash/files/streamtuner-0.99.99.tar.gz
/home/cozski/.local/share/Trash/files/buildstreamtuner/streamtuner-0.99.99.tar.gz
/home/cozski/.local/share/Trash/info/streamtuner-0.99.99.tar.gz.trashinfo
/home/cozski/Downloads/streamtuner-0.99.99.tar.gz

After going through the process of moving the file and then extracting again it returned this:

cozski@cozski-laptop:~$ mkdir ~/Downloads/streamtuner-0.99.99tar gz ~/Downloads/buildstreamtuner
cozski@cozski-laptop:~$ cd ~/Downloads/buildstreamtuner
cozski@cozski-laptop:~/Downloads/buildstreamtuner$ tar -zxvf streamtuner-0.99.99.tar.gz
tar: streamtuner-0.99.99.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
cozski@cozski-laptop:~/Downloads/buildstreamtuner$

---

### Post by ajgreeny on 2009-12-30
> **cozski said:**
> At the point of moving the file to the newly created folder it returns this message:

mv: cannot stat `/home/cozski/Downloads/**steamertuner**-0.99.99.tar.gz': No such file or directory
As others have said, use the repos for ease, but also note it is not "streamertuner" as you wrote but "streamtuner" which may be why your command is getting you nowhere.

Also note that in post 11 you are trying to use a file/folder in trash, which can not be done.  You need to restore it to a usable folder, preferably in home, first.

---

### Post by cozski on 2009-12-30
> **kellemes said:**
> ```
sudo apt-get install streamtuner
```from a terminal-window should work if you're using Karmic.

What version of Ubuntu are you using?

Thanks... I did it this way... I'm using 9.10 which I only installed yesterday with no other OS installed. Anyway, that has worked. It seems there's a problem installing the other way and I'd be concerned the same problem may arise with another application... should I be doing something to check? Also, how do I enable 'root'... in some install instructions I looked at it said I needed to ensure that I have this... any thoughts?

Big thanks again for all the support :P

---

### Post by cozski on 2009-12-30
> **ajgreeny said:**
> As others have said, use the repos for ease, but also note it is not "streamertuner" as you wrote but "streamtuner" which may be why your command is getting you nowhere.

Also note that in post 11 you are trying to use a file/folder in trash, which can not be done.  You need to restore it to a usable folder, preferably in home, first.

Hey... yeah, I kinda noticed that too but I corrected it and it still wasn't happening. Also, you;ll notice that their are several versions of the file because I ditched 2 of them and downloaded it thinking it may have been an issue with the d/l process. There's still a version of it in my Download folder. Thanks.

---

### Post by ajgreeny on 2009-12-30
I have never installed a tarball for anything in ubuntu so far and not needed to, other than a beta version of Thunderbird 3, which does not need compiling but simply contains an executable file in the archive.

Almost everything is available from the repositories, so forget about doing things the windows way, and open up synaptic, or Add/Remove (or whatever it is now called in 9.10) and search in that first, then ask here if you can't find something, as a deb may be available from a ppa repo, if not in the main repos.

---

### Post by kellemes on 2009-12-30
> **cozski said:**
> It seems there's a problem installing the other way and I'd be concerned the same problem may arise with another application... should I be doing something to check?

No, everything is fine..

> **cozski said:**
> Also, how do I enable 'root'... in some install instructions I looked at it said I needed to ensure that I have this... any thoughts?

Yes, read [this]("https://help.ubuntu.com/community/RootSudo").
You should never 'enable' root, not needed. Just read the documentation, it's important to know.

Glad we could help.

---

### Post by cozski on 2009-12-30
Thanks again... really appreciate it. I completely ditched my XP OS yesterday after duel booting with Ubuntu for the last couple of months and I'm prepared to put the leg work in to become as familiar with my functionality needs within Ubuntu... but a little help goes a long long way! :)

---

### Post by oldos2er on 2009-12-30
> **cozski said:**
> It seems there's a problem installing the other way and I'd be concerned the same problem may arise with another application... should I be doing something to check? 

You just need a little more familiarity with shell commands. See [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) and [http://ubuntulinuxhelp.com/friday-fun-useful-linux-terminal-commands-for-new-users/](http://ubuntulinuxhelp.com/friday-fun-useful-linux-terminal-commands-for-new-users/) and [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by cozski on 2009-12-31
Thanks for the sign posting Ann... I'll take a look :)

---

### Post by cozski on 2010-01-02
Thanks... I just did a clean install from the link you gave me... works fine... although it doesn't appear to be able to connect to the 365live list so probably not going to be that useful :( Cheers for help though folks :)

---

