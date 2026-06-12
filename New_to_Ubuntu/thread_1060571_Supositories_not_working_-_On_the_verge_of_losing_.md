---
title: "Supositories not working - On the verge of losing it here - help !"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-04
Hello,

I think if I don't get help with this I'm just going to explode !:(

I have two computers side by side both with ubuntu 8.10

On one, the **us.archive.ubuntu.com/main** has MANY more options in it than the same one on the other computer.  Specifically, Mozilla-Thunderbird (which I want to install).

Why would they be different on the same version of Ubuntu on different computers?


Thanks

---

### Post by RomeReactor on 2009-02-04
Hi. My guess is that you have different repositories enabled in each machine; go to 'System->Administration->Software Sources' and on the first tab (Ubuntu Software) make sure the same repositories are enabled.

---

### Post by niteshifter on 2009-02-04
Hi,

Differences in /etc/apt/sources.list on the two machines.

---

### Post by mistypotato on 2009-02-04
> **RomeReactor said:**
> Hi. My guess is that you have different repositories enabled in each machine; go to 'System->Administration->Software Sources' and on the first tab (Ubuntu Software) make sure the same repositories are enabled.

That was my first thought...but I'm only focusing on the one mentioned and they are both active on both computers.  But the files lists are VERY different for the same supository.

---

### Post by mistypotato on 2009-02-04
> **niteshifter said:**
> Hi,

Differences in /etc/apt/sources.list on the two machines.


Can I update this on the short listed machine ?

---

### Post by DariusS on 2009-02-04
just a quick note,

suppositories:
[http://en.wikipedia.org/wiki/Suppository](http://en.wikipedia.org/wiki/Suppository)

repositories:
[http://en.wikipedia.org/wiki/Software_repository](http://en.wikipedia.org/wiki/Software_repository)

Not to be a grammatical stickler, but merely in the face of the humorous and continuous typo, please know the vocabulary of the subject you are inquiring after. :D

---

### Post by RomeReactor on 2009-02-04
> **mistypotato said:**
> Can I update this on the short listed machine ?
There's no need to manually edit the sources.list file; that's what the Software Sources application is for.

Please open a terminal (Applications->Accessories->Terminal) in each machine and run this command on both:
```
aptitude search thunderbird
```
and post back the output of each machine.

---

### Post by DariusS on 2009-02-04
> **mistypotato said:**
> Can I update this on the short listed machine ?

You can actually copy one from the other. You could copy/paste the one you *want* into an email to yourself and replace the undesired one with this same list (provided the installations are the same version, i.e 8.04, 8.10 etc...)

---

### Post by mistypotato on 2009-02-04
> **niteshifter said:**
> Hi,

Differences in /etc/apt/sources.list on the two machines.


Hi,

Checked both files....

EXACTLY identical  :confused:

---

### Post by DariusS on 2009-02-04
> **mistypotato said:**
> Hi,

Checked both files....

EXACTLY identical  :confused:

Exactly the same, even down to the ##'s?
Those are very important, as they comment out the following code, making it ignored. In a default install, even after enabling all the other repo's, the sources.lst will be very similar, except for the removing of several important comment characters (#).

---

### Post by mistypotato on 2009-02-04
> **RomeReactor said:**
> There's no need to manually edit the sources.list file; that's what the Software Sources application is for.

Please open a terminal (Applications->Accessories->Terminal) in each machine and run this command on both:
```
aptitude search thunderbird
```
and post back the output of each machine.


Hi Rome,

Interesting....when I run the command you suggested, those files are there but not in the "ummm....REpository (thank you Darius) listing.

I tried reloading the lists but nothing changed.

---

### Post by mistypotato on 2009-02-04
> **DariusS said:**
> Exactly the same, even down to the ##'s?
Those are very important, as they comment out the following code, making it ignored. In a default install, even after enabling all the other repo's, the sources.lst will be very similar, except for the removing of several important comment characters (#).

Hi,

Yes, I carefully looked at them line for line...exact duplicates ???

---

### Post by RomeReactor on 2009-02-04
> **mistypotato said:**
> Interesting....when I run the command you suggested, those files are there but not in the "ummm....REpository (thank you Darius) listing.

Not sure what you mean by this; did you get the same output on both systems?

---

### Post by dmizer on 2009-02-04
Is there anything in /etc/apt/sources.list.d/ ... specifically [medibuntu](https://help.ubuntu.com/community/Medibuntu)?

---

### Post by mistypotato on 2009-02-04
> **RomeReactor said:**
> Not sure what you mean by this; did you get the same output on both systems?

Rome, you are correct.

I ran the command "aptitude search thunderbird" on both machines and the result output was identical.

---

### Post by mistypotato on 2009-02-04
Rome, I digress...

There IS a very subtle difference...
On the first line on the machine showing everything, there is a "i" instead of a "p"
and on the 5th line, there is a "i" and an "A" instead of a "p"

**[COLOR="Red"]p[/COLOR]**   mozilla-thunderbird             - Transition package for mozilla-thunderbird
p   mozilla-thunderbird-bidiui      - BiDirectional support for Thunderbird     
p   mozilla-thunderbird-dev         - Transition package for mozilla-thunderbird
p   mozilla-thunderbird-enigmail    - Transitional package for enigmail         
**[COLOR="Red"]p[/COLOR]**   thunderbird                     - mail/news client with RSS and integrated s

---

### Post by RomeReactor on 2009-02-04
> **mistypotato said:**
> Rome, I digress...

There IS a very subtle difference...
On the first line on the machine showing everything, there is a "i" instead of a "p"
and on the 5th line, there is a "i" and an "A" instead of a "p"

**[COLOR="Red"]p[/COLOR]**   mozilla-thunderbird             - Transition package for mozilla-thunderbird
p   mozilla-thunderbird-bidiui      - BiDirectional support for Thunderbird     
p   mozilla-thunderbird-dev         - Transition package for mozilla-thunderbird
p   mozilla-thunderbird-enigmail    - Transitional package for enigmail         
**[COLOR="Red"]p[/COLOR]**   thunderbird                     - mail/news client with RSS and integrated s

**I** means it's installed; **A** means it was installed automatically, as a dependency of another package.

It looks like the repositories are giving you the same packages after all.

---

### Post by mistypotato on 2009-02-04
Thanks everyone :)

Unfortunately, I still don't know why I can't see all of Mozilla's packages in the RE-pository.  :(

---

### Post by RomeReactor on 2009-02-04
Please post a list of the Mozilla packages you find in one machine that are not available in the other.

---

