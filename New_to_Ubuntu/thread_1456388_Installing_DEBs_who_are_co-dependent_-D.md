---
title: "Installing DEBs who are co-dependent :-D"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by unixisfreedom on 2010-04-17
I'm new to Ubuntu but as a result of installing have been bitten by the open source bug BIGTIME.  I wrote a cool Java app tonight at work on a Windows machine and am trying to install a JRE on Ubuntu at home so can run her there.  So I got all the DEBs to install JRE 1.6 and I'm clicking on them in Gnome, but two of each tells me they need the other?  This machine has no internet connection yet by the way (long story) so I can't use the easier automatic install procedures for stuff...

---

### Post by fromthehill on 2010-04-17
[s]you don't need the debs

you should install JRE with the following command:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

this will install JRE and the java browser plugin[/s]

nvm
answered too soon :P

you should use this command
```
sudo dpkg -i package1.deb package2.deb
```

---

### Post by mikewhatever on 2010-04-17
> **unixisfreedom said:**
> I'm new to Ubuntu but as a result of installing have been bitten by the open source bug BIGTIME.  I wrote a cool Java app tonight at work on a Windows machine and am trying to install a JRE on Ubuntu at home so can run her there.  So I got all the DEBs to install JRE 1.6 and I'm clicking on them in Gnome, but two of each tells me they need the other?  This machine has no internet connection yet by the way (long story) so I can't use the easier automatic install procedures for stuff...

You would have done that if you were in Windows, in Ubuntu, you open The Software Center, search for sun java, and click the 'Install' button. Welcome to the 21st century.;)

---

### Post by mcduck on 2010-04-17
> **fromthehill said:**
> 
you should use this command
```
sudo dpkg -i package1.deb package2.deb
```
That will do the trick.

In addition, if you have many .deb apckages you wish to install, and you are lazy (like me), this would install all the packages from the current directory:
```
sudo dpkg -i *.deb
```

> **mikewhatever said:**
> You would have done that if you were in Windows, in Ubuntu, you open The Software Center, search for sun java, and click the 'Install' button. Welcome to the 21st century.;)

Like the original poster's message tells you, he has no Internet connection on the machine, so using Software Center/Synaptic/apt-get is out of the question.

---

### Post by unixisfreedom on 2010-04-17
Thanks for the replies everyone (and so quickly!!!)...  Still can't get this to work, even though I've done "dpkg -l whatever" so make sure all the underlying dependencies of both exist... (and yes, I've sorta read that you can 'defer' the 'linkage' using dpkg)  This is exciting tho :-)  I hope I'm one day helping others like you are attempting to help me :-)

---

### Post by mcduck on 2010-04-17
What kind of roblem mare you having?

If the dpkg command complains about not finding the files, then just make sure you run the command in the same directory where the .deb packages are.

Other than that, if I remember right the Java package doesn't actually include Java but instead just loads it from the net, so that would make it a bit tricky one to install with no network connection... If that's the case you could try downloading the Java package directly from java.com.

---

### Post by unixisfreedom on 2010-04-17
Totally off topic here, but I can't put this into words how much "sense" the name "ubuntu" makes to me at this second.  This just dawned on me... Africa. The notion is "Back to the roots".  Recently I heard on National Public Radio about an African man who was writing up the news on a big board every day so his neighbors could see...  This is Ubuntu.  USAToday (not to pick on any specific corp) is Mircosoft, etc, but that guy was "Ubuntu"(?)

---

### Post by mikewhatever on 2010-04-18
Oh yeah, not internet. Here is a good tutorial for java.
[http://ubuntuforums.org/showthread.php?t=1455280](http://ubuntuforums.org/showthread.php?t=1455280)

---

### Post by unixisfreedom on 2010-04-18
Hey!  Got her to work!  Wanted to tell everyone what I did...  I took McDuck's suggestion but found I needed to change this to "sudo dpkg --force-depends -i /(path)/*.deb" ...  Not sure how 'safe' that '--force-depends' was being a n00b and all, but I can now run my Java app :-) ... Thanks everyone!

---

### Post by unixisfreedom on 2010-04-18
The only remaining squalk I have has nothing to do with Ubuntu.  One of the reasons I wanted to move this app over is because of the font "URW Gothic L Semi-Bold" that comes with Ubuntu.  Windows doesn't come with this font, and I kid you not, I love this font exactly like I would a wife (she's that fine to me). My Java app tries to use this font.  Sun's (Oracle's :-D) website says what fonts are portable depends on your JRE implementation unless is TrueType font.  Guess I missed out on this beautiful girl despite my efforts...

---

### Post by unixisfreedom on 2010-04-18
I think this raises a lot of interesting questions.  If this font is shipped with Ubuntu, is the font then open-source?  Does this mean the font author wouldn't mind porting their font into another file format?  For that matter is there a pre-written tool already to make this port?  Obviously whatever format she's in, she similar to a truetype font... (e.g. I can make her infinitely large and quality only improves--  She's done with "angles" not "bitmapped") ... There must be a way to convert into something Java 1.6 under Ubuntu can read?

---

