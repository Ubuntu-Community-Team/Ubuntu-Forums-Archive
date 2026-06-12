---
title: "Verifying running Python scripts (and deleting if necessary)"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by biofuelfarmer on 2009-09-11
A few questions from a novice Jaunty user:  

[LIST=1]
[*]How does one determine what Python scripts are loaded and running (or that can load based on a chron job)?
[*]Once you find them how do you examine them?
[*]And how does one delete those scripts if necessary?
[/LIST]
I have not picked the right phrases to put in Google to figure this out.

(I used a Python script to do a Firefox 3.5.3 update so I could add an FTP plug-in.  The Firefox update script -ubuntuzilla- worked great, came off of Sourceforge with lots of positive comments etc, seemed quite legit.  But when I went to give the developer a few $ I noticed that his main product was a keystroke logger.   It looks like the files for this upgrade script went into a directory called kcopyd_job that I can't delete.  Giving me the heebie jeebies!)

Many thanks to anyone that can help.

---

### Post by Liolikas on 2009-09-11
ps wa | grep *.py
Something like that if we believe that all python scripts end with .py. 
You can **less** them like:
less blabla.py (give maybe even nothing if you do not know python look python.org for tutorial)
Use folder manager or **rm** them. 
Be careful avoid removing important things!

---

### Post by Copernicus1234 on 2009-09-11
Which ftp plugin is this? Sounds strange. Are you sure you havent misunderstood it?

Is the plugin on mozillas plugin site as well?

---

### Post by biofuelfarmer on 2009-09-11
Thanks for your note Copernicus.  I see my original post wasn't as clear as it should be.   It was the update script to get to Firefox 3.5.0 that I was talking about.  I needed to get to that rev so I can install the FireFTP plug-in.  (Unfortunately no Cute FTP for Linux I have come to learn.)

Oh and Liolikas, I ran the command you suggested and all I got was:

14131 pts/0    S+     0:00 grep *.py   

That is a pretty innocuous looking response, and one that looks good, I think.

The pertinent links about ubuntuzilla are here:

[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#tochome7](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#tochome7)
[http://sourceforge.net/project/project_donations.php?group_id=147501](http://sourceforge.net/project/project_donations.php?group_id=147501)

Undoubtedly I am just being paranoid, and this developer is totally above board.  Frankly the script worked as advertised.   That is why I decided to donate.   It was just a surprise to be linked to a keystroke logger donation page.

I would like to learn how to better understand everything that is running in the background in Ubuntu.  The folks from McAfee "protected" me from all that stuff when I was using Microsoft.  Of course the computer often slowed to a crawl because of their program, but I digress.  The other thing I used to do in XP was periodically look through everything that showed up in task manager.  If I didn't recognize the process, I Googled it.

I really appreciate the assistance from this board.

---

### Post by Liolikas on 2009-09-11
> 
Oh and Liolikas, I ran the command you suggested and all I got was:

14131 pts/0 S+ 0:00 grep *.py

That is a pretty innocuous looking response, and one that looks good, I think.

You see shadow of yourself here: nothing interesting.
try to run custom python script and try again same command you see good results.

>It was just a surprise to be linked to a keystroke logger donation page.
So donate. :D 

>The folks from McAfee "protected" me from all that stuff when I was using Microsoft. 
So try to scan that zip file from 3rd link with mcafee and you maybe will change your mind. Maybe not.

Important stuff that py is just text files so you really on people who understand Python and will not allow to place keylogger.py renamed into fun_game.py and so on. Not like exe where it is almost impossible to tell what is inside you just guess or really on anti virus soft and that soft makes mistakes 1 time from 10.

---

### Post by nanotube on 2009-09-11
> **biofuelfarmer said:**
> 
(I used a Python script to do a Firefox 3.5.3 update so I could add an FTP plug-in.  The Firefox update script -ubuntuzilla- worked great, came off of Sourceforge with lots of positive comments etc, seemed quite legit.  But when I went to give the developer a few $ I noticed that his main product was a keystroke logger.   It looks like the files for this upgrade script went into a directory called kcopyd_job that I can't delete.  Giving me the heebie jeebies!)


Hi :)

i'm the developer of ubuntuzilla (and also of pykeylogger). i can assure you they are completely separate projects, and have nothing to do with each other. (everything being open source, you don't have to take me at my word, and can examine the source directly.)

also, nothing in ubuntuzilla does anything with "kcopyd_job" - that must have come from somewhere else. i did a quick google, and it seems that kcopyd is some memory management thing for the linux kernel.

hope that helps... :)

---

### Post by nanotube on 2009-09-11
> **biofuelfarmer said:**
> 
Undoubtedly I am just being paranoid, and this developer is totally above board. 

a little paranoia never hurt anyone.
> 
Frankly the script worked as advertised. 

glad to hear that :)
> 
That is why I decided to donate.   It was just a surprise to be linked to a keystroke logger donation page.

that was simply a typo (a copy-paste-o, really) on my part, that link has now been corrected to point to ubuntuzilla project donations.

> 
I would like to learn how to better understand everything that is running in the background in Ubuntu.  
take the same approach as you would in windows - look at the process list, and google each one you don't know. 

getting a process list is easy - just run "ps -ax" in a terminal, or run the gui system monitor and select "view -> all processes" in the processes tab.

---

### Post by biofuelfarmer on 2009-09-11
Liolikas and nanotube, thanks for your comments back.   

This has been a good learning experience for me.   Great that the code is open and easily examinable on a peer review basis; the community at large keeps everyone honest.

Oh and yes, I followed the new link and donated! :)

---

### Post by nanotube on 2009-09-12
> **biofuelfarmer said:**
> Liolikas and nanotube, thanks for your comments back.   

This has been a good learning experience for me.   Great that the code is open and easily examinable on a peer review basis; the community at large keeps everyone honest.

Oh and yes, I followed the new link and donated! :)

really appreciate your support! :D

---

