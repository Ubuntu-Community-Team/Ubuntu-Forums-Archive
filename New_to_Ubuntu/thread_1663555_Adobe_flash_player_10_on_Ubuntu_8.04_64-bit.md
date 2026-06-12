---
title: "Adobe flash player 10 on Ubuntu 8.04 64-bit"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by alemariscal on 2011-01-09
[SIZE=4]I have been having problems trying to install adobe flash player10 on ubuntu 8.04. i've googled my problem and foun[/SIZE][B][SIZE=3]d some that say they have solved it. i followed the same steps but it still seems not to work for me. not to mention i'm a 64-bit... so is there a solution or am i a lost case? :confused: 
[/SIZE][/B]

---

### Post by Sensiva on 2011-01-09
> **alemariscal said:**
> [SIZE=4]I have been having problems trying to install adobe flash player10 on ubuntu 8.04. i've googled my problem and foun[/SIZE][B][SIZE=3]d some that say they have solved it. i followed the same steps but it still seems not to work for me. not to mention i'm a 64-bit... so is there a solution or am i a lost case? :confused: 
[/SIZE][/B]

You seem really angry to the extent you forgot to mention "What exactly the problem??"
:D

---

### Post by cgroza on 2011-01-09
And could you describe the problem? I see people who had luck with a plugin called flash aid. Did you try that?

---

### Post by alemariscal on 2011-01-09
**I've tried downloading the .deb package from the adobe website but all i get when i try running it is i386 wrong architecture. so then i tried it from the terminal and it says the file does not exist.** so i dont know if i'm supposed to change the location to desktop on the terminal before i even do anything???

---

### Post by cgroza on 2011-01-09
Install the 64 bit one.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by alemariscal on 2011-01-09
> **cgroza said:**
> Install the 64 bit one.
i have tried but i keep on getting the same error message or "wrong architecture"

so then i found this but still does not work for me:

**For 64 bit Users**
 Thanks to Alejandro for this nice script.First you need to Download shell script from [URL="http://queleimporta.com/downloads/flash10_en.sh"]here
[/URL] Using the following command
 wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)
 Now you need to give execute permissions using the following command
 sudo chmod +x flash10_en.sh
 Run the script now
 sudo sh ./flash10_en.sh

  
[LEFT]
[/LEFT]

---

### Post by alemariscal on 2011-01-09
on that website there's only downloads for 32 bit?

---

### Post by sandyd on 2011-01-09
> **alemariscal said:**
> i have tried but i keep on getting the same error message or "wrong architecture"

so then i found this but still does not work for me:

**For 64 bit Users**
 Thanks to Alejandro for this nice script.First you need to Download shell script from [URL="http://queleimporta.com/downloads/flash10_en.sh"]here
[/URL] Using the following command
 wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)
 Now you need to give execute permissions using the following command
 sudo chmod +x flash10_en.sh
 Run the script now
 sudo sh ./flash10_en.sh

  
[LEFT]
[/LEFT]

click link in signature (Adobe Tools)

---

### Post by alemariscal on 2011-01-09
thank you everyone!! i tried the flash Aid mentioned above and it worked perfectly!! thanks :):KS

---

