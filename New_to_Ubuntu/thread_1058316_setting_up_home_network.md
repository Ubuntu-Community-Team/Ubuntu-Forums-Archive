---
title: "setting up home network"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-02
okay hi everybody.  i want to set up a home network and need help.  i have looked through the threads and howtos but havent found anything i can understand.  let me outline what i want to do if possible.
i am currently running a laptop on 8.10 and a desktop on xp.  both machines log onto the internet via a wireless router/hub (from british telecom if that helps). so to me it resembles  a letter Y with the two machines at the ends of the top arms and the router at the junction leading out to the web at the bottom
i seem to have a sort of network in that i can look at certain files on the desktop from the laptop although only when my particular user account on xp is logged on - no other users.
but i cannot make the desktop see the laptop at all - and when i try to do anything with the network on windows it doesn't want to do anything but setup its own prescribed ms network and i want to be able to read/edit files in both directions depending on which machine i am using (here are other reasons too eg wife also works on my business records but only likes the desktop) - is this not possible?
also i have a wired ethernet connection AND a wireless connection from desktop to router - should i remove one of them and would it be better to keep the wireless (which only connects to the desktop) cos the laptop is wireless too, or the wired because it looks as if its faster.
can someone lead me through this - i am finding it very confusing.  i just want it to work both ways and preferably with linux being the 'master' since it can adapt to windows and my windows doesnt look like it wants to play nicely.
this seems very complicated to me and i am sorry about the wordiness.  if you need any more information i will be happy to post it.  please help cos i think the bodge up of a network is making my internet access a bit wobbly.
again, please help.
thanks in advance
nigel

---

### Post by jerrrys on 2009-02-03
networking is not the easiest thing to do. router has to be configured, ports to be delt with, software to be installed. that your two computers even partially communicate is amazing. i would suggest starting here:

[http://www.google.com/search?q=networking+basics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=networking+basics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by capnthommo on 2009-02-03
hi jerrrys, thanks for that, i will give that site a good read through. i didn't think it could be simple - there are too many variables involved!
thanks again
nigel

---

### Post by billgoldberg on 2009-02-03
Take a look at this how-to I've written.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

---

### Post by lazyart on 2009-02-03
> **jerrrys said:**
> networking is not the easiest thing to do. router has to be configured, ports to be delt with, software to be installed. that your two computers even partially communicate is amazing. i would suggest starting here:

[http://www.google.com/search?q=networking+basics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=networking+basics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

I'm afraid Jerrrys is a bit off base here.  You don't need to configure the router or open any ports.

On the Windows side, share a folder.
On the XP side, go to Places->Connect to server

Enter the IP address and the name of the share.  Make a bookmark.  You're connected.

To go the other way-
Right click on the folder you want to share.
Select sharing options
Check the relevant boxes.
From XP go to Start->Run
enter the IP address of the Ubuntu machine, preceded by \\.  For example:
\\192.168.1.101

It should prompt you for your ubuntu username and password.  And you're in.

---

### Post by johnjohn2 on 2009-02-03
> **lazyart said:**
> I'm afraid Jerrrys is a bit off base here.  You don't need to configure the router or open any ports.

On the Windows side, share a folder.
On the XP side, go to Places->Connect to server

Enter the IP address and the name of the share.  Make a bookmark.  You're connected.

To go the other way-
Right click on the folder you want to share.
Select sharing options
Check the relevant boxes.
From XP go to Start->Run
enter the IP address of the Ubuntu machine, preceded by \\.  For example:
\\192.168.1.101

It should prompt you for your ubuntu username and password.  And you're in.

Enter the workgroup for windows in > shares-admin from terminal or read this

[http://ubuntuforums.org/showthread.php?t=1058720](http://ubuntuforums.org/showthread.php?t=1058720)
the bottom post from me;)

BTW i am a fellow Northamptonian.

Regards john

---

### Post by capnthommo on 2009-02-03
okay thanks people,  i have to go out now but i will get on this as soon as i can.  if i need (and i'm sure i will) any more help i will re-post.
thanks again
nigel

---

