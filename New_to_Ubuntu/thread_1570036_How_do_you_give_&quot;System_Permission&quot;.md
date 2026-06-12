---
title: "How do you give &quot;System Permission&quot;?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by DayLite on 2010-09-07
I downloaded Thunderbird from[ here]("http://sourceforge.net/projects/ubuntuzilla/files/") It is Thunderbird 3.1.2. Now I tried to see about updates and this message came up.
[IMG]http://inlinethumb34.webshots.com/12961/2936520180056553245S425x425Q85.jpg[/IMG]

How do I give system permissions so I can receive updates? The latest stable is Thunderbird 3.1.3.

I downloaded it directly from Thunderbird but I don't know how to install it. It ends in
tar.bz2.

Source forge hasn't updated their file so I can't get it from there.

---

### Post by gldearman on 2010-09-07
I don't use Thunderbird, but, 

Instead of launching Thunderbird in the normal way, launch it from the command line with:

```

sudo thunderbird

```

Then, go about trying to update as before.  Since you'll be acting with root privileges, you should have all of the privileges you need.

Another alternative would be to install Thunderbird 3.1.4 from the Ubuntu Mozilla Daily Build Team&#8217;s package archive.  You can follow the instructions on [this website]("http://digitizor.com/2010/06/25/how-to-install-thunderbird-3-1-in-ubuntu-10-04/").  Of course, that's a bleeding-edge build, and not a stable release.  So, you may not want to do that.

I think it is most likely that your tar.bz2 file contains source code, and you could install from source as a last resort.  I generally shy away from installing from source if I don't have to, since it has caused me more problems than it has been worth in the past.  But, if you need to do it, post back here, and someone will help you out.

Hope this helps.

---

### Post by Bölvaður on 2010-09-07
read it all through before doing anything.

there seems to be some repository for it, unofficial. [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I dont know what you got there, but it is a file archive (.tar) that has been compressed (.bz2) so all you need to do to get to those files is to double click it (open with file-roller) or right click and click *open with Archive Manager*. And from there you put it where ever you keep the programs your user owns.

I dunno.. how did you install it to begin with?
If you did it through some repos but they havent been updated yet and want the internal updating machansm to work then all you need to do is something like pressing Alt+F2 and type
```
gksu thunderbird
```
enter your password and QUIT the program right after it updates, you do not want to have programs using higher privileges than they need

---

### Post by Bölvaður on 2010-09-07
> **gldearman said:**
> Your tar.bz2 file is source code

umm... no... it's just a file archive with already compiled files. When I move large number of photos between places I put them in a .tar.gz or .tar.bz2. It really doesnt need to be source to be in this type of file.

---

### Post by gldearman on 2010-09-07
> **Bölvaður said:**
> enter your password and QUIT the program right after it updates, you do not want to have programs using higher privileges than they need

That's an excellent point, and very important.  Whether you use sudo or gksu, close immediately after updating.

> **Bölvaður said:**
> umm... no... it's just a file archive with already compiled files. When I move large number of photos between places I put them in a .tar.gz or .tar.bz2. It really doesnt need to be source to be in this type of file.

Well, yeah.  I mean, anything could be in that archive.  It could be a copy of the Voynich Manuscript :).  I din't download the archive and open it, so I don't know.

But, usually, when I have downloaded the latest version of software, and it's only available as a .tar.gz or .tar.bz2 file, the archive contains the source code.  I don't think I've ever seen it contain anything else, though, of course, it could.  It will also probably contain instructions to build from source, if that's what it is.

---

### Post by DayLite on 2010-09-07
> **gldearman said:**
> I don't use Thunderbird, but, 

Instead of launching Thunderbird in the normal way, launch it from the command line with:

```

sudo thunderbird

```Then, go about trying to update as before.  Since you'll be acting with root privileges, you should have all of the privileges you need.



[SIZE=3]**It worked**:D[/SIZE] Thank you so very much. When Thunderbird was launched I asked it to check for updates and it updated to [SIZE=2]**Thunderbird 3.1.3**[/SIZE]

---

### Post by DayLite on 2010-09-07
> **Bölvaður said:**
> 
I dunno.. how did you install it to begin with?


I don't understand how to use the terminal, so I went to [http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)  I found this on the site ```
[thunderbird-mozilla-build_3.1.2-0ubuntu1_i386.deb]("http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1.2-0ubuntu1_i386.deb/download")
```
and it downloaded and I clicked on it and it installed very easy.

---

### Post by DayLite on 2010-09-07
> **gldearman said:**
> That's an excellent point, and very important.  Whether you use sudo or gksu, close immediately after updating.

Well, yeah.  I mean, anything could be in that archive. .

I downloaded the file from[ http://www.mozillamessaging.com/en-US/thunderbird/download/?product=thunderbird-3.1.3&os=linux&lang=en-US]("http://www.mozillamessaging.com/en-US/thunderbird/download/?product=thunderbird-3.1.3&os=linux&lang=en-US")

That is the Official Thunderbird Download site.

---

