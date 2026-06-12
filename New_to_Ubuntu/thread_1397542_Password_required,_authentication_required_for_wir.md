---
title: "Password required, authentication required for wireless"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by brawd on 2010-02-03
Hi all,

I've spent all afternoon, mostly sorting out the wireless dongle to get online. I've just managed it. As a check I did a reboot and then got this sequence of demands.

Block comes up with:

     ENTER PASSWORD FOR DEFAULT KEYRING TO UNLOCK.

So I tried the passwords that I made up and got nowhere. Took the DENY option. What's a keyring anyway?

After the DENY I got another block:

AUTHENTICATION REQUIRED BY WIRELESS NETWORK.

So I tried the passwords I had made up and got nowhere.

The two passwords I had made up were 
1. For the user to use Ubuntu.
2. As part of configuring the wireless network.

After a bit of thought I typed in my WEP key number and got the wireless back, but I don't remember which one!

The thing is we can't type this 26 digit number in every time we want to use the internet. It never used to be like that. How do I get it to not ask for these things

I'm using Ubuntu 9.10 (Karmic)

regards,

brawd.

---

### Post by rustutzman on 2010-02-03
If you go in to the network connection and edit it's properties to automatically connect you shouldn't have to re-type the key.

Russ

---

### Post by Scunnered on 2010-02-03
**brawd**

You may find that the password for the wireless network is depends on who your ISP is. I am on Virgin Media broadband and my password is the one I agreed with Virgin when I first connected via a wireless connection.

It is as rustutzman says possible to automatically connect and should you wish to automate both login to the system and also to the wireless network it is possible. There is a certain insecurity in doing so but if you are the only one and are happy to do so then it is possible.

Hope this assists

---

### Post by nothingspecial on 2010-02-03
Just a possibly way off the mark thought.

If you have upgraded to karmic, but kept your home partition, or settings ...... and changed your password for the new install........then your keyring password will be your old login/sudo password.

A shot in the dark but who knows.

---

### Post by QuimNuss on 2010-02-03
If you don't want to use keyrings, you should've left it blank the first time you where asked to set a password for the keyring. Being that so, the wireless keys are stored unencrypted. However, you won't be asked the WEP key again if you store it on:

right-click on Network Manager icon, edit connections, wireless connections, there you choose yours, edit, input your user password, Wireless security. store your WEP key there and apply. 

Sometimes the WEP key is printed somewhere on the router, but you said you had it already, didn't you?

So, AFAIK, there's a password for the keyring (where applications' passwords are stored) and your user password, but I've never gone deep into keyrings, they are mostly handled automatically.

---

### Post by brawd on 2010-02-03
Thanks to all of you for helping, but I took the cop out and installed 8.04.
I'm not disappointed that I've gone back, (sort of). It's a very good operating system, certainly more than adequate for my needs.

It solved all my problems.

I had the feeling I'd shot myself in the foot when I initially configured this machine, and it seems that there was no simple back out.

Once again thank you all.

brawd

---

### Post by Tholley on 2010-02-03
If you use a wireless network, all you have to do is check the box "allow all users", under your network connection, and you would never be bothered with being asked for your Keyring password! 
 
there would have been no need to convert back!
 
Sorry you were not made aware of this before you changed back...

---

### Post by brawd on 2010-02-04
After reading the very helpful replies I (sort of) felt guilty, as though I had let everyone down so I re-installed 9.10.

It all works fine.


brawd

---

### Post by Tholley on 2010-02-04
> **brawd said:**
> After reading the very helpful replies I (sort of) felt guilty, as though I had let everyone down so I re-installed 9.10.
 
It all works fine.
 
 
brawd
 
Glad we were able to help!

---

