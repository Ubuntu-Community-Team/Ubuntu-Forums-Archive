---
title: "i have no idea what i'm doing....HELP"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by mandator23 on 2007-06-05
i just installed ubuntu over my windows XP under the impression that my internet would not be harmed.

and i have NO idea how to get my internet connected. some one PLEASE reply to this. i can NOT go much longer without internet on my computer, and using my moms laptop is getting old.

---

### Post by steveneddy on 2007-06-05
UM....how exactly did you connect to the internet before?

Is it a DSL modem or Cable modem?

If so it should work out of the box.

---

### Post by meng on 2007-06-05
Yes, you'll have to provide some details please.

---

### Post by mandator23 on 2007-06-05
it's highspeed.
 i have a modem and a router.
i really don't know too much about this. i just kind of bullshit, for lack of a better word when it comes to computers..
my desktop has a wireless thing in the tower though, so idk if that has anything to do with anything either.

---

### Post by steveneddy on 2007-06-05
OP IMed me with this:

[QUOTE=mandator23]idk, i think it's DSL? 
idk.. i know i have a modem and a router. and i have this wireless chip in my desktop. 
so idk how to make my internet work..

sorry if i'm bothering you but if you know how to help me that'd be greatly appreciated[/QUOTE]

Don't IM me - use the forums so others can get something out of this. Also, there are more people than me looking at your thread, so go back to the thread.

---

### Post by steveneddy on 2007-06-05
OK - the desk used wireless and there is a DSL connection. Open up Firefox and see if it will connect to the internet. 

Where's Firefox? Applications --> Internet --> Firefox Web Browser

Firefox is a web browser much like Internet Explorer.

I don't know where you are so we are starting at the basics.

EDIT: What version of Ubuntu?

---

### Post by mandator23 on 2007-06-05
okay basics is good, 
okay so i do that. i mean,i knew how to open up the internet browser..
but it just shows the UBUNTU page. and wont let me search anthing, basically acting as if i'm not connected....

---

### Post by mandator23 on 2007-06-05
oh my bad, 
really OLD version, 
5.10

i was just going to update it from the internet after i had it installed.

---

### Post by steveneddy on 2007-06-05
do you have a place in the back of the PC box to plug in an Ethernet cable?

Looks like a phone line, but almost twice the size.

And if so, do you have a cable to plug into the machine and then to the router to connect without wireless at the moment?

FYI - 5.10 is a very old version and you will have to update through each level to get something modern and up to date.

I recommend sending off for the new Feisty CD's. They are free and complete.

Or Download the Feisty CD and burn it to a CD yourself.

---

### Post by mandator23 on 2007-06-05
i have the ethernet cable that goes from the router to th emodem.

on the back of my tower i have this antennae thing for my wireless chip that is in there.
but if i connect an ethernet cable from the back of that into one of the places on my router would that make my internet work?

i know i have to update alot. but, 
i have to get my internet to work first..
and i'm struggling.

---

### Post by steveneddy on 2007-06-05
I think the key here is to make sure you can connect with a hard line to the router.

After you plug this in, if there is a place for that on your PC, then to the router, the connection should be automatic

I haven't even SEEN 5.10 in so long that I don't remember what is has for programs, but I don't think that wireless will be easy on 5.10. 

Try to get a hard line hooked up and see if it connects to the internet

something simple like Google.com and search news or something to test the connection.

That is the first step.

---

### Post by shijirou on 2007-06-05
Here's the thing, if you have a wireless router and you're connecting to it wirelessly Ubuntu should automatically detect the wireless connection, then again you are on 5.10, I suggest you upgrade to 7.04 first before doing anything else as its more automated than 5.10.

You can also try plugging in that ethernet cable going to your router. It might help but you might want to setup some settings on Ubuntu if your router isnt set to DHCP. You need to know if your router is set to DHCP, do you know how to access your router?

---

### Post by mandator23 on 2007-06-05
okay, i hate to say this and sound really dumb..

but should i attatch the ethernet cable from my routher to the part in my tower? or from the modem?

---

### Post by mandator23 on 2007-06-05
i need to know how to find out if my router is set up to DHCP i guess.

whatever advice you have. please enlighten me

---

### Post by steveneddy on 2007-06-05
from the PC to the router - that is IF the router is plugged into the modem.

It should go from a small phone line, in the wall, to the modem, then an Ethernet cable from the modem to the router, THEN to the PC with another Ethernet cable.

Even in 5.10, once the cable is plugged up correctly and the power is on in the modem and router, then it should connect automatically. 

You can deal with your other issues after you get a good connection to your router.

Your router should be set up already if Windows was working before.

---

### Post by steveneddy on 2007-06-05
> **mandator23 said:**
> i need to know how to find out if my router is set up to DHCP i guess.

whatever advice you have. please enlighten me

Plug in an Ethernet in first. Get a hard line going, then we can deal with DHCP.

If it connects after the cable is connected, DHCP is working.

---

### Post by steveneddy on 2007-06-05
> **shijirou said:**
> You need to know if your router is set to DHCP, do you know how to access your router?

First things first. Don't confuse the poor girl with the facts.

She was connecting before with Windows, so it must have DHCP already.

We need to get her going through a hard line. Wireless in 5.10 is a pain and he needs to get a basic connection that will work in 5.10.

---

### Post by mandator23 on 2007-06-05
there's 4 different jacks to choose from aside from the ethernet cable connected to the modem.
i put it in number 1. 
and then connected it to the jack in my tower.


then i unplugged my modem and plugged it back in. 

...still not working.

---

### Post by mandator23 on 2007-06-05
and, i guess you were talking about me,
i'm a girl. my names amanda.

---

### Post by steveneddy on 2007-06-05
> **mandator23 said:**
> and, i guess you were talking about me,
i'm a girl. my names amanda.

Sorry Amanda.

Open Firefox and type in the address bar this address:

192.168.1.1

That should be the basic address of the router.

Do this in Windows, your Mom's PC and see if it see's the router that way also.

ALSO - in a terminal - type in

```
ifconfig
```

and post the output.

When you put the 5.10 CD in, it should have been a live CD, right? Did it connect from the live CD? Did youtry to connect to the internet from the live CD?

---

### Post by steveneddy on 2007-06-05
> **mandator23 said:**
> and, i guess you were talking about me,
i'm a girl. my names amanda.

I reworded my post, Amanda.

---

### Post by mandator23 on 2007-06-05
i didn't try on th elive CD however, i have it.. and on my moms laptop it says i need a username and password to get to the router part, but i guess it worked on here besides that. 

uhm and on ubuntu it says the connection was refused.

---

### Post by steveneddy on 2007-06-05
When you typed the address on Ubuntu, the connect was refused?

OK - open a terminal and type 

```
ifconfig
```

Look for a listing that has "lo" on the left with some numbers listed there.

Look for the address

127.0.0.1

Also - there is a listing for "eth0" that should have an address that may start with

169 - 

like 169.32.34.1

Another question - does Mom's lappie connect through a wireless connection?

And does she know the password for the router?

---

### Post by mandator23 on 2007-06-05
i doubt she knows the password however my aunt my know these things.

i really need to get to bed now, 
but if i get back on here and try these things again and repost. 
will you get back incontact with me about it.

i'll let you in on whatever details or conclusions i come to
i'll also speak with my teacher tomorrow, who introduced me to this operating system, and tell him what's going on. and find out his opinions
and see what page we're all on.


i really have to get going, but if you think of anything else i could try doing, please post to me about it and i'll update you tomorrow.

---

### Post by steveneddy on 2007-06-05
It's getting late here - 

Try [http://ubuntuguide.org/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections](http://ubuntuguide.org/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections) for lots of help with Breezy

I'll check on you tomorrow.

EDIT:
Also look [here.]("http://ubuntuguide.org/wiki/Ubuntu#THIS_VERSION_OF_UBUNTU_IS_UNSUPPORTED.2C_PLEASE_UPGRADE")

---

