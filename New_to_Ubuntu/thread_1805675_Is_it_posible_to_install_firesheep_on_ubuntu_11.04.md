---
title: "Is it posible to install firesheep on ubuntu 11.04?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by Stephaans on 2011-07-16
I cannot install the addon (firesheep) in firefox after compiling it. Says it doesn't support firefox 5.0. :(

---

### Post by dFlyer on 2011-07-16
If it's not supported you will have to wait for an update. Sorry.

---

### Post by mikewhatever on 2011-07-16
In Ubuntu or in Firefox 5? ...and if Firefox 5 is not supported, use the version that is.

---

### Post by Stephaans on 2011-07-16
> **mikewhatever said:**
> In Ubuntu or in Firefox 5? ...and if Firefox 5 is not supported, use the version that is.

exactly how do I install a previous version? Sorry if this is a stupid question but i am relatively new to Ubuntu.

---

### Post by Dangertux on 2011-07-16
Am I the only one who finds it disturbing that people request help on how to perform session hijacking?

IMO if you can't figure out which browser is supported, you probably are not qualified to be doing it legally. Thus you are likely doing this illegally.

---

### Post by Stephaans on 2011-07-16
> **Dangertux said:**
> Am I the only one who finds it disturbing that people request help on how to perform session hijacking?

IMO if you can't figure out which browser is supported, you probably are not qualified to be doing it legally. Thus you are likely doing this illegally.

I'm only going to try it out on my own router just to see what everyone's doing when they ask me if they can connect to it. It really has nothing to do with doing something illegal I am really just exploring. Maybe catching a wifi thief or two. Lol.
Secondly I know which version I need, just don't know how to install. No such option in package manager.

I'm really just interested in how not the illegal stuff themselves. Curiosity is the reason I use Ubuntu not windows

---

### Post by 3ncrypt0 on 2012-01-05
################################################## ############
# Before we do any thing we need to change some stuff FIRST! #
################################################## ############
First we need to change the install.rdf 
go to firesheep/xpi 
open the install.rdf with any text editor.
scroll down to em:minVersion>3.6.10</em:minVersion>
<em:maxVersion>3.6.*</em:maxVersion>
change to what version you are running in firefox.
<em:minVersion>5.0.0</em:minVersion> << this will be your current version
<em:maxVersion>7.0.1*</em:maxVersion> <<this is firefox current version
save it.

Before we do the git submodule update --init we need to change some stuff.
open up firesheep/.git/config and .gitmodule << both of these files are hidden.
open both files with your text editor and change to>> url = git://github.com/joyent/http-parser 
Save it.

Now we can do the git submodule update.

cd firesheep
git submodule update --init

Next to compile Firesheep Ubuntu 10.04 or 10.10 we need some packages installed.
sudo apt-get install autoconf libtool libpcap-dev libboost-all-dev libhal-dev xulrunner-1.9.2-dev

Next run ./autogen.sh && make and hoplfully you'll don't get any errors

If everthing went ok we should get a build folder (firesheep/build/ firesheep.xpi) 

add "firesheep.xpi" to your add-ons

---

### Post by penseBien2 on 2012-10-27
After following the instruction as stated, I still have this error
------------------------------------------------------------------------------------------------------
The following packages have unmet dependencies:
  libhal-dev: Depends: libhal1 (= 0.5.14-0ubuntu5) but 0.5.14-0ubuntu6 is to be installed
  xulrunner-1.9.2-dev: Depends: libnotify-dev but it is not going to be installed
=----------------------------------------------------------------------------------------------------
Unfortunately I find it difficult to install the backend  repository most other tutorials are talking about. could some1 please help me with that I am trying to install the firesheep on my Ubuntu Lucid FF 10.0

---

### Post by penseBien2 on 2012-10-27
> **Stephaans said:**
> exactly how do I install a previous version? Sorry if this is a stupid question but i am relatively new to Ubuntu.
same issue

---

### Post by squakie on 2012-10-27
> **Dangertux said:**
> Am I the only one who finds it disturbing that people request help on how to perform session hijacking?

IMO if you can't figure out which browser is supported, you probably are not qualified to be doing it legally. Thus you are likely doing this illegally.

I agree - there is too much damage done when people help for something that is specifically for these types of activities who claim "I'm only going to use it at home".   I once saw someone who specifically wanted to hack ask for help, and when someone told them they wouldn't get that help here and why, they started arguing about that Ausuage (or what ever his name was) because he was confused about wiki leaks versus wikipedia.

I don't know what the forum rules might be on something like this, but just me personally think a thread for this should be kept of the forum to somewhere private.

Just me.

---

