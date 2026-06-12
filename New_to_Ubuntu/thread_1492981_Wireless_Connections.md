---
title: "Wireless Connections"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by InsaniaEx on 2010-05-25
So, yeah. First problem solved. Next is to do with wireless, firstly, it doesn't show up, on my laptop (Windows 7 OS) or my netbook (ubuntu). So I decided to start with the netbook. Connect to hidden network, as the list given by Network Manager doesn't show my network, but does for others, neighbours etc. So I put in the password (WPA & WPA2 Personal security) begins trying to connect, then appears again with Authentication required, with some long password already there, 45b19...etc. I'm using Network Magic on my main computer, and the password I set is the one I used first. I don't remember encrypting, or whatever you do, to make it hidden. But it's definitely there because I am connected to it on this computer.

---

### Post by nhasian on 2010-05-25
if i understood you correctly, your wifi adaptor is working and the network manager lists several different wifi networks, but you are having difficulty connecting to a hidden network?

do you know what type of security the hidden network is using?  WEP, WPA, WPA2, open, etc?

---

### Post by InsaniaEx on 2010-05-25
I realise now that was a lot in pretty much 3 sentences. WPA2.

I try to connect to it with Connect to Hidden Network. And it shows up on list while trying to connect, and the blue bar shows that its strength is zero. And then it asks for authentication, with the wrong password in the...entry box. So I fill in the right one, but the authentication just pops up again with wrong password and all the frustration it entails.

---

### Post by adamk918 on 2010-05-25
> **InsaniaEx said:**
> So, yeah. First problem solved. Next is to do with wireless, firstly, it doesn't show up, on my laptop (Windows 7 OS) or my netbook (ubuntu). So I decided to start with the netbook. Connect to hidden network, as the list given by Network Manager doesn't show my network, but does for others, neighbours etc. So I put in the password (WPA & WPA2 Personal security) begins trying to connect, then appears again with Authentication required, with some long password already there, 45b19...etc. I'm using Network Magic on my main computer, and the password I set is the one I used first. I don't remember encrypting, or whatever you do, to make it hidden. But it's definitely there because I am connected to it on this computer.
OK, so you're 100% sure you made *zero* typing errors when entering your key?

---

### Post by InsaniaEx on 2010-05-25
I am 100% sure, I ticked show password, and I have entered it numerous times.

---

### Post by InsaniaEx on 2010-05-25
It would help if someone actually gave me some sort of solution xD

---

### Post by anewguy on 2010-05-25
> **InsaniaEx said:**
> It would help if someone actually gave me some sort of solution xD

Let's see - you started this thread about two hours ago.  This post was made 40+ minutes ago.  You do realize this is an all-volunteer forum?  Consider if you will that the forum guidelines state not to bump a thread (i.e., post a message in a thread just to move it back to the top of the list) for 24 hours?  So, the first suggestion is to be patient.  You'll get the help you need eventually.  However, a post like this one will get you nowhere and get you enemies instead.

So, now I'm a suggestion or 2:

- when you set up the router whose connection you are attempting to make (the one with the hidden SSID), did you specify a passphrase or a password?  This could be were the difference is coming up with a hex string you say isn't your password.  Since you said you have this problem with both a Windows 7 notebook and an Ubuntu netbook, it suggests the problem is at your router, since you see networks (wireless adapter must therefore be working) and the router is really the only thing in common between the 2 systems running different OS's.

- something I normally suggest when this type of problem is encountered:

....in network manager, click on edit connections and clear any connections listed there for the network you are trying to connect to.  Sometimes these old connection definitions seem to step on things when you are trying to "correct" a connection

....temporarily set your router for an open network -> no encryption, no MAC list, no hidden SSID, just wide open.  Can you connect now?
......if so, try adding in just WEP temporarily until you get that to work
......now, change WEP to your WPA flavor and put in a made-up hex string password, then match the WPA flavor and password via network manager/edit connections/add
......once you get that working, then hide the SSID at the router
......add MAC filtering at the router if you want another layer of security.

The whole idea is to take away everything, then add 1 thing at a time and get it working, then stepping up to the next thing.  Some routers don't support the same flavors of WPA, especially older ones (or some DSL modems/wireless routers for me).


Remember, we've all been there, we know the frustrations.  Being patient is the key to ever getting help here.

Dave ;)

EDIT:  Should also ask what release of Ubuntu you are running, hopefully current, as some of the really older versions didn't have wpa-supplicant running by default.

---

### Post by InsaniaEx on 2010-05-25
Nevermind, my sister reset the router the other day, meaning it reset its name aswell. I feel like an idiot now, spent all day looking for a non-existent network.

---

### Post by ScottinSoCal on 2010-05-25
> **InsaniaEx said:**
> I feel like an idiot now, spent all day looking for a non-existent network.

If we didn't occasionally do things that make us feel like idiots, we'd get great big swelled egos and be impossible to live with. Don't sweat the small stuff.

---

### Post by nhasian on 2010-05-25
great, glad you got it working.  don't forget to mark your thread solved.

---

### Post by anewguy on 2010-05-25
Don't feel bad - I do "dumb" stuff all the time -> just see some of my threads on the forum!

And remember:  "I thought I made a mistake once but I was mistaken"

Welcome aboard.

Dave ;)

---

