---
title: "Sift not working an Ubuntu 8.10"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by flo-alb on 2009-03-12
Hi friends,

i am on ubuntu since 2 weeks. dont know what happend but now my shift key is not working any more. caps is ok on normal letters. but it is not possible for me to write perentesis - shift + 7 - or so.

my system
lenovo think pad T400
ubuntu 8.10 with all fixes
german keyboard - set to layout GERMAN DEAD ACUTE with keyboard model IBM THNIKPAD R60+T60+R16+T61

i have read a lot about that problem. but nothing solved it. also - setxkbmap - is not working or any reboot. it is just like that. but if iam working on my windows in vmware player everything is just fine.

can anybody help me....

THANKS

---

### Post by jijlj on 2009-03-13
I had the same problem, with just the shift key not working. After hunting around online I think I found the solution provided by mkirchbe here: 

[http://ubuntuforums.org/showthread.php?t=785029](http://ubuntuforums.org/showthread.php?t=785029)

I went to:

System -> Preferences -> Appearance -> Visual Effects

I noticed that none of the options were selected. I selected the Extra option and that seems to have fixed it. I don't know how all of them were de-selected, but they were and selecting something fixed it for me.

I was disappointed that I did not find this first on the Ubuntu forums, but on a Google search on a yahoo site: [http://answers.yahoo.com/question/index?qid=20080615105659AA7EBNc](http://answers.yahoo.com/question/index?qid=20080615105659AA7EBNc)

---

### Post by flo-alb on 2009-03-13
Hi, 

thanks for your reply - but it has not change anything. But you have had pasted a link - and from there i got the following side with the solution:

[URL="http://ubuntuforums.org/showthread.php?t=785029"]http://ubuntuforums.org/showthread.php?t=785029
[/URL]
> Thanks because of you I was able to fix it as I had the same problem.

System>Preferances> Advanced Desktop Settings

Click on General Options
click commands tab extend key bindings

Run Command 0 will say Shift+F19 in my case.


Change it to shift+ alt or just disable it.

Mine was caused because I installed grandr. I removed it because I couldn't get it to work and if it works for you it may render the shift + f7 shortcut useless.

This worked for me !!!!

Thank YOU very much - you are my personal Hero now! :D =D> \\:D/ ):P

Florian

---

