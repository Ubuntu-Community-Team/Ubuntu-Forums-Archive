---
title: "Installing Planeshift???"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by boodomi on 2009-07-17
Ok so i tell you that i havent been using Linux for long. Just month ago i got so pissed to Windows Vista that i deleted it and installed Ubuntu 9.04..Ok then to the main point. I downloaded this game PlaneShift, From the games website [http://www.planeshift.it/download.html#linux](http://www.planeshift.it/download.html#linux) . Well first problem is that i dont know which version i had to download? 32bit or 64bit? Well i thought that i play safe and i downloaded them both. Then i tried to install the game. First i tried 32bit version but it said like this:
boodomi@boodomi-laptop:~$ chmod +x PlaneShift-v0.4.03-x64.bin
chmod: tiedostoa ”PlaneShift-v0.4.03-x64.bin” ei voi käsitellä: Tiedostoa tai hakemistoa ei ole
boodomi@boodomi-laptop:~$ cd ~/Työpöytä
boodomi@boodomi-laptop:~/Työpöytä$ chmod +x PlaneShift-v0.4.03-x64.bin
boodomi@boodomi-laptop:~/Työpöytä$ sudo ./PlaneShift-v0.4.03-x64.bin
[sudo] password for boodomi: 
./PlaneShift-v0.4.03-x64.bin: 3: Syntax error: ")" unexpected
boodomi@boodomi-laptop:~/Työpöytä$ 
 
And then i tried 64bit version of the game and it went like this?:

boodomi@boodomi-laptop:~/Työpöytä$ chmod +xPlanetShift-v0.4.03-x64.bin
chmod: ”+xPlanetShift-v0.4.03-x64.bin”:n jälkeen puuttuu operandi
Lisätietoja komennolla ”chmod --help”.
boodomi@boodomi-laptop:~/Työpöytä$ chmod +x PlaneShift-v0.4.03-x86.bin
boodomi@boodomi-laptop:~/Työpöytä$ sudo ./PlaneShift-v0.4.03-x86.bin
[sudo] password for boodomi: 
boodomi@boodomi-laptop:~/Työpöytä$ 

?? Nothing happens there? Did i forget something? Please help me, im a little noob :D

---

### Post by mathay on 2009-07-17
First, let's determine whether your CPU is a 32bit or 64bit. Type this into the terminal:

```
uname -m
```
For installation instructions, [here]("http://www.hydlaaplaza.com/smf/index.php?topic=19389.0") is the "generic install" for both 32-bit and 64-bit. For a more in-depth installation guide go [here]("http://planeshift.svn.sourceforge.net/viewvc/planeshift/trunk/docs/compiling.html"). 

Hopefully that helps.

---

### Post by boodomi on 2009-07-17
boodomi@boodomi-laptop:~$ uname -m
i686
boodomi@boodomi-laptop:~$ 
 So this means what?

---

### Post by jerome1232 on 2009-07-17
That your running 32bit

---

### Post by mathay on 2009-07-17
So--from here you will want to follow the directions for 32-bit. If you follow those two guides that I linked two, you should have no problem.

---

### Post by boodomi on 2009-07-17
I really suck on English when it comes to computer terms so i dont understand almost anything from that Compiling Guide.So im hoping that if someone is so friendly that just tells here what i have to do. I would really apreciate that. Please someone? And thank you both who have already helped.

---

### Post by jerome1232 on 2009-07-17
You shouldn't need to compile those are binaries which you downloaded. I'm not sure why it's not running though it should pop up with a little gui that guides you through installing.

---

### Post by mathay on 2009-07-17
boodomi: I used Google Translator to translate the page into Finnish. I'm about to head to work so I would not be able to do a sufficient job of writing a guide out. Hopefully the translated site makes some sense.

[Here is the site]("http://translate.google.com/translate?hl=en&sl=en&tl=fi&u=http%3A%2F%2Fplaneshift.svn.sourceforge.net%2Fviewvc%2Fplaneshift%2Ftrunk%2Fdocs%2Fcompiling.html").

Hopefully it will work. PlaneShift is a fun game. :)

---

### Post by boodomi on 2009-07-17
Are you using MSN jerome? So i could have real time advice? This thing is really starting to piss me off :D And i would really need some help.

---

### Post by jerome1232 on 2009-07-17
What happens if you just double click the .bin file?

---

### Post by boodomi on 2009-07-17
It says that the type is unknown

---

### Post by jerome1232 on 2009-07-17
I'm starting to wonder if the download was corrupted somehow md5sum that binary file see if it matches theirs


To check it's md5sum

```
md5sum *pathtofile*
```

It should take a while then spit out some numbers

If they don't exactly match what's below the download is corrupt and you need to re-download the file, if they match exactly then the download is good and I'm not sure what to do.
```
cf1270be1a71aef2cef37b283e6bccc2
```

---

### Post by boodomi on 2009-07-17
boodomi@boodomi-laptop:~/Työpöytä$ md5sum PlaneShift-v0.4.03-x64.bin
7412c12e164eab2de5a320b0da0ce512  PlaneShift-v0.4.03-x64.bin

So it is corrupted right?

---

### Post by jerome1232 on 2009-07-17
Run it on the 32 binary that was the 64 bit one, should be called PlaneShift-v0.4.00-x86.bin

---

### Post by boodomi on 2009-07-17
Yeah it didnt still match. Am i able to run this game under wine? Im coming hopeless :D

---

### Post by jerome1232 on 2009-07-17
I would just re-download it from here: [http://www.planeshift.it/download.html#linux](http://www.planeshift.it/download.html#linux)

Make sure you download the 32 bit linux binary and try it again.

---

### Post by boodomi on 2009-07-17
Ok i give it another go.

---

### Post by boodomi on 2009-07-17
boodomi@boodomi-laptop:~/Työpöytä$ chmod +x PlaneShift-v0.4.03-x86.bin
boodomi@boodomi-laptop:~/Työpöytä$ sudo ./PlaneShift-v.0.4.03-x86.bin
[sudo] password for boodomi: 
sudo: ./PlaneShift-v.0.4.03-x86.bin: command not found
boodomi@boodomi-laptop:~/Työpöytä$ 

Now it says like that? By the way when that [sudo] password for boodomi comes does it mean my account password? And why doesent it still work??

---

### Post by boodomi on 2009-07-17
Ok little bit progress here. I got the game installed, but how am i supposed to get and play it ? When i go to the folder PlaneShift it says that i dont have the rights?

---

### Post by boodomi on 2009-07-18
Thank you big time :) Problem solved and PlaneShift is working just fine :) Next operation. Install Perfect World under Wine. :)

---

