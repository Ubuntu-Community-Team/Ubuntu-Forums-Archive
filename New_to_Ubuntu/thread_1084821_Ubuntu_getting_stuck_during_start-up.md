---
title: "Ubuntu getting stuck during start-up"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by nanso on 2009-03-02
Hello,

I installed Ubuntu 8.10 a couple of days ago and it was working fine, today it is getting stuck before starting up... After I choose the operating system (I have Windows Vista also installed) the Ubuntu logo appears with a bar showing that it's loading, this is followed by a command prompt screen showing messages like "battery power manager loading... ok" and alot of other things... And it just stays there. I left it for quite a long time, and tried a few times, but it gets stuck at the same point. When I press and hold the power on/off button to manually power off, it says "Stopping Gnome" and then turns off. Please help!

Thanks alot :)

---

### Post by FreewheelinFrank on 2009-03-02
What did you do the final day Ubuntu was working? Install new programs, updates, change settings etc. Anything you can remember might be helpful.

Did you remove the "quiet" command in GRUB to get the verbose output? Sounds like you might have.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Ben Crisford on 2009-03-02
Your ubuntu doesn't want to load the GUI it seems...  (hope the "it doesn't want to" bit don't sound to geeky :p).

Are you sure that your system specs are up to the job.  When I ran 6.10 on an old tatty laptop, it only ever loaded the GUI occasionally.

It sounds like recovery mode, if you get an oppurtunity to login as root, login and type "init 2".  (sorry if i'm offending your knowledge, you might be a genius, and i'm a bit of a numpty so sorry, but im just trying to help :s.)

---

### Post by nanso on 2009-03-03
Thanks for your replies :)
First, let me make one thing clear... I am an absolute Ubuntu beginner, so Ben, you have not offended my knowledge and I really appreciate the help :) 
FreewheelinFrank, I haven't changed anything, just installed alot of updates through Update Manager. 
The good thing is Ubuntu started when I restarted one more time (I am currently using it)...then sometime later when I restared it got stuck again, so i kept restarting till it started! 
Again, after that I installed some more updates with Update Manager.. I also installed NS2 today, which is the main reason why I installed Ubuntu in the first place...
My computer is quite new, so it should be up to the job? If u require more spec details let me know... 
Any idea what might be wrong?
Thanks again!

---

