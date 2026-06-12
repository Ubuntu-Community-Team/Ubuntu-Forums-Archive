---
title: "i need know how to get wireless set up"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by billw11 on 2007-08-09
ok , ill try this again.
ive got my wireless card blacklisted because it was wrong one installed and not connecting. 
im switching back and forth between ubuntu & win xp just so i can get internet for help.
ndiswrapper was not installed and wasnt on cd , i downloaded to ubuntu desktop.
now i need step by step instructions on putting the driver on so i can finnally get a connection .
i have not been able to do anything at all with ubuntu without a connection because everything i want to install or do needs a connection for missing files

---

### Post by kevinlyfellow on 2007-08-09
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by Kralizec on 2007-08-09
Just a tip, but while I was trying to get my wireless working, I used a physical connection; that seemed to work fine. 
And this ([http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)) is the guide I used (don't pay any mind to the Dell name at the top, it worked on my Gateway beautifully).

---

### Post by kevdog on 2007-08-09
How about you tell us something about your card to make sure we are proceeding down the right path?? Please type at command line and cut and paste output:

lspci -nn
lshw -C network

---

### Post by billw11 on 2007-08-09
yes , it would be nice to directly hook up an ethernet cable.
im not trying to be smart, but i already bought a smaller monitor just because of ubuntu not recognizing my lcd tv as a monitor.
under windows xp , i didnt need a monitor so didnt buy one because i use my 32" lcd tv as my monitor. $150 for something i shouldnt need (the price of win xp 64) display garbled under ubuntu. cant adjust it if you cant read it.
my usb linksys installed in less than 10 minutes with working connection in win xp.
there no encryption or passwords needed for my wireless network i connect to.
in order to use a cable, i need to go to a computer store and have the cable custom made because its 250 feet away, id need 2 days to run the cable and weatherproof it. id be looking at the cost of a new quad core system in order to do it.
 NOT worth it. i set up the wireless access point to avoid running cables & make things easier , more secure.
exactly the reason i went with linksys, because all the needed info is stored automatically onto the unit. everything on the system is windows based except for my failing attempts at ubuntu. weve attached 2 new computers to the system , 1 of which became the new server running vista.
no problems whatsoever with nothing to do but turn the units on , as the wireless adapter holds all the information needed to run the network, even when main server is turned off , i still have my connection.

my problem here is that i was told to blacklist the installed driver on ubuntu and have ndiswrapper on desktop.... NOW what???
i try opening it , NOTHING...
im new to this and frustrated to the point that i actually ordered win pro xp 64.
ill keep trying to figure out ubuntu until i get win 64 in the mail.
but with no internet connection, i cant even install anything i want to try on ubuntu. if everything needed to run ubuntu needs a further download to do it, why isnt there a DVD ISO download for ubuntu ?
even microsoft puts current releases with needed updates onto dvd.

---

### Post by billw11 on 2007-08-09
its a 54 G linksys usb adapter.
ubuntu installed it as a 11 mbs wireless usb card.
i just need to know how to get it recognized properly to get a lousy connection. i dont care what speed i get at this point.
ive nothing to lose as ubuntu is running off a 80 gig drive , that in about a week will become win xp 64 if i cant get this resolved.

---

### Post by kevdog on 2007-08-09
Blacklist what installed driver -- be more forthcoming with the details of your system, not your situation.

---

### Post by Kralizec on 2007-08-09
Sorry for sending you on that incredibly long tandem about your cables. I assumed--as many probably would--that since you are setting up wireless you were working from a laptop, not a desktop thats tethered to an enormous television set. And by the way, wouldn't it just be easier to get an extra-long ethernet cable rather than an extra-long monitor cable? Cat-5 cables are nice and cheap, even when bought in bulk.

Now when you say you open ndiswrapper and get nothing, what do you mean? There's no response from the system? Nothing comes out of the package? And which of the provided how-tos are you using? That'll make it easier to follow what you're trying to do.

---

### Post by billw11 on 2007-08-09
terrific.print out 19 pages in order to try installing a driver just to find out i need to switch back to windows again to down load more stuff thats not on the install cd.
heres a very simple question if somebody can give me a straightforward answer.
why bother using ubuntu if everything is a 20 page how to , in order to simply do 1 thing...?
ubuntu sees my printer correctly , but i cant even print anything without downloading more files for  which i have no connection.

im sorry , but it has to be mentioned.
of course theres no viruses. hardly anyone can get online.
im not the smartest by far, but by the time i get ubuntu online , my neighbor fred flintstone will have a faster system than me.

---

### Post by Kralizec on 2007-08-09
If it is this much of a hassle for you, then perhaps Ubuntu and Linux in general isn't for you. It seems as though it would be better for you to simply switch back to Windows rather than waste the time of those on this forum who are trying to give you assistance.

---

### Post by ugm6hr on 2007-08-09
For anyone trying to help here - see this previous thread:
[http://ubuntuforums.org/showthread.php?t=517437&page=4](http://ubuntuforums.org/showthread.php?t=517437&page=4)

---

### Post by billw11 on 2007-08-09
the cat 5 cable is cheap in comparison to the work involved and other materials needed to drill holes in the wall of the house the router is located as well as mine.weatherproofing the cable , as well as the holes drilled out. not to mention digging a 250 foot trench and pvc pipe needed to bury the pipe and cable to get it to my location.
id be looking at about a $500 bill to do this.
many better things to waste my money  on than a connection that i already have with xp.

im sorry but why doesnt this needed stuff like ndiswrapper automatically install if needed?

---

### Post by Kralizec on 2007-08-09
I was unaware that you would be transversing buildings with your network, I'm sorry. But to answer your question about why ndiswrapper doesn't come pre-installed/configured, its because Ubuntu is designed to work on all systems and due to closed-source restrictions, the developers have to come up with workarounds for certain issues *after* they come up. In addition to that, many wireless adapters work out of the box with Ubuntu, although sadly I can't tell you which ones, as I don't know.

---

### Post by billw11 on 2007-08-09
hey , what can i say. i didnt continue the next day because i had to go to work.
so thanks for the help.
i printed off the 19 pages of wireless setup instructions.
ill go through it every step of it.
so if i cant get it to work , thanks for the help.
ill just wait until somebody actually supports ubuntu

---

