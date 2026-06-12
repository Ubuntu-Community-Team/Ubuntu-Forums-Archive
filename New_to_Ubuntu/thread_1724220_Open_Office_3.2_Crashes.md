---
title: "Open Office 3.2 Crashes"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by nns2006 on 2011-04-08
Hello,
I was writing my master's thesis in OpenOffice 3.2. I was using it because of its easy to use mathematical formula functions. However, It gives me nightmare yesterday when it crashes multiples( more than 10) times within 10 min. 
what I was doing: writing document which contains a lot of equations and I wanted to copy these three pages of document into the main document. first few crashes occurs while copying these equations and further crashes occurs when i pasted (when I think that it has copied, which it has not) in into main document. 
My question: what should I do now? should I use some other program to write my thesis which involves a lot of equations. due date is 30th april.

My system: Ubuntu 10.10, 2 gb ram, 1.6ghz c2d processor, 160gb hard disk,

---

### Post by Paddy Landau on 2011-04-08
Yeesh, I've had similar problems. My OO often crashes when I use large graphics. My workaround has been to close every single other program on the computer, so nothing else but OO runs; and even then it still often crashes.

I hope someone can answer this question.

Have you considered installing [Libre Office]("http://www.libreoffice.org/")? It will replace OpenOffice in an upcoming release of Ubuntu. I haven't had the time to try, but it's worth checking if it solves the problem.

---

### Post by Enigmapond on 2011-04-08
> **Paddy Landau said:**
> Yeesh, I've had similar problems. My OO often crashes when I use large graphics. My workaround has been to close every single other program on the computer, so nothing else but OO runs; and even then it still often crashes.

I hope someone can answer this question.

Have you considered installing [Libre Office]("http://www.libreoffice.org/")? It will replace OpenOffice in an upcoming release of Ubuntu. I haven't had the time to try, but it's worth checking if it solves the problem.

+1! I HAVE had the time to try it and it is, by far, a much better programme than OO. I highly recommend it. I also use it at the office with a room full of MSOffice and have had NO problems!

Cheers!

---

### Post by r-senior on 2011-04-08
Do you happen to have a .log file in your home directory? I can't recall the exact name, but it's something like h1234pid.log.

If you do, and it was about the same time Open Office crashed, could you post it? (Remember to wrap it in code tags - or highlight and use the '#' button in the forum toolbar).

EDIT: Another +1 for LibreOffice by the way. Renders MS Office documents much better, fonts are better.

---

### Post by Paddy Landau on 2011-04-09
> **Enigmapond said:**
> +1! I HAVE had the time to try it and it is, by far, a much better programme than OO. I highly recommend it. I also use it at the office with a room full of MSOffice and have had NO problems!
> **r-senior said:**
> Another +1 for LibreOffice by the way. Renders MS Office documents much better, fonts are better.
Well, it looks as though I will be installing Libre Office soon!

> **r-senior said:**
> Do you happen to have a .log file in your home  directory? I can't recall the exact name, but it's something like  h1234pid.log.
I have not seen such a file in my home directory, despite many crashes. I also searched through the .openoffice.org folder, and none there. Maybe the OP has something.

---

### Post by Daniel0108 on 2011-04-09
I had crashes too, but then I installed LibreOffice and it worked perfect :D

So, +1 for LibreOffice,

Daniel

---

### Post by Paddy Landau on 2011-04-09
Boo! :( I've installed Libre Office, and it crashes exactly the same as does OO.

I have the log file, though. I have [attached it]("http://ubuntuforums.org/attachment.php?attachmentid=188548&d=1302347357") (I had to compress it first). The crash seems to have something to do with Java:
```
A fatal error has been detected by the Java Runtime Environment
```

EDIT: The log file says to submit a report to [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp), which I have done.

---

### Post by r-senior on 2011-04-09
Hmm, I was going to suggest trying another Java, i.e. if you were on Sun, try OpenJDK and vice versa.

However, I found this:

[https://lists.launchpad.net/openjdk/msg05177.html](https://lists.launchpad.net/openjdk/msg05177.html)

Which looks like almost exactly the same problem with OpenJDK. Your Java, Paddy, is Sun's Java.

I did some Googling of the error message but found no solutions.

So I've run out of suggestions really. Apart from that you ought to report it as a bug with OpenOffice and LibreOffice rather than Sun Java (or indeed with OpenJDK). The common factor appears to be a library from OpenOffice/LibreOffice.

In case you weren't aware, LibreOffice is a fork of OpenOffice and shares the same code base. Over time it will diverge of course - the reason for the LibreOffice project being to have a guaranteed FOSS project regardless of what Oracle choose to do with OpenOffice.

---

### Post by uRock on 2011-04-09
I have had this problem with OpenOffice in the past.

I found that the reason in my case was just the need to save the file, so that OO has something to do its backup saves to.

---

### Post by Paddy Landau on 2011-04-09
Hmm, thanks for that.

The automated reporting system has already reported it to Open Office umpteen times. I shall check the OO forum to see if anyone else has reported it.

---

### Post by Paddy Landau on 2011-04-09
> **uRock said:**
> I found that the reason in my case was just the need to save the file, so that OO has something to do its backup saves to.
I don't quite understand that. These are documents that I have saved and am editing. I have turned off the automatic backup save, because for large documents it's way too slow.

---

### Post by uRock on 2011-04-09
> **Paddy Landau said:**
> > I found that the reason **in my case**I don't quite understand that. These are documents that I have saved and am editing. I have turned off the automatic backup save, because for large documents it's way too slow.

OO creates a backup file every so often. If there is no filename for it to use when it makes the ~bak file, then it will crash. To prevent this I have to save the file when I first start so that OO has a filename to use.

---

### Post by Paddy Landau on 2011-04-10
> **uRock said:**
> OO creates a backup file every so often. If there is no filename for it to use when it makes the ~bak file, then it will crash. To prevent this I have to save the file when I first start so that OO has a filename to use.
Thanks for the clarification. I always save my document very soon after starting a new one, so that's a problem I won't get.

I wish I knew the answer to this. As I mentioned in post #7, it seems to be Java-related.

@nns2006: You have not responded. Do you get an error log file in your home directory?

---

### Post by Ophidion on 2011-04-11
I had the same problem trying to copy from writer. I have been running another java application that was monitoring clipboard that I thought it is the reason for the crash. Of course after I closed that application the crash stopped happening any more.

---

### Post by Ophidion on 2011-04-11
> **Paddy Landau said:**
> .... it seems to be Java-related....

I think so as I said closing the other java app and writer stopped crashing!!

---

### Post by 5149.5 on 2011-04-11
> **uRock said:**
> OO creates a backup file every so often. If there is no filename for it to use when it makes the ~bak file, then it will crash. To prevent this I have to save the file when I first start so that OO has a filename to use.

Thanks. I'll keep that in mind now.

---

### Post by Paddy Landau on 2011-04-12
Oracle has accepted this bug report:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7035324](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7035324)

If you register and log in, you can vote for the bug:
[http://bugs.sun.com/bugdatabase/addVote.do?bug_id=7035324](http://bugs.sun.com/bugdatabase/addVote.do?bug_id=7035324)

Be aware that Sun's site is extraordinarily slow. Load the page and wait a few minutes (really) before it responds. But be patient in order to vote for it. It will be worth it to stop the crashes in Open Office and Libre Office.

---

### Post by nns2006 on 2011-09-11
First of all I am very sorry that It took me so long to reply. But in April I was so busy writing my thesis that I forget I have asked a question. I will answer each one categorically now.


> **Paddy Landau said:**
> Thanks for the clarification. I always save my document very soon after starting a new one, so that's a problem I won't get.

I wish I knew the answer to this. As I mentioned in post #7, it seems to be Java-related.

@nns2006: You have not responded. Do you get an error log file in your home directory?

My problem was related to copying a large equation containing page, which I had written earlier into main thesis. I realized it that OO is having problem handling large document.So, I started writing in pages. One page at a time, if it contains equation. and copying it to the main document in 4-5 parts. it helps me overcome crashes.
I tried the java suggestion but it does not help me. 

> **Paddy Landau said:**
> Boo! :( I've installed Libre Office, and it crashes exactly the same as does OO.

I have the log file, though. I have [attached it]("http://ubuntuforums.org/attachment.php?attachmentid=188548&d=1302347357") (I had to compress it first). The crash seems to have something to do with Java:
```
A fatal error has been detected by the Java Runtime Environment
```

EDIT: The log file says to submit a report to [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp), which I have done.

Tried LO now. It also can't handle the heavy equations.:( Though, LO & OO have distinct advantage over MS in equations according to me.

> **uRock said:**
> I have had this problem with OpenOffice in the past.

I found that the reason in my case was just the need to save the file, so that OO has something to do its backup saves to.

Now, I have made auto-save at every 5 min, so that I don't loose my work. Name the file and then save it and start writing in it. This way I didn't loose any of my work.

Thanks to OO for it, without which I could not have been possible.

---

### Post by Paddy Landau on 2011-09-12
> **nns2006 said:**
> Now, I have made auto-save at every 5 min, so that I don't loose my work.
That doesn't work for me. For me, when OO or LO save a large document, it sits around for two or three minutes; so, putting it on autosave means every two minutes I have to stop working and wait for three minutes, after which it might or might not have crashed!

This constant crashing is a nuisance.

---

### Post by nns2006 on 2011-09-12
> **Paddy Landau said:**
> That doesn't work for me. For me, when OO or LO save a large document, it sits around for two or three minutes; so, putting it on autosave means every two minutes I have to stop working and wait for three minutes, after which it might or might not have crashed!

This constant crashing is a nuisance.

Thats true. But if you don't want to loose your work please do so unless some workaround is found for it.

Also, when I was writing thesis, I split the document in Chapter, Heading and sub-heading . This way I can go on writing without keeping all of the work at a single place. Towards the end , put all of them into a single one . Amount of copying will vary, if only text- you can go ahead with a page at a time. If equations or graphics- do it part wise.

This strategy has helped me. I hope it might help you too.

---

### Post by Paddy Landau on 2011-09-12
> **nns2006 said:**
> But if you don't want to loose your work please do so unless some workaround is found for it.
Unfortunately for me, it won't work. For those large documents, autosave just makes me wait significantly more than 50% of the time, and often crashes anyway. I manually save at strategic points, and don't add the large images until everything else is perfect.

> **nns2006 said:**
> ... I split the document...
Now, that would be an idea if my document had such a structure, and if the pages didn't need moving around in relation to each other. Sadly, even that option is not available to me.

Thanks for the ideas, though.

---

