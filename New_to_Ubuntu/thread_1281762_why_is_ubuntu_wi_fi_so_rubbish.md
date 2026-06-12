---
title: "why is ubuntu wi fi so rubbish"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by blake7 on 2009-10-03
i have change over to wicd manager and still cant link up in cafes
what is the problem 
why cant i just get on with it like windows and mac users who have no problems 
???

cheers

---

### Post by muteXe on 2009-10-03
any info about your machine please?  Don't you think that might help...?

---

### Post by Bartender on 2009-10-03
Stuck with dial-up at home, so I often go downtown to the library with an Acer 5920 Centrino laptop.  I get online effortlessly.  Have seen several people fuss with their Windows laptops for quite a long time before finally getting on.  With Windows, we were never sure why it finally worked.

---

### Post by halitech on 2009-10-03
> **blake7 said:**
> i have change over to wicd manager and still cant link up in cafes
what is the problem 
why cant i just get on with it like windows and mac users who have no problems 
???

cheers

because hardware manufacturers don't care about *nix so the *nix community has to get the hardware and then try to code drivers to make them work. This is not easy to do without their help so the longer a device has been around, the better the odds are that it will work.

As far as windows users having no issues, try doing a fresh install and then find all the drivers needed to get the system to actually work properly. Thanks but I'll take messing with wireless for 15 minutes and have a working system over 3 weeks of doing updates, installing drivers, doing more updates to find it killed a driver, reinstalling drivers, wash, rinse repeat.

---

### Post by blake7 on 2009-10-03
i have a ibm x60s 
honestly thier are so many cafe that i cant load up on to whcih everone else is cool with??

help

---

### Post by halitech on 2009-10-03
open a terminal and run
```
lspci
```and```
lsusb
``` and post the results. Does the wireless connect anywhere?

---

### Post by gnudoc on 2009-10-03
"the problem", essentially, is that the wifi card makers don't particularly believe you should have the right to use your wifi card with ubuntu, or any other form of linux.

If you're here to rant, then by all means do so. Don't expect a solution to your problem though. The folks on these forums provide support out of the goodness of their heart, out of their own free time, and the overwhelmingly vast majority of them have nothing to do with the existence of your problem.

If you're here to get help, however, then let's start with some basic information about your computer, its wireless card, and what version of ubuntu you're using.

I'm guessing it's a laptop, since you mentioned a cafe. What brand? what model?

Next, go to System -> Administration -> Hardware Drivers. After a short while, you'll see a window called Hardware Drivers, like the screenshot below. Tell us what's listed where my screenshot shows Nvidia drivers, and whether things are activated (green light) or not (grey).

Then, go to Applications -> Accessories -> Terminal. Maximise the window, then type the following: ```
lspci -nn
```

Exactly as you see it. Note the space between the i and the -.

You should get several lines of text appear, like my 2nd screenshot below (except it's probably black text on white, not transparent like mine). Paste this text into your reply. Also do the same with ```
lsusb
```

Also tell us what version of ubuntu you're running. If you're unsure, a quick ```
lsb_release -cs
``` will tell you.

Good luck
gnudoc

---

### Post by blake7 on 2009-10-03
yea it can see all the net works but spends a long time trying to link then it says sorry im rubbish and could nnot do a simplest of  jobs  

if you know what i mean

---

### Post by halitech on 2009-10-03
> **blake7 said:**
> yea it can see all the net works but spends a long time trying to link then it says sorry im rubbish and could nnot do a simplest of  job 

if you know what i mean

if you can see the networks then it is another issue then the wireless card not working. If you could give us the exact message you are getting and not a bunch of rubbish then we will be able to help you help yourself but if you don't really want the help and just want to complain, then go for it but don't expect a lot of sympathy from the users here that have had issues themselves and gotten things to work by helping themselves.

---

### Post by blake7 on 2009-10-03
it works with some but not others thiers no error message it just say not connected after a long time trying
or im rubbish and could not do the simplest of tasks that even  windows can do that any day   of the week and windows is really rubbish and hopeless

cheers   :)

---

### Post by nickpaton on 2009-10-03
> **halitech said:**
> open a terminal and run
```
lspci
```and```
lsusb
``` and post the results. Does the wireless connect anywhere?

You need to post the results of each of the above commands if you want anyone to help you.

We hear and understand what you're saying but if you want help then you need to at least do the above.
If you're not sure how to do them just say - it's OK to say that!

---

### Post by nickpaton on 2009-10-03
Also can you post the output from a terminal:

```
iwconfig
```

---

### Post by nickpaton on 2009-10-03
Done a search on "X60s wireless" within the forums and it appears there is a wireless problem.

Check [**this**]("http://ubuntuforums.org/showthread.php?t=1269667") for instance, but try the search yourself.

---

### Post by fela on 2009-10-03
> **blake7 said:**
> it works with some but not others thiers no error message it just say not connected after a long time trying
or im rubbish and could not do the simplest of tasks that even  windows can do that any day   of the week and windows is really rubbish and hopeless

cheers   :)

Umm, no. It's not windows that performs all the tasks that so many people credit it to be able to do. It's the drivers and other software made for it.

Windows on its own is actually pretty damn primitive. XP would not even detect my integrated ethernet or my integrated audio, which really is the simplest of tasks. It was up to the hardware manufacturer to code a driver for it, of course they did because everyone uses windows.

+1 to the guy trying to help you, if you want help you have to give error messages, not stupid things like 'ubuntu cant connect to wireless omg lolzorz ubuntu sucks how can i fix it'.

---

### Post by freechiru on 2009-10-03
Wish I was getting this kind of help XD  I don't suppose anyone could help me with my wireless?  You'd have to tell me how to post text from a terminal to here first, though.

---

### Post by halitech on 2009-10-03
> **freechiru said:**
> Wish I was getting this kind of help XD  I don't suppose anyone could help me with my wireless?  You'd have to tell me how to post text from a terminal to here first, though.

check your thread, just posted some help there for you. You may also want to post the link so people can go take a look and keep the info here just for the OPs issue.

---

### Post by freechiru on 2009-10-03
Of course... Sorry, so long since I've used forums, my etiquette is right down the drain!  Thanks for the help.  The other thread's [http://ubuntuforums.org/showthread.php?t=1281785&page=2](http://ubuntuforums.org/showthread.php?t=1281785&page=2) if anyone was interested.

---

### Post by anewguy on 2009-10-03
Silly me - I'm from the states, and here "rubbish is equated to trash/garbage, and we have a couple of sayings here:

- garbage in, garbage out

- one man's trash is another man's treasure


The point?  You need to post back the information requested by others previously in this thread, and we need specifics, not things like rubbish if you know what I mean (we don't).  So far, the information has been for the most part rubbish for us to help you.  The best you've done so far is to post the model of your laptop - and you notice that after you did someone posted a response about possible wireless problems with it.

It's already been mentioned, but Ubuntu/Linux isn't the problem - it's the lack of support from the vendors.  They write drivers for their pieces of hardware (like wireless adapters) for Windows (and Windows wouldn't work with them without them either) and provide support for their products for Windows.  The vast majority of them do not do the same for Linux, as they feel a "free" operating system and "free" software means no money for them.  And who knows - Microsoft might even have said that in order for us to put your hardware on our approved list you must not develop it for other operating systems.

There may be a legitimate problem with the support for your wireless from a Linux standpoint - but again this isn't Linux's fault, rather that for the most part hard working people spend part of their free time at home trying to write drivers for some of the hardware, for free to boot, with no support from the vendors.  I don't know what you knowledge depth is in computers, but I can whole heartedly guarantee you that writing a driver from scratch is not an easy task.

So, to be honest with you, some of your posts just seem to be complaining without providing any real information that is needed for everyone trying to help you.  Remember - nobody here gets paid for doing this, everyone is doing it in their free time when they could be enjoying other things, and everyone is here simply to try to help.  It's that easy.

Please provide all the information that has been requested, and people will try their best to help you.

Thanks!
Dave :)

---

### Post by itsbrad212 on 2009-10-03
[LEFT]when i had windows, my network connection was always at 5 connection bars. But when I dumped windows and switched to ubuntu, the same connection wont go above 2 bars, however the loading speed is faster. it might not be an ubuntu thing, but an entire *nix thing. It also does the same on my mac.
[/LEFT]

---

### Post by fela on 2009-10-03
> **itsbrad212 said:**
> [LEFT]when i had windows, my network connection was always at 5 connection bars. But when I dumped windows and switched to ubuntu, the same connection wont go above 2 bars, however the loading speed is faster. it might not be an ubuntu thing, but an entire *nix thing. It also does the same on my mac.
[/LEFT]

On our laptop that has windows on it, it lies about the connection strength. I think it's just a windows thing and you're getting the same strength on both UNIX/Linux and Windows.

---

### Post by theozzlives on 2009-10-03
> **freechiru said:**
> Wish I was getting this kind of help XD  I don't suppose anyone could help me with my wireless?  You'd have to tell me how to post text from a terminal to here first, though.

try:
```
lspci > pci.txt
lsusb > usb.txt
```
and attach the files to a message.

---

### Post by Jakey_TheSnake on 2009-10-03
I think this person is either very young, or mentally challenged. Or a windows Troll. 

Hello halitech, long time no see, good to know you're still alive and kicking. Even if you don't remember me >_>

---

### Post by running_rabbit07 on 2009-10-03
OP, you really need to post the stuff that is requested in order to remove your connection from the rubbish bin.

---

### Post by fela on 2009-10-03
quick sticks OP, this thread is in danger of being closed.

---

### Post by gnudoc on 2009-10-04
Yeah, it's starting to look our friend the OP was here to rant, and nothing else.

Ah well, I hope that worked for him. :)

---

