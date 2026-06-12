---
title: "Opera Browser problems"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by tropdoug on 2009-07-01
I am trying the Opera browser and really like its speed and features, except one thing I have a website with an embedded mp3 player (a google Gadget) and the browser wont display it. Its also will not display audio acrobats audio player. They both display perfectly in Firefox. Does anyone know why this might be?

I have the flash plugin installed and Java is working. 

The script for the player is this [HTML]<script src="http://www.gmodules.com/ig/ifr?url=http://mike.s.duffy.googlepages.com/mp3player.xml&amp;up_songURL=http%3A%2F%2Fwww.dollarsflowtoyou.com%2FRachelOliver.mp3&amp;synd=open&amp;w=320&amp;h=50&amp;output=js"></script>[/HTML]

I am only just learning html so not sure what would be in that to make Opera not display it as it works elsewhere so think it must be something in opera itself. 

Any ideas?

---

### Post by TeoBigusGeekus on 2009-07-01
Could you post some links?

---

### Post by tropdoug on 2009-07-02
I can, but am I allowed to? The site I am building is an opt in site for a business opportunity, and I don't want to be accused of advertising here.

---

### Post by tropdoug on 2009-07-03
Bump

---

### Post by TeoBigusGeekus on 2009-07-04
> **tropdoug said:**
> I can, but am I allowed to? The site I am building is an opt in site for a business opportunity, and I don't want to be accused of advertising here.
No problem from me.
Could a mod answer please?

---

### Post by benerivo on 2009-07-05
The script works for me in Opera. It shows a pink coloured flash audio player in the top left, that plays an Aussie lady's voice. Just copying and pasting the web address, plays some guitar music. I'm using the latest 64bit [snapshot of Opera]("http://my.opera.com/desktopteam/blog/"), with the 64bit flash plugin [downloaded from adobe]("http://labs.adobe.com/downloads/flashplayer10.html"). I'm not sure what your problem may be (java does not have to be enabled), other than possibly an adblock term, or javascript block for that page in Opera's settings. Maybe try closing Opera, renaming ~/.opera to ~/.opera.backup and the opening it again to try it with the default preferences. I'm no moderator, but this is a genuine problem, so I would just post a link that you think might help.

---

### Post by tropdoug on 2009-07-08
Thanks for the reply, 

I tried renaming the ./opera directory and it started a new browser as you said, but again no dice. Although I have an amd 64 but chip I am running 32 bit perhaps that could be the difference. 

Ok the website is [http://www.dollarsflowtoyou.com](http://www.dollarsflowtoyou.com) 

If I wanted to load up Jaunty 64 bit on a spare partition and then try Opera 64 bit, how do I do that so that I do not have to reload all the programs I have? I have a seperate home partition. 

Ta:confused:

---

### Post by benerivo on 2009-07-08
I think this is a problem with Opera. I've tried your website, and it is fine in Firefox and Konqueror, but not in Opera. If i just paste the web address in to the address bar, or just open the script by itself (see below), then it works. Before bothering with repartitioning, i would post to the Opera forums, which are very helpful. I've tried running the live 64bit cd, and installing 64bit Opera and Flash in the live session, and still get the same problem in Opera.

If you really wanted to install it, then use gparted from the live cd to shrink a partition to get 8GB free space. Then install 64bit Jaunty in to that, with no separate /home, and using the existing swap partition.


```
<html>
<script src="http://www.gmodules.com/ig/ifr?url=http://mike.s.duffy.googlepages.com/mp3player.xml&amp;up_songURL=http%3A%2F%2Fwww.dollarsflowtoyou.com%2FRachelOliver.mp3&amp;synd=open&amp;w=320&amp;h=50&amp;output=js"></script>
</html>
```

---

### Post by tropdoug on 2009-07-09
Wow, Thanks a heap Benerivo you have certainly gone to some lengths to help. OK I think your suggestion is a good one so I will head over to the Opera forums and see what happens there. I still have a sound issue to work out here with audacity and Kino. Linux is really great but sometimes it does give me a headache. LOL. Anyway thank again, I will post my final results here when I can get a result.

---

