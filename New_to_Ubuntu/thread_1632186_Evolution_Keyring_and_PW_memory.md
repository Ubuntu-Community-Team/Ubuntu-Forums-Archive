---
title: "Evolution Keyring and PW memory"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by holadebob on 2010-11-27
I am at my wits end trying to understand 10,000 posts on keyrings and Evolution.

Can someone just make it simple for a stupid old man? I am trying to set up Evolution, and it sort of works, except every time I start Evolution, it asks me for my password, and I have all the blocks checked to remember it. 

The other thing is that I have to go through this mouse click challenge to get rid of a window labeled Unlock Login Keyring-enter password to unlock your login keyring. I'm sure 90% of you out there have heard of a keyring. I don't understand Keyrings. I remember a token ring by Big Blue many years ago, but I don't think this is that.

Just tell me how to get rid of these thorns and I will fade away into the distance like I have been trying to do. If it ain't got a simple fix, just tell me and I'll throw the stupid program away.

Thank you,
Bob

---

### Post by grey1beard on 2010-12-21
Hang on in there Bob.
I can't offer any solution yet, being another old fogey with very slow brain and with the same problem.
I've moved it down the list of niggles I need to sort out, but I'm so impressed with my moving over from windows that I'm sure someone will throw us a life line.
I've not got as far as you in trying to sort it, but perhaps this bump will help.
Regards
John

---

### Post by mcduck on 2010-12-21
The keyring is used to store different passwords, encryption keys and such from all the programs, keeping them secure in one place and encrypted when you are not logged in.

If you use a login password, the keyring should unlock automatically for you when you log in. With automatic login this doesn't happen, and you need to input the keyring password to unlock it when some program tries to access the keyring first time. (This also happens if your login password and keyring password are different)

So, the problem with Evolution not remembering your password is actually result from you not unlocking the keyring, so it can't access the password it has saved.

Anyway, there are couple of ways to solve the problem, depending on what kind of setup you prefer. Do you want to use automatic login, or do you prefer using a password login?

If you use a password login, all you need to do is make sure both login password and the keyring password are the same. This is what you should have when you install Ubuntu, but if you change your login password you may need to also manually change the keyring password as well.

..and if you prefer automatic login, you can simply remove the keyring password. This allows programs to access the keyring without having to unlock it in any way, but on the other hand it also makes the Keyring to store the password in unencrypted format. Which of course doesn't make any real difference in security if you use automatic login.

Anyway, to change (or unset) the keyring password go to System/Preferences/Passwords and Encryption Keys. Right-click on the "Passwords:login"-keyring, and select "Change Password" from the popup menu. Type in your old password, and either set the new one to same as your current login password is, or leave the fields empty, depending on if you use password login or automatic login.

(And yes, it not the same as token ring. Good for us, I'd say. I'm happy to never have to work with *that* any more :D)

---

### Post by wkralt on 2010-12-21
Thank you mcduck for the concise and clear explanation. This grey head has also struggled with the challenges that precipitated Bob's sentiments! Another question then, seeing I have such a knowledgeable resource in you. Is Ubuntu, as an operating system,  really 'safe' from viruses and Internet attack as I understand people in the forums to frequently make reference to, or is this security really a function of the Keyring and Passwords we have just been talking about???


Cheers,
Bill

---

### Post by mcduck on 2010-12-21
The short answer is "yes". :)

There are practically no Linux viruses around, and most of the ones that exist are either just proof-of-concepts, never seen in the wild, or target very specific setups with outdated software. (Like the only really big Linux worm, Slapper, that targeted server computers running outdated version of Apache).

And the default install of Ubuntu has no running services that would listen for incoming network connections, making it secure enough  to not even need a firewall (there would be nothing for a firewall to block).

Anyway, it's a complicated question and the security in Linux doesn't come form any single thing or feature, it's pretty much a question of security features layered on every level of the OS, strict use of permissions (even if it might sometimes feel inconvenient to new users), and of course the large amount of developers that can help to find and fix any bugs and security problems.

I suppose it's much easier to get security issues fixed when anybody with skills can look for them and suggest fixes, without having to worry about what releasing a certain fix might do to corporate image or simply being not able to access the code in the first place.

..not to forget about the meaning of having a package management system that gives you all the software you need, downloaded from trusted sources maintained by Ubuntu's developers, instead of getting stuff from random web sites and such.

Of course even a good Linux setup isn't completely invulnerable. The biggest threats are still there, user himself, and physical access to the computer. Both being things that are outside of what any software can really help with.

But I'm not a security expert of any kind, and you'll probably want to read this (rather long) post about the security in Ubuntu: [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812"). Some of the stuff is complicated, some is only relevant on servers and some only makes sense if you work for a secret government agency or happen to be really paranoid. But there are good answers and explanations for a normal desktop user as well.

---

### Post by wkralt on 2010-12-21
> **mcduck said:**
> The short answer is "yes". :)

There are practically no Linux viruses around, and most of the ones that exist are either just proof-of-concepts, never seen in the wild, or target very specific setups with outdated software. (Like the only really big Linux worm, Slapper, that targeted server computers running outdated version of Apache).

And the default install of Ubuntu has no running services that would listen for incoming network connections, making it secure enough  to not even need a firewall (there would be nothing for a firewall to block).

Anyway, it's a complicated question and the security in Linux doesn't come form any single thing or feature, it's pretty much a question of security features layered on every level of the OS, strict use of permissions (even if it might sometimes feel inconvenient to new users), and of course the large amount of developers that can help to find and fix any bugs and security problems.

I suppose it's much easier to get security issues fixed when anybody with skills can look for them and suggest fixes, without having to worry about what releasing a certain fix might do to corporate image or simply being not able to access the code in the first place.

..not to forget about the meaning of having a package management system that gives you all the software you need, downloaded from trusted sources maintained by Ubuntu's developers, instead of getting stuff from random web sites and such.

Of course even a good Linux setup isn't completely invulnerable. The biggest threats are still there, user himself, and physical access to the computer. Both being things that are outside of what any software can really help with.

But I'm not a security expert of any kind, and you'll probably want to read this (rather long) post about the security in Ubuntu: [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812"). Some of the stuff is complicated, some is only relevant on servers and some only makes sense if you work for a secret government agency or happen to be really paranoid. But there are good answers and explanations for a normal desktop user as well.
Thank you! I appreciate the reply... and it was helpful.
Bill

---

### Post by holadebob on 2011-02-27
Thank you McDuck and wkrait! I was just reviewing my posts and found your replies, sorry for the long delay.

Nice clear explanation and now I understand. 

I'll (finally) mark this solved and go play with Evilution again.

Have a good one.
Bob

---

