---
title: "Help!!! I can only see square instead of words"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by MindController on 2011-02-03
Hi All,

After installed one of gtk+ packages, all of words changed to square. I can't remember the package name. I have no idea what to do. Please Help
Ubuntu version is 10.10. Thanks for all.

---

### Post by DiSTORT3D on 2011-02-03
have you tried to use another appearance?

---

### Post by MindController on 2011-02-03
It doensn't work either. I've already tried it.
Thanks for your help.

---

### Post by DiSTORT3D on 2011-02-03
```
cat /var/log/dpkg.log | grep "\ install\ "
```

purge the lastest installed gtk+ packages?

---

### Post by sandyd on 2011-02-03
what language are you using on the system? - it might have been corrupted (squares generally appear when languages are not installed, or improperly installed)

---

### Post by MindController on 2011-02-03
@ DiSTORT3D
I typed what you said but I just saw squares :D :D

@ sandyd
I only use english. Do I nee to update the font. If so pls guide me to update the font.

Thanks Guys!!!

---

### Post by sandyd on 2011-02-03
> **MindController said:**
> @ DiSTORT3D
I typed what you said but I just saw squares :D :D

@ sandyd
I only use english. Do I nee to update the font. If so pls guide me to update the font.

Thanks Guys!!!
unfortunately, I cant guide you to update your font. Fonts are managed differently on Gentoo Linux.

---

### Post by DiSTORT3D on 2011-02-03
one more try after that i dont know 

```
sudo apt-get install -y pastebinit && cat /var/log/dpkg.log | grep "\ install\ " | pastebinit
```

in one line it will generate a link above the command with or without squares you would be able to click it

---

### Post by Lt. Surge on 2011-02-03
Reinstall Linux??

---

### Post by MindController on 2011-02-04
@ DiSTORT3D
i've already installed pastebinit and restart. nothing happen. still see the square.

@ Lt. Surge
I don't wanna reinstall the linux. :)

---

### Post by DiSTORT3D on 2011-02-04
so if you use the command to post on pastebin, its on pastebin also with squares?

```
root@Machine:/home/distort3d# cat /var/log/dpkg.log | grep "\ install\ " | pastebinit
http://pastebin.com/UUAqH51H
root@Machine:/home/distort3d# 
```

```
http://pastebin.com/UUAqH51H < this will be also in squares but your be able to click hyperlinks in terminal
```

is it on pastebin also square output?

---

### Post by MindController on 2011-02-04
@ DiSTORT3D
strange!!!! If I click on the link nothing happen. Firefox can not open either. When I open the firefox one box appear and i cannot read and what to do. Huh........ 

Thanks for the Help!!!

Update!!!!!
I've got this error when I clicked on the link
```

Operation not supported
Could not open the address &#8220;http://pastebin.com/UUAqH51H&#8221;

```
P.S
I copied to the gedit and opened in the window machine

---

