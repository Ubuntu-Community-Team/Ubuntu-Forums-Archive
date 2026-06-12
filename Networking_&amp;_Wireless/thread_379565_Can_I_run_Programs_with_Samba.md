---
title: "Can I run Programs with Samba"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by G_Stewart on 2007-03-08
Or can I just view files with it. I'd like to know what it's capable of before loading it. I would like to open programs on the windows machine as well as access files.
Both machines are mine (I have complete control/access).

Thanks
Gary:confused:

---

### Post by Mr. C. on 2007-03-08
No, it is for sharing the same type of resources that Windows Files and Printer's sharing accomplishes.

You can make a connection to your Windows desktop, and see that remote desktop on your local Ubuntu system.  This will allow you to work just like you were there at the remote system at the keyboard/mouse.  Is this what you are looking for?

MrC

---

### Post by G_Stewart on 2007-03-08
Maybe? I have a program, PhotoByte, it's a windows exe file. Can I work with this program?

---

### Post by Mr. C. on 2007-03-08
You cannot use Samba to run this program on your Ubuntu workstation.  Your options are:

1) connect to your remote system's screen and take control of it with Ubuntu
2) use a Windows emulator (such as Wine) and attempt to run your program on Ubuntu
3) configure a virtual pc on Ununtu and install/run Windows and your program in that emulator

Number (1) is very easy.  (2) is more problematic, and (3) is not terribly difficult, but will take a substantial amount learning and your time.

MrC

---

### Post by G_Stewart on 2007-03-08
So, with a linux (Ubuntu) box, I can simply control a Windows machine? Wow, didn't know that.
Here is the whole issue, I tried Wine, doesn't work right for me. I have two machines, the Ubuntu and windows.
I only need windows for that "one" program, there is no linux version.
Instead of having two boxes, keyboards, mice and monitors, I'd like to atleast access the windows machine (which is tucked away in a corner or something).
Is choice #1 the way to go?

Gary

---

### Post by Mr. C. on 2007-03-08
Absolutely, #1 is the way to go for your situation.

Here are the choices:

1) either use Window's built in Remote Desktop and connect with with the Terminal Server client in Ubuntu

2) Install and use VNC on your Windows PC and connect with the VNC client in Ubuntu

With (1), your Windows PC screen will go blank whenever you connect remotely, thus you cannot see both screens at the same time (eg. PC and PC's screen on Ubuntu).  And when you disconnect from the session, you have to log back into Windows, which has logged you out.  In my opinion, this is a nuisance.  I prefer (2).  The VNC server is easy to configure, and allows access to both systems at the same time - in fact, someone at the PC can use the mouse and keyboard at the same time as you!

Let me know which interests you, and we'll go further.

MrC

---

### Post by G_Stewart on 2007-03-08
Definately #2. My ideal situation is to only have the windows box, no mouse, keyboard or monitor. Just a storage bin for that one program (LOL).

---

### Post by Mr. C. on 2007-03-08
Smart man! 

Ok, go pickup UltraVNC at: [http://www.ultravnc.com/](http://www.ultravnc.com/)

Pick the Ultr@VNC 1.0.2 Setup.  Virus scan and install on your PC.

It will startup asking to configure admin options.  Install as a service if you want it to always be running - that's safe on your LAN.  Enter the VNC Password to use, and close the dialog.

Now, go to your Ubuntu station, and launch Applications->Internet->Terminal Service Client. 

Enter the name or IP address of your PC, select the VNC protocol, ignore  username and domain and client hostname (not used here) and click Connect.  Enter the password you typed with you configured the VNC properties on your PC, and you should see your desktop appear.

MrC

---

### Post by G_Stewart on 2007-03-09
OK, now. Should I use a router, install a second NIC, or some other means to communicate?

Gary

---

### Post by Mr. C. on 2007-03-10
Hmmm... so are you saying the two machines are not currently network?  I had been assuming they were since you asking about share between the two.

If they are connected, just run the apps I mentioned.

Perhaps I'm misunderstanding something?
MrC

---

### Post by G_Stewart on 2007-03-10
:confused:  I appologize, they are not connected yet. They're both on my desk (taking up way too much room), which is where the idea for the query came from.
So, yes, I have to connect them and don't know which is the best route.

Gary

---

### Post by xSauronx on 2007-03-10
> **G_Stewart said:**
> :confused:  I appologize, they are not connected yet. They're both on my desk (taking up way too much room), which is where the idea for the query came from.
So, yes, I have to connect them and don't know which is the best route.

Gary

if you have a broadband connection you want to share between them anyway, a router and some cat5 cables would work well. if they both have NICs, a crossover patch cable should be all you need.

but if you just need this one program, setting up the VNC session for the sake of experience is a good idea, but it may well be worth installing wine and seeing how your program runs. Its easy, and wont take long, and if it works properly, could remove the need to even have the windows box. 

i use wine for a couple of minor programs without a problem. i downloaded photobyte 5.2 (what i can only assume is what youre referring to) and it seems to work ok under wine. I only played around with it for a couple of minutes, however.

---

### Post by SuSUntu on 2007-03-10
> **xSauronx said:**
> 
but if you just need this one program, setting up the VNC session for the sake of experience is a good idea, but it may well be worth installing wine and seeing how your program runs. Its easy, and wont take long, and if it works properly, could remove the need to even have the windows box. 


Yes. I'm afraid the OP thinks an UltraVNC session on the Ubuntu client is going to be just like running PhotoByte directly on the host machine. It won't be. It will be slower, and just how slow will depend on a variety of factors, but in any event the lag may be too annoying to deal with.

I know I could never use UltraVNC in this manner if I had other choices, likely in this order:

1. Dual boot
2. Virtual Machine
3.. Use the second machine directly when I needed to use PhotoByte 
4. Wine (if it can be used)

UltraVNC for me has been a tool of last resort when I physically could not gain access to the host machine. I don't think I've ever considered it in such a case as this.

Of course as they say, choice is good and everyone is different.

---

### Post by Mr. C. on 2007-03-10
Guys, we've already discussed and clarified the choices of how the OP wants his configuration, and I've explained where the application be executing.  Please read the entire thread.

G_Stewart: minimally, I would recommend a switch and two ethernet cables to connect the two systems.  I disagree with the other poster's advice about a direct cable between the systems - older systems have problems with 100Mbit and autodetection of correct speeds and duplex for Ethernet networking, and it is simply not worth the hassle.  A switch allows your local machines to communicate with each other over Ethernet.

Now, if you have, or plan to have broadband, then get a "router" as they are commonly called in the consumer world (they are really multifunction network appliances).  This also acts as a switch,  and allows multiple PCs to communicate.

The statement below about VNC being slow over a local 100Mbit network is incorrect.  VNC is very fast, you'll hardly notice any difference in speeds.  I use it quite well, even remotely; locally, its performance is excellent.

The dual boot and virtual PC solution are workable, but it requires more knowledge and learning.  This seems far too much for what your desired solution is.

When you get the hardware to connect the two, let's continue.

MrC

---

### Post by SuSUntu on 2007-03-10
> **Mr. C. said:**
> Guys, we've already discussed and clarified the choices of how the OP wants his configuration, and I've explained where the application be executing.  Please read the entire thread.

<snip>

The statement below about VNC being slow over a local 100Mbit network is incorrect.  VNC is very fast, you'll hardly notice any difference in speeds.  I use it quite well, even remotely; locally, its performance is excellent.

The dual boot and virtual PC solution are workable, but it requires more knowledge and learning.  This seems far too much for what your desired solution is.

When you get the hardware to connect the two, let's continue.

MrC

Mr. C,

- The thread is not exclusively yours. 

- Yes, the options had been decided, but only after the OP read input from you. Perhaps he would like to see other opinions. 

- Yes, I did read the entire thread, and at no point prior to me mentioning it was the possibility of lag brought up. Despite what you say, a number of factors can come into play besides the speed of the connection. If lag is not an issue in this particular case, then great. But it does not hurt to mention that it is a possibility.

- Apparently, so far, you are in the minority in preferring UltraVNC over other solutions. What the OP prefers is in direct relation to what he learns here as he has admitted to lacking the knowledge to understand what his choices are and how to implement them.

- Yes, UltraVNC **may** be less hassle, but that is not always the best criterion for a solution.

I would not have posted with such a tone, but you seem to have grabbed the thread as your own to the exclusion of others, and I find it both funny and pathetic at the same time.

Edit:

I apologize to you, G_Stewart, for interrupting your thread with this last post, but I felt compelled to make it.

---

### Post by Mr. C. on 2007-03-10
I have no problems with other advice.  All opinions are valid and useful.

The OP already rejected wine on his own accord, after trying it.  It is not a solution he desires. The OP has expressed that much of this stuff is new to him, and as such offering advanced solutions that require more configuration and complexity than less, does not satisfy a novice's requirements.  We discussed an emulator, and my simplistic ranking system helped determine the OPs preference for difficulty.  The more difficult configuration should tried if and only if the simple ones do not satisfy the requirements.

I object to other's making assessments of what the OP wants or thinks  ("the OP thinks an UltraVNC session on the Ubuntu client is going to be just like running PhotoByte directly on the host machine").  You cannot think for him/her.

Let the OP decide after trial of the simplest solutions first.  Cluttering of the clarity of this dialog with unwarranted fears of "lag" at this point serves little purpose.

Majority rule does not override sensibility.

MrC

---

### Post by G_Stewart on 2007-03-10
:eek: Let's take it easy. I don't want hard feelings for anyone, just so we are all on the same page I will reiterate my knowledge and experiences:

* I am not a complete novice (Although not offended by the statement), I have simply not dug really deep into the guts yet. Plenty of installs and simple configurations.
*  I have tried wine and was not happy with it. For some reason the text is very small and misaligned.
* I have a single peice of software (PhotoByte 5.2) that I want to run.
* I also tried VMWare, just too cheap to buy it. LOL
* Lag time, if minimal (a second?) may be acceptable.
* Dual boot is a last resort also, I really want to access both PhotoByte and Ubuntu at the same time.
* The thread is surely open to anyone with ideas, which I am sure Mr. C agrees.
* Ease of introduction???? Well I'd prefer not needing a computer science degree to do it, but I learn best by doing.
* Up front, I want to thank everyone for trying to help and...
* In the "absolute" worst issue, I will just have two machines with Monitor, keyboard and mice switches between them. Ugh.


Gary

---

### Post by Mr. C. on 2007-03-10
Excellent clarfication Gary - thanks.  No harm meant by novice; we all are at one point.

Let us know if you need more assistance.  I think you have enough to take the next steps.

Cheers,
MrC

---

### Post by dmizer on 2007-03-10
> **G_Stewart said:**
> * I also tried VMWare, just too cheap to buy it. LOL

wait ... vmware [COLOR="Red"]server[/COLOR] is what you need to build your virtual machine, and it's free of charge.  you just have to register (which is also free of charge) and they give you a key (again, free of charge).

if your ubuntu machine is faster than 1.8ghz cpu with about 512meg of ram, you will not notice much (if any) performance issues unless you're using some very cpu intensive programs (gimp for example).

vmware server is right here: [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) don't forget to register.  it is fantastically simple to install even from source.  then, installing windows is nearly identical to how you would install it on a new computer (ie. stick the disk in and follow the prompts).

no cost option, and will not require you to have two computers.  won't have the lag of vnc, and you can have access to your program on demand in an actual windows environment.

---

### Post by Mr. C. on 2007-03-10
> **dmizer said:**
> ...unless you're using some very cpu intensive programs (gimp for example).

Ummm.... didn't the OP say the *only* application he wanted to run was a photo-processing app ?

It is not at all obvious in my mind that an *emulator* will be faster than intelligent bit blasting across a 100Mbit network.

MrC

---

### Post by dmizer on 2007-03-10
> **Mr. C. said:**
> Ummm.... didn't the OP say the *only* application he wanted to run was a photo-processing app ?

It is not at all obvious in my mind that an *emulator* will be faster than intelligent bit blasting across a 100Mbit network.

MrC
the only app in windows ... yes (photobyte appears to be a business management application rather than a photo processing app).  but it might be too costly to use gimp or openoffice in ubuntu with the virtual machine open, so it might be a good idea to close the virtual machine.

here's the deal, i used vnc for about a month because i had no choice.  and it was painful.  i used vnc to access my windows machine so i could print to my company's multi-function networked printer (for which there are no cups drivers)

i tried to make the vnc setup as optimized as possible.  i dedicated a second network adapter for the connection, and ran a crossover cable directly from the host to the client.  but the usability factor was terrible.  artefacting and lag even at low resolution made the arrangement barely passable for daily use. 

now i run windows in a vmware server emulation and it works quickly ... no lag, no arefacting, and i can have it on demand without having a second computer on all the time.  at worst, i have to wait a minute or two for windows to boot.

that said ... vnc is certainly easy enough to implement and try.  and if it works to the desired level ... no worries.  but considering my experience with vnc, i thought it would at least be prudent to offer a viable alternative.

---

### Post by Mr. C. on 2007-03-10
> **dmizer said:**
> the only app in windows ... yes (photobyte appears to be a business management application rather than a photo processing app).
Yes, this is correct.  I presumed incorrectly.  Such an app should perform fine under a VM.

> 
here's the deal, i used vnc for about a month because i had no choice.  and it was painful.  i used vnc to access my windows machine so i could print to my company's multi-function networked printer (for which there are no cups drivers)

It's clear to me that the performance you saw was a show stopper for you.  I have been using virtual desktops for at least 15 years, and am pretty comfortable assessing with how they perform over a network, and which apps are problematic.  The Citrix solution is an outstanding implementation, those shows a virtual desktop across the internet can perform well enough that most light users don't notice the difference.  My wife is upstairs now infact, using Lotus Notes, Office products, and various other apps, all remotely.

> 
i tried to make the vnc setup as optimized as possible.  i dedicated a second network adapter for the connection, and ran a crossover cable directly from the host to the client.  


I wonder if you tested the performance of this network.  Some NICs simply do not behave well, and drop to 10Mbps.  Are you sure there were no packet drops, retransmissions, etc. ?

I agree with your assessment as well - the OP will give his/her feedback as to how well any of the setups work.   I'm all for simplest first, and then increase complexity as requirements dictate and familiarity slides towards solid competency.

Cheers,
MrC

---

### Post by G_Stewart on 2007-03-12
I looked into VMware, I was under the impression (possibly wrong I see now) that there were only a few programs available to run under it?
I have no objections to running it. How exactly does it work, ie, how is it different from VMwares virtual machine?

Gary

---

### Post by Mr. C. on 2007-03-12
VMWare is a hardware emulator.  It emulates instructions at the machine language and operations level.  It is a virtual machine.

Some kernels are starting to support virtualization at the kernel level to run multiple OS's, each within its own virtual machine.

MrC

---

### Post by dmizer on 2007-03-12
> **G_Stewart said:**
> I looked into VMware, I was under the impression (possibly wrong I see now) that there were only a few programs available to run under it?
I have no objections to running it. How exactly does it work, ie, how is it different from VMwares virtual machine?

Gary

vmware server is the software that allows you to build your own virtual machine.  so, install vmware server, stick your windows xp/2000 disk in your cdrom, and install windows ... while ubuntu is running.

like so (click to enlarge):
[[img]http://dmizer.dnsdojo.net/albums/screens/vmware.thumb.png[/img]](http://dmizer.dnsdojo.net/albums/screens/vmware.sized.png)

obviously ... in the above environment, your software will have no problem running.

---

### Post by G_Stewart on 2007-03-14
Thanks,
Does this actually install windows onto my HD or do I need to put the win disk in everytime I want to run it?

Gary

---

### Post by Mr. C. on 2007-03-14
It installs it onto your hard disk, either in a private partiion, or in one very large file which will later be configured to look like a file system that vmware uses.  So, no, you will not need to keep your Win XP disk in the CD/DVD tray.

MrC

---

