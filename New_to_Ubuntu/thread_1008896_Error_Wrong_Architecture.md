---
title: "Error: Wrong Architecture???"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-12
Every time i try and download a .deb of anything from skype to flash it ends up downloading fine and then when i try and install it (it usually starts this process by itself) it tells be Error: wrong architecture 'i386'

Im stumped lol any ideas?

Thanks in advance!

---

### Post by mobilediesel on 2008-12-12
> **11010110 said:**
> Every time i try and download a .deb of anything from skype to flash it ends up downloading fine and then when i try and install it (it usually starts this process by itself) it tells be Error: wrong architecture 'i386'

Im stumped lol any ideas?

Thanks in advance!

What kind of processor does your computer have? i386 compatible would be Intel, AMD or IBM. It would seem you have something different.

---

### Post by 11010110 on 2008-12-12
intel dual core 1.6 1.7ghz. i have no idea what the problem could be

---

### Post by mobilediesel on 2008-12-12
> **11010110 said:**
> intel dual core 1.6 1.7ghz. i have no idea what the problem could be

Hmmm. Do your downloaded files say what processor they're for?

---

### Post by 11010110 on 2008-12-12
i had to chose between the 64 bit version and the 32 bit version so i chose the latter and now im stuck lol. 

its happened with opera adobe flash skype and others...

---

### Post by prshah on 2008-12-12
> **11010110 said:**
> Error: wrong architecture 'i386'


What version of Ubuntu are you using? 64bit (X86_64) or 32 bit (i386 / i686)? You can find out by opening a terminal (Applications-Accessories-Terminal) and giving the command```
uname -m
```

If you get i386 or i686, then you have 32 bit and need the 32bit version of whatever software you choose to use.

If you get amd64 or x86_64 then you are using a 64bit operating system and need to get the 64bit version of whatever software you choose to use.

---

### Post by 11010110 on 2008-12-12
I used teh wubi installer... it must have chose to put in a 64bit version. you would think it would have some clue lol. I thought i picked the right settings. Tomorrow ill erase and reinstall ubuntu. that is unless someone knows a way i could swap out OS without losing any data (ive only had linux via a wubi install for tonight)

Thanks for your help looks like i have a lot of work ahead of me lol

---

### Post by redgilda on 2008-12-25
I've got a similar problem..

I tried to add flash to Firefox, it pointed me to adobe site and suggested the x86 version

when I check in terminal:
redgilda@redgilda-ubuntu:~$ uname -m
x86_64

so why do I get the 'wrong architecture error'?

any help appreciated, screenshots attached ;-)

---

### Post by ugm6hr on 2008-12-25
> **redgilda said:**
> when I check in terminal:
redgilda@redgilda-ubuntu:~$ uname -m
x86_64

so why do I get the 'wrong architecture error'?

The .deb is an i386 file (for 32-bit Linux).

Your Ubuntu is 64-bit.

Hence the wrong architecture error.

---

### Post by redgilda on 2008-12-25
well on the flash site it said that its an x86 version so thats the one I took. it was the only .deb available.

but for now I upgraded to ubuntu 8.10 and the flash item in the site that didnt work before - works now, so I'm happy for now...

---

### Post by Moop on 2008-12-25
The 64 bit version of flash is in a different place called Adobe Labs. It's still alpha so they don't put it on the main download page. 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by white3911 on 2009-02-25
> **Moop said:**
> The 64 bit version of flash is in a different place called Adobe Labs. It's still alpha so they don't put it on the main download page. 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Thanks for this the link! However when I download the file, extract it and then try to open the file, I get the following error code:

Could not display "/home/user/Desktop/libflashplayer.so"
This is no application installed for this file type.

Which application do I need to run .so files?

---

### Post by jimmyhacker on 2009-02-25
the applications wich needs .so must read it.no program can open .so files.so its like DLL on windows.

---

### Post by oldos2er on 2009-02-25
> **white3911 said:**
> Thanks for this the link! However when I download the file, extract it and then try to open the file, I get the following error code:

Could not display "/home/user/Desktop/libflashplayer.so"
This is no application installed for this file type.

Which application do I need to run .so files?

 You don't "run" the *.so file, just copy it to your plugins directory (/usr/lib/firefox/plugins and/or /usr/lib/mozilla/plugins).

---

### Post by white3911 on 2009-02-25
Thanks for the quick response. If you could, walk me through how I'm supposed to "copy to my plugins list". I'm a huge newb with the computer literacy of a 5 year old. Again thanks for your help, this is why I love Linux! 

PS I have the extracted .so file saved on the desktop.

---

### Post by white3911 on 2009-02-25
bump...\\:D/

---

### Post by presence1960 on 2009-02-25
try this to get flash working :  [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by oldos2er on 2009-02-25
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by white3911 on 2009-02-25
okay... when I try to extract the files to /usr/lib/firefox/plugins and/or /usr/lib/mozilla/plugins I receive the following message:

"You do not have the right permission to extract achieves in the folder "file:///usr/lib/mozzila/plugins""

---

### Post by presence1960 on 2009-02-25
> **white3911 said:**
> okay... when I try to extract the files to /usr/lib/firefox/plugins and/or /usr/lib/mozilla/plugins I receive the following message:

"You do not have the right permission to extract achieves in the folder "file:///usr/lib/mozzila/plugins""

go to the link in post #17. download the flash alpha 64bit file. right click on the tar.gz file and choose extract here. There will be a Get Flash 64bit file. Double click it and choose run in terminal. simple, if that doesn't work open a terminal and enter > sudo apt-get install nspluginwrapper flashplugin-nonfree

the first method worked in Mint5 64bit and the second worked in Kubuntu 8.10 64 bit

---

### Post by white3911 on 2009-02-26
> **presence1960 said:**
> go to the link in post #17. download the flash alpha 64bit file. right click on the tar.gz file and choose extract here. There will be a Get Flash 64bit file. Double click it and choose run in terminal. simple, if that doesn't work open a terminal and enter 

the first method worked in Mint5 64bit and the second worked in Kubuntu 8.10 64 bit

Thank you so much! This solved my problem!

---

### Post by presence1960 on 2009-02-26
> **white3911 said:**
> Thank you so much! This solved my problem!

No problemo. Someone helped me when I needed help. Just sharing info I have learned since using Linux. I am glad it is now working for you! Now dive in there and share what you learn. What goes around comes around.

---

### Post by tonychar on 2009-03-03
> **presence1960 said:**
> go to the link in post #17. download the flash alpha 64bit file. right click on the tar.gz file and choose extract here. There will be a Get Flash 64bit file. Double click it and choose run in terminal. simple, if that doesn't work open a terminal and enter 

the first method worked in Mint5 64bit and the second worked in Kubuntu 8.10 64 bit
Brilliant!  Worked for me too, with tyhe exact same problem.  Thanks so much!

---

### Post by stchman on 2009-03-03
> **11010110 said:**
> Every time i try and download a .deb of anything from skype to flash it ends up downloading fine and then when i try and install it (it usually starts this process by itself) it tells be Error: wrong architecture 'i386'

Im stumped lol any ideas?

Thanks in advance!

Use 32 bit version on i386 installs and 64 bit on x86_64 installs.  Pretty straightforward.

---

