---
title: "some help with qt4 (i think) related issues."
date: 2009-01-20
forum: New to Ubuntu
---

### Post by techno-mole on 2009-01-20
hello.

im trying to run the linux version of myscribe (available from cafescribe.com) its basically a program for reading and anotating pdf files, i used it on my last open university course, and as im about to start another i want to use it again, but i cant for the life of me get it running.

i had it working a while ago, but due to a recent upgrade i am now running 64 bit ubuntu, i am running a couple of applications that dont have a 64 bit version and they are working fine.

the problem is that when i install the file (its a .deb file) everything goes okay, normally if there are dependancy problems you get a message about it, or if it needs extra packages it will install whats needed as well, but i get no such messages, so i thought great its installed its going to work......wrong :-)

so when i try to run it nothing happens, so i thought i would run it in a terminal and see what i get, here is the out put - 
```

myscribe_bin: error while loading shared libraries: libQtAssistantClient.so.4: 
cannot open shared object file: No such file or directory

```

but the thing is i have the required qt3 and qt4 packages, as im runnign other stuff that uses them, so why do i get the error ? i have tried searching synaptic for the " libQAssistantClient.so.4 " but nothing comes up, i tried apt-get as well, no joy either.

i have tried searching google for the error and havent found anything remotely like the error i get, i also tried looking for a package that included the libqtassistantclient, and couldnt find anything either.

i have looked in the .deb file and there is a libqtassistant in the libs folder (along with alot of other stuff) so im wondering if that when im installing the paths arnt right, meaning that links to where libraries etc are dont get made, or something like that.

so im looking for a some help from anyone who has had the same issue with myscribe (or other app) or some one who knows about these things.

cheers in advance for any help.

PS - the windows version doesnt run through wine, i have posted on the winehq forums and the advice was try and get the linux version working.

---

### Post by stderr on 2009-01-20
apt-file allows you get search through the files provided by each package. You need to install it separately and update its file cache before you can use it:

```
sudo apt-get install apt-file && sudo apt-file update
```

My search returned this:

```
ace@ace1:~$ apt-file search libQtAssistantClient.so.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4.4.3
libqt4-dbg: /usr/lib/libQtAssistantClient.so.4.4.3.debug
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4.4
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4.4.3
```

So I'd recommend trying

```
sudo apt-get install libqt4-dev
```

I would think that libqt4-assistant will be a dependency of libqt4-dev anyway, and so will also be installed by that command.

Hope that helps

---

### Post by techno-mole on 2009-01-20
okay, cheers for the tip, but it seems i have some other type of problem, the reason i say this is because after running apt-file search i get this 

```
techno-mole@HAL:~$ apt-file search libQtAssistantClient.so.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4.4
libqt4-assistant: /usr/lib/libQtAssistantClient.so.4.4.3
libqt4-dbg: /usr/lib/libQtAssistantClient.so.4.4.3.debug
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4.4
libqt4-dev: /usr/share/qt4/lib/libQtAssistantClient.so.4.4.3

```

which, if i read it right is saying i already have it installed, so maybe the problem is that when i install myscribe it isnt setting up the links to the various libraries ? or some thing like that ?

cheers

---

### Post by BattleStarJesus on 2009-03-01
> **techno-mole said:**
> 
im trying to run the linux version of myscribe (available from cafescribe.com) its basically a program for reading and anotating pdf files, i used it on my last open university course, and as im about to start another i want to use it again, but i cant for the life of me get it running.


I am trying to get MyScribe to work also, but my problem is slightly different.  I am tyring to runn it through WINE.  Do you have a link for the deb package?  I must be missing something because I am not finding it.
[URL="http://forum.winehq.org/viewtopic.php?p=20536#20536"][COLOR="Blue"]
I have started a thread on the WINE Forum.[/COLOR][/URL]

---

### Post by techno-mole on 2009-03-04
sorry it has taken so long to reply, i still havent as yet got myscribe to run under wine on 64 bit ubuntu (i did have it working with wine on 32 bit ubuntu)

as for the .deb package, you wont find a link, basically the only reason i have a .deb myscribe file is because i did an open university course a while ago, and there was a .tar file available with the course material, i made it into a .deb and installed it.

for the most part the linux version works quite well, but again i havent managed to get that to work on a 64 bit system, so if you still want the .deb to mess about with i can always e-mail it to you, or i can e-mail the original .tar archive, however you wont get any support from cafescribe regarding the linux version as they seem to be denying all knowledge of there ever being a linux version, it may well have been done just for the open university though.

cheers, ill post on the wine forums as well.

---

### Post by lakotajames on 2011-01-31
I'm to run this program as well, thorough wine, but I'd much rather run it natively.  Could you send me either the tarball or the deb, if you still have either?  I'd prefer the tarball, but either would be ok. :)

---

