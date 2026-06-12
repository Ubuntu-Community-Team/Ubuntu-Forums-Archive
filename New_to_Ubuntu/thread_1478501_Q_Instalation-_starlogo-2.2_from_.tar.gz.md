---
title: "Q: Instalation- starlogo-2.2 from .tar.gz"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by bryan.hatton on 2010-05-09
Hello and thank you for your time.

I couldn't find the file on synaptic so I downloaded the .tar.gz
Extracted the file to /usr/local/src. I navigated to /usr/local/src/starlogo-2.2 in terminal and ran 
*./configure*
"no such file or directory"

Then I ran
*sudo checkinstall*
Which gave(after I hit enter to verify package values)

[I]Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.[/I]

File is found at [http://education.mit.edu/starlogo/](http://education.mit.edu/starlogo/)

I'm not really sure what's going on. What else should I give *checkinstall* in order to install starlogo?
Thanks

---

### Post by Sealbhach on 2010-05-09
Could you copy and paste the instructions you are using, probably from the readme file?  

.

---

### Post by bryan.hatton on 2010-05-09
Well the readme doesn't have anything to do with installation, just version number and other things, so I used a basic compiling guide archived at 
[http://web.archive.org/web/20080213043303/http://cutlersoftware.com/ubuntuinstall/](http://web.archive.org/web/20080213043303/http://cutlersoftware.com/ubuntuinstall/)

I could be that the download was already compiled but I can't find any excutable or installation file...

---

### Post by djchandler on 2010-05-09
> **bryan.hatton said:**
> Hello and thank you for your time.

I couldn't find the file on synaptic so I downloaded the .tar.gz
Extracted the file to /usr/local/src. I navigated to /usr/local/src/starlogo-2.2 in terminal and ran 
*./configure*
"no such file or directory"

Then I ran
*sudo checkinstall*
Which gave(after I hit enter to verify package values)

[I]Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.[/I]

File is found at [http://education.mit.edu/starlogo/](http://education.mit.edu/starlogo/)

I'm not really sure what's going on. What else should I give *checkinstall* in order to install starlogo?
Thanks
Did you see this?

[http://education.mit.edu/openstarlogo/compilerun.html](http://education.mit.edu/openstarlogo/compilerun.html)

Not to be negative, but you may have better luck getting this to run by getting support through MIT. This is not a package supported by Canonical in Ubuntu.

One option may be running the Windows version under [WINE, the Windows compatibility layer]("http://www.winehq.org/").

If you follow the instructions for running under Mac OS X, you may be okay with the icedtea-6-jre-cacao virtual machine that is  installed by default in Ubuntu. I don't believe there was any such thing  when Starlogo went open source four years ago. A perhaps better option may be to install the Sun Java Runtime Environment (and maybe other Java packages--there are a lot of them) from the repositories via Synaptic or Ubuntu Software Center (that repository must be enabled by checking the "Software restricted by copyright or other legal issues [multiverse]" box). Then follow the instructions for running under Mac OS X. You may want to research that before trying it.

We are talking about [FONT=Verdana, Arial, Helvetica, sans-serif]the "modeling environment  for exploring the workings of decentralized systems -- systems that are  organized without an organizer, coordinated without a coordinator[/FONT]," not the programming language used to introduce computer science and programming to children, are we not?

This is a quote from the above referenced page:

> On Linux: There are build scripts that should work on Linux as well.  Though they  may need testing and updating.One other issue you may be running into is one of permissions. I would maybe try doing this in my home directory.

You may also find a ready answer in this forum:
[Ubuntu Forums  > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming > Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44")

---

### Post by bryan.hatton on 2010-05-11
Success via wine, thank you guys.
\(^.^)/

---

