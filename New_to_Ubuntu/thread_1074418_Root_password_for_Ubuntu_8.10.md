---
title: "Root password for Ubuntu 8.10"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by noelb on 2009-02-19
Hi,

Last week I set up Ubuntu 8.10 to dual boot with Win XP.

I set up the user name and password which gives me access to Ubuntu :D - that was no issue.

should this password also be usable by me to change to ROOT using sudo ?

If not, can anybody suggest how I find or set up the ROOT password ?

Thanks

noelb

---

### Post by PocketDog on 2009-02-19
The established convention is; if you need to ask how, then you don't have the skills required not to mess up your system. We can't help you log in as root, sorry. [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by sisco311 on 2009-02-19
> **noelb said:**
> 

should this password also be usable by me to change to ROOT using sudo ?



Yes, use sudo/gksudo to run applications as root.

[uhelp]community/RootSudo[/uhelp]

---

### Post by noelb on 2009-02-19
Pocket Dog.
Id like to say thanks for your help.
But you did'nt actually offer any so I'll leave it there.

For your information, I am a computer science student experimenting with Ubuntu OS for the first time. Sometimes questions you conside beneeth you come up and people like me come to these forums for assistance in learning, not to her your nerdy CRAP.

---

### Post by PocketDog on 2009-02-19
I'm not going to argue with you. We're not allowed to help you log in as root, as I said. I even posted a staff link to help you understand why, and what alternatives you have. Sorry you don't think I helped, but that was all I was doing.

---

### Post by egalvan on 2009-02-19
> **PocketDog said:**
> The established convention is;** if you need to ask how, then you don't have the skills required not to mess up your system.**
 We can't help you log in as root, sorry. [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Ditto this, as I'm sure many others will.
And please read the link, it has **excellent** explanations as to the rules and **reasons**.
(the author doesn't just spout the rules; many thanks to *aysiu*) 

sudo will accomplish (almost) everything a regular user will need to do on Ubuntu.
(almost) everything else can be accomplished with command-line or gksudo-type tricks...or work-arounds...

"Almost", because there ARE situations you NEED root.
But these are either so esoteric, or so restricted, 
that by that time you do have, or should have, the experience to accomplish this without asking HOW.

In the last year, I've set up over three dozen Ubuntu machines for others, and a dozen or so for myself, and have yet to NEED a root account.
sudo has been enough.

A root account can be dangerous for an un-experienced user.
Experienced users know to limit its use.
Use it with extreme care.

ErnestG

---

### Post by bolucpap on 2009-02-19
noelb, if you read the link in his post, you will find that he is only following the established forum guidelines. If he did break those guidelines and gave you the answer (which I don't know myself, btw) then you still would not see his answer in the forum because the forum admins would remove the post. You can't blame a person for trying to follow the rules of the forum he's posting in and it is certainly unfair to insult him the way you just did.

---

### Post by noelb on 2009-02-19
Hi back, so I dont need a full ROOT account. All I want to be able to achieve is to install VMware Player on Ubuntu platform. If a lesser privalige will allow this, Im happy with that.

---

### Post by sisco311 on 2009-02-19
[uhelp]community/VMware/Player[/uhelp]

---

### Post by tarps87 on 2009-02-19
Instead of using a root account in Ubuntu the sudo command is used.
The sudo command will run the process/program with root privileges.
e.g.
```
sudo apt-get install *programName*
```
This gives apt-get root rights so that in can install the program.

On think to remember is the command "rm -rf" forcefully removes all directories and files in the give directory so rm -rf / will remove every directory and file on the system. NEVER use this command with root privileges(sudo)

---

### Post by egalvan on 2009-02-19
To noelb:

CAUTION, the following answer is **nerdy CRAP**.
Read no further if this kind of stuff insults your intelligence.  :(
Or chaps your hide. ;)
Or gets your knickers in a knot. :)








If you have not done so, PLEASE READ the link given to you in the second post (first answer given by PocketDog)

The author (aysiu) is extremely knowledgeable in *nix matters.
The post has very relevant information, presented in a very-readable manner (better than most of us are capable of doing).

If you are a student, and you are truly wanting to learn,
then reading posts by aysiu is one way of gaining valuable knowledge (aysiu **explains** stuff).

Reading the "rules and regulations" regarding these forums is also highly-recommended.

And keep in mind, **EVERYBODY** on these forums is an **UN-PAID VOLUNTEER**.
A bad attitude is good way to get ignored. :)

---

### Post by sarang on 2009-02-19
Forum policy prevents us from telling the OP how to enable GUI root logins (which are a bad idea anyway, IMO). However, that is not what s/he seems to be asking for.

In ubuntu, you should mostly never have to login as root. If certain tasks require root privileges, you can run them using [FONT="Courier New"]sudo name_of_command[/FONT] or [FONT="Courier New"]gksudo name_of_command[/FONT]. This is mostly equivalent to
```

su root
name_of_command
exit

```
on other linuxes.

---

### Post by Tony Flury on 2009-02-19
> **noelb said:**
> Hi,

Last week I set up Ubuntu 8.10 to dual boot with Win XP.

I set up the user name and password which gives me access to Ubuntu :D - that was no issue.

should this password also be usable by me to change to ROOT using sudo ?
noelb

Assuming that you did nothing complicated and the user you created is the primary account on the machine, then it should be in a list called sudoers (which is essentially a list of all accounts which are allowed to use the sudo command).

When you run something using sudo - it prompts you for a password. It is not prompting you for the ROOT password - it is prompting you for your own password - in order to ensure 2 things : 
[LIST=1]
[*]You are who you say are - that you have not just wandered by an unattended machine
[*]The you recognise that Sudo is going to do something as root - it is an effective "Are you sure"
[/LIST]
So if you are logged in - and sudo prompts you for a password - you type your password - you don't need the ROOT password.

---

### Post by tarps87 on 2009-02-19
> **egalvan said:**
> And keep in mind, **EVERYBODY** on these forums is an **UN-PAID VOLUNTEER**.
A bad attitude is good way to get ignored. :)

What are the beans for then ;)

---

### Post by philinux on 2009-02-19
> **noelb said:**
> Hi,

Last week I set up Ubuntu 8.10 to dual boot with Win XP.

I set up the user name and password which gives me access to Ubuntu :D - that was no issue.

should this password also be usable by me to change to ROOT using sudo ?

If not, can anybody suggest how I find or set up the ROOT password ?

Thanks

noelb

Two sites to help you install anything.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Happy ubuntuing.

---

### Post by Corniger on 2009-02-19
Hi guys!

I've been fiddling around with Ubuntu for about 30 hours now and haven't even got to get the most basic things thinkable to run.

Aside from the WLan problem that seems impossible to solve and 6 fresh installations everytime after a tutorial failed because there IS no "Networking Tab" and there is no "Network administration tool" I'd like to finally install the 3d graphics driver from NVidia, that claims to need being run as "root"

So I setup the root account, but Ubunto won't let me login with root user&pwd.

So please can someone tell me how to get at least THAT done so I can use it to run Blender which originally was ma intention to try Ubuntu after all.

Thanks!

---

### Post by hollowhead on 2009-02-19
Corniger, you are going to have to be a bit more specific with your problems have to posted the wlan problem to the networking forum?  One piece of advice don't delete your root user using SUDO I did and my system was unusable.  On this system I have only found sudo to be not enough to install anything once, then I used the su command.  Now on the specifics I'm surprised the networking applet is not installed by default.  Go to system ->admin->synaptic package manager enter network in the quicksearch box and make sure network manager is installed, if not click on it and select mark for installation and apply.  Once its installed it should automatically connect via a network cable although wifi can be more tricky.  Hope this helps....

---

### Post by Corniger on 2009-02-19
@hollowhead: 
for the root question: even in root I can't install my driver, because I'm running an "X Server" that I'd have to exit and don't know how. Can installing a driver be MORE complicated??

for the network issue: sorry, but imo I've been as specific as I could be. I've reinstalled Ubunto intrepid 6 times now to revert all changes I made.
I can't use a cable to connect, because I'm using an access point with someone else and my device (or the one of the three of my one device listed in the compatibility chart :P ) is supposed to work "out of the box" anyway. I don't even HAVE a cable anymore, except for a 20 cm cable that connects with the modem.
I need a "Networking" Menu item to complete the installation with ndiswrapper, or which of the 400000 different approaches I tried that was again, but there is none, bug known since July 08, not fixed!
I'll try the ndiswrapper procedure once again. If this doesn't work, I already leeched Wubi 8.04.

---

### Post by cariboo on 2009-02-19
@Corniger

It would really help if you listed your hardware, open an Applications-->Accessories-->Terminal and type:

```
lspci
```

please paste thoutput in your next post.

To install the restricted graphics driver all you need to to is go to System-->Administration-->Hardware Drivers, enter the password you setup when you installed, and wait fro the driver to download and install, depending on which server you are connecting to, it may take a while. This assumes you have either an ATI or Nvidia graphics adapter.

Jim

---

### Post by coka on 2009-02-19
hi..
for creating a root password 
use
Administration>>User and Groups>>

unlock by ur simple login password.click on root nd properties and set a password
it may be same as ur ubuntu login password.

---

### Post by Corniger on 2009-02-19
Thanks Cariboo :)

Shouldn't this perhaps be moved somewhere else?

My system data:

> 00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 11)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)


 > 
To install the restricted graphics driver all you need to to is go to System-->Administration-->Hardware Drivers, enter the password you setup when you installed, and wait fro the driver to download and install, depending on which server you are connecting to, it may take a while. This assumes you have either an ATI or Nvidia graphics adapter.

All I get here is a message telling me there's a new driver. I can't download it, because my wireless won't connect. I already tried all sorts of things to get past that issue, also [this]("http://ubuntuforums.org/showthread.php?t=1010650"), but no connection. Networks listed, clickabel, disconnection.

---

### Post by neugier on 2009-02-19
Howdy all! 
 It's been interesting following this thread.  Corniger's recent post goes right to the heart.  It seems to illustrate a very fundamental misunderstanding between Linux users and “previous-windows-users-new-to-linux”.  I feel the latter's frustration, being one.  The former seem no longer able to appreciate how monumental the differences are between the utility of the two operating systems. To a new user, the complicated methods required to do the simplest of tasks, such as change the boot order, are daunting.  Believe me, I've spent the last 2 days trying to do this very task.  For the record, so far, I find any configuring to be unnecessarily complicated. 

I'm into my second day with Ubuntu 6.06 installed from the Live CD in a dual-boot with WinME for my wife.  She has no internet connection for that machine.  I had previously installed Kubuntu 7.10 – nice enough until I needed to do more than check out a couple of the on-board apps.  I had Live CD version of both Ubuntu and Kubuntu and after deciding that community support for Ubuntu seemed more “beginner-friendly”, I installed Ubuntu 6.06 and I’m still trying to solve the same problem.

I appreciate that there's only the bare-bones apps available to me with no web access, but why there'd be no Start-Up Manager where it’s said I’ll find it (to change the default boot order which Psychocats Guide made sound so simple) is a mystery.  Hence, the connection to my remark about this thread being so interesting: previous to my visiting this forum for help, I had googled for help and had many hits showing how to accomplish this boot order change through a command line.  Tried them all - nothing worked. There started to be this wonderful loop that involved "sudo" (whatever the heck THAT is), and "rights" and all the rest of that security stuff.  I'd hoped that installing as simply as possible, I'd be able to avoid all that and I'd be able to do some small configuration when needed. I've tried to view every program on my Ubuntu and there's just no simple way to change my boot order.  And trust me, I'd much rather do it from a GUI as described in the Psychocats Guide as ever have to use command line. Is there something wrong or missing with my version (it's the ordered-through-the-mail-from-authorized-distributor-version), or will Corniger and I forever wander the web corridors going through the many solutions offered until one works for OUR Ubuntu?  I mean, we’re not even up-and-running yet.  What awaits us? (and regarding using “root”, what kind of an operating system prevents you from doing anything you want to it even at the risk you'll screw it up? Isn’t it ours now? Isn't that part of the learning experience, too?)

I truly do admire your willingness to provide assistance to beginners. Please continue to show patience - it’s not a smooth transition for all of us.

---

### Post by Corniger on 2009-02-19
@coka: I already got into root, but it keeps telling me I'm "probably running an X Server" that I have to exit. No chance yet!

---

### Post by rhcm123 on 2009-02-19
> **Corniger said:**
> @coka: I already got into root, but it keeps telling me I'm "probably running an X Server" that I have to exit. No chance yet!

Are you saying you got graphical root access (read: you loged in from the main login screen into root?) That's kinda bad. I learned that the hard way on Gentoo.

---

### Post by Corniger on 2009-02-19
@neugier. what disturbs me personally most of all is, that the user is made believe installing and running Ubuntu is a piece of cake. It's my worst experience since the last 19.5 years of using computers for 20 years now. I've already posted that somewhere else, and frustration amounts are constantly rising and have made me a pissy, unfriendly person for 2 days now. I'm not used to this.

The perfect expression "My Ubuntu" - I couldn't have expressed that any better. There's talk about Network menu items, about system tools that aren't there on MY Ubuntu. How the heck am I as a n00b going to figure this out? I just wanna run Blender and firefox, maybe Gimp and Inkscape and some players. I don't want, and I don't have time to lurk in the murk for weeks. Blender is equally hard to learn, but noone EVER said it was easy. But Ubuntu "just works". Duh.

Luckily, I bitched long enough to make myself read, preventing the worst foulness brimming up to my skullcap from spilling. I'm REALLY not a whiny bitch normally, not at all, but this definitely makes me one.

So, as you said: thanks to all those investing their time in our not having time/brain/stamina with this. You should see paradise, no kidding. /rant

---

### Post by Corniger on 2009-02-19
@rhcm123: I logged out, logged back in with root+root pwd. I opened a terminal and typed, as referred to on the NVidia website "sh", Space, and dragged the Nvidia_blah.run" file into the terminal, as it seemed to work with other files. User is root, so that must be right. All I get then is the X-Server Message.

Edit: I tried all sorts of other root access possibilities mentioned before in these posts. None worked. At least I'm not able to run them properly. I just want to simply run the system, not become a badass Ubuntu crack (yet)

SHOULD I SWITCH TO HARDY, COMMUNITY??? Maybe this one has all menu items?

---

### Post by Perfect Storm on 2009-02-19
After this rant, this thread have run its course.


Closed.

Please start a new one if needed, but note to keep it calm.

---

