---
title: "new apartment internet problem"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by bigdidz on 2008-06-03
Hi, I just moved to my new apartment and I should have internet but....

I'm presently on a old computer (running Window XP).  I tryed to take the ethernet wire from this computer and put it on my laptop (Hardy Heron) put it doesn't work.(even if I reboot my laptop)

The problem is I do not know what is on the other side of the wire.  Probably a router or a modem.  I cannot acces the room where the 'source of the internet' is but, I can shutdown the electricity there.

On the computer running on windows it says...
IP address:   192.168.1.103
mask:         225.225.225.0
bridge:       192.168.1.1
(the computer is in french so this is my translation)

If you have suggestions, I'm open to suggestions

Thanks

---

### Post by bigdidz on 2008-06-03
Come on folks, I really need your help!!!

---

### Post by vexingmodstwo on 2008-06-03
> **bigdidz said:**
> Come on folks, I really need your help!!!

I had responded to you before but the db crashed.

Anyway, you need to do a couple of things.

First, find out the default gateway IP address for the router.  (Usually, you have to be able to log in to the router to get this... so I don't know what to tell you on this front)

After you get that, manually configure the connection in the network manager and put all that information you listed (plus the default gateway) into the settings for the connection.

Automatic DHCP doesn't seem to work consistently so you might have better luck forcing the connection.

---

### Post by bigdidz on 2008-06-03
I tryed it and it doesn't work.

thanks but I think that my 'bridge' is the default gateway.  I translated the word so my default gateway would be : 192.168.1.1.

but when I look on wikipedia it says that the range would be from192.168.4.1 to 192.168.4.254.  So it doesn't fit.

What should I do?

---

### Post by vexingmodstwo on 2008-06-03
> **bigdidz said:**
> I tryed it and it doesn't work.

thanks but I think that my 'bridge' is the default gateway.  I translated the word so my default gateway would be : 192.168.1.1.

but when I look on wikipedia it says that the range would be from192.168.4.1 to 192.168.4.254.  So it doesn't fit.

What should I do?

The default gateway is the IP address the rest of the internet would see.  The stuff you're listing is all "private" IP addressing for the router.

That 192.168.1.1 is actually the router's "inside" facing IP address.  You can actually type that ip address into a browser and get the routers login screen.

Where did you get the stuff you listed the first time on the windows box?  Was it from doing an "ipconfig" command in the Command Prompt window?

---

### Post by bigdidz on 2008-06-03
Sorry for the delay but now the screen of the windows internet doesn't to work anymore...  anyway.

I took the information that I gave to you by wright-clicing on the icon on the bottom bar of windows.  I think it does exactly the same thing than the 'ipconfig'.

When I try to the router's "inside" facing IP address it asks me a password that I do not have.

But I look on [www.whatismyip.com](www.whatismyip.com) and it gave me an answer (that unfortunately I do not have now) do you thing it can do the job?

When the screen will want to work agint I'll try (I didn't take the ip number on a pice of paper).

Thanks a lot.

---

### Post by vexingmodstwo on 2008-06-03
> **bigdidz said:**
> Sorry for the delay but now the screen of the windows internet doesn't to work anymore...  anyway.

I took the information that I gave to you by wright-clicing on the icon on the bottom bar of windows.  I think it does exactly the same thing than the 'ipconfig'.

When I try to the router's "inside" facing IP address it asks me a password that I do not have.

But I look on [www.whatismyip.com](www.whatismyip.com) and it gave me an answer (that unfortunately I do not have now) do you thing it can do the job?

When the screen will want to work agint I'll try (I didn't take the ip number on a pice of paper).

Thanks a lot.

I just checked the outcome of that site and its different than the default gateway but you can try using it.  It won't break anything.

---

