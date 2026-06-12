---
title: "Mail Help"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by hmsiegel on 2010-12-14
The last piece of my Ubuntu puzzle is being able to check my mail.  Unfortunately, I can't get either Thunderbird or Evolution to run.  Thunderbird will start in the task bar (Is it called that in Ubuntu?), and then close.  Not sure why.  I've searched around and can't get anything to work.  If I start Evolution, I will get to the setup screen and if I try to select Exchange, it crashes.  
And that brings me to my second problem.  I would like to be able to get my Exchange email.  I can access it through OWA, but it's not the same.  Is there a way to get Exchange on Ubuntu.  My company gets our Exchange through a company called Sherweb.  Don't know if that helps at all, but I figured it couldn't hurt.  
Thanks

Harlan

---

### Post by Wobblybob on 2010-12-18
Hi, can you open a Terminal and type;

thunderbird 

and press [enter] and this should open thunderbird and the terminal should show you any error messages created. Copy and paste them back here and we may be able to sort things out. The thread below may help with your exchange mail although it may be out of date now.


[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=404728[/COLOR]]("http://ubuntuforums.org/showthread.php?t=404728")

---

### Post by hmsiegel on 2010-12-19
When I type thunderbird in the terminal, I get:
```
Segmentation fault
```

---

### Post by Wobblybob on 2010-12-19
Did you install thunderbird from the software centre or from another source? You could try using synaptic to remove it completely and delete or rename the hidden folder in your home called .thunderbird then reinstall.

---

### Post by hmsiegel on 2010-12-19
I had installed from the Software Center.  Then uninstalled it through the Software Center as well, and then reinstalled it again and am still getting the same error.  
How would I uninstall it from the Synaptic?
I don't mind losing the config files because I haven't been able to start it to begin with.

---

### Post by Wobblybob on 2010-12-19
[system], [admin...], [synaptic package manager] qick search box for thunderbird right click on the thunderbird package and select [Mark for complete removal] this should remove everything. Then re install using the same method but choosing [mark for instalation from the list].

Just an off the wall question, you have not installed a package called SCIM which is used to input different languages have you - you could check y searching for scim in synaptic just in case. The reason I ask is that I've read that this casues some problems for thunderbird.

---

### Post by hmsiegel on 2010-12-20
Still having the same issue.  I uninstalled Thunderbird from Synaptic.  Did a complete uninstall.  Then reinstalled.  Still having the same problem.  And no, I don't have SCIM installed.

Harlan

---

### Post by Wobblybob on 2010-12-20
bit stumped here, but I found this post, does this solve your problem?
[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=9347811&postcount=10[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9347811&postcount=10")

if not can you give some more details about how you have ubuntu setup, version, file system etc.

---

### Post by hmsiegel on 2010-12-21
It's still not working.  I'm not concerned about it just yet.  I found out by calling the company that hosts my Exchange account that Linux (and Evolution) isn't really supported.  The workaround I found for it is to use the IMAP settings for the Exchange account.  It doesn't sync automatically, but it works.  For sending I set up a Gmail account that I am having redirect to my Exchange.  It works for now. 

As for my machine, I have Ubuntu installed in Wubi right now.  I've been giving it a test to see if I like it and if I can use it (which I think I can).  In the next week or so I will probably uninstall it and then install Ubuntu alongside Windows.  I can't get rid of Windows completely.  For one, I've spent too much money on programs (Office).  Also, a lot of the scripts I've written for Excel programs probably won't work in OO.  I also have one program for my work that I know won't work in Linux.  And finally, there's the iTunes dilemma.  I have bought a lot of music over the years and a lot of it won't play in Linux.  For that, I'm going to have to burn a lot of discs.
Thanks

Harlan

---

### Post by Wobblybob on 2010-12-22
ok mate good luck with your Ubuntu journey I've been using it exclusively for several years now. I suspect your having problems either because you have a problem with one of your sticks of your RAM or are using Ubuntu within Windows, I've never been a fan of wubi. Installing Ubuntu as a dual boot may be worth a try the installer works well and will resize your Windows partition. You could try installing WINE to run your windows prog and OO can be quite good with MS docs and is able to save them out as .doc.xls etc. again good look.

---

