---
title: "Ubntu + Ubuntu Server on one machine"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Taamalus on 2011-03-05
Hello!
I tried to use a search, but had to many hits to sift through, and hope I won't bore you with yet another n00b set of questions.
 

 
[LIST=1]
[*]I'm familiar with Ubuntu only.
[*]I would like to install a server     on the same machine where Ubuntu resides.
[*]The reason to want to install it     is for my own education, I have no plans to actually run a web site     from home, just test things out before I go to a Unix/Apache host.
[*]I have Gparted.
[*]The Hard Drive is only 40 Gb
[/LIST]
 

 Now the actual question: Do I have enough room, and if yes, how should I partition Ubuntu and Server. If I don't have enough room, besides getting a larger computer what option should I consider.
 

 I'm used to Visual Studio (Pro) and the 'test' server there to try things out, now I move to the Linux community and am hopelessly lost on how one does things. So any suggestions, even what seems obvious to a Linux Pro, is very much appreciated. :confused:

---

### Post by maqtanim on 2011-03-05
I'm little bit confused. Let me ask a question. Do you want a dual boot between Ubuntu-Desktop-Edition and Ubuntu-Server-Edition? or Do you want a local server (like lamp) in your Ubuntu-Desktop-Edition?

---

### Post by Taamalus on 2011-03-05
That was quick! Thanks, maqtanim!

Not sure about a Dual Boot. I thought you need this when two conflicting OSs are installed. So if Ubuntu Server and Ubuntu Desktop don't work together, then the answer is: Yes. As for Lamp, sorry, I have had no clue what this is, nor that it exists. I did a Google, and it looks like a solution I will test out this evening.
 Meanwhile, you see, I love to play around, so if there is a way to install Ubuntu Server and Desktop, it would be preferred, even if I need a bigger computer. :)

---

### Post by wep940 on 2011-03-05
My understanding, which may be wrong, is that the server edition doesn't have the GUI and some other non-essential things and the setup is I believe LAMP.  While not recommended for any type of access outside of your own computer, you can either add the GUI and other software you want to the server, or you can just simply install the LAMP things into the desktop version.  A lot of people do this for development and testing prior to moving things to a different server for the real world.

---

### Post by GWBouge on 2011-03-05
Right, everything available to Ubuntu Server is available to the Desktop edition, and vice versa.  Installing a GUI desktop onto a Server opens up security issues, though (don't ask me what, but that's what I read, hehe), so likewise adding Apache/MySQL/PHP, vsftpd, etc, to an Ubuntu Desktop machine isn't really the best practice for an open box.

If you just want to mess around with the LAMP stuff, ftp server, whatever, you can do all that just fine in Ubuntu Desktop.

If you just wanted to get a taste of the server installation options, configuration, command prompt work, etc etc, without adding a desktop environment to it, easiest thing to do is run it in a VM with VirtualBox.  Once you feel comfortable with that, you can apply what you've learned to installing and running Ubuntu Server on a real machine.

---

### Post by jerome1232 on 2011-03-05
Seconding a Virtual Machine, they are great for using a distro just to educate yourself. I use Oracles Virtualbox to play around with different operating systems frequently.

I wouldn't install servers on a computer that is used as your regular desktop, it can open you up to possible attack (ie if you have a poorly secured ssh server people can actually get shell access to your box) especially if you are inexperienced with securing a server.

---

### Post by HermanAB on 2011-03-05
Howdy,

Linux is Linux is Linux...

You can run Apache on regular desktop Ubuntu.

If you want to experiment, then VMware or Virtualbox is the way to go though, in order to ensure that when you mess things up, you don't blow your whole system out of the water.

---

### Post by maqtanim on 2011-03-06
> **Taamalus said:**
> That was quick! Thanks, maqtanim!

Not sure about a Dual Boot. I thought you need this when two conflicting OSs are installed. So if Ubuntu Server and Ubuntu Desktop don't work together, then the answer is: Yes. As for Lamp, sorry, I have had no clue what this is, nor that it exists. I did a Google, and it looks like a solution I will test out this evening.
 Meanwhile, you see, I love to play around, so if there is a way to install Ubuntu Server and Desktop, it would be preferred, even if I need a bigger computer. :)
Sounds like LAMP is the solution that you need. **LAMP** means **L**inux, **A**pache, **M**ySQL, **P**erl/**P**HP/**P**ython. So LAMP is an acronym for a solution stack of free, open source software, originally coined from the first letters of Linux (operating system), Apache HTTP Server, MySQL (database software) and Perl/PHP/Python, principal components to build a viable general purpose web server. [Read here more]("http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29").

---

### Post by Taamalus on 2011-03-06
Thanks, for all your commends. As for the Virtual server, I have this also. Yet, manuals from say Joomla! and Drupal caution to limit one's development only on Virtual Machines, and suggest to fine tune on a real server environments. Also, I should have mentioned it, this is not my regular working desktop, therefore, there are no security issues since it is not connected to my network either.
 

 LAMP is now installed, and love it. Since I have Ubuntu Desktop I don't have to install Ubuntu Server, well, it can't get simpler. I'll give this post another three days and will mark it solved, since  maqtanim  gave the suggestion I was not even looking for yet answered the question.
 

 Cheers Henry :D

---

