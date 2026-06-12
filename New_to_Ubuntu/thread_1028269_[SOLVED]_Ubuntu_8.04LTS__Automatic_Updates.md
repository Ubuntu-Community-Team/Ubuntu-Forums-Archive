---
title: "[SOLVED] Ubuntu 8.04LTS  Automatic Updates"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by mike272rr on 2009-01-02
Hello,

New to Ubuntu and notice almost every time I start using Ubuntu I get informed at updates are available.  Is it improtant to keep applying all these updates almost daily?  I am trying to use this as a Microsoft OS alternative but it seems to have even more updates than Windows.  Your comments are much appreciated.

I have posted a few times before and this is an excellent forum for information.  Thanks to all who continue with their support of people new to this OS.

Mike

---

### Post by balaknair on 2009-01-02
Fully updated system= more secure, fewer bugs

Updates on Ubuntu generally fall into 3 categories- 
- Security updates(install these, definitely useful)
- Recommended updates(usually bugfixes, installing these improves system performance)
- Optional updates(bugfixes or additional features for non-critical apps)

You can choose not to install any of these, but it's not advisable. 

A major difference between Windows updates and Ubuntu updates- The updater in Ubuntu updates **all applications** installed via the package manager(so the updates you see include updates for drivers, Firefox, Adobe Flash, Java, Evolution eMail client, Open Office, GIMP, the music player, in addition to the Ubuntu OS updates- the more apps you have installed, the more updates you'll see), whereas Windows update provides updates only for the Windows OS(plus Internet Explorer and Windows Media Player). So if you have Firefox, Thunderbird, RealPlayer or anything non-Microsoft on your PC, you have to update them separately. Windows Update also does not install MS Office updates(you can use Microsoft Update to get both Windows and Office updates though).

Another major difference- Ubuntu issues updates as soon as they are available. MS Windows updates are usually rolled out once a month(on 'patch Tuesday'). 
The disadvantage- more frequent patches.
The advantage- your system is vulnerable for a shorter period of time.

An example of this is the recent IE vulnerability(for which MS had to issue an out of cycle patch), exploits for which were published right after patch Tuesday(making it a zero-day vulnerability). MS at first seemed geared to put off issuing a patch for this till the next patch Tuesday, and that was just what the cyber-criminals were counting on- that would give them a whole month to wreak havoc. Once reports of the vulnerability being actively exploited started pouring in, MS finally got their act together and issued an emergency patch(and posted some workarounds to use till the patch was available).

If you're using Windows, I'd suggest using Secunia Personal Software Inspector(PSI) to scan your system and find and fix unpatched/vulnerable applications on your PC.
[http://secunia.com/vulnerability_scanning/personal/](http://secunia.com/vulnerability_scanning/personal/)

---

### Post by chrisod on 2009-01-02
I'm on 8.04, with the backport repositories enabled, and I only see updates once or twice a week. How often do you use Ubuntu? If you only use Ubuntu once a twice a week that would mean you see updates every time you start Ubuntu.

---

### Post by sadaruwan12 on 2009-01-02
Hi,

Well normally in the world of open source every thing is fast and rapidly developed. And the other thing is that lot of people get involved in developing open source stuff like Ubuntu so more and more bugs are found and corrected security is enhanced stability of the OS is increased and all of these things are passed though to the users as updates not only Ubuntu most of the open source software are like this. Please update your Ubuntu release frequently as possible that makes your system very stable and more secure.

---

