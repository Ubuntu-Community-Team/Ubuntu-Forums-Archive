---
title: "no menu page on skype"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by dulce on 2011-04-26
i took this to the skype forum where no one has answered. someone else had the same problem with ubuntu 10.04.

basically when i launch skype i get a list of my contacts which are exactly 2 friends who have added me. other than that its a blank page. i can search for contacts but not add them because the window just loads and loads and the add button is blocked. i have no buttons to answer a call  and if i make a call it fails.

i suppose the problem is that i just poked the linux button to download  skype. i see from searching this forum that there is another procedure. maybe someone can walk me  thru it. 

past experience on this forum tells me that some genius on this planet will answer me pretty quickly. i admit that i know very little but am capable of learning. :)

---

### Post by Ghost|BTFH on 2011-04-27
You have to make sure everything is set up properly in Skype.  There is a section (can't recall off the top of my head where, but I'm sure you could find it fairly easy) called "Options" I believe.

Look in there and make sure sound and video both work properly, and utilize the test call to make sure everything's working peachy.  If all that is working fine and you still can't do anything with it...well, there goes my limit on Skype knowledge.

Cheers,
Ghost|BTFH

---

### Post by Vi3tHoneyX on 2011-04-27
Have you tried uninstalling it and downloading a different version from the Skype website (make sure you choose the correct version) or maybe the software center?

---

### Post by dulce on 2011-04-27
> **Vi3tHoneyX said:**
> Have you tried uninstalling it and downloading a different version from the Skype website (make sure you choose the correct version) or maybe the software center?

which software center?

---

### Post by dulce on 2011-04-27
> **Ghost|BTFH said:**
> You have to make sure everything is set up properly in Skype.  There is a section (can't recall off the top of my head where, but I'm sure you could find it fairly easy) called "Options" I believe.

Look in there and make sure sound and video both work properly, and utilize the test call to make sure everything's working peachy.  If all that is working fine and you still can't do anything with it...well, there goes my limit on Skype knowledge.

Cheers,
Ghost|BTFH

i don't have enough of a menu page to find any options tho i will look again.

---

### Post by Vi3tHoneyX on 2011-04-27
> **dulce said:**
> which software center?

The Ubuntu Software center

---

### Post by dulce on 2011-04-27
i did find those options and everything checks out but the test call, which failed

i went to the software center where it was noted as already installed but i reinstalled it. it did say 'this software is available from the 'lucid partner' source which you are not currently using'. but installed it anyway.

i did learn that that is the ubuntu menu page. everything is still the same tho-- can't add contacts, calls fail.

---

### Post by dulce on 2011-04-28
well i guess this thread is misnamed, since the page i have is the menu page for skype.

should i give up on skype?

what is lucid-partner? should i get that?

---

### Post by frank604 on 2011-04-28
First of all, use the version of skype that is in the official ubuntu repository as it includes fixes that aren't included from the skype website.  

You should remove it completely.

Reinstall by typing in terminal:
sudo apt-get install skype

Then in terminal, launch it by typing:
skype

leave the terminal window open as it will produce any error messages occuring while skype is being run.  Copy paste any error messages here and we can proceed to troubleshoot further.

---

### Post by dulce on 2011-04-29
thank you frank. that was the answer i was waiting for. :)

i ran it in terminal, no errors and it launched itself without typing 'skype'. it *appears* to work now-- it let me add my contact,etc. i'll know for sure later when my contacts come online and we can call each other.

---

### Post by dulce on 2011-05-08
thanks so much frank, everything works now. have marked this thread 'solved'.

---

### Post by frank604 on 2011-05-08
No problem.  Enjoy :)

---

