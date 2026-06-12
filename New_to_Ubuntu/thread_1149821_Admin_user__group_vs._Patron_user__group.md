---
title: "Admin user / group vs. Patron user / group"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by marianlibrarian on 2009-05-05
I am having a hard time understanding how authorizations and privileges work for users. I have myself set up as an admin user in the admin group. Then I have patrons set up as patron in the patron group.

I just recently read a thread that said to make sure that users are in their correct group. I originally did not have any user assigned to any group.

I need to limit the patron group so that this user cannot move the panels or have access to the majority of menu items found under the System menu. It would be nice if I could remove the Administration menu item from the Patron user's menu, but still have it available when the Admin logs in.

I found something called ubuntu-tweak and installed it. It is nice but it is added to the Applications / System Tools menu. I tried to block this from user Patron by going through Authorizations from the Administration menu. But this item is still available to the Patron user. It doesn't even ask for their password. 

I have also explored Pessulus and liked it. But again this item is available from the Administration menu.

I know many have suggested Kiosk setup. I am desperate right now. My summer reading program is getting into full swing and I am by myself in this endeavor. I won't be able to learn and apply myself to a Kiosk setup until July or August.

Could someone please explain how to properly set up a user and how to limit access to menu items such as hiding the Administration Menu from the low level user.

I apologize that I posted this originally in the Security Discussions before posting it here. It is still there and I have violated the cross posting rule.

---

### Post by marianlibrarian on 2009-05-05
I have searched through the following trying to understand how users and user groups work:
Official Ubuntu 8.0.4 manual
The Free Ubuntu Pocket Guide
Multiple searches with different search terms in multiple forums

Is it not possible to have Administrative type things like the Administrative Menu be hidden from a user who is NOT admin in Hardy Heron??

If it is not possible then is there another version that will?

Almost all of our public access computers are shut down for various reasons like deleting the panels or deleting the minimize, maximize, and exit icons in the top of any window that is open. That happened yesterday and I had just installed 8.0.4 that morning. Now once a window is open, there is no way to exit or minimize because the buttons are gone.

Any help is appreciated. I have just spent two days on this. Tomorrow I will have children visiting the library and have a bunch of preparation. 

If this is a stupid question, please forgive me. I am a Desperate Librarian:confused:

---

### Post by achase79 on 2009-05-05
Check out Pessulus.  it is in the repos and does lock down the gnome window manager in some ways.  I have not used it personally but I have started looking into it.

---

### Post by decoherence on 2009-05-05
OP said

> I have also explored Pessulus and liked it. But again this item is available from the Administration menu.

I have not used Pessulus. Does it not require administrative access to run? In which case, even if it is in the menu, Patron wouldn't be able to do anything with it.

Also, if you right-click the menus you have to option to edit them. Perhaps this, in conjunction is Pessulus, will give you what you want?

Good luck,

---

### Post by marianlibrarian on 2009-05-05
:P
I leave for a few minutes and the calvary arrives.

I was right clicking but not in the right place. It has to be on a menu item. So I eventually found the right place and logged in on the patron user account and unchecked the items that I did not want to be there. 

Hopefully this will tide me over until I get through our summer reading program and can learn about and implement the Kiosk thing that was suggested in several threads.

My main problem until then is that the patron will also right click in the correct place and see all the menu goodies they are missing.

But until then.... Thank you to this forum and to each person who has helped me these past two days.

---

### Post by Niniel on 2009-05-05
And why is that a problem?
So they know they are denied some access; big deal. 
Or are you saying they'll still get access?
If your users are tech savvy and mean-spirited enough to mess up your computers all the time, you may also want to think about creating an image and copying it back onto your computers every morning.

Btw, have you seen [this ]("http://ubuntuforums.org/showthread.php?t=707688")yet? Looks exactly like your situation.
[This ]("http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/")might also interest you.

---

### Post by achase79 on 2009-05-05
> **Niniel said:**
> And why is that a problem?
So they know they are denied some access; big deal. 
Or are you saying they'll still get access?
If your users are tech savvy and mean-spirited enough to mess up your computers all the time, you may also want to think about creating an image and copying it back onto your computers every morning.

Btw, have you seen [this ]("http://ubuntuforums.org/showthread.php?t=707688")yet? Looks exactly like your situation.
[This ]("http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/")might also interest you.

I agree with the image idea.  It would be easy to set up a tar file of a clean home directory (with all tweaks and links set up already).  Then setup a shell script to run on boot that will erase everything in the home directory then restore from the tar file.  The tar file could be put in the /etc or /opt directories and therefore would have only root access making it inaccessable to users other than the administrator.

---

### Post by marianlibrarian on 2009-05-05
Thank You! :)

Imagine that... Ubuntu in a public library... did I think about searching for THAT?? no..

TODO: create user ima doofus

Thank you for the two links. And thanks to all who have helped me here. It is starting to make sense. Yesterday, I read the Official Manual for 8.0.4 My head exploded and my brain fell out. But I'm ok today.

---

### Post by achase79 on 2009-05-05
Removing the panel for the user and just placing links on the desktop is also a good idea.

---

