---
title: "Software Center Hanging and Package Manager Errors"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by tdupu on 2011-07-08
When I try to install or even view what software I have installed with the software center it hangs. When I attempt to open synaptic package manager I get the following error. 
{{{
E:Encountered a section with no Package: header
E:Problem with MergeList /var/lib/apt/lists 
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E:The package lists or status file could not be parsed or opened
E: _cache -> open() failed, please report.
}}}

---

### Post by Muskegman on 2011-07-08
Hi there the first thing i would do is , open terminal and type in:
 "sudo apt-get update" without the quotations

---

### Post by Rubi1200 on 2011-07-08
Hi and welcome to the forums tdupu :)

Open a terminal (Ctrl+Alt+T) and run the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by _Narcisse_ on 2011-07-08
Hello tdupu, 

You might want to check this rather old thread: 

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

and especially [page 7]("http://ubuntuforums.org/showthread.php?t=863742&page=7") which contains more recent posts.

Don't hesitate to use the search. Many issues have already been solved. :)

Cheers

---

### Post by tdupu on 2011-07-12
> **Muskegman said:**
> Hi there the first thing i would do is , open terminal and type in:
 "sudo apt-get update" without the quotations

not working, same error about a header

---

### Post by tdupu on 2011-07-12
> **Rubi1200 said:**
> Hi and welcome to the forums tdupu :)

Open a terminal (Ctrl+Alt+T) and run the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

what are these things I'd be removing? I don't want to mess up my computer more.

---

### Post by westie457 on 2011-07-12
> **tdupu said:**
> what are these things I'd be removing? I don't want to mess up my computer more.

That command is a safe one taking in to consideration the poster 'Rubi1200' is an Ubuntu Member. He probably has too much reputation and standing to lose in these forums by deliberately asking you to do something dangerous to your system without eithout explaining the risks and dangers involved.

That particular command will remove only the files it has been told to and nothing else.

Very rightly you have asked about a command which if written differently could and in some cases will wipe everything from your system. Here is something for you to read and take note of the warnings. [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

---

### Post by philinux on 2011-07-12
Post #3 is spot on. The OP is right to question commands though as this type if used wrongly can result in a borked system.

This has been seen before. e.g.
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by Rubi1200 on 2011-07-12
> **tdupu said:**
> what are these things I'd be removing? I don't want to mess up my computer more.
You have every right to question the commands I posted and I applaud you for doing so.

Better to be safe than sorry, as they say.

westie457 pointed something out, but I will clarify what the commands do.

The first one removes corrupted package lists and the second one refreshes them.

It is also good practice to copy and paste the commands to avoid typing/syntax errors etc.

Thanks to both westie457 and philinux for the vote of confidence.

In future, I will try and be more conscientious about saying what the commands do.

---

### Post by tdupu on 2011-07-14
Awesome! It worked! Thanks a ton guys!

---

### Post by Rubi1200 on 2011-07-14
Nice one! I am really glad this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by pulencio on 2011-09-01
> **Rubi1200 said:**
> Hi and welcome to the forums tdupu :)

Open a terminal (Ctrl+Alt+T) and run the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Thank you very much! It worked for me.
Cheers!

---

### Post by Rubi1200 on 2011-09-02
> **pulencio said:**
> Thank you very much! It worked for me.
Cheers!
Excellent! And welcome to the forums :)

---

