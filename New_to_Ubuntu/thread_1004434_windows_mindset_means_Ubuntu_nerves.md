---
title: "windows mindset means Ubuntu nerves"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by charlesdb on 2008-12-07
I've been using Ubuntu now for a couple of weeks.  I really like it.  But my'Windows' mindset means I am very nervous about security.  I know this has been written about a lot.  And I have read voraciously to make my computer secure.  I have Firestarter, ClamAV and have installed chrootkit and rkhunter - although if a rootkit does show up, how on earth do I get rid of it?  I've also got a strong administrator pasword and run a single PC.  I'm also careful about the websites I visit and as I use Opera, I've disabled Javascript on a blanket basis, unless I need it on a trusted site.  I'm careful about software downloads - all from the repository except rkrootkit, as far as I can remember.
I've read about other security ideas, but as they involve changing code, I've really no intention of going through all that.  In any case, I don't really understand them.
However, I don't have the confidence to visit my bank accounts or to order goods on Ubuntu.
This is a pshycological block.  On 'Windows' I know I have good security and that any malware will be eradicated automatically (yes I know nothing is 100% certain, but it does give me confidence).
I'm just an ordinary user and the 'Windows;' mindset has got me trapped. Have I done enough to ensure my security on a single computer?
You'll probably reply yes - but I still have a kernel of insecurity.  It just shows how clever Microsoft have been, by making computer users Paranoid about other Operating Systems, because of their own insecure system. 
One answer might be for an Ubuntu Security Suite.  Unnecesary maybe.  Psychologically though, a piece of clever marketing - although maybe the Linux community isn't too keen to make their systems too popular for good reason.

---

### Post by Idefix82 on 2008-12-07
> **charlesdb said:**
> 
However, I don't have the confidence to visit my bank accounts or to order goods on Ubuntu.

When you visit your bank account or put in your account details into some html form, the only realistic danger is not the viruses on your computer but the risk of ending up on somebody else's server than on your bank's or the online shop's. This has got nothing to do with how your computer is set up but with somebody pretending that he is the bank, when he isn't. If you enter the address into the browser yourself and do not go to the bank's website by following a link from some email then you should be fine. To find out more, google for 'man in the middle attack'. You can also check the security certificate of the website by clicking on the appropriate icon in the bottom right corner of the browser window.

As far as protecting your computer goes, I think that the fact that you don't need an antivirus and no malware filter is really a huge advantage of Linux. It makes it much faster to boot and to operate. By installing all this stuff you are negating this advantage.

I hope, this will put your mind at ease.

---

### Post by albandy on 2008-12-07
In Unix/Linux based systems you can't execute nothing without execution permisions.
For example to install a rootkit you should download it, assign execution permisions and then execute it as root.

---

### Post by HotShotDJ on 2008-12-07
> **charlesdb said:**
> I'm just an ordinary user and the 'Windows;' mindset has got me trapped. Have I done enough to ensure my security on a single computer?
You'll probably reply yes - but I still have a kernel of insecurity.The problem here psychological.  You've already stated that you won't accept the answer of "yes."  But that IS the correct answer. The only way to completely secure your computer is to unplug it, put it back in the box, and return it to the manufacturer.  However, short of that, a DEFAULT installation of Ubuntu will provide you with a system that is at least as secure as a Windows installation with all the anti-virus, anti-spyware and firewalls enabled.

Anti-Virus on a Linux system is primarily for servers in order to protect Windows clients.  Getting a "rootkit" is highly unlikely on a typical desktop installation.  Linux is designed from the ground up for security. I've been using Linux desktop systems for online Banking and online shopping for YEARS without any problems.

As long as you are getting your software from trusted sources, you'll be fine.  I suspect, however, you will not believe me. :(

---

### Post by scorp123 on 2008-12-07
> **charlesdb said:**
>  although maybe the Linux community isn't too keen to make their systems too popular for good reason. This is FUD. First of all Linux already is popular in the professional area. I have worked at places where they have 1000's of Linux servers deployed and where Microsoft is outright banned because of its horrible reputation as platform for spreading viruses. Secondly: a "security suite" is not needed. What for? There are no Linux viruses (viruses would have one hell of a hard time to function in any similar way as they do on Windows; beginning with the fact that they cannot infect anything unless they are executed with "root" priviledges ...), most desktop users are not running any services in the background that would need the protection of a firewall (which is different e.g. from Windows XP: per default there are tons of obsolete network services that are constantly running in the background and without your knowledge!!), and besides: I can see nothing "clever" whatsoever about Microsoft and their OS. The BS they teach users such as "you absolutely need a firewall" and "you absolutely need a virus scanner" only serves one purpose: to cover up what a horrible crap BS design their operating system has. People are trained to regard rebooting a PC even for small changes and updates as being "normal". People are taught to accept the fact that their OS might break all of a sudden and that they have to reinstall everything every few months (again BS! Linux can run for years without breaking!!), people are taught that they have to "defragment" their harddrives or their OS might slow down (again BS! Linux filesystems are better designed and try hard to avoid fragmentation from ever happening!!).

The best medicine for you would be to let go of that useless Microsoft thinking.

You said you were "paranoid". That's fine. Installing Linux was the first good step. Now let go of your old habits and enjoy the comfort that all those stupid things Microsoft got on your nerves with (malware, viruses, defragmenting harddisks, etc.) are gone now. :D

---

### Post by Dr Small on 2008-12-07
> **charlesdb said:**
> However, I don't have the confidence to visit my bank accounts or to order goods on Ubuntu.
This is a pshycological block.  On 'Windows' I know I have good security and that any malware will be eradicated automatically (yes I know nothing is 100% certain, but it does give me confidence).



I am the exact opposite. I do not trust Windows with all it's security, to be placing confidential information on a website. On linux, I feel much more at ease. Alot of Windows "good security" is security theater, and I have reports from relatives that their anti-virus detects things and won't eliminate it...

Most people are not this paranoid on Windows because it is the *de facto standard* of "security", yet when they come to a new, more secure operating system, they become very overly paranoid for no reason.

---

### Post by louieb on 2008-12-07
> **charlesdb said:**
>  - although if a rootkit does show up, how on earth do I get rid of it?

The only sure cure is to reinstall.

---

### Post by albinootje on 2008-12-07
If you are really so concerned about security in Linux,
make sure your /home and /tmp are separate partitions, and use
the mount-options noexec,nosuid,nodev on them.
Furthermore i strongly recommend the no-script add-on in firefox.
It is sometimes a bit of a hassle to get used to it, but it is also
interesting to see via no-script what is under the hood of a webpage.
But of course the most important is the user-input, make sure you maintain
a healthy way of using the internet, not just randomly clicking on files
from unknown sources. And with Linux you should relax a bit more,
it's by far not as badly designed as MicroSoft Windows when it comes to
computer security.

---

### Post by The Cog on 2008-12-07
I'm with Dr Small. I feel much safer on a default Ubuntu install with no firewall or antivirus than I would on a Windows install with firewall enabled and multiple antivirus tools.

Your paranoia is good - they really are out to get you. But your faith in windows security tools is badly misplaced. Most AV tools only find 50-70% of known viruses, and of course they don't find any of the unknown ones.

---

### Post by PocketDog on 2008-12-07
I'm totally immune to all forms of malware. My data's backed up, I don't bank online. I use Linux. How can I lose? And what does an attacker have to win?

---

### Post by chrisod on 2008-12-07
You are not security conscious, you are paranoid. That is not necessarily a bad thing, but it your case it seems to be sucking all the joy from what should be a fun or at least productive task - using a computer online.

Really, you need to either relax, or unplug from the Internet and stay unplugged. Living in fear of every mouse click can't be healthy.

---

### Post by som1special2 on 2008-12-07
Simple fact: A high percentage of viruses are written for Windows based OS's and not for linux OS's. Run a search on it. CALM DOWN! I have been using high risk OS's from windows since inception and I have NEVER been compromised. It's not really as much as an issue as you would believe. :popcorn:

---

### Post by Dr Small on 2008-12-07
> **chrisod said:**
> You are not security conscious, you are paranoid. That is not necessarily a bad thing, but it your case it seems to be sucking all the joy from what should be a fun or at least productive task - using a computer online.

Really, you need to either relax, or unplug from the Internet and stay unplugged. Living in fear of every mouse click can't be healthy.
I totally agree.

P.S.> Are you on the RMLUG mailing list?
P.S.S> [http://ubuntuforums.org/showthread.php?t=404523](http://ubuntuforums.org/showthread.php?t=404523)

---

### Post by aktiwers on 2008-12-07
charlesdb please relax a moment :)
Listen, you are way to paranoid. Look, I have been using Ubuntu for about 3 years now, and never used any security software other than what comes default with Ubuntu. 
And Yes I surf the darkside of the web, hardcore porn, cracks and serials etc...

Sometimes though I find it funny to install ClamAV and scan to check if anything is there..  And only one time did ClamAV find malware/virus, it was in my old Windows Backup folder and the virus was an .exe file (it won't run on Ubuntu, maybe through Wine but then only Wine gets infected, and the virus only "works" when you run Wine, if you do not decide to reinstall Wine offcause). Anyways, my point being that you really shouldn't worry that much :)

---

### Post by charlesdb on 2008-12-07
Thank you for all your replies.  I'll try and calm down.  Ubuntu is a very slick OS.  I love it.  I feel reassured by your replies.  Don't know if I'm ready to surf the dark side of the net though.  I'll give it a few months, when hopefully my paranoia will have diminished!!!

---

### Post by residualbit on 2008-12-07
I agree with a lot of the others on here in that I *only* do my banking, online shopping etc on ubuntu based pc. I've been using solely ubuntu for about 3 years now and have never had any problems related to security. The only place I have to use windows is at work (a large web design/hosting company), which sucks, and even we are switching over to Debian.

As far as viruses and malware go, I like to look at it like this: almost all capable hackers(unless they are idiots) write their files and hack from linux based machines. Would they really write something that had the potential to screw up their own machines? Very doubtful. The biggest thing you have to worry about with viruses is unknowingly downloading one and somehow passing it along to a friend that uses windows.

---

### Post by Old_Grey_Wolf on 2008-12-07
When I was first trying out Linux, I detected an infection in Windows XP. I thought nothing of locating the infected file using Linux, and sending it to the Anti-Virus vendors. My Linux install was not going to get infected. You can read the message board exchange here 
[http://www.dslreports.com/forum/r19884237-What-is-cbpnkrymgexe](http://www.dslreports.com/forum/r19884237-What-is-cbpnkrymgexe)

That opened my eyes to how safe my Windows was with all the Anti-this and that installed.

---

### Post by Paqman on 2008-12-07
> **charlesdb said:**
>   I have Firestarter, ClamAV

Neither of these will make your machine any more secure than it would be without them.

Firestarter is not a firewall. Ubuntu's firewall is a preinstalled and preconfigured system called iptables. All Firestarter does is allow you to make changes to iptables. Since the default configuration for Ubuntu is completely secure, there's no real need to use Firestarter (or Gufw, which is an equivalent package) unless you have installed services which are listening on a port. Normally that means some kind of server software. 

One thing you definitely must not do is allow Firestarter to run continuously, like a Windows firewall would. Firestarter runs as root, and thus having it running all the time would constitute a (potential) security risk.

As for ClamAV, it searches for Windows viruses. These can't execute on your system without your permission, and even if you did execute them deliberately they wouldn't find any of the Windows system files they need to complete their mission. So ClamAV on a desktop system is pretty pointless. It's useful if you're running a server connected to a Windows network though.

The best way to protect your Ubuntu machine is to stay current with security updates, and to not install any servers unless you know how to secure them.

---

### Post by aktiwers on 2008-12-07
I remember I read about this some time ago when rereading the thread..
[http://www.heise-online.co.uk/security/Hacking-competition-Vista-cracked-but-not-Ubuntu--/news/110429](http://www.heise-online.co.uk/security/Hacking-competition-Vista-cracked-but-not-Ubuntu--/news/110429)

> The only notebook to remain unhacked [at the end of the competition]("http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up") is the Sony VAIO running Ubuntu 7.10. 

---

### Post by pi.boy.travis on 2008-12-07
Even back when I used XP with IE 6, I had only been compromised once, which was the result of my own stupid mistakes.  You have very, *very* little to worry about.  You do not need ClamAV, as it is for the protection of Windows clients only.  A firewall would be a good idea, but I would recommend reading up on ufw, and using that instead of firestarter.  If your computer is connected via a router, you don't need a firewall, as most have one built in.

---

### Post by anjilslaire on 2008-12-07
> **louieb said:**
> The only sure cure is to reinstall.

Agreed, and this goes for most malware that get to s system-level infection. Even if your AV software cleaned it, you have no idea what other backdoors were opened & what other undetected virus/worm(s) have compromised the system.

On Windows, of course.

---

### Post by ZootNerper on 2008-12-07
HI,

I switched to Ubuntu just over 18 months ago and what a relief it was! I have no virus/spyware/etc checker or firewall installed. I quickly discovered that you don't need them. I don't have to remember to run daily updates and checks and worry about other people's thumb drives. A great weight was lifted off my shoulders. Breathe easy, use Linux.

-- Zoot

---

### Post by ReverendPaul on 2009-01-05
Er,

Sorry to crash someone else's thread, but I got the following warnings from rkhunter:

/usr/sbin/unhide                                         [ Warning ]

/usr/sbin/unhide-linux26                                 [ Warning ]

Checking /dev for suspicious file types                  [ Warning ]
File properties checks...
    Files checked: 127
    Suspect files: 2

Any need to be concerned? I checked the relevant files, and they seem inocuous enough.

---

### Post by albinootje on 2009-01-06
> **ReverendPaul said:**
> 
/usr/sbin/unhide                                         [ Warning ]

/usr/sbin/unhide-linux26                                 [ Warning ]


I'm getting the same on Intrepid/8.10

```

$ ls -la $(which unhide)
lrwxrwxrwx 1 root root 24 2008-12-27 15:06 /usr/sbin/unhide -> /etc/alternatives/unhide
$ ls -la /etc/alternatives/unhide
lrwxrwxrwx 1 root root 24 2008-12-27 15:06 /etc/alternatives/unhide -> /usr/sbin/unhide-linux26
$ ls -la /usr/sbin/unhide-linux26
-rwxr-xr-x 1 root root 515040 2008-06-22 03:35 /usr/sbin/unhide-linux26

```

---

### Post by heatpumpcontrol on 2009-01-19
same here when I ran rkhunter but none under chkrootkit. Hmm.. maybe a quirk?

I'll keep you guys posted. This is related to this thread. 

I apologize if we're hijacking the topic.

---

