---
title: "Bad root password issues"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by KristinTheMathmagician on 2010-05-07
I got called to my folk's place because they could not get root.  They are on a Dell mini 10 netbook that had Ubunu 8.04LTS pre-installed.  I cannot get into GRUB to go into safe/recovery mode or whatever it is called as Dell has it "tweeked" to have the GRUB menu time at zero.  Yeah, I tried pounding on the esc and ent keys to get at it...

And the root password has been a problem.  Last week they called me to fix it.  It was not accepting the password that I SET.  After about eight tries I got root, using the same damned password.

So I ask of you Ubuntu gurus, should I just hose the OS and start over, replacing it with 9.04?  Should I try the ever risky upgrade?  What to do?  And why the crap can't I get into GRUB?

This is serious as my parents somehow think this is my fault.  And they are happy with their dual boot XP/Intrepid Ibex desktop.  The netbook, not so much.

Kristin The Mathmagician

---

### Post by Mustard on 2010-05-07
Just a thought, but I wonder if you have some keys that are repeating that are causing the password to be entered incorrectly without your knowledge.  I know I have an old laptop that has that problem.

---

### Post by KristinTheMathmagician on 2010-05-07
Good thought** Mustard**.  When you sudo passwd you do not even see the *******.  Instead you see nothing.  You are probably right.  Sticky keyboard or something.  That also explains why it did not accept the password after multiple attempts but then did so.

Good on ya, mate!

---

### Post by Peter09 on 2010-05-07
Depending on the version you are using, try holding the shift key down during boot to get a grub prompt.

---

### Post by Mustard on 2010-05-07
If it is sticky keys, its going to be a bitch to get into. :)

---

### Post by KristinTheMathmagician on 2010-05-07
> **Mustard said:**
> If it is sticky keys, its going to be a bitch to get into. :)
My next attempt involves me plugging in the keyboard I am using now...  And thanks again for the obvious suggestion!

If that fails I guess I will put the latest Ubuntu release on it.  Or I can lie to my parents saying that there is no reason to have root.   That's kind of true as they use it to read email, check the tele listingts, etc.

---

### Post by Peter09 on 2010-05-07
In Ubuntu I'm not sure why you need a root password at all - seems a security risk to me.

---

### Post by KristinTheMathmagician on 2010-05-07
OK, plugging in a keyboard did nothing.  Something is really wonky  here.  I would prefer to keep 8.04 LTS instead of upgrading.  I just  need to figure out how to get to GRUB which Dell makes very hard to do  since the time is set at zero.  Someone please help!  Your reward will  be my gratitude.  Sorry, that's all I can offer.

My other options are just telling them that it is fine the way it is.   That's pretty accurate actually, but when they get update notices my  father thinks it is something vital.  Plus, that just is awful.  I am so  angry that it won't give me root.  Or I can upgrade to the latest  Ubuntu which is discussed in the paragraph below.

I don't know how to upgrade the netbook.  Can I install it from an ISO  on their home network?  Do I need to put the ISO on a thumbdrive?  I've  never worked on a computer that did not have a CD or DVD drive before.    Well, recently.  My first computer had a 5.25 drive.

---

### Post by cariboo on 2010-05-07
Are you actually having a problem with the root password or sudo password? Can you still get in as a regular user? Can you edit /boot/grub/menu.lst to set the time out to a longer duration?

---

