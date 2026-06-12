---
title: "Frustrated Beginner"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by krstofer on 2009-06-16
Hey Guys,

I have gotten some help on this forum already, and I hate to keep posting for help, but I am getting nowhere fast. It seems everytime I try to do an everyday task, I get nothing done.

The most recent is I am trying to get an FTP program that will allow me to work with my website (m3fu.com shameless plug). I tried to download both guiFTP and IglooFTP. I tried to install both of them but I keep getting the same error:

"No Rule to make target install. Stop."

I have yet to be able to install anything outside the synaptics manager. Also, when I do install a program from synaptics manager, I often have no idea where it is or how to access it. Like I installed apache and I have no idea how to run it, where the directories are, how to set up the site, Etc.

I REALLY want to move to ubnuntu, but if I can't make anyheadway soon, I am going to have to dump it all together (which would suck).

I'm not a computer noob and I have used unix and unix commands. I am comfortable using the command prompt. When I tried to do the install I used the command "sudo make install"

I know you guys get a lot of help request, but from what I read the ubuntu crowd is the most forgiving. Any direction would be appreciated. Even how to find programs and install them properly.

---

### Post by Sef on 2009-06-16
[How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html")

It is best to to post each problem in a separate thread.

---

### Post by halitech on 2009-06-16
not to knock you being a new user but I would suggest instead of trying to download and manually installing things, synaptic is much easier. There is also Add/Remove Programs to help install items. Normally, items will show up in the menu according to the type of program you installed.

since you are familiar with the command line, I would suggest using it to install filezilla

```
sudo apt-get install filezilla
```
this will install filezilla under Apps - Network - filezilla

As far as apache, it doesn't show up in the menu but should be running as soon as you finish installing it. If you open a web browser and type in the address of [http://localhost](http://localhost) you should see your web page. As far as where the files are located, by default it is in/var/www

---

### Post by swoody on 2009-06-16
Hi krstofr, and Welcome to The Forums ):P

Unfortunately, I can't help you out with your issues, but I just wanted to let you know, that it's *PERFECTLY* ok to post new threads for *ANY* issues you have! We were all in your shoes at one point, and we all had problems that hounded us. Luckily, this is one of the most friendly and helpful forums I've ever come across on the web, so you're in good hands :D

Since you're just starting off in Ubuntu, I would *really * recommend clicking on the link in my signature and downloading a copy of The Ubuntu Beginner's Guide. It's truly a great resource to have on hand while you're learning Ubuntu, and may answer many questions that you may have! 

Again, welcome aboard! And hopefully someone else can peek in here, and lend us some advice about your ftp issue :)

---

### Post by ~sHyLoCk~ on 2009-06-16
If you want to compile a program and install from the source then you will need build-eesential.

```
sudo apt-get install build-essential
```

Now go to where the files are extracted from the tar.gz file and use:

```
./configure
make
make install
```

If it's a .deb package use:
```
sudo dpkg -i filename.deb
```

---

### Post by Fully216 on 2009-06-16
I know the transition to ubuntu can be frustrating at first, but it is definitely worth in the long run.  I now LOVE ubuntu, and very happy I stuck with it.

To transfer files to my website, I use filezilla, which you can install via synaptic.  It is usually easiest to install things there.  I have found the second easiest method to install things would be a pre-packaged *.deb file.  Making code from source would be the most difficult.

Since you are new to ubuntu, why not try what is easiest first, especially if you are getting frustrated.  Remember, we are here to help you as best we can, so feel free to ask lots of questions.

---

### Post by SOULRiDER on 2009-06-16
> **Sef said:**
> [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html")

It is best to to post each problem in a separate thread.

Reading about package management is a must, it will make installing something as simple as typing one command and everything on your system will be updated at once too!

---

### Post by Iowan on 2009-06-16
> **krstofer said:**
> I have gotten some help on this forum already, and I hate to keep posting for help, but I am getting nowhere fast. The forum would be a pretty boring place without some new "challenges". Thanks for the opportunity to expand BOTH of our minds...

---

### Post by treesurf on 2009-06-16
For a simple solution try installing the program gFTP.  You can find it in Add/Remove... or Synaptic Package Manager, or simply type in the terminal

```
sudo aptitude install gftp
```

It's an easy to use simple ftp client, and after installation it should show up in the Internet section of your Applications menu.

---

### Post by elysianfields44 on 2009-06-16
Why not connect to FTP from Ubuntu without installing third-party programs? From the top menu, try 

Places > Connect to Server > FTP with login

then enter your server and username and voila! It might not be a fancy FTP program but it works, no installation required :-)

---

### Post by HermanAB on 2009-06-16
As mentioned above, just use Nautilus (the file browser).  Click-drag-drop.  I use it all the time and it can do several protocols including SSH, FTP and SMB.  You don't need to install anything!

---

