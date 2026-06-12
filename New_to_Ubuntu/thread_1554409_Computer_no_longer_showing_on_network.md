---
title: "Computer no longer showing on network"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by adam_himself on 2010-08-16
So, a day or two ago my uBuntu machine was showing fine to my Macbook.  They are both hard wired to my router.  I could see it on my Macbook and even transfer files to my shared folder.  But, today my uBuntu machine (named black_box) is no longer showing to my Macbook (named white_box).  

The only things that have changed since then is installing of gufw and some other security things.  

My Macbook (white_box) is pinging when I "ping 192.168.1.102" but inside of "Places" in Mac OS X "black_box" isn't showing up.  I have two folders I am sharing.  Like I said, it was working just fine 2 days ago...

Is there a port or something I need to open?  If so, whats the proper way?

Thanks,
Adam

---

### Post by hudsonl on 2010-08-16
> **adam_himself said:**
> So, a day or two ago my uBuntu machine was showing fine to my Macbook.  They are both hard wired to my router.  I could see it on my Macbook and even transfer files to my shared folder.  But, today my uBuntu machine (named black_box) is no longer showing to my Macbook (named white_box).  

The only things that have changed since then is installing of gufw and some other security things.  

My Macbook (white_box) is pinging when I "ping 192.168.1.102" but inside of "Places" in Mac OS X "black_box" isn't showing up.  I have two folders I am sharing.  Like I said, it was working just fine 2 days ago...

Is there a port or something I need to open?  If so, whats the proper way?

Thanks,
Adam


First thing I would do is test to see if ufw is what is blocking you ..

Open a terminal and type:
> **sudo ufw disable**

If you can then see the Ubuntu machine from your Macbook ... you know that's where you need to open a port.

Check out "**Opening the UFW Firewall for Samba**" in 

[http://ubuntu.swerdna.org/ubulanprimer.html#firewall](http://ubuntu.swerdna.org/ubulanprimer.html#firewall)

---

### Post by adam_himself on 2010-08-16
Nope that didn't fix it.

---

### Post by adam_himself on 2010-08-16
Odd.  It just came online.  I typed "sudo tuncfg" and now its online... 

What the hell?  I felt like that might have something to do with it.

Can someone explain this? lol:lolflag:

EDIT:  Its only letting me access some folders.  Its saying a folder I have shared isnt available, even though I have it set to sharing...

EDIT AGAIN:  LOL!  I think I might have figured it out....

What would tuncfg have to do with it?

---

### Post by hudsonl on 2010-08-16
> **adam_himself said:**
> Nope that didn't fix it.


Weird ... then it must be one of the "other security changes" that were made ?

You could always try a reboot first on the Ubuntu box ... but disabling ufw should have took affect without a reboot ... but you never know.

---

### Post by adam_himself on 2010-08-16
So, I transferred most of the files I wanted to... so I decided to restart both systems and see what that did for me...

Well, I restarted typed sudo tuncfg and it didn't work.  So, I am beginning to think that has NOTHING to do with it showing up.

I am looking at my Mac as we type this and its not showing up.  Still pinging each other though.

Wow... as I was typing this is popped up on the network.  Maybe it is UFW and my Mac is taking a real long time to establish network connections?  I dunno... 

I am getting rid of Mac OS X... way too many headaches.  I am going to put uBuntu Netbook Edition on it :P  Thats the whole reason I wanted to move those files off it via my network.

Thanks for your help hudsonl!

---

