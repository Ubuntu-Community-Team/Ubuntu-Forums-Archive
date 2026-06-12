---
title: "Program requireing flash under wine"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by professorTHC on 2009-01-02
i had a problem with the flash installation earlier which woldnt allow me to watch videos on youtube and such, including a program i had running underwine called 'MYTVIL' which is a client for streaming videos from Israel. But after searching on google for a bit i managed to resolve the flash problem on firefox. however after searching on google for a day or two now i turn to you hoping you might be able to help me with this issue. 
the program installed under wine fine, but when i open it, where the window for the (windows) flash player should be is just a tiled image of the jpg around it. I tried downloading the flash player for windows and running that under wine, hoping that it would install it in the C: drive (i have no idea how to check that that IS where it installed, but i have to assume) but had no luck. Is it possible that since the flash player in this program had a windows flash player and that the shift from windows to ubuntu is what is causing the problem?  any help is appreciated, 
thanks!
prof.

heres a print screen i took that might give you an idea of the issue.
[http://i112.photobucket.com/albums/n186/synshadow/asd.jpg](http://i112.photobucket.com/albums/n186/synshadow/asd.jpg)

---

### Post by professorTHC on 2009-01-02
anyone?
ive been advocating UBUNTU to my computer illiterate parents for quite some time now, and this is the farthest ive gotten to being able tyo convince them for the sole purpose of being able to use this program. while ive been trying to get this to work so i can teach them how to use a computer (quite easily thanks to ubuntu) they are ready to ask me to go back to windows so they can watch their native television. please help, id love to see my parents become even a little bit tech-savvy, but they are stubborn..

---

### Post by donkyhotay on 2009-01-02
First of all the wine 'C:' drive is located at
```
~/.wine/dosdevices/drive_c/
```
Second, in regards to getting that program working under wine it sounds to me as if it's a program that uses flash but not a web browser, is that correct? If it does need a browser you will probably need to install the windows version of firefox with wine. I don't know if you have looked at it but you might try looking at [http://appdb.winehq.org](http://appdb.winehq.org) which deals specifically with wine and getting applications to work with it. Unfortunately it sounds like a less commonly used program so there may not be a lot of knowledge about it.

---

