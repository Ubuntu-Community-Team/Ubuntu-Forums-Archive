---
title: "Firefox and chromium problem"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by anand_30 on 2010-05-10
I installed ubuntu 10.04 yesterday.Its very good experience to use it.Its one of the best os i have used.Thank you ubuntu.

But due to my old computer(2.4 Ghz, 1.25 gb RAM, 40Gb HD which has booting troubles) i am facing some problems.


Today morning while i was downloading some songs using firefox my comp as usual hung up and restarted.Then when i tried to open firefox,it was showing me nothing,so i reinstalled it.Still i was unable to open firefox.So i installed chromium using synaptic and while installation also it hung up and restarted(what a comp!!!!).After that i removed broken packages and then again installed chromium.At the end of the installation it showed me some error message but i ignored it as chromium was working perfectly.

As i use firefox for mass downloading,i thought of removing it completely and again installing,and did it.That time also i got some error message.

Now when i am trying to completely remove or remove or reinstall firefox or chromium i am getting this error message:-

An error occurred

The following details are provided:
E: chromium-browser: subprocess installed post-installation script returned error exit status 2

Help me to get proper firefox and chromium browser.
At present they are working normally.

---

### Post by narendraD on 2010-05-10
How much RAM do you have? 1.25GB or 125MB?

---

### Post by anand_30 on 2010-05-10
I have 1.25 Gb of RAM,(256Mb was initially present and I added 1 Gb extra 3 years back).I have used 9.10 for complete six months and i preferred to install 10.04 instead of upgrading from 9.10.Its a dual boot with windows xp.I am new to such type of error.

Is bad condition of my HD the cause of such problem?because my HD is about 5 and half years old and its giving me booting problems.

---

### Post by narendraD on 2010-05-10
I do not think it has anything to do with age of your hardware. It may have everything to do with any site that you were browsing at that moment. Java, Flash or downloads sometimes do crash firefox. But a simple restart should have brought it back.

---

### Post by anand_30 on 2010-05-10
[IMG]http://ubuntuforums.org/home/anand/Desktop/Screenshot.png[/IMG]I have attached file showing detailed error message when I tried to reinstall chromium.
[IMG]http://ubuntuforums.org/home/anand/Desktop/Screenshot.png[/IMG]

---

### Post by anand_30 on 2010-05-11
There was no way of getting over this problem.I also tried repair broken dependencies in recovery mode but there also i got the same error.


So today i freshly installed ubuntu 10.04 again.Now everything looks great,no troubles uptill now.Thank you narendraD for your help.


I know this is not the place to ask such question but can anyone please help me telling that if my computer is not booting properly(it requires some tries atleast 10 to 20),what is the problem? should i buy a new hard disk(as computer repair person told me to buy new one)but i think there is some other problem,please advice me as i am gonna use this comp for a month or two(Its really bad when you have such comp during your holidays when u want to do chatting,gaming and surfing).

This pc worked OK when the repair person done something called low level formatting four months back!!!Also it always tends to hang.

An advice will be good:)

---

### Post by narendraD on 2010-05-11
> **anand_30 said:**
> There was no way of getting over this problem.I also tried repair broken dependencies in recovery mode but there also i got the same error.


So today i freshly installed ubuntu 10.04 again.Now everything looks great,no troubles uptill now.Thank you narendraD for your help.


I know this is not the place to ask such question but can anyone please help me telling that if my computer is not booting properly(it requires some tries atleast 10 to 20),what is the problem? should i buy a new hard disk(as computer repair person told me to buy new one)but i think there is some other problem,please advice me as i am gonna use this comp for a month or two(Its really bad when you have such comp during your holidays when u want to do chatting,gaming and surfing).

This pc worked OK when the repair person done something called low level formatting four months back!!!Also it always tends to hang.

An advice will be good:)


10 to 20 tries just to boot ? Its difficult to pinpoint but my guess would be the hard disk has too many bad sectors. Get into the BIOS of your motherboard and see if you can enable SMART. SMART is a utility in the MB that keeps track of the Hard Disks health and the OS can read it. If its already there it should show up in Sysytem--> Admin--> Disk Utility as a SMART status.

My comp too is over 4 years old and the HD has some bad sectors, but not so bad. If your HD is the culprit then i think you should not trust it with your personal and irreplaceable data. An OS can be reinstalled any number of times, but photos and other stuff cant be regenerated. So advice you to backup to CD or other plave and then if HD is the problem then replace it.

---

### Post by anand_30 on 2010-05-11
> **narendraD said:**
> 10 to 20 tries just to boot ? Its difficult to pinpoint but my guess would be the hard disk has too many bad sectors. Get into the BIOS of your motherboard and see if you can enable SMART. SMART is a utility in the MB that keeps track of the Hard Disks health and the OS can read it. If its already there it should show up in Sysytem--> Admin--> Disk Utility as a SMART status.

My comp too is over 4 years old and the HD has some bad sectors, but not so bad. If your HD is the culprit then i think you should not trust it with your personal and irreplaceable data. An OS can be reinstalled any number of times, but photos and other stuff cant be regenerated. So advice you to backup to CD or other plave and then if HD is the problem then replace it.

SMART utility is on and surprisingly its showing me that my DISK IS HEALTHY !!!!!
How this is possible?I think the problem is somewhat different than i thought of.

Oh and thanks for suggestion about important data on my HD,I have backed it up on DVD.

Thank you for your advice.I really appreciate your help.

---

