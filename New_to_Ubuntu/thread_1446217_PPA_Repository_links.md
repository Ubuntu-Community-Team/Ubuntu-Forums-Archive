---
title: "PPA Repository links?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by jcettison on 2010-04-03
It seems silly to me that the links for PPA reps online must be copied and pasted into the resource manager or manually added by command line. Wouldn't it be best to have these as hyperlinks so that software developers could simply have "Add our repository!" hyperlinks or graphics?  

I'd envision something similar to the aim:// or ***e***mule:// handlers that are used to import information from a hyperlink to a windows application.

---

### Post by new_tolinux on 2010-04-03
Absolutely not.

The most common way it goes is "first click then read", although it should be "first read then click".

Adding repositories isn't something you should do that much.

---

### Post by Naitsirhc Hsem on 2010-04-03
Agreed

---

### Post by Arand on 2010-04-03
Giving root access (by means of packages) is not something that should be done lightly. In my opinion PPA usage should rather be more complicated, in order to discourage one-click-no-thought usage.
- Arand

---

### Post by nothingspecial on 2010-04-03
On the other hand.....

......This is linux --- Do what you will.

Even break your own system.

The choice is your`s.

Nice, isn`t it?

---

### Post by new_tolinux on 2010-04-03
> **nothingspecial said:**
> On the other hand.....
......This is linux --- Do what you will.
Even break your own system.
The choice is your`s.
Nice, isn`t it?
That's right, but it shouldn't be encouraged by adding a "feature" that makes Linux as vulnerable as Windows is.
One of the reasons many people click before they read is the amount of "Would you like the system do this-or-that?"-messages that Windows produces.
Thereby, adding repositories requires root (sudo) access. Not something I'd like my browser to ask for.

---

### Post by nothingspecial on 2010-04-03
I agree with you.

But how is anyone going to learn without messing up?

Easier to fix with linux (unix) I think - (no expert)

Of course, if you just want a computer that computes - don`t mess about with ppas in the first place!

---

### Post by new_tolinux on 2010-04-03
> **nothingspecial said:**
> I agree with you.

But how is anyone going to learn without messing up?

Easier to fix with linux (unix) I think - (no expert)

Of course, if you just want a computer that computes - don`t mess about with ppas in the first place!
For me (Windows: system admin&network admin / Linux: check my forum-name ;)) it's way more easy to fix Windows, either by reinstalling or by removing the unwanted.

And you're assuming that someone wants to learn. From my background as a professional who spent lots of his private time to get the computers of other people back on track, I can say that the amount of people who want to learn is <10%. ---Edit: The people who _say_ they want to learn is about 90%. But there's a big gap between saying that and wanting it.
Most people prefer a fool-proof system where they can do anything they want without any limitation (the impossible :p). You can tell them to read, but they only think of that _after_ they clicked "OK". Since there's nothing to read once you clicked "OK".....

Then they call me, tell me that their system broke down again, and that they didn't do anything wrong :lolflag:

---

### Post by NightwishFan on 2010-04-03
I am sure it would be possible, and probably implemented. Personally I do not mind using the:
```
sudo add-apt-repository *ppa-name*
```

---

### Post by Arand on 2010-04-03
Is not as much a matter of "mess up" as it is of completely surrendering the computer in installing whatever malware the author decides to push through the untrusted repo (occurs seldomly if ever today, thankfully).
Also taking into account the "target group" of Ubuntu (which I think is noexistant in many cases, but that's another rant) ...bad idea, very bad.
- Arand

---

### Post by lidex on 2010-04-03
Ubuntu is what it is - as is windows - let's keep it that way. :rolleyes:

---

### Post by jcettison on 2010-04-03
Many of the conclusions here aren't based on usability, functionality or security but rather some inane opinion that accessibility = doom. You can still provide system side deterents and warnings/cautionary disclosures regarding the safety of adding repositories. You could also host a list of trusted repositories, after all the firefox stable repo is of little harm to anyone.

Please, more reasonable reponses in regards to why this should or should not be.

---

### Post by nothingspecial on 2010-04-03
You are all correct.

I just wish you wern`t.

I wish people understood what a computer is and what it can do (especialy when connected to the web) before they .........

---

### Post by new_tolinux on 2010-04-03
What do you call more reasonable?

As for a fact I know that "first click then read" is the most common thing that happens. Like it or not, but that's causing the most problems.
Adding a repository requires root/sudo-access. Therefore, if your browser asks you to grant that access (in order to add the repository) _it will have rights to do other things to the system_. Simply because any kind of virus/malware/adware/etc. could gain access that way, for example by presenting you a link which looks like a "normal" repository, but instead it is no repository, it only is a way to gain root access.

I'm skipping "what is root access" and "what can you do with it", as I assume that's known. If not: google something like "linux root access" or something.

Then what is a "trusted repository"? Firefox? Then why does the Ubuntu repository has Firefox in it?
If (and only if) the Firefox repository was trusted that much, it should be included by default. Since it's not, I have no reason to trust it, because the Ubuntu repository has Firefox included.
Sabnzbdplus (just another example, which I happen to have used in the past). They have an (unsupported) repository. But it's also included in the Ubuntu repository. Ok, Ubuntu ships an older version in their repository, but when I added the unsupported repository, I ended up with a not-working beta, because it was marked as a stable upgrade. "Luckily" for me that was around the time Karmic came out and still had so many issues that I had to reinstall Jaunty anyway, but I learned my lesson there.

I prefer to install through the official repositories. _Or_ use .deb packages/compiling, since those will not list in update-manager, so I manually have to update that programs. Chances are that they will never be upgraded, as "what works, does work" goes well for many programs.
A nice working firewall on Linux and one between "Linux" and "Internet" will stop many attempts to exploit software-vulnerabilities, so no urge to update soon anyway. Besides, isn't an update a possible new set of vulnerabilities?

---

