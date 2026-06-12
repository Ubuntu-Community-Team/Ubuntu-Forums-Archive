---
title: "ur lisnce has expired !!!!"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by mountdiat on 2011-01-24
pleas ...
after installation of oss  this time   it said  ur lisnce has expired !!!!  and icant listen any sounds

i type osstet in terminal ..i hear sound !!!   but all media not have any sound 
 what is the problem?

---

### Post by mountdiat on 2011-01-24
pleas the sound stop after 3 monthes of excellent and fine use of ubuntu ...what is the problem?

---

### Post by bioterror on 2011-01-24
First of all tell us what's your version of ubuntu, what have you been using and something more.

This doesnt tell us anything.

---

### Post by migs73 on 2011-01-24
By the looks of wikipedia ([http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)) you didn't install from the repos?

If you did it would be the older free version, rather then the newest (V4) licensed one, which it would appear you have.

---

### Post by mountdiat on 2011-01-24
ubuntu 10.4 descktop

motherboard giga bite g41 
using ubuntu from 15/10/2010
only this problem
sound not installed well .
i use oss to install sound ....and no problems 

but now when install oss4.2.deb.........message appear at end of installation ..your oss  license has expired

---

### Post by migs73 on 2011-01-24
> **mountdiat said:**
> ubuntu 10.4 descktop

motherboard giga bite g41 
using ubuntu from 15/10/2010
only this problem
sound not installed well .
i use oss to install sound ....and no problems 

but now when install oss4.2.deb.........message appear at end of installation ..your oss  license has expired

See the link I posted above, V4+ (oss**4.2**.deb) are closed source/licensed software.

If you install using synaptic package manager, you will get the free (V3?) version of the software.

EDIT- I tell a lie, just checked synaptic and it is V4.2??? Are you downloading the deb from 4Front or using synaptic?

---

### Post by mountdiat on 2011-01-24
4Front.......

---

### Post by migs73 on 2011-01-24
> **mountdiat said:**
> 4Front.......

That'll be your problem then.

Use Synaptic (System>Administration>Synaptic Package Manager) put in your password when requested.

Type OSS in the search box, click on the box next to the package to install (it'll tell you if it requires to install other packages and auto select them if you wish)  and select 'Mark for installaition'. Click the green tick (Apply) and it'll do its stuff.

Regards

Mike

---

### Post by mountdiat on 2011-01-24
click on the box next to the package



any package...oss4base ...oss4dev...etc

---

### Post by mountdiat on 2011-01-24
must i remove oss  already installed?

---

### Post by migs73 on 2011-01-24
Base sounds good to me!

As I said if there anre any other packages (dependencies) it requires it'll tell you, just accept them to be downloaded too.

I believe from your other posts, you have a GUI for controlling OSS, if not mark the GTK for download too.

---

### Post by mountdiat on 2011-01-24
thanks migs .... now i going to do some thing and i well tell you what happen   thanks for your help:KS

in Arabic....&#1587;&#1604;&#1575;&#1605;
by English ...peace;)

---

### Post by migs73 on 2011-01-24
You're welcome,

In Scots Gaelic....Slainte Mhath

In English....... Good Health


Mike.

---

### Post by mountdiat on 2011-01-24
hi mig
i remove  4front deb  and install ossbase and gtk...making test  


mghiar@ubuntu:~$ osstest
/dev/mixer: No such file or directory
mghiar@ubuntu:~$ 

see....the same problem.....
in SM the version of oss is 4.2

---

### Post by Bölvaður on 2011-01-24
Is there any special reason why you are using OSS ?
ALSA replaced OSS as default in 2007 and now PULSE is taking over pretty seamlessly (for me but not everyone). The people that have problem with PULSE are recommended to use ALSA and not OSS unless there is a special reason for it.

My recommendation would be to uninstall OSS completely and install ALSA.

May I ask why you dont use the defaults like they come of the installation disk?



btw it might not always been good idea to install things outside of the repositories, specially when you are starting out and if the package already is in official ubuntu repositories.

---

### Post by mountdiat on 2011-01-24
now i remove oss from SM and re download afresh 4front oss deb "oh the file version is changed...my old is 4.2 2003  but now 4.2 2004" installing and every thing is good ..[COLOR=DarkRed]but it remain trial [/COLOR]:confused:
thanks again migs for your time   
Now...in Arabic [SIZE=4][COLOR=DarkGreen]&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605; &#1608;&#1585;&#1581;&#1605;&#1577; &#1575;&#1604;&#1604;&#1607; &#1608;&#1576;&#1585;&#1603;&#1575;&#1578;&#1607;[/COLOR][/SIZE]
in English[SIZE=4][COLOR=DarkGreen] Peace, mercy and blessings of God....):P[/COLOR][/SIZE]

---

### Post by mountdiat on 2011-01-24
[Bölvaður]("http://ubuntuforums.org/member.php?u=338535")
my lover,,,[COLOR=Black][URL="http://ubuntuforums.org/member.php?u=338535"]i install ubuntu in alot of my freinds computer and sound is ok 
but my motherboard not accept deault alsa .. if you have amethod please tell me
my motherboard is giga g41[/URL][/COLOR]

---

### Post by migs73 on 2011-01-24
> **mountdiat said:**
> now i remove oss from SM and re download afresh 4front oss deb "oh the file version is changed...my old is 4.2 2003  but now 4.2 2004" installing and every thing is good ..[COLOR=DarkRed]but it remain trial [/COLOR]:confused:
thanks again migs for your time   
Now...in Arabic [SIZE=4][COLOR=DarkGreen]&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605; &#1608;&#1585;&#1581;&#1605;&#1577; &#1575;&#1604;&#1604;&#1607; &#1608;&#1576;&#1585;&#1603;&#1575;&#1578;&#1607;[/COLOR][/SIZE]
in English[SIZE=4][COLOR=DarkGreen] Peace, mercy and blessings of God....):P[/COLOR][/SIZE]

Did you follow the instructions you weree given before regarding installing OSS ([http://ubuntuforums.org/showpost.php?p=9872284&postcount=4](http://ubuntuforums.org/showpost.php?p=9872284&postcount=4))

This is the first time I have seen mention of this error (/dev/mixer: No such file or directory)in your posts i think it would be better to try and get that sorted than use the licensed version. At least you won't have to do this every 3 months!
I'm not at Ubuntu machine right now, but a quick google on the error has thrown up a few possibilties, if you want to look into it more.

---

### Post by sdowney717 on 2011-01-24
why bother with OSS anymore?

Now you use ALSA and Pulse
here is what I have installed for ALSA and PULSE

---

### Post by migs73 on 2011-01-24
> **sdowney717 said:**
> why bother with OSS anymore?

Now you use ALSA and Pulse
here is what I have installed for ALSA and PULSE

You're right it would be even better (easier!!).

I assume the OP is using OSS for reason?

---

