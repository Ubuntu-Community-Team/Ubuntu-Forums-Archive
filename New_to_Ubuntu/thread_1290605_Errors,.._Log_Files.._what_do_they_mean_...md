---
title: "Errors,.. Log Files.. what do they mean .. ??"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Kaizzer on 2009-10-13
Hello everyone .. 
The following are absolutely a newbie questions. 

im new to this Linux/Ubuntu world (3 weeks or so) and in this time i've been trying to install/compile/modify several applications or files..from Desktop Themes to applications like conky passing through USB modem configuration. Since im new to this, its not an extrange thing that i made some mistakes.. but this i think is a very good way to lear about Linux. 

The problem is that in some cases, i made my ladtop crash a lot and it has stoped me to keep learning couse im affraid to damage this Ubuntu instalation and some how lost all my data.. and here the very frist question:

1) Is there a real danger of loosing all my data some how? im using a personal folder on my desktop to manage all my files. (work & personal). What operations/acctions should i consider as forbiden in linux so i wont face that risk ?

2) in some crashes, my machine goes directly to reboot so i can not see what errors are.. (i was trying to complile the "conky" app on 8.04 and it was a mess....) is there any log where i can see what went wrong? .. also in some of those crashes and on reboot, it shows some errors but they dont appear for long .. (looks like windows error when having files corrupted.. ) 

3) i've looked . on the log file viewer but it has little information for me to pull of since i dont know where to lookup to .. if someone could redirectme to the propper information link or explain it to me.. would be most appreciated. 

Thank you all in advance.. 
Regards.

---

### Post by oldos2er on 2009-10-13
There's always a possibility of data loss; keeping good backups is always a must, in my opinion.

 Why are you compiling programs? Much easier to install them from the repositories. See [https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html) and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Kaizzer on 2009-10-14
> **oldos2er said:**
> There's always a possibility of data loss; keeping good backups is always a must, in my opinion.

 Why are you compiling programs? Much easier to install them from the repositories. See [https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html) and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

yup .. i know it easier but some applications or versions are not "packageged" for my version ie 8.04 .. that was the case of conky .. but the main reason is ... i wanted to doit :) 

Thank you for your post !
Regards.

---

### Post by Kaizzer on 2009-10-15
what about Log Files ?? could anyone give me a clue on what to search in where.. ?
TIA

---

### Post by Zill on 2009-10-15
> **Kaizzer said:**
> yup .. i know it easier but some applications or versions are not "packageged" for my version ie 8.04 .. that was the case of conky ...
[http://packages.ubuntu.com/hardy/conky]("http://packages.ubuntu.com/hardy/conky")

---

### Post by Kaizzer on 2009-10-15
> **Zill said:**
> [http://packages.ubuntu.com/hardy/conky](http://packages.ubuntu.com/hardy/conky)

Yes ive got to this page...but i wanted to use conky 1.7.2 and that version is for conky 1.5.1..

Regards..

---

### Post by Zill on 2009-10-15
> **Kaizzer said:**
> Yes ive got to this page...but i wanted to use conky 1.7.2 and that version is for conky 1.5.1..
Unless you are *very* experienced with Linux I suggest that this is really not a good idea!

If you want your system to be stable and reliable then stick to the version appropriate for the OS.  If you start trying to install later versions of software you may well end up in "dependency hell" and break your system.

Similarly, if you install compiled software, rather than deb packages, you will lose the automatic update capability that helps make Ubuntu so wonderful. :-)

---

### Post by Kaizzer on 2009-10-15
> **Zill said:**
> Unless you are *very* experienced with Linux I suggest that this is really not a good idea!

If you want your system to be stable and reliable then stick to the version appropriate for the OS.  If you start trying to install later versions of software you may well end up in "dependency hell" and break your system.

Similarly, if you install compiled software, rather than deb packages, you will lose the automatic update capability that helps make Ubuntu so wonderful. :-)

i see your point... but ...if i take all the necessary precautions and back up all my work and and applications that i need.. and i still wanted to install some applications, the question is.. where do i look for the errors... 

some times, doing some of the things that ive learned here (Forums) .. Ubuntu crashes and bloks..or simply reboots (unclean reboot) ..  but i don't know what went wrong .. if i follow your advise.. i feel ..(please lets discuss if i am right in this statement ) that im not gonna learn anything at all.. 

thats the main reason for this thread, where, what & how to read the errors form systems log. Take in consideration that im completly new to this linux environment, although i had some experienciene with Unix in the past and ive been workking in SW development on Lotus Domino for 6 years now.. ie .. it is not like i was my mother traying to learn about linux when all she knows is how to turn on a computer.. 

hope you see my point here .. looking forward for your responce..
kind regards..

---

### Post by Zill on 2009-10-15
Kaizzer:  My PC *never* "...crashes and bloks..or simply reboots (unclean reboot)..." - but I stick to the right apps for the OS and do not compile my own software. :-)

However, you do what you like - it's your PC!

As far as logs are concerned, you will find them all in /var/log.

To view a log either use the GUI in the System, Administration Menu or use the terminal eg:
```
cat /var/log/syslog | less
```

---

### Post by Kaizzer on 2009-10-19
Zill, Thanks for your responses to this thread. i will take your comments into notice but still .. the main question of log files or where to see errors remains.

what kind of errors or notifications are shown in each log file ? 
where do i look for information when the PC freezes and doesnt come back .. ? o when it raises and error on console and re-boots instantly ? where can i see the last error msg that was shown on console..? 

thanks in advance. 
regards.

---

### Post by Rayve on 2009-10-19
Kaizzer,

As stated by others, I think it's best to use stable packages appropriate for your distribution and the capabilities of your computer, but again, you're free to experiment and learn.  :)

I'm a beginner myself, and part of the learning process is reading the logs.  Checking out the code that Zill provided will allow you to view some of the logs (in a new window, if I'm not mistaken).  There you can see all sorts of messages, and if there are some you don't understand, you can post them back here (use [code] tags) and folks can take a better look at exactly what problems you may be running in to.

A netbook user on the forums was having an issue with not booting up properly, and it looks like some error logs were written to /var/log/kern.log but yours may be different.  You may need to do some searching in your /var/logs files, just choose to "open in window" or "read" or whichever the option is (I'm not on my Linux partition just yet) instead of "execute" if you happen to use the GUI option vs CLI.

Here's that other post I mentioned: http://ubuntuforums.org/showthread.php?t=1290732

Happy learning!

---

### Post by Kaizzer on 2009-10-19
Rayve

Thanks for your post. As i said, ill try to install only recommended .deb files for my actual OS. but sometimes you can't play by the book. ie .. im now trying to install an USB Modem (i really dont have much option here) and its giving me some headaches.. system crashing .. and .. all the same stuff that ive described earliaer.. 

so the primary questions remains 
regards :)

---

### Post by Zill on 2009-10-19
Kaizzer:  I understand that you, as we all do, want to learn more about Ubuntu.

However, it seems to me that you are intent on breaking your system by using the wrong apps for the OS version and then playing around with compiled versions of programs, rather than using the correct packages.

I expect your log files to be full of errors showing this.  All I can suggest is that you look at all the logs in /var/log as I described earlier.  This should list the errors you are experiencing and help you get more familiar with the syntax.  Most logs have a date/time stamp to show a particular event.

Unfortunately, I doubt that you would be able to eliminate these errors if you continue installing as before. :-(

---

### Post by Kaizzer on 2009-10-19
ok ..ok .. i wont anymore ..

---

