---
title: "dhcp not working in dapper"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by notepad on 2006-10-18
is anybody else finding that their dhcp is not working since upgrading to dapper? every time i boot ubuntu i need to issue

sudo /etc/init.d/networking restart

to get my network up. why is this so? any ideas?

---

### Post by carontis on 2006-10-18
It is probably fault of updating. In normal installations it doesn't happens. If you can, you should try with a clean installation with last release. I'm afraid your update was wrong in sonething, but not having here the pc, I can't tell you more.

---

### Post by Iowan on 2006-10-18
I presume the System>Administration>Networking has the interface active and enabled.

---

### Post by notepad on 2006-10-19
iowan the interface is active and enabled which is why the whole problem is so annoying. unfortunately i think carontis is right. i have searched out this problem on this forum and elsewhere and followed heaps of instructions which helped other people and did nothing for me. 

i have never been able to use the dist-upgrade feature without incident which is really annoying. doing fresh installations all the time reminds of ugly days long gone where most of us used win98.

any ideas on a simple script that i can use to issue my networking restart command? (remembering that my wife uses a no-admin-priveleges user account)

---

### Post by CatKiller on 2006-10-19
Not that it really helps you any, but my DHCP has always been fine, and I upgraded from Breezy to Dapper. If you know more about the startup process than I do, you could look at why the "Starting Basic Networking" step doesn't work for you. That's where my networking starts from.

---

### Post by notepad on 2006-10-21
does anybody know how to setup a script/whatever to run 
"sudo /etc/init.d/networking restart" on system startup??

---

### Post by CatKiller on 2006-10-21
The only way I know to do it is through the sessions manager: System -> Preferences -> Sessions -> Startup Programs

---

### Post by mausr on 2006-10-21
> **notepad said:**
> is anybody else finding that their dhcp is not working since upgrading to dapper? every time i boot ubuntu i need to issue

sudo /etc/init.d/networking restart

to get my network up. why is this so? any ideas?

I'm suffering from the same problem unfortunately. I made a fresh install, but it was unhelpful. @S40networking is in /etc/rcS.d, but after boot i can't see any sign of the script's running in the syslog. ](*,)

---

### Post by Lozzie on 2006-10-21
i'm on DHCP, and a new user =].
new install, recognises that my network card is in place, and can tell me it's an atheros, which i've found out are quite dogdy, but it cant seem to detect the model (5005G), and i can't get on to the internet to download linux-restricted-modules, which apparently are needed.

if anyone can help, i'd be soo grateful, i'd buy you a beer.

Lozzie

---

### Post by handy on 2006-10-21
> **notepad said:**
> does anybody know how to setup a script/whatever to run 
"sudo /etc/init.d/networking restart" on system startup??

I had to find out how to do that once for a different problem.  The sudo without password bit was what had me stumped. :confused: 

**Huygens**, supplied 2 beautiful solutions, secure & incredibly secure. :KS  [See here]("http://ubuntuforums.org/showthread.php?t=245618"), his is **Post 3**.

---

### Post by notepad on 2006-10-25
thanks handy. i need to have a closer look at huygens solution there. theres some difference with my requirement i think since i need to run networking rather than cp and from things i tried earlier, the networking command seems to behave a little differently to commands that other blokes were using in their scripts for some reason.

i have tried simply calling /etc/init.d/networking from sessions > startup programs and it didnt work so perhaps on the weekend if i have more time i will look into creating huygen's ghost group and user and seeing if i can get it to work.

lozzie sounds like youre in a crap situation unless you can temporarily install a card that the system will recognise. then you could use whichever repositories etc you want to get your preferred card going and take the temporary card out again.

---

### Post by notepad on 2007-01-16
i fixed my problem by installing 6.10 on a freshly formatted ext3. not a very elegant or satisfactory solution but thats how it is. upgrading realeases doesnt work. fresh install every time.

---

