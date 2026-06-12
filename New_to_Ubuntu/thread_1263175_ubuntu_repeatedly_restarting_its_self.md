---
title: "ubuntu repeatedly restarting its self"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by mbyrd11 on 2009-09-10
alright so i have a problem that started last night while i was doing my homework
while i was doing my homework i also had another workspace with youtube open lisening to music
then my computer restarted its self
i finish my homework and today it did the same thing begining the same as it had before except now at the worst ive had ubuntu restart just a few seconds after logging in, or on the internet just using google or something like that.
ive tryed using both the -15 kernal and the -11 kernal with no differnce

im using ubuntu on a hp pavilion dv4



any help is appreciated!

---

### Post by cholericfun on 2009-09-10
maybe temperature problem?

although then it should just shutdown and not restart...

when youre on the computer do a 
```
top
``` in a command-window to see processes running,
maybe you get a glimpse of something before system reboots

---

### Post by mbyrd11 on 2009-09-10
im actually on the laptop right now and i know for sure its not a overheating problem because im on a desktop.
but were should i type "top" in at?

---

### Post by Paqman on 2009-09-10
> **cholericfun said:**
> 
although then it should just shutdown and not restart...


Depends on the BIOS. I'd put money on it being overheating, although I guess it could be a loose connection on the power supply.

---

### Post by mbyrd11 on 2009-09-10
> **Paqman said:**
> Depends on the BIOS. I'd put money on it being overheating, although I guess it could be a loose connection on the power supply.
i dont recall it being overly hot whenever it would restart.
and it doesnt appear to have a loose connection.
i honestly dont think that it could be the problem, however could very well be.

---

### Post by starcannon on 2009-09-10
Yeah mines doing it as well when I resize transmission details window; not sure if its related, but for now I don't resize that windows :(

---

### Post by Dr Belka on 2009-09-10
> **mbyrd11 said:**
> i dont recall it being overly hot whenever it would restart.
and it doesnt appear to have a loose connection.
i honestly dont think that it could be the problem, however could very well be.

This laptop has run ubuntu 9.04 just fine for about one month, maybe a bit more, just fine.  It is still able to drop to a root shell when you go to the system recovery sections under either kernel at grub.

---

### Post by Dr Belka on 2009-09-10
It seems like firefox, especially when using a plugin for youtube vids or when using java for some sort of game is a sure fire way to get this thing to restart.

Sometimes, it wont even make it from grub to the gdm.

---

### Post by mbyrd11 on 2009-09-10
another funky thing that it has done is when i try to log in i find that the scroll pad and keyboard dont seem to be responding

also whenever i attempt to start up vista all that i get is the microsoft corporation loading screen and it stays there and never goes onto the loggin menu.

when it does restart it likes to make little patches green bars across the screen


and cholericfun would it be helpful for me copy and paste whatever i get when i type "top" into the terminal?

---

### Post by lovinglinux on 2009-09-10
> **mbyrd11 said:**
> another funky thing that it has done is when i try to log in i find that the scroll pad and keyboard dont seem to be responding

also whenever i attempt to start up vista all that i get is the microsoft corporation loading screen and it stays there and never goes onto the loggin menu.

when it does restart it likes to make little patches green bars across the screen


and cholericfun would it be helpful for me copy and paste whatever i get when i type "top" into the terminal?

Looks like a hardware problem. I had similar restarts sometime ago and discovered that my motherboard was burned, literally.

---

### Post by mbyrd11 on 2009-09-10
well its a relatively new computer i got it just in the middle of july

---

### Post by lovinglinux on 2009-09-10
> **mbyrd11 said:**
> well its a relatively new computer i got it just in the middle of july

Boot from LiveCD and perform a memory test.

---

### Post by wojox on 2009-09-10
May need to turn acpi=off

---

### Post by egalvan on 2009-09-10
> **lovinglinux said:**
> Boot from LiveCD and **perform a memory test**.

Absolutely,

and while you are at it, check it for dust build up.

And please don't say "it's too new for dust",
because dust can build amazingly fast.

And checking for dust costs nothing but time.

And if it's a Dell, it may have too much heatsink paste on the CPU heatsink.

---

### Post by mbyrd11 on 2009-09-10
> **lovinglinux said:**
> Boot from LiveCD and perform a memory test.
i didnt do it off of a liveCD however i did manage to do a memory test with vista and it said there were hardware problems.
tommarow my friend is going to help me out with it and use a live usb or something like that.
it very well may be a hardwer problem were i need to to send it in.

> and while you are at it, check it for dust build up.

And please don't say "it's too new for dust",
because dust can build amazingly fast.

And checking for dust costs nothing but time.

how would i go about doing a check on dust build up.
were the fan it looks like there are no abnormal quantities of dust.

---

### Post by cholericfun on 2009-09-14
re: top command
sorry was away for a bit,

just type "top" in the terminal

Applications-Accessories-Terminal

but that probably wont as much help as i originally thought it would.

---

### Post by earthpigg on 2009-09-14
if it's still under warranty, take it back and tell them to deal with the overheating problem caused by manufacturer defect and/or 'hardware failure occurring as a result of normal use.'

if you don't want to do that or it isn't under warranty:


> **mbyrd11 said:**
> how would i go about doing a check on dust build up.
were the fan it looks like there are no abnormal quantities of dust.

ensuring the computer is unplugged and you protect the computer from ESD, pop the hood and look. spray a compressed air can around and see how much dust flies in your face.

while in there, see if the heatsink/fan is firmly seated against the CPU. there should be no wiggling occurring here if it is firmly seated. this could be an overheating problem, too, caused by that. on intel systems, the heatsink is frequently held in place by cheapo little plastic things.

a power cable could also be lose, preventing a fan that should be spinning from spinning.

both an improperly installed heatsink and a lose power cable inside could be the result of some new guy at the factory not pushing firmly enough, and it finally came all the way lose when you nudged your computer desk or something.

but, before we physically fiddle with hardware let's go ahead and see what temperature your motherboard reports it's components as being at:

install lm-sensors.

```
sudo apt-get install lm-sensors
```

configure lm-sensors

```
sudo sensors-detect
```

if sensors-detect tells you to restart so kernel modules can get loaded, do so. if not, dont bother. and post the output of

```
sensors
```

---

### Post by mbyrd11 on 2009-09-15
i cant even get to ubuntu any more becuase i just got my system recovery disks because i was just going to redo everything and see if i had any luck.
now every time its almost done i get one of two blue screens
one says
"IRQL_NOT_LESS_OR__EQUAL"
and the other
"PFN_LIST_CORRUPT"
 
im not sure if anyone knows what this means but i thought that id put it up
 
sorry whoever just posted that looks really helpfull i just now got access to another computer and did the recovery disk today :(

---

