---
title: "Too may downloads"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2009-01-20
Hi,
I just downloaded 6 out of a possible 519. How do I clear the rest so the computer doesn't keep telling me about them?

---

### Post by RequinB4 on 2009-01-20
If you're talking about updates, you can choose to have the program stop notifying you of available updates for that program:

[http://ubuntuforums.org/showthread.php?t=747470](http://ubuntuforums.org/showthread.php?t=747470)

However, it is HIGHLY recommended that you keep your system updated (just keep it downloading overnight or something), to prevent security risks and fix annoying bugs.  The ubuntu devs don't release updates willy-nilly.  If something is there, you should definitely have it.

---

### Post by OldTimeTech on 2009-01-20
If you don't download and install all of the downloads you leave your machine open to problems...as it says in the download, these are to maintain your security and keep your machine running at optimal condition.

Since you've installed ubuntu either hardy or intrepid a large number of update have come out to fix problems...you need these...so finish the download...it doesn't take that long.

---

### Post by oldsoundguy on 2009-01-20
> **OldTimeTech said:**
> it doesn't take that long.

except if you are on dial-up or entry level DSL!! LOL

I just did an Intrepid re-install using my original disk last month .. 20 minutes to install everything from the disk .. then nearly 2 hours on 15mbps cable to get the updates from all of the repositories! (they doubled my cable speed since.)

---

### Post by Dermot Doyle on 2009-01-20
I take the point and have updated everything in the past, but a Farsi translation update and a Slovakian Thesaurus among the 513 don't seem vital to the security of my computer. If I can't just delete the ones I don't want I'll download them all. I don't doubt for a second that the originators of the updates know more then me, nor am I not grateful for all the work that goes into open source software, but I am surprised that I can only chose between updating everything and not being notified of available updates.
Cheers

---

### Post by shredder12 on 2009-01-20
You might have not noticed this but you have a check box at the beginning of the name of the software to be updated ( in you update manager ) if you don't want to download that update then you can uncheck that checkbox .. 
I think this will probably solve your problem..

---

### Post by lukjad on 2009-01-20
Never cancel an install halfway through. I did that a few times, and almost had to reinstall.

---

### Post by Joe computer on 2009-01-20
It was my impression that you could do what the above poster mentioned (with the check boxes), but i'm not on my ubuntu box

---

### Post by oldsoundguy on 2009-01-20
Lots of those "updates" are in reality, just an update MANAGER that leads to the file in the repository.  It would be completely impossible to store all of that info on a standard computer.  So when you update, you are just updating the device for INSTALLING the program, not the program itself and if you don't INSTALL the program, it will not be on your computer.

Only those programs you have actually installed will update automatically from the repositories when you do your do on the update notice!

---

### Post by lukjad on 2009-01-21
> **oldsoundguy said:**
> Lots of those "updates" are in reality, just an update MANAGER that leads to the file in the repository.  It would be completely impossible to store all of that info on a standard computer.  So when you update, you are just updating the device for INSTALLING the program, not the program itself and if you don't INSTALL the program, it will not be on your computer.

Only those programs you have actually installed will update automatically from the repositories when you do your do on the update notice!

Ummm... What? I'm not sure I understand you. Do you mean to say that updating is bad?

---

### Post by Paqman on 2009-01-21
> **Dermot Doyle said:**
> a Farsi translation update and a Slovakian Thesaurus among the 513 don't seem vital to the security of my computer.

You can use localepurge to trim down the language updates you receive. It's in the repos.

Also, you could limit your updates to security-only. Go to System > Admin > Software Sources > Updates and uncheck everything except security.

---

### Post by tom56 on 2009-01-21
Not really a fix, but it might make sense to download the updates then install them later. That way you can just let them download in the background while you do other stuff but if decide you want to turn off the computer you can cancel without any damage.

Running the following command in a terminal will download the updates, but not install them.
```
sudo apt-get update && sudo apt-get -yd upgrade
```
If you want to stop and carry on later just close the terminal window. Run the same thing again to carry on downloading the rest. Once it says download complete, close the terminal and run Update Manager to actually install the updates.

Hope this helps!

---

### Post by Dermot Doyle on 2009-01-21
Thanks for all the advice. Shredder12, yes I used the tick boxes to chose the few I wanted to upload, it was the other 513 that the computer carried on notifying me about that I was concerned with. In fact I have taken notice of an erlier reply and let it upload them all. As long as I'm not filling my computer needlessly I guess I'm not bothered.
Cheers

---

### Post by Paqman on 2009-01-22
> **Dermot Doyle said:**
> As long as I'm not filling my computer needlessly I guess I'm not bothered.
Cheers

The update should notify you of how much extra space will be required after you update. Generally this is very little, and sometimes updates actually use less space than the current versions.

---

### Post by rzrgenesys187 on 2009-01-22
If the amount of time is going to be a factor if you open synaptic and check software sources there is a test you can run which will switch the server you are downloading from to one that gets you faster speeds.  I'm not running ubuntu right now so I can't tell you exactly how to do it but it was pretty easy if I recall correctly

---

