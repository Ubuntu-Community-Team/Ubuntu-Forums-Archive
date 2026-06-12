---
title: "problems with Ubuntu 9.10"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Scholar1987 on 2009-11-25
Hi

I have just upgraded my OS from Ubuntu 9.04 to Ubuntu 9.10, but I am facing these problems...

1. I get this error message when I login
 
                  **[SIZE=1]Could not update .ICEauthority file [/SIZE]/home/scholar./.ICE authority**

2. the search engines (one beside ) the navigator,  in mozilla(3.6 namaroka) aren't working..if I give any text in it, It didnt even load any page and no action is performed.

3. I am using WINE to access some of the files of windows....example I am trying to access Ultrasurf.exe, but no  action is performed

4. I have inbuilt speakers in my CPU... but I am unable to get the sound outside if play any song or movie...I have checked all the preferences but it aint working.

 Please answer to my queiries...Reply will be appreciated...please try to fix them 

Thank you :p,
[B] Scholar
[/B]

---

### Post by Sealbhach on 2009-11-25
Hi, here's a possible solution to your ICE authority issue:

[http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)

so for you the commands would be:

chown scholar:scholar /home/scholar/.ICEauthority
chmod 644 /home/scholar/.ICEauthority
exit
That browser you're using is a prerelased Beta, as far as I know. So if you want that feature I suggest you would use browser 3.5.3 which was released in Uubntu 9.10.

For your sound, try running alsamixer (run the command alsamixer in a terminal) and turn up the volume on everything you can.

EDIT: read here about Ultrasurf in Wine [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8759](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8759)
Do you really need it? Can you find an alternative native Linux app?

.

---

### Post by orawax on 2009-11-30
It seems that automatic login is currently broken in Karmic.

I had a recurring problem with .ICEauthority but couldn't figure out when it started. Then I enabled automatic login also in my laptop, and got the same problem there. So I disabled autologin and since then the error's gone.

---

