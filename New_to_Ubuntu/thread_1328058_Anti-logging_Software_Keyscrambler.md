---
title: "Anti-logging Software Keyscrambler"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Richiegs on 2009-11-16
I have used Ubuntu for almost 2 weeks and I already found a few viruses thru Avast and Clamtk. There is an anti-logging software called Keyscrambler in Windows. I wonder if there is a similar program in Ubuntu.  Many thanks

---

### Post by Paqman on 2009-11-16
> **Richiegs said:**
> I have used Ubuntu for almost 2 weeks and I already found a few viruses thru Avast and Clamtk.

These are either Windows viruses or false positives, they're highly unlikely to be any threat to you.

---

### Post by skymera on 2009-11-16
> **Richiegs said:**
> I have used Ubuntu for almost 2 weeks and I already found a few viruses thru Avast and Clamtk. There is an anti-logging software called Keyscrambler in Windows. I wonder if there is a similar program in Ubuntu.  Many thanks

It's highly unlikely this is a genuine virus. 
It's even less likely to run if it was.

This is most probable a Windows virus that has been picked up.

---

### Post by openuniverse on 2009-11-16
.

---

### Post by t0p on 2009-11-16
> **Richiegs said:**
> I have used Ubuntu for almost 2 weeks and I already found a few viruses thru Avast and Clamtk. There is an anti-logging software called Keyscrambler in Windows. I wonder if there is a similar program in Ubuntu.  Many thanks

Running 2 AV programs, huh?  Belt-and-braces behaviour in Windows; complete and utter crazy-paranoia in Linux.

What makes you think these are Ubuntu viruses?  Have you even googled them?

These are almost definitely either false positives or Windows viruses.  Windows viruses can't harm your Ubuntu setup.

---

### Post by wilee-nilee on 2009-11-16
> **t0p said:**
> Running 2 AV programs, huh?  Belt-and-braces behaviour in Windows; complete and utter crazy-paranoia in Linux.

What makes you think these are Ubuntu viruses?  Have you even googled them?

These are almost definitely either false positives or Windows viruses.  Windows viruses can't harm your Ubuntu setup.

Belt and braces not sure what that means; always be prepared would be what I think it means. I have W7 and have 4 diffrent AV programs only 2 run live 
1st is the windows latest
2nd avast
3rd superantispyware
4th malwarebytes. 
The last two are very good
I just like to have fun, and these are all free.

I started on Linux though that is where I am 90% of the time, I just got W7 for 29$ so why not eh.

---

### Post by 3rdalbum on 2009-11-16
> **wilee-nilee said:**
> Belt and braces not sure what that means; always be prepared would be what I think it means.

"Belt and braces" means the same as "everyone does it" or "par for the course".

> I have W7 and have 4 diffrent AV programs only 2 run live

You have two anti-virus programs running live at the same time? That's a very bad idea. Very, very bad idea. Besides which, even one live scanner makes your computer noticeably slower.

---

### Post by Sir Jasper on 2009-11-16
Hi,

Belt and braces means maximum protection so that your trousers don´t fall down.

If you are using Wine then by all means use Avast (Much faster than Clam?) on your Home directory. I assume you have Broadband so you could also use a-squared Free [http://download1.emsisoft.com/a2usb.zip](http://download1.emsisoft.com/a2usb.zip) unpack it and run a2free.exe. 

In Windows On Access or On Executions guards _may_ slow your computer but surely that is a price worth paying since Prevention is better than detection or cure.

My regards

---

### Post by Richiegs on 2009-11-16
The virus is called pua.script.packed-2. Is it from Windows or just a false positive?

---

### Post by 3rdalbum on 2009-11-16
> **Sir Jasper said:**
> Hi,

Belt and braces means maximum protection so that your trousers don´t fall down.

Of course it does, what an idiot I am  :-)

> In Windows On Access or On Executions guards _may_ slow your computer but surely that is a price worth paying since Prevention is better than detection or cure.

Ahem. It's not prevention. Prevention is where malware doesn't get to your system in the first place. Cure is where the infection gets removed from your system, which is what "On Access" or "live" scanners do. They WILL slow your computer - do you think scanning a file and trying to match it to an item in a database won't use any I/O or CPU time?

---

### Post by Richiegs on 2009-11-16
> **t0p said:**
> Running 2 AV programs, huh?  Belt-and-braces behaviour in Windows; complete and utter crazy-paranoia in Linux.

What makes you think these are Ubuntu viruses?  Have you even googled them?

These are almost definitely either false positives or Windows viruses.  Windows viruses can't harm your Ubuntu setup.

Why are you so confident that Ubuntu won't get virus? I guess I better want to be safe than sorry.

---

### Post by 3rdalbum on 2009-11-16
> **Richiegs said:**
> The virus is called pua.script.packed-2. Is it from Windows or just a false positive?

"pua" means "Possibly Unwanted Application". You can treat it as a false positive, I guess. Where is the file location of the virus?

---

### Post by Trebaruna on 2009-11-16
> **3rdalbum said:**
> Ahem. It's not prevention. Prevention is where malware doesn't get to your system in the first place. Cure is where the infection gets removed from your system, which is what "On Access" or "live" scanners do.
By that definition there's nothing preventing me from getting a virus, either. Someone could email it to me, and the code would be right here on my machine!
These scanners prevent execution of code if it matches some signature, so they do, in fact, prevent infection.

---

### Post by 3rdalbum on 2009-11-16
> **Richiegs said:**
> Why are you so confident that Ubuntu won't get virus?

A virus is just a malicious program. 99.999% of viruses are Windows programs, which Ubuntu does not run natively. The only way they can possibly run is if you explicitly open a terminal and run them with Wine. Even then, most of them won't run or won't do anything, because they require access to the real Windows internals, or see the Wine instance as being a virtual machine or emulation and are designed to stop running in that case.

There are no viruses that run natively on today's Linux systems. Old Linux viruses won't run anymore. If somebody did create a virus (difficult work considering the inherent securities of the typical GNU/Linux system design), we'd know about it at the same time as the anti-virus companies.

---

### Post by Richiegs on 2009-11-16
> **openuniverse said:**
> i've tried my best to understand what keyscrambler does, and how effective it might be. what it is essentially is a rootkit, that sits on a very low-level of your operating system (windows) hopefully at a lower level than your keylogger. then it handles information between applications, so that an application-level keylogger won't get anything useful.

neat idea. but in gnu/linux rootkits (which operate at the same level of the paid version of keyscrambler) should be able to thwart keyscrambler itself, and pass the unencrypted information. (technically, windows could suffer from this too. the only reason it doesn't is that less sophisticated viruses are often just as effective, so why write a more sophisticated one?) in short, anti-rootkits and anti-virus are superior protection from keyloggers. if you want another layer of protection just to feel better, try the personal version of keyscrambler which is just for your internet browser. but i don't trust security software when not even the source is available anyway.

I think Keyscrambler has only Windows version.

---

### Post by Richiegs on 2009-11-16
> **3rdalbum said:**
> "pua" means "Possibly Unwanted Application". You can treat it as a false positive, I guess. Where is the file location of the virus?

It resides in home/ubuntu/.opera/cache/opr00/ya.
Should I just ignore it?

---

### Post by Trebaruna on 2009-11-16
> **Richiegs said:**
> It resides in home/ubuntu/.opera/cache/opr00/ya.
Should I just ignore it?
It's likely a piece of malware that got downloaded by your browser. Most likely a(n infected) website was hoping you were on Windows so it could attack you.

It will not harm you because Ubuntu is unaffected by it. Ignore it or delete the file. Either way there's no problem.

---

### Post by Sir Jasper on 2009-11-16
Hi,

Upload the file to [http://www.virustotal.com/](http://www.virustotal.com/) and preferably also submit it to the Program developer that located it,

In Windows use Avast for Windows or another highly rated program (free or paid) with active guards.

Also clone and backup. I messed up Ubuntu quite a few times, but every time I was pleased with my progress I cloned and it didn´t take me long to clone back.

Firefox 3.5 on and I think IE8 both provide some protection against Phishing Frauds. Else consider the free OpenDNS at router or browser level. Linux is not more protective than Windows for Phishing, but most of all avoid doing rash things - especially if some offer seems too good to be true.

My regards

---

### Post by Richiegs on 2009-11-16
Thanks. 
1) I wonder why ClamAv or Avast didn't detect the virus when it was first downloaded or infected?
2) Do you mean that a virus intended for Windows will never cause any harm to Ubuntu?

 > **Trebaruna said:**
> It's likely a piece of malware that got downloaded by your browser. Most likely a(n infected) website was hoping you were on Windows so it could attack you.

It will not harm you because Ubuntu is unaffected by it. Ignore it or delete the file. Either way there's no problem.

---

### Post by Paqman on 2009-11-16
> **Richiegs said:**
> It resides in home/ubuntu/.opera/cache/opr00/ya.
Should I just ignore it?

That's the cache of your browser. Probably some kind of drive-by download. Just empty Opera's cache and it'll be gone.

If it's Windows malware then it can't execute on your machine. Additionally, nothing downloaded by your browser is marked as executable. And on top of that, nothing located in your /home folder has the ability to mess with anything outside of your /home folder.

So it has absolutely 0% chance of doing anything seriously nasty, even if it is malware. Welcome to the relaxing world of desktop Linux!

---

### Post by Richiegs on 2009-11-16
Since the stuff that Avast detected was not virus, I would like to know if Ubuntu has any anti-logging program which is similar in function as Keyscrambler. Many thanks.

---

### Post by Paqman on 2009-11-16
Security in Linux isn't something you bolt on, it's an integral part of the system. To keep yourself protected:
[LIST=1]
[*]Keep your system up to date. Ubuntu will install security updates for every package on your system, meaning you should have no vulnerabilities. This is something Windows and Mac just can't do, and is a major reason we don't need extra software to keep safe.
[*]Never install software from an untrusted source. Best practice is to always use the Ubuntu repositories
[*]Never run a command in the terminal that you don't understand. Feel free to ask people what they mean.
[/LIST]

If you want to read more about security on Ubuntu, there's a great thread on the security sub-forum:
[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by wilee-nilee on 2009-11-16
> **3rdalbum said:**
> "Belt and braces" means the same as "everyone does it" or "par for the course".

You have two anti-virus programs running live at the same time? That's a very bad idea. Very, very bad idea. Besides which, even one live scanner makes your computer noticeably slower.

I am not sure they really run live actually I have avast turned off. Actually since I keep the W7 clean with ccleaner it runs just slightly slower then Karmic on the net-book. I have 2 gigs of ram. I have a few auto start things off as well W7 runs quite fast. I wouldn't run McAfee which has 5 different processes going in the task manager, it also misses stuff I have a friend on who's XP, McAfee said was clean I found about 50 hits with the last 2 scanners.

---

### Post by scorp123 on 2009-11-16
> **Richiegs said:**
> It resides in home/ubuntu/.opera/cache/opr00/ya.
Should I just ignore it? You probably visited a web site you shouldn't have visited ... and those guys were hoping you were running Windoze. Just delete the cache. Done. Problem solved.

> **Richiegs said:**
>  1) I wonder why ClamAv or Avast didn't detect the virus when it was first downloaded or infected? You're probably not running any real-time scanning module. And running ClamAV or Avast or anything is totally not necessary on Linux. Those programs are scanning for Windows viruses anyway and they only really make sense if you are running a file or mail server that gets accessed by Windows machines as well.

> **Richiegs said:**
>  2) Do you mean that a virus intended for Windows will never cause any harm to Ubuntu? Can a car designed for gasoline run on Diesel fuel? Can a truck designed for Diesel fuel be run with gasoline? Can you run Playstation 3 games on a Nintendo Wii? Can you run Nintendo Wii games on an ancient Commodore Amiga computer?

No.

Viruses are programs. And programs only run on the specific platform they were designed for. A Windows virus will only run on Windows.

> **Richiegs said:**
> Why are you so confident that Ubuntu won't get virus?  I am a Linux user since 1996. "One day Linux will have viruses too!!!"  <== Yeah, riiiight. I keep hearing that bullsh*t since 13 years. I am still waiting.

Fact is that UNIX-like operating systems such as Linux, FreeBSD, Mac OS X and what not have a far superior design than the crapware Microsoft sells for money. It starts with strict separations of priviledges (super-user "root" vs. normal users), strict separations of files (normal users store their files in /home, super-user stores his stuff in /root ... and normal users can't go there!), strict separation of system config files (underneath /etc) vs. personal config files (underneath /home), strict limits on what a user can run but not write to (/usr/bin) ... and so on and so on.

UNIX-like OS had their fair share of virus troubles, yes. But that was in the 1980's .... 20+ years ago. Look it up:

The Morris Worm
[http://en.wikipedia.org/wiki/Morris_worm](http://en.wikipedia.org/wiki/Morris_worm)


This is a nice picture:

[IMG]http://upload.wikimedia.org/wikipedia/commons/b/b6/Morris_Worm.jpg[/IMG]

It shows where you will find most UNIX viruses .... **_In the museum._** Because modern UNIX-like operating systems such as Linux are written from the ground up in such a way that such viruses have no chance whatsoever anymore.

That's one of the key differences between Windows and the world of UNIX. When Windows gets a virus because of a security flaw, Microsoft just declares "it's not a bug -- it's a feature!" and people have to make do with it and keep running anti-this and anti-that .... When UNIX got a virus they changed the OS from the ground up so it could never ever happen again. Result: **No virus or worm outbreaks that I know of since 1988!**

Here on UNIX-like operating systems you'd have to worry more about human hackers ... those guys are real and the crackers (= guys who not just get in but also destroy stuff on purpose ...) amongst them are a real threat ...

But viruses???? **Forget it.**


> **Richiegs said:**
>  I guess I better want to be safe than sorry. Riiight. Let go of your Windows-thinking, OK? :D

---

### Post by openuniverse on 2009-11-16
.

---

### Post by scorp123 on 2009-11-16
> **openuniverse said:**
>  if there's a security tool for windows that doesn't exist in gnu/linux, chances are it's because it's irrelevant- or you were using "toy" security. Bingo!

And as for keyloggers ... to install one, an intruder would have to be "root" ... but if he's already "root" and therefore has already achieved unlimited powers ... why would he need a keylogger software at all? Such an intruder already has all the powers he could ever wish for and can do whatever he wants. And even if some anti-keylogger software existed: Having gained unlimited "root" powers it would be extremely easy for such an intruder to simply kill the software so it becomes inoperable. Hence: no point having such a software. Because if someone has gained "root" access then everything else has already failed and you'd all of a sudden have a lot more serious security problems to deal with ...

---

### Post by fromthehill on 2009-11-16
one virusscanner is more than enough
even on a windows vista/7 system

if you click and install everything you see, no virus or malware scanner will help

If you are really that paranoid it wont really help if I say that you can make your ubuntu unusable by just typing one command:p(something I didn't manage to do in windows). linux is a very secure OS, but it's definitely not fool-proof

---

### Post by markbuntu on 2009-11-16
Nothing is foolproof because fools are too ingenious,

---

### Post by MasterNetra on 2009-11-16
> **fromthehill said:**
> one virusscanner is more than enough
even on a windows vista/7 system

if you click and install everything you see, no virus or malware scanner will help

If you are really that paranoid it wont really help if I say that you can make your ubuntu unusable by just typing one command:p(something I didn't manage to do in windows). linux is a very secure OS, but it's definitely not fool-proof

Well you know what they say. "Idiot Proofing only makes better idiots."

---

### Post by fromthehill on 2009-11-17
> **MasterNetra said:**
> Well you know what they say. "Idiot Proofing only makes better idiots."
I've seen people screw up their computer in ways I couldn't imagine :D

install the same virus and spyware just three minutes after I cleaned the pc really is no exeption.](*,)

---

### Post by markbuntu on 2009-11-17
> **fromthehill said:**
> I've seen people screw up their computer in ways I couldn't imagine :D

install the same virus and spyware just three minutes after I cleaned the pc really is no exeption.](*,)

Consider it job security.

---

