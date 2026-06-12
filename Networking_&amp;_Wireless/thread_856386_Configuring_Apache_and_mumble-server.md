---
title: "Configuring Apache and mumble-server"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by Aardolan on 2008-07-11
Hi, I was looking at running mumble-server for a group of friends, and installed mumble and mumble-server, but have yet to figure out how to set it up. Looking at mumble's sourceforge site I read something about setting my webserver to run murmur (mumble-server) as a cgi script. 

I've also checked that apache is indeed installed (although I don't really know when it was installed), and tested it through [http://localserver](http://localserver) to ensure at least that much works so far.

I'm rather new with this kind of thing, so please forgive the ignorance. Any assistance would be greatly appreciated.

Edit: I'm on an AMD X2 system with 64bit Ubuntu installed, in case that helps

---

### Post by openxs on 2008-08-23
I can point you in the right direction...

How to install Mumble:
Ref: [http://mumble.sourceforge.net/Installing_Mumble](http://mumble.sourceforge.net/Installing_Mumble)

I downloaded and installed Mumble on my laptop via Synaptic. I found I had to install libqt4-sql-sqlite to make mumble start as it couldn't find the database.

```
sudo apt-get install libqt4-sql-sqlite
```

I had to configure a mumble-server.ini file too, it's well commented so be sure to read it.

```
sudo nano /etc/mumble-server.ini
```

After this I found the documentation got me up and running fairly quickly. I have set up Murmur on a separate server with lots of bandwidth and no GUI install.

Please try to be more specific with any errors you see, or at what point the software fails, you're more likely to get a quicker response.

---

### Post by Moezzie on 2008-11-21
So did you guys ever figure out how to get it working properly?
Ive been trying hard for a couple of days now. I got everything working except for the registration.cgi and weblist.cgi. The Apache does'nt seem to run them, it just sends its contents to the browser as a bunch of text.

Any ideas on how to fix this?

---

### Post by axel1973 on 2009-03-08
i guess, they dont. or they just ignore the facts that those packages and manuals packed with it are incomplete.

it looks like nobody realy cares.

id say, usualy if you install a software package officialy supported it should "run out of the box" and include some manuals. in case of ubuntu's mumble packages it does not seems so.

all talk about a webinterface, cgi and other crap, but there is no HOW AND WHERE. 

and the worst thing i think, there seems to be no apropriate admin too for the CLI. only crapy/cryptic dbus thingies that wont work either.
 

SAD!! Real SAD!

---

### Post by clenched_sphere on 2009-07-01
Seconded.

I've been trying to get an open source, cross platform voip server up and running for a while, mumble was the best one that fitted the bill.
Got the server configured and running over the command prompt, got everyone connected OK.

Now, as for administration...... absolutely no tangible help or guides for this at all. Alot of random Dbus stuff that, as said above, does not seem to work at all. So I'm stuck with a basic voip server that I have no administrative control over whatsoever.

I have also tried various PHP webmin packages, but again no dice. Apache with PHP already installed just throws up errors found in the PHP files..... and line numbers - don't know PHP so can't fix them.
The only other admin option is a GUI that uses SSH and is written for (brace yourself) windows.
Out of desperation, tried to run that on wine, no luck.

Someone who knows or has managed to solve these problems needs to write an up to date and comprehensive walkthrough, or even a proper php webmin or linux gui that does not fail with no explanation (and has installation instructions if anything special is required). 
I wish I could be that person but I'm banging my head on the desk with this, I think I'm going to have to just give up and find something else.

Hopefully someone will manage to write a good guide in English sometime in the future. <hint hint>

---

### Post by ljrossi on 2009-08-26
Same trouble, This might help.


[http://www.howtoforge.com/mumble_voice_chat_fedora_7](http://www.howtoforge.com/mumble_voice_chat_fedora_7)

---

### Post by Rhubarb on 2010-02-01
I've just recently switched to using mumble 1.2.1
I must say that it's a really big improvement from older mumble releases.

1.2.1 isn't in the Karmic repositories, but there is a PPA package for it around (check mumble's [website]("http://mumble.sourceforge.net/")).

To setup your mumble server and for details how to register users:-
[http://mumble.sourceforge.net/Murmurguide](http://mumble.sourceforge.net/Murmurguide)

Registering users can be performed by the users themselves via the mumble client.
It is also possible to set ACLs via the mumble client as well.

So there's no need to use dbus or webserver stuff to get it running now :D

---

### Post by hamiltenor on 2010-02-25
> **Rhubarb said:**
> I've just recently switched to using mumble 1.2.1
I must say that it's a really big improvement from older mumble releases.

1.2.1 isn't in the Karmic repositories, but there is a PPA package for it around (check mumble's [website]("http://mumble.sourceforge.net/")).


I've been looking for a way to install this release (1.2.2) which is only in the Intrepid repositories, and for stability sake, I'm running Karmic on my headless server box. ANyone have some tips on upgrading or reinstalling so I don't have to use the god awful 1.1 app in OS X?

---

