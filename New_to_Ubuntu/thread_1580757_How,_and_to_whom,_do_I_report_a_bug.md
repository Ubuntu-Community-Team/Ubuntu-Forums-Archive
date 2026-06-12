---
title: "How, and to whom, do I report a bug?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-09-23
Hello:

I have posted twice about 'system testing' freezing and forcing me to power off my pc.

A couple of days ago I re-installed ubuntu because I am certain that I have screwed a few things up over the past 6 weeks - maybe even 'system testing'!

Anyway, 'system testing' still freezes after the re-install so, I assume it is a bug to be exterminated by ubuntu programmers.

How do I report this problem, or, is that a newbie no-no.

Thanks

---

### Post by ddnev45 on 2010-09-23
I think this is current. Make sure it hasn't already been reported:

[Reporting a bug.]("https://help.ubuntu.com/community/ReportingBugs")

*Edit: I just noticed there is a sticky for how to report a bug at the top (beginning) of the Absolute Beginner page, probably best to read through that.*

---

### Post by jtarin on 2010-09-23
Start the application from the terminal to get any possible reason why it would.

---

### Post by Robert.Thompson on 2010-09-23
> **jtarin said:**
> Start the application from the terminal to get any possible reason why it would.

I did: /usr/bin/checkbox-gtk in the terminal and the app started and the locked up my pc - there was no additional output to my limited knowledge.

---

### Post by sandyd on 2010-09-23
> **Robert.Thompson said:**
> I did: /usr/bin/checkbox-gtk in the terminal and the app started and the locked up my pc - there was no additional output to my limited knowledge.
create the bug through
[https://launchpad.net/ubuntu/+source/checkbox/+bugs](https://launchpad.net/ubuntu/+source/checkbox/+bugs)

and attach the following files to the bug (note, you need to make a copy of them and then chown the copy to your username)
/usr/log/dmesg
/usr/log/Xorg.0.log
/usr/log/kern.log
and the output of
```

lspci
```

---

### Post by Robert.Thompson on 2010-09-23
> **sandyd said:**
> create the bug through
[https://launchpad.net/ubuntu/+source/checkbox/+bugs](https://launchpad.net/ubuntu/+source/checkbox/+bugs)

(note, you need to make a copy of them and then chown the copy to your username)


Yikes, what's that flying over my head!!!:)

Is this a typo or did you say: "...and then chown the copy to your username."

---

### Post by baddog144 on 2010-09-23
> **sandyd said:**
> create the bug through
[https://launchpad.net/ubuntu/+source/checkbox/+bugs](https://launchpad.net/ubuntu/+source/checkbox/+bugs)

and attach the following files to the bug (note, you need to make a copy of them and then chown the copy to your username)
/usr/log/dmesg
/usr/log/Xorg.0.log
/usr/log/kern.log
and the output of
```

lspci
```

It's really much easier to use "ubuntu-bug" as described [here]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by jtarin on 2010-09-23
> **Robert.Thompson said:**
> Yikes, what's that flying over my head!!!:)

Is this a typo or did you say: "...and then chown the copy to your username."chown=change owner

---

### Post by Robert.Thompson on 2010-09-23
Went to "Bugs in Ubuntu" and there are a number of entries concerning CheckBox. (AKA: System Testing, I think).

So, I don't think I need to bother them with this.

---

### Post by robert shearer on 2010-09-23
> 'system testing' freezing and forcing me to power off my pc.

For future reference, powering off/hard reset risks file corruption.

Here is a link to the right way to exit a freeze. 

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down. :)

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

---

### Post by Robert.Thompson on 2010-09-23
> **robert shearer said:**
> .

For future reference, powering off/hard reset risks file corruption.

Here is a link to the right way to exit a freeze. 

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down. :)

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

Raising Skinny Elephants Is Utterly Boring - I've got it. Thanks.

---

### Post by sandyd on 2010-09-23
> **baddog144 said:**
> It's really much easier to use "ubuntu-bug" as described [here]("https://help.ubuntu.com/community/ReportingBugs")
this is what happens when I know ubuntu too much ;). I start offering solutions that are harder than they should be lol.

---

