---
title: "terminal commands"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by fauna on 2008-12-11
Sorry for being so ignorant but aside from buying a book where does one find out about all the terminal commands.The forum has been very helpful but what I usually do is cut and paste and that sure doesn't help understand what's going on.I love Ubuntu-principles and practice but sometimes it's like being in deep water and not knowing how to swim.If i could knowingly do more it would be goodbye XP which always seems on the edge of dying.  Fauna:-({|=

---

### Post by howefield on 2008-12-11
Browse a few chapters here,

[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

---

### Post by cardinals_fan on 2008-12-11
Entering ```
man command
```will give you some info on it.  You can find tons of these man pages [here]("http://linux.die.net/man/") and some good docs [here]("http://linux.die.net/").  You have to register for it, but IBM has an interesting guide [here]("https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?source=dw-linux-lpic1103&S_TACT=105AGX59&S_CMP=GR&ca=dgr-lnxw09LPI101103").

---

### Post by bodhi.zazen on 2008-12-11
that and learning to read the man pages :twisted:

You can add color to the man pages with most :

```
sudo apt-get install most
```Then add this to ~/.bashrc

```
pager='most'
```then . .bashrc

man man

---

### Post by redandgreen on 2008-12-11
I'm pretty new to it as well, and I find I've learned best by doing. Find a nice clear set of instructions for something harmless, and google them between cutting and pasting. Unpack and repack some tars. Play with switches. Be careful of rm!

---

### Post by Stan% on 2008-12-11
Start here: [http://linuxcommand.org/](http://linuxcommand.org/)

Then here: [http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)

---

### Post by stevek123 on 2008-12-11
A list of the actual commands and a basic bkgnd can be found here

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

---

### Post by fauna on 2008-12-12
Thanks for all the suggestions-I'll be busy checking them out.This is what I tell people is good about the Ubuntu community-people respnd and offer help.You know what would happen if I tried to get help for my XP or ,even worse,from the antivirus company-bad answers days later or no response at all.Again,thanks,    fauna

---

### Post by hyper_ch on 2008-12-12
I'd also recommend [http://www.linuxcommand.org](http://www.linuxcommand.org) to learn the basics (and not so basic stuff also)...

In addition I recommend those two cheat sheets:
[http://files.fosswire.com/2007/08/fwunixref.pdf](http://files.fosswire.com/2007/08/fwunixref.pdf)
[http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf)

That's a nice overview over the most used commands and doing some stuff in the cli (although I spotted a few mistakes or rather things to improve)

---

### Post by Kevbert on 2008-12-12
Here's a website on the [[COLOR="Red"]command line[/COLOR]]("http://www.linuxcommand.org/").
Here's a [COLOR="Red"][cheat sheet]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/")[/COLOR] that you may find helpful.

---

### Post by carml on 2008-12-12
In alternative you can also find a brief description of the commands for shell in System->Help and support-> Advanced arguments->Basic commands ):P.

---

### Post by capnthommo on 2008-12-12
hi fauna, i'm new too and want to say thanks for this question 'cos i was thinking of asking it too - you saved me one.  and i echo what you say about the community, it really feels like 'coming home'.
cheers
nigel

---

### Post by linux_tech on 2008-12-12
Keyboard shortcuts 
[http://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/](http://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/)

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

linux command line reference
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf](http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf)

---

### Post by mkvnmtr on 2008-12-12
I don't remember how I did things very well so learning commands is hard. It helps me a lot if every time I do something I write a note in Tomboy. Later when I want to do the same thing there it is.

---

### Post by Keith Hedger on 2008-12-12
Something that hasn't been suggested is the "apropos" command, if you are not sure which command you need to look up with man try (for instance)```
apropos mpeg
``` to get a list of relevant commands and a brief description

---

### Post by ibuclaw on 2008-12-12
Something that has been priceless to me are the various LPI coursebooks out there.

They aim at helping you passing the LPI exams, and becoming an LPI Certified Linux System Administrator, but they go through each course section at a level that even a new user can understand/follow them through.

You'll learn alot about how Linux works, from filesystem structure to the X screen server.

There are four lots of OpenOffice Books here:
[http://www.nongnu.org/lpi-manuals/](http://www.nongnu.org/lpi-manuals/)

and IBM have their own documentation too:
[http://www.ibm.com/developerworks/linux/lpi/](http://www.ibm.com/developerworks/linux/lpi/)
Though, it requires free registration with them first

Regards
Iain

---

### Post by Nico-dk on 2008-12-12
10 min [crash course](http://www.brighthub.com/computing/linux/articles/7116.aspx) that'll teach you the basics in a very newbie friendly manner. 

> **cardinals_fan said:**
> Entering ```
man command
```will give you some info on it.
+1

From time to time I have use AIX at work, and whenever I get stuck man is there to poit me in the right direction.

---

