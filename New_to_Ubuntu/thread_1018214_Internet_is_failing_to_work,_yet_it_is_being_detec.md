---
title: "Internet is failing to work, yet it is being detected."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by coldworld on 2008-12-21
Hello,

I am extremely new to ubuntu, but have decided to acquire the latest version after a friend's referral. I must say I love it, although I've been having this problem.

I use a standard linksys router, and connect to the internet wirelessly. Everything had been running smooth until a couple days ago when all of a sudden I was receiving a "page not found" screen when trying to connect. It had been working perfectly before. I have tried with different browsers, and even tried on different laptops. It all seems to work fine on the other computers, and I am stumped.

How can I fix this problem?

Thanks in advance!

{edit} By the way, my computer is detecting the Linksys, and claims to have 99% connectivity. Still "page not found"

---

### Post by abn91c on 2008-12-21
make sure you have the correct passkey, WEP or WPA setup and it matches the routers

---

### Post by coldworld on 2008-12-21
I also forgot to mention that I am absolutely terrible with computers. What does all of that mean?

---

### Post by abn91c on 2008-12-21
> **coldworld said:**
> I also forgot to mention that I am absolutely terrible with computers. What does all of that mean?
if you have a Linksys router go to the router setup and setup the wireless security, ssid, keys etc
 for the router go to [http://192.168.1.1/Wireless.htm](http://192.168.1.1/Wireless.htm)
 the default password is admin, no user name, you must change the password  to your own liking. WPA security is the best.

---

### Post by the yawner on 2008-12-21
Might be a problem with your DNS? Open up a terminal and try to ping any website to see if your OS can hit the corresponding IP.

---

### Post by GmoUnit on 2008-12-22
Can someone pls help me my firefox internet was working perfectly on ubuntu but than the next day a update thing was in the top right hand corner and when I clicked it it started updating all available updates(iv only had the computer for a day before) and I was trying to open mozilla during the updater and it wouldnt open for some reason and the updater seemed like it froze because it wasnt loading so i restarted the computer when the updater was only like halfway or possibly less done and now when i start it up mozilla never opens when i click it and the help menus that usually go to the internet dont open either and when i try to open the updater thing it loads a bit and i click check and it loads a bit than stops and says the a error and to correct it i have to run 'dkpg configure -a' and it says the updates are complete on some other page even though i restarted the computer before it was done and but there now way to access a comand prompt program on ubuntu to type in the dkpg stuff that i can find and i dont know how to run what it tells me to run but i looked up the details or what was being updated on some other page and it said like mozilla and other stuff was updated during the updater even though I think it was only party udated and somehow it messed up and does anyone know how to post a new forum on this site because im lost

---

### Post by abn91c on 2008-12-22
> **GmoUnit said:**
> Can someone pls help me my firefox internet was working perfectly on ubuntu but than the next day a update thing was in the top right hand corner and when I clicked it it started updating all available updates(iv only had the computer for a day before) and I was trying to open mozilla during the updater and it wouldnt open for some reason and the updater seemed like it froze because it wasnt loading so i restarted the computer when the updater was only like halfway or possibly less done and now when i start it up mozilla never opens when i click it and the help menus that usually go to the internet dont open either and when i try to open the updater thing it loads a bit and i click check and it loads a bit than stops and says the a error and to correct it i have to run 'dkpg configure -a' and it says the updates are complete on some other page even though i restarted the computer before it was done and but there now way to access a comand prompt program on ubuntu to type in the dkpg stuff that i can find and i dont know how to run what it tells me to run but i looked up the details or what was being updated on some other page and it said like mozilla and other stuff was updated during the updater even though I think it was only party udated and somehow it messed up and does anyone know how to post a new forum on this site because im lost
open a terminal type sudo dpkg --configure -a, after it finishes running
sudo apt-get install -f

---

### Post by coldworld on 2008-12-22
I tried pinging various websites and my computer is not detecting it whatsoever. Thanks for everyone's help, but nothing has worked yet. If you need any information about my OS or computer I can provide.

---

### Post by cake_or_death on 2008-12-22
Do I understand correctly that you are able to connect to your network, but firefox (or any browser) won't load any pages?  If so, I am having this same problem as of today.  I am also unable to install any updates because it fails to connect to the software sources.  I can, however, access shared files on my local network, so I'm completely stumped here.  Sorry I can't help.  Does anyone have any ideas?

---

### Post by antmenj on 2008-12-23
Has firefox got into "off line mode"?  File -->work offline .

---

### Post by the yawner on 2008-12-23
> **coldworld said:**
> I tried pinging various websites and my computer is not detecting it whatsoever. Thanks for everyone's help, but nothing has worked yet. If you need any information about my OS or computer I can provide.

If by latest OS I assume Intrepid Ibex? Anyway, kindly check the following:
- Check what is your DNS IP which you can check on the network manager
- Type this on the command line:
```

nslookup

```
then enter any valid website (i.e. yahoo.com, google.com) and see if it will output a corresponding IP.
- If you are unable to get any result, compare your DNS settings with the other functional laptops you mentioned. Or just change your DNS to any [public DNS]("http://www.tech-faq.com/public-dns-servers.shtml") IP: ex. 4.2.2.1


> **cake_or_death said:**
> Do I understand correctly that you are able to connect to your network, but firefox (or any browser) won't load any pages?  If so, I am having this same problem as of today.  I am also unable to install any updates because it fails to connect to the software sources.  I can, however, access shared files on my local network, so I'm completely stumped here.  Sorry I can't help.  Does anyone have any ideas?
You are probably having the same DNS problems. Kindly check as stated above.

---

