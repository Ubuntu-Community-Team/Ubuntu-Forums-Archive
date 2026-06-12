---
title: "Some very basic questions"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by scottjr on 2010-02-22
I recently migrated from Windows Vista to Ubuntu 9.10.  So far I'm absolutely ecstatic about the switch.  However, perhaps I should have read alot more before I dove head first into this; I just became so frustrated with Windows that I converted almost in a fit of rage.  While I am certainly happy with my new operating system, there are some very basic things with which I must become competent before I am completely comfortable with it.  For your information: I am/was a relatively advanced Windows user.  Certainly no Guru, but much more informed than your average user, and have been dabbling on and off with programming since I was a wee lad.

1) On security: I have read snippets here and there about Linux being far more secure than Windows and "you just won't get viruses", and while I love the sound of that, I'm certainly not naive enough to assume my new system is immune to malicious attack.  Just how secure is Ubuntu for someone like myself, who at present is navigating his way through a labyrinthine mess of new information?  In other words, are there any special tasks I need to be routinely performing to maintain the security of my computer?  I have yet to notice a virus scan run, which would lead me to believe there isn't one unless Linux is just so smart that it only does these things whilst I am away from the computer.

2) On the download and installation of new software: I am loving this newfound "package" metaphor, and in particular Ubuntu's Software Center, which seems to me to be the opensource equivalent of the iTunes store :P.  It's simply a breath of fresh air to just type in what I'm looking for and download/install with a single click.  However, the sad reality is that I live in the country and have terrible (satellite) internet, prone to fits of "rate limitation" and sometimes need to drive up the road to the nearest WiFi hotspot, download the desired software to my netbook (now running Ubuntu Netbook Remix), return home and transfer the downloaded files to my desktop.  How can I download the package file/installer/whatever-it's-called to my netbook without installing, so that I can transfer it to my desktop simply?  Is it possible to perform a similar procedure with the updates normally obtained from the Update Manager? If not I would have to run updates during "off peak free bandwidth time", which begins at 3am :(. What about updates already installed on my netbook which I need to retrieve for my desktop?  Also, when it comes time for the transfer step, I normally move the files to my iPod (which I use like an external storage device) then from there to the desktop.. is there some package I can install which will allow me to transfer the files wirelessly across my home network instead?  I love the "one click install" approach until I require a slightly more complex approach to file acquisition.

So many more questions pending, but I suppose I'll read some documentation first and see if I can't answer them for myself.  Anything more immediate will come in later threads. 

Thank you all so much and Viva Ubuntu!
scottjr

---

### Post by TurnOfTide on 2010-02-22
For some reason the string 'Linux is immune to viruses' is itself a virus; it keeps replicating in the wild. There are a few viruses (you can find source for agobot3/botnet) which are capable of running on linux too. But for most virus/spyware writers, it makes way more sense (way more lucrative sense anyway) to go after windows, more users and the users are less computer savvy. Although botnet'ers don't care as much, the more bots the merrier for them.

---

### Post by NightwishFan on 2010-02-22
As for security, this link will give you anything you need to know:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

On the whole you will be targeted by less malware and equivalent. Linux is not compatible with Windows software. Also, the administration system in Linux is much more clever and better implemented. Even if you get targeted by such things you may be better off than you would be with Windows. You do not have to do all or any of the suggestions in that link. Personally I just use the GUFW firewall frontend and set it to deny. I also use the noscript Firefox extension, and only add pages I trust. (You can install Noscript in Software Center if you do not want to install it manually). Good internet and security habits by the users are much more effective.

To install packages offline:

This link will help you, basically it adds on to what I say below:
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

If you run the same exact version of Ubuntu on both machines. (Example: Karmic 32-bits, if it is netbook remix does not matter). Then you can download packages for the netbook and put them on the desktop. If it is a 64-bit or a different version this will not work.

[LIST=1]
[*]Go to the Synaptic Package Manager under System -> Administration menus.
[*]Mark all updates and check the packages you want to install.
[*]When you hit apply check the **Download Only** box.
[*]Hit ok, and the package manager will download all the packages to /var/cache/apt/archives.
[*]You can copy the packages from there, or use APTONCD to burn them to an installable CD.
[/LIST]
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

### Post by florus on 2010-02-22
As I understand it, q virus which is written to run under windows will not run under Linux. Ditto a program.
You are also protected by the fact that you do not run your computer with root privileges. A malicious program will have to ask your permission to run before doing any damage.
Very very few Linux users run any sort of anti-virus program.

---

### Post by Temposs on 2010-02-22
> **scottjr said:**
> I recently migrated from Windows Vista to Ubuntu 9.10.  So far I'm absolutely ecstatic about the switch.  However, perhaps I should have read alot more before I dove head first into this; I just became so frustrated with Windows that I converted almost in a fit of rage.  While I am certainly happy with my new operating system, there are some very basic things with which I must become competent before I am completely comfortable with it.  For your information: I am/was a relatively advanced Windows user.  Certainly no Guru, but much more informed than your average user, and have been dabbling on and off with programming since I was a wee lad.

1) On security: I have read snippets here and there about Linux being far more secure than Windows and "you just won't get viruses", and while I love the sound of that, I'm certainly not naive enough to assume my new system is immune to malicious attack.  Just how secure is Ubuntu for someone like myself, who at present is navigating his way through a labyrinthine mess of new information?  In other words, are there any special tasks I need to be routinely performing to maintain the security of my computer?  I have yet to notice a virus scan run, which would lead me to believe there isn't one unless Linux is just so smart that it only does these things whilst I am away from the computer.

There is no virus scanner installed with Ubuntu by default. In general, you won't need one. There aren't really any viruses or malware in the wild for Linux, so you don't really need to worry about it. The main reason someone runs a virus scanner on Linux is to protect Windows machines on the same network, since a virus sitting on a Linux machine usually can't do anything, but it would be bad if it got transfered to the Windows machine. If you really want a virus scanner, there are some for Linux. And Linux is certainly not 100% secure. You need to keep a good administrator password, and use the Software Center to install software when at all possible, since all that software is safe. If you start installing software from random websites and giving the software administrator access, your computer could be comprimised.

> 2) On the download and installation of new software: I am loving this newfound "package" metaphor, and in particular Ubuntu's Software Center, which seems to me to be the opensource equivalent of the iTunes store :P.  It's simply a breath of fresh air to just type in what I'm looking for and download/install with a single click.  However, the sad reality is that I live in the country and have terrible (satellite) internet, prone to fits of "rate limitation" and sometimes need to drive up the road to the nearest WiFi hotspot, download the desired software to my netbook (now running Ubuntu Netbook Remix), return home and transfer the downloaded files to my desktop.  How can I download the package file/installer/whatever-it's-called to my netbook without installing, so that I can transfer it to my desktop simply?  Is it possible to perform a similar procedure with the updates normally obtained from the Update Manager? If not I would have to run updates during "off peak free bandwidth time", which begins at 3am :(. What about updates already installed on my netbook which I need to retrieve for my desktop?  Also, when it comes time for the transfer step, I normally move the files to my iPod (which I use like an external storage device) then from there to the desktop.. is there some package I can install which will allow me to transfer the files wirelessly across my home network instead?  I love the "one click install" approach until I require a slightly more complex approach to file acquisition.

Unfortunately, to use the Software Center and Update Manager as intended, you need a reliable internet connection with which to download the software. 

If you want to download software as an install file that can be transferred between computers, there are a few sites like: [http://www.getdeb.net/](http://www.getdeb.net/)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Packages for Ubuntu generally have the .deb file extension. You can install just by double clicking them on an Ubuntu machine. getdeb.net is an unofficial source of software downloads for Ubuntu. It's fairly reputable. packages.ubuntu.com is the official Ubuntu packages archive, where you can find any package that you can download in Ubuntu. This is how I would go about downloading software that I wanted to transfer to another computer.

> So many more questions pending, but I suppose I'll read some documentation first and see if I can't answer them for myself.  Anything more immediate will come in later threads. 

Thank you all so much and Viva Ubuntu!
scottjr

---

### Post by oldsoundguy on 2010-02-22
On the virus .. you do not need AV on Linux FOR Linux. (only to protect windows users if you forward eMail  ..(which a stupid thing to do in the first place .. CUT AND PASTE .. then nothing gets sent on!) There are NO .. repeat NO know virus files in the wild that will attack the Linux operating system.  There is SOME crap that will go for your browser IF YOU install it YOURSELF.  Now, just why would you do THAT?

The steps required to put a program into the kernel of ANY Linux build are far too many to install something by accident or the (shudder) "single click method" so prevalent in Windows.

Wish I could help you on #2 ..  but I have a screamingly fast unlimited cable connection and do my on line through my own home network .. and I don't do iPoad.

---

### Post by jmszr on 2010-02-22
scottjr,

Here is a Ubuntu Security sticky: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) . That should answer most of your security questions.

Between the following, installing software offline should be covered: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) , and this: [http://keryxproject.org/](http://keryxproject.org/)  using this (the instructions from"MacTheKnife"): [http://keryxproject.org/forums/index.php?topic=19](http://keryxproject.org/forums/index.php?topic=19) .

Hope that helps.

---

### Post by golanbatrac on 2010-02-22
> 1) On security: I have read snippets here and there about Linux being far more secure than Windows and "you just won't get viruses", and while I love the sound of that, I'm certainly not naive enough to assume my new system is immune to malicious attack. Just how secure is Ubuntu for someone like myself, who at present is navigating his way through a labyrinthine mess of new information? In other words, are there any special tasks I need to be routinely performing to maintain the security of my computer? I have yet to notice a virus scan run, which would lead me to believe there isn't one unless Linux is just so smart that it only does these things whilst I am away from the computer.

To enable your firewall, open a terminal (Accessories > Terminal) and enter the following:

```
sudo ufw enable
```
```
sudo ufw default deny
```

Sticking with the packages available in the Software Center is a good idea until you know a bit more what you're doing.

Also, never enter anything into the Terminal that you don't understand.  If someone tells you to type anything in the terminal (as I did above), take a few seconds to do a little research (google, or the man pages installed on your system) and make sure that what you're being told to do does what you want it to do and won't harm your system.

> 2) On the download and installation of new software: I am loving this newfound "package" metaphor, and in particular Ubuntu's Software Center, which seems to me to be the opensource equivalent of the iTunes store :razz:. It's simply a breath of fresh air to just type in what I'm looking for and download/install with a single click. However, the sad reality is that I live in the country and have terrible (satellite) internet, prone to fits of "rate limitation" and sometimes need to drive up the road to the nearest WiFi hotspot, download the desired software to my netbook (now running Ubuntu Netbook Remix), return home and transfer the downloaded files to my desktop. How can I download the package file/installer/whatever-it's-called to my netbook without installing, so that I can transfer it to my desktop simply? Is it possible to perform a similar procedure with the updates normally obtained from the Update Manager? If not I would have to run updates during "off peak free bandwidth time", which begins at 3am :sad:. What about updates already installed on my netbook which I need to retrieve for my desktop? Also, when it comes time for the transfer step, I normally move the files to my iPod (which I use like an external storage device) then from there to the desktop.. is there some package I can install which will allow me to transfer the files wirelessly across my home network instead? I love the "one click install" approach until I require a slightly more complex approach to file acquisition.

Any package you download to your laptop will be stored in /var/cache/apt/archives.  Transfer the files to your desktop computer and double click the ones you want to install.

Also, look into the program 'aptoncd' which creates an offline repository on CD for installing downloaded packages to an offline computer.

---

### Post by lisati on 2010-02-22
In the time I've been using Ubuntu (over 2 years), I've only had a handful of suspect files come my way by email, probably less than 10. These are usually fairly easy to spot: a Windows program sent by someone whose email address I don't recognize. There have been a few attempts at "social engineering" - trying to steal my personal details - but these have been rare and usually easy to spot as well.

I only have AV software available because (a) I use Windows for some of my work, and (b) my ISP likes me to have it (I run an email server), and (c) I interact with Windows users.

---

### Post by rrashkin on 2010-02-22
I, too, live in the country with a "quirky" satellite feed (Wild Blue).  So far I have managed with just patience.  Even when I'm downloading at 800-something kbps, eventually, I get updated.

---

### Post by scottjr on 2010-02-22
> **rrashkin said:**
> I, too, live in the country with a "quirky" satellite feed (Wild Blue).  So far I have managed with just patience.  Even when I'm downloading at 800-something kbps, eventually, I get updated.

I wish I had the luxury of "patience-as-a-fix".  Not that I'm impatient, but I'm talking about rate-limited speeds measured in the bps, not Kbps, if I download more than, I believe 100 or 150mb in a 24 hour period.

Yea.  Don't buy DirecTV (Hughes net) unless it's your only option, as is my unfortunate situation.

---

