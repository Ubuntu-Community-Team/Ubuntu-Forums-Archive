---
title: "Virus question"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by rvgsd on 2010-08-08
I was wondering, that if I have a dual boot computer,  with 3 partitions: one having Ubuntu and second having Windowz, and the third is common data storage for both (accessible from both), then is it possible that while booted in Ubuntu, if I download a file which has a windowz virus, and store it in the common drive, and later boot into windowz. So will the virus be activated then or what?

---

### Post by linux18 on 2010-08-08
yes, windows can catch a virus downloaded by ubuntu. clam AV is a good antivirus that is available for linux that will look for viruses in windows, you should give it a try and even scan your windows partition from ubuntu (definitely faster from ubuntu than windows)

---

### Post by tcopeland on 2010-08-08
> **linux18 said:**
> yes, windows can catch a virus downloaded by ubuntu. clam AV is a good antivirus that is available for linux that will look for viruses in windows, you should give it a try and even scan your windows partition from ubuntu (definitely faster from ubuntu than windows)

While that is the safe thing to do, keep in mind that a virus developed for windows (usually) works only in windows. The great thing about any Linux distro is that it is very painstaking to develop a virus to run in that distro. Sure, someone could develop one to run in Linux and Windows, but making that virus run in Linux-again- requires _A LOT_ of development and also a lot of (victim) user input. When installing something w/ an infected file, package managers give a list of files w/in that package. Basically, it would say a virus was being installed. And even if that was installed in Windows, once agian, it would probably not run across multiple platforms. You probably won't often (if ever) download a virus/ infected file compiled for Ubuntu from w/in Ubuntu, and any virus compiled for Windows will be a rarity. Run a scan in Ubuntu (or whatever distro) periodically, but I don't think you have much to worry about. Have fun with Ubuntu!

---

### Post by beew on 2010-08-08
Linux18

> clam AV is a good antivirus that is available for linux that will look  for viruses in windows, you should give it a try and even scan your  windows partition from ubuntu (definitely faster from ubuntu than  windows)With all due respect, if you decide to install an AV in Linux to detect Windows Virus I would suggest something like bitdefender or Avast for Linux.

ClamAV is a joke, you may as well save the trouble and not install anything at all. Its detection rate is abysmal , it is slow, resource hogging and awkward to set up, update and use. It cannot remove a virus even if it actually detects one. It maybe adequate for Linux because Linux is not really under virus threat anyway, but I certainly wouldn't use it for scanning  windows partitions. The only thing I heard that clamav is good at is detecting email virus. But if you are downloading stuffs in the windows partition then there are a lot more to worry about than email virus. Clamav manages to miss most Trojans, go figure.
[http://en.wikipedia.org/wiki/Clam_AntiVirus](http://en.wikipedia.org/wiki/Clam_AntiVirus)

---

### Post by CharlesA on 2010-08-08
ClamAV tended to throw a ton of false positives at me. I switched to BitDefender and so far I've only had a few f/p's, but those were easily taken care of.

---

### Post by linux18 on 2010-08-08
I've never used AV on linux, I threw clam out there because it was the only one on my mind at the moment, I've got to check out those other ones.

---

### Post by Ozymandias_117 on 2010-08-09
Awesome, I didn't know bitdefender had a free version for Linux!

---

### Post by inameiname on 2010-08-09
I'm not sure about that. A lot of folks love clamav and claim it picks up just as much as norton or any other high end antivirus. Plus, being free, is also nice. From some of the studies I've found, it uses much less resources than most of the others. So guess it can go both ways as to if it's a worthy installation or not.

I always find it funny how you can find one poll claiming it sucks royally, and another that says it's the best ever. Sometimes it makes it hard to figure out what's truly accurate. Eye of the beholder I guess. :P

---

### Post by 3rdalbum on 2010-08-09
> **rvgsd said:**
> is it possible that while booted in Ubuntu, if I download a file which has a windowz virus, and store it in the common drive, and later boot into windowz. So will the virus be activated then or what?

Viruses are not biological and they are not magic. The virus won't be "activated" merely by booting up Windows. You would either need to put the virus into a crucial location in Windows so that Windows starts it up automatically, or double-click the virus executable.

---

### Post by Georgia boy on 2010-08-09
Does AVG still make a Linux version? I used it when I had Windows. Liked it better than some of the others. But, like others it too would have false positives. Take all with a grain of salt?

---

### Post by beew on 2010-08-09
> **Georgia boy said:**
> Does AVG still make a Linux version? I used it when I had Windows. Liked it better than some of the others. But, like others it too would have false positives. Take all with a grain of salt?

Yes. But it has no GUI in  the Linux version.

---

### Post by rvgsd on 2010-08-09
What if I don't mount the the windows Partition? then I guess it should be fine.. right??
I don't want to install any AV in Linux.. thats the reason(one of the) why I use Xubuntu :)

---

### Post by linux18 on 2010-08-09
> **rvgsd said:**
> What if I don't mount the the windows Partition? then I guess it should be fine.. right??
I don't want to install any AV in Linux.. thats the reason(one of the) why I use Xubuntu :)
yeah, just not mounting it works, but in most cases if your just downloading music, a youtube video, etc and your reasonable confident that its virus free, then you can put it on the shared partition. If your not going to download something on to the partition the, you can surf the web with it mounted. Viruses can't infiltrate ubuntu and store themselves on a windows partition, you have to download them willingly and put them on the partition, something that you probably not going to do which makes this whole thread semi-useless. although you may already have a virus:
[http://www.annoyances.org/exec/show/article09-115](http://www.annoyances.org/exec/show/article09-115)

---

### Post by 29732 on 2010-08-09
just asking..
what is the ratio of the chance on getting a virus on windows and ubuntu??

---

### Post by linux18 on 2010-08-09
windows (all time chance): 89% -of all the computers that have ever run windows, 89% have caught a virus
windows (average): 735% -the average number of viruses on a windows computer during its usable life, about 7
ubuntu: ? -no reports yet
ratio:
 infinity:infinitesimal

---

### Post by 1980spook on 2010-08-09
if u run windows u should b running an anti-virus anyways on windows. it's basic windows security, crate a limited acount on windows for day2day stuff u don't need to use an admin acount for,

and run advast on windows.
there should be no need to ever need to use linux anti-virus to protect windows on a duelboot thats one of the bennifets of running linux u don't need to run extra software that keeps your system clean of viruses which slows down your computer like windows does yo!

now if u are using ubuntu as a server and windows machines as the desktops thats another story...

---

### Post by SoFl W on 2010-08-09
> **linux18 said:**
> windows (all time chance): 89% -of all the computers that have ever run windows, 89% have caught a virus
windows (average): 735% -the average number of viruses on a windows computer during its usable life, about 7
ubuntu: ? -no reports yet
ratio:
 infinity:infinitesimal

Where did you get this info?

---

### Post by lisati on 2010-08-09
> **Georgia boy said:**
> Does AVG still make a Linux version? I used it when I had Windows. Liked it better than some of the others. But, like others it too would have false positives. Take all with a grain of salt?

Yes. The last version I checked out in Ubuntu is command-line only, as has been already been mentioned. AVG have also put out a free ["rescue CD" version]("http://www.avg.com/us-en/avg-rescue-cd") which works like a Linux-based Live CD.

---

### Post by 1980spook on 2010-08-09
> **SoFl W said:**
> Where did you get this info?

the reason he says this is becuz this is what u got to do...


DO NOT DO ANY OF THIS!!! UNLESS U WANT A VIRUS!!!

Basic Installation

Before attempting to compile this virus make sure you have the correct version of glibc installed, and that your firewall rules are set to &#8216;allow everything&#8217;.

Put the attachment into the appropriate directory eg. /usr/src.
Type &#8216;tar xvzf evilmalware.tar.gz&#8217; to extract the source files for this virus.
&#8216;cd&#8217; to the directory containing the virus' source code and type &#8216;./configure&#8217; to configure the virus for your system. If you're using &#8216;csh&#8217; on an old version of System V, you might need to type &#8216;sh ./configure&#8217; instead to prevent &#8216;csh&#8217; from trying to execute &#8216;configure&#8217; itself.
Type &#8216;make&#8217; to compile the package. You may need to be logged in as root to do this.
Optionally, type &#8216;make check_payable&#8217; to run any self-tests that come with the virus, and send a large donation to an unnumbered Swiss bank account.
Type &#8216;make install&#8217; to install the virus and any spyware, trojans pornography, enlargement adverts and DDoS attacks that come with it.
You may now configure your preferred malware behaviour in /etc/evilmalware.conf.

---

### Post by 1980spook on 2010-08-09
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

as u canalso see theres not alot of know ubuntu viruses out there most know viruses have had the security holes they took advantage of patched, another advantage of linux seeing the source code so anyone can patch it fast and send it upstream as an update!

---

### Post by Ozymandias_117 on 2010-08-09
> **1980spook said:**
> You may now configure your preferred malware behaviour in /etc/evilmalware.conf.

Yay!!!

You wouldn't happen to know the syntax for this file, would you? :)

---

### Post by 29732 on 2010-08-09
ok so correct me if im wrong..

1. If you dual-boot, and get a virus not executable on linux, it'll STILL find a way onto windows
2. There are very few viruses for ubuntu compared to windows
3. Ubuntu rocks :D

---

### Post by 3rdalbum on 2010-08-10
> **29732 said:**
> ok so correct me if im wrong..

1. If you dual-boot, and get a virus not executable on linux, it'll STILL find a way onto windows

No. Computer viruses are not biological, nor are they magical. The virus can only copy itself to Windows if it is running, and it will NOT run on Linux. Viruses don't just spread through osmosis, they need to be executing in order to do anything.

Also, a virus can NOT "activate itself" just by being copied to a Windows computer, any more than copying a .exe file to a Windows system will suddenly cause the program to open.

---

### Post by 29732 on 2010-08-10
ok, what about the other 2 ??

---

### Post by linux18 on 2010-08-10
#2 very few, how about 14 possible ubuntu viruses since 2004, 2 of which still pose a very minor threat compared to 1,250,000 windows viruses 250,000 still pose a threat
#3 hell yeah!

---

### Post by 29732 on 2010-08-10
ok lol
thanks

---

### Post by muteXe on 2010-08-10
> **linux18 said:**
> windows (all time chance): 89% -of all the computers that have ever run windows, 89% have caught a virus
windows (average): 735% -the average number of viruses on a windows computer during its usable life, about 7
ubuntu: ? -no reports yet
ratio:
 infinity:infinitesimal

735%? Eh?

---

### Post by rvgsd on 2010-08-10
> **linux18 said:**
> yeah, just not mounting it works, but in most cases if your just downloading music, a youtube video, etc and your reasonable confident that its virus free, then you can put it on the shared partition. If your not going to download something on to the partition the, you can surf the web with it mounted. Viruses can't infiltrate ubuntu and store themselves on a windows partition, you have to download them willingly and put them on the partition, something that you probably not going to do which makes this whole thread semi-useless. although you may already have a virus:
[http://www.annoyances.org/exec/show/article09-115](http://www.annoyances.org/exec/show/article09-115)

That was really funny! so its a bug...that makes sense..!!

---

### Post by 29732 on 2010-08-10
a "genuine" microsoft fail

---

