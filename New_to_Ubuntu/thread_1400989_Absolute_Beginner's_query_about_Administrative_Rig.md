---
title: "Absolute Beginner's query about Administrative Rights"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by slowdiver on 2010-02-07
[FONT=Tahoma]Hello folks. This is only my second post here, please bear with me. Just before Christmas I bought a Toshiba NB100 which came preinstalled with Ubuntu Remix (not sure of the release number, or indeed if I have the correct distro, this is absolutely my first "serious" venture into Ubuntu, I have tinkered with Knoppix and Ubuntu in the past using live discs, but the netbook was deliberately purchased so I could get my "feet wet" so to speak).

I've been pottering about with the netbook, which seems to work perfectly fine so far. However I have a problem. The machine was bought from a local chain, as an "end of range" model, at a discounted price. Accordingly, the o/s was already set up and preconfigured by the store staff before I bought the computer. Which means that there is an administrator's password on there, that they have neglected to tell me and which is pretty much hampering me doing anything. I'm currently showing 160+ updates on the update manager, but I can't action a single one as each time I try to run the application it asks me for the password.

Sorry for rambling a bit, but I hope you can see my problem. As said, I'm a complete Linux novice (although I have over a decade's experience with Windows and nearly 3 decades experience with computers in one form or another, so I'm not totally computer illiterate).

If anyone can advise me if I can a) change/remove the password authentification, WITHOUT KNOWING the current existing pass, or b) how I can go about finding out what the pass is, if option a) is not viable. 

I'm very cautious about trying anything more ambitious at this stage because I don't want to get halfway into trying anything only to be halted by something so simple.

Any help or suggestions would be most welcomed. I have tried contacting the store that I purchased the machine from, but they can't help me (it's a large high street electrical retailers rather than a computer specialists so I suspect that whoever set the machine up initially simply followed printed instructions and didn't note down the pass anywhere).

Many thanks in advance,

Chris. 
[/FONT]

---

### Post by mushwars on 2010-02-07
it is asking you for YOUR password even though it says root password. So just enter the password you use to login.

If you really want to have a root password, it is scrambled and you can set it by doing this, though you dont have to.

```
sudo passwd root
```
when it asks you for a password type in your LOGIN password.

cheers.


[ps. it asks you for a password to protect your computer from someone doing damaging thigs, such as deleting important files or installing programs that the administrator doesnt approve of possibly]

---

### Post by slowdiver on 2010-02-07
Thanks for that. Unfortunately when I first boot up the machine, it automatically logs in to "user1". There's no password input at that point, and no other passwords other than the pre-Ubuntu passes that it asks for immediately when the machine is switched on (I set these myself in the BIOS to stop anyone even getting in there). The problem is that the machine's been configured to go straight "on" if that makes sense, rather than taking me to an optional login screen.

I suspect that it was an ex-display machine and has been set up in this fashion to allow customers to restart or generally fiddle about with the computer without a member of staff having to keep inputting a login password.

Thanks again for the suggestion though :)

---

### Post by Iowan on 2010-02-07
[This]("http://www.psychocats.net/ubuntu/resetpassword") may be helpful. It'd be easier with a Live CD, but there are alternatives. Have you tried using **sudo** without a password?

---

### Post by switch10 on 2010-02-08
I would bring it back to that store and ask them what the password is, and explain that it is useless without it.  

You could always just reinstall Ubuntu netbook remix.  This may be the better option anyway, so you can configure the system how you want it (ie your name instead of "user one", have your own password, etc.)

---

### Post by slowdiver on 2010-02-08
Iowan that did the trick!  Thank you very much :)

---

