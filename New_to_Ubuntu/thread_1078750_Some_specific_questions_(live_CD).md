---
title: "Some specific questions (live CD)"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by sunnymw on 2009-02-23
Today I finally took the plunge and downloaded the 8.10 live CD and "test drove" Ubuntu. I really loved the look of it, and just had a few questions.

1. Migration Assistant--how does this work? Do I have to back up any files (if, say, I am ditching Vista completely), or will it "move" them for me without having to have an external hard drive, etc? Also, will it import my Firefox bookmarks also?

2. If everything worked fine in the live CD version, is that a guarantee that everything will also work once I actually install it? For example: sound worked, memory card reader worked, music player worked, internet would have worked if I'd remembered my password for my router :p ; does that mean those things WILL work once I ditch Vista?

3. Will I---without complication---be able to put MP3s on my Sidekick3 (cell) via USB?



If it helps, I have a Toshiba Satellite A205-S5855, and I connect wirelessly to cable internet via a Netgear WGR614 v9 Router


Thank you so much for your help!


Sunny

---

### Post by bodhi.zazen on 2009-02-23
> **sunnymw said:**
> Today I finally took the plunge and downloaded the 8.10 live CD and "test drove" Ubuntu. I really loved the look of it, and just had a few questions.

1. Migration Assistant--how does this work? Do I have to back up any files (if, say, I am ditching Vista completely), or will it "move" them for me without having to have an external hard drive, etc? Also, will it import my Firefox bookmarks also?

It will copy data for you. I usually do this manually as the migration takes a long time, but give it a try.

> 2. If everything worked fine in the live CD version, is that a guarantee that everything will also work once I actually install it? For example: sound worked, memory card reader worked, music player worked, internet would have worked if I'd remembered my password for my router :p ; does that mean those things WILL work once I ditch Vista?

Well, it takes time to familiarize yourself with a new OS. How much time is variable, It seems 3-6  months. Ubuntu is not a drop in replacement for Visat ;)

Otherwise , yes that is what the live CD is for. Of course nothing is guaranteed, but odds are high if it works on the CD it will work if you install Ubuntu as well.

> 3. Will I---without complication---be able to put MP3s on my Sidekick3 (cell) via USB?

It will probably work, you can test this with the live CD as well. Should be able to plug it in and start using it right away.

You will need to install the "restricted formats" if you wish to play mp3 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by minsf on 2009-02-23
I dont know about the migration assistant, but backing up your data is always important. what you can do, is to squeeze the vista, and create another empty partition on your hard drive, into which you will install ubuntu. then set up _dual boot_, which means that when you boot you can choose between ubuntu and vista. when you finish transferring the data into your ubuntu partition, and if you are satisfied with the results, you can remove the vista completely. 
however, it is always important to back up you data on external source, especially before such installations.
by the way, i am not sure that mp3 java and flash work out of the box in ubuntu (because they are not free), but you should be able to install these quickly with the command "sudo apt-get install ubuntu-restricted-extras".
you definitely need the password for your router (sometimes it can be reset by connecting with a cable directly to the router and pointing the browser to 192.168.0.1 or to 192.168.1.1 and log as "admin" with a blank password or another default password (unless you changed the default admin password))
EDIT: didnt see post #2 while i was writing... sorry for repetitions :)

---

