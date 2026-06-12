---
title: "Help me to set up my internet connection on usb modem"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by ZuruxKakyn on 2007-07-29
ok i know that usb is also stands for "UnSuitable for Bandwith" .My other friends who has route can easily access the net without problems, but for me , i am glad that i can't, which serves me the chance to learn linux:) .Since i have only one modem on my machine, i have to figure out a way to connect it to my machine.

I searched through most of the tut on ubuntu forum but none seems to be for my modem brand, blue thunder. So i google for quite some time and found this : 
[http://nalsur8.blogspot.com/2007/04/macam-mananak-setting-modem-v2-pada.html]("http://nalsur8.blogspot.com/2007/04/macam-mananak-setting-modem-v2-pada.html")

at first i stuck at the making cxacru-fw part so i left a comment there, as zurux. after then i know that it is because i haven't install my gcc, and i fixed the problem.

i continue following the tut and now i get stuck again on other parts, please help me.
1. on the part that i have to enter the ```
'username@isp' * 'password'
```  into chap-secrets and pap-secrets files, should i delete ALL the content and replace with the code, and whether should i include the (') mark? and also whether should i replace with MY OWN username and password?

just for your information, what i did was replace the whole thing by putting MY OWN username and password there, without the (') mark.

2. assume that i got that right, the next part again , on making "access" file, should i include  the (') mark again?

3. the third part is about the "dial" file, the tut there says put the dial file on home folder, my question is, is /home in the / folder the home directory mentioned? i am doubtful because i saw some tuts on installing ubuntu says that we have to have 3 partitions in order to install linux, ext2 for /, swap, and another ext2 for /home. Mine has only 2 partitions for linux, / and swap.

4. on the step where it asks to type ```
chmod +x dial
``` in console,
should i see anything like lists of codes? when i type this on terminal it is as if nothing happened, no codes, no errors, just a new line.

5. after i restarted my machine, i type ```
sudo ./dial
``` as the tut asks, by right i should see codes and should be already connected to the net, but i don't. Instead, i get a line that says something like bash : ./dial is not a command.

thanks in advance for those who are going to help me:)

---

### Post by ddrichardson on 2007-07-29
> **ZuruxKakyn said:**
> ok i know that usb is also stands for "UnSuitable for Bandwith" .My other friends who has route can easily access the net without problems, but for me , i am glad that i can't, which serves me the chance to learn linux:) .Since i have only one modem on my machine, i have to figure out a way to connect it to my machine.

I searched through most of the tut on ubuntu forum but none seems to be for my modem brand, blue thunder. So i google for quite some time and found this : 
[http://nalsur8.blogspot.com/2007/04/macam-mananak-setting-modem-v2-pada.html]("http://nalsur8.blogspot.com/2007/04/macam-mananak-setting-modem-v2-pada.html")

at first i stuck at the making cxacru-fw part so i left a comment there, as zurux. after then i know that it is because i haven't install my gcc, and i fixed the problem.

i continue following the tut and now i get stuck again on other parts, please help me.
1. on the part that i have to enter the ```
'username@isp' * 'password'
```  into chap-secrets and pap-secrets files, should i delete ALL the content and replace with the code, and whether should i include the (') mark? and also whether should i replace with MY OWN username and password?

No just replace or add the username and password line.

> just for your information, what i did was replace the whole thing by putting MY OWN username and password there, without the (') mark.

You'll need the ' marks.

> 2. assume that i got that right, the next part again , on making "access" file, should i include  the (') mark again?

3. the third part is about the "dial" file, the tut there says put the dial file on home folder, my question is, is /home in the / folder the home directory mentioned? i am doubtful because i saw some tuts on installing ubuntu says that we have to have 3 partitions in order to install linux, ext2 for /, swap, and another ext2 for /home. Mine has only 2 partitions for linux, / and swap.

4. on the step where it asks to type ```
chmod +x dial
``` in console,
should i see anything like lists of codes? when i type this on terminal it is as if nothing happened, no codes, no errors, just a new line.

5. after i restarted my machine, i type ```
sudo ./dial
``` as the tut asks, by right i should see codes and should be already connected to the net, but i don't. Instead, i get a line that says something like bash : ./dial is not a command.

You need to sudo chmod + x as if you're going to run it as sudo

---

### Post by ZuruxKakyn on 2007-07-29
Thanks for the reply, i had changed the pap-secret and chap-secret as you asked. then sudo chmod +x dial.

after i restarted the system, and sudo ./dial , terminal still says unable to execute ./dial : no such file or directory.

so i tried to browse to the /home folder, and it says bash: ./dial : Permission denied.

to make things clearly i include an image in this post , here it is: [IMG]http://img156.imageshack.us/my.php?image=screenshotvc1.png[/IMG]

about the permission thing, i actually tried to change the permission by right clicking the file> properties> permission tab but the thing is locked and i cannot change the settings there, and at the bottom it says things like "you are not the owner".

is it because of the permission thing or any other reason why it doesn't work?

---

### Post by ZuruxKakyn on 2007-07-29
Thanks for the reply, i had changed the pap-secret and chap-secret as you asked. then sudo chmod +x dial.

after i restarted the system, and sudo ./dial , terminal still says unable to execute ./dial : no such file or directory.

so i tried to browse to the /home folder, and it says bash: ./dial : Permission denied.

to make things clearly i include an image in this post , here it is: 
[http://img156.imageshack.us/my.php?image=screenshotvc1.png]("http://img156.imageshack.us/my.php?image=screenshotvc1.png")

about the permission thing, i actually tried to change the permission by right clicking the file> properties> permission tab but the thing is locked and i cannot change the settings there, and at the bottom it says things like "you are not the owner".

is it because of the permission thing or any other reason why it doesn't work?

---

### Post by ddrichardson on 2007-07-29
open dial in an editor and have a look at the first line - it needs #!/usr/sh or dome such to tell it what execute the script.

---

### Post by ZuruxKakyn on 2007-07-29
the first line is as in the tut, which is ```
#!/bin/bash
```

---

### Post by ZuruxKakyn on 2007-08-05
Thanks ddrichardson for his personal tutor with me in msn, i sm using kubuntu feisty fawn to post this right now.:)

---

### Post by ddrichardson on 2007-08-05
Thank goodness for that ;-)

---

