---
title: "WPA Personal password different from what I typed?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by revengeofthecow on 2009-08-15
The house I'm currently staying in has a wireless adapter. I have no problems connecting to it under Windows. When I'm in Ubuntu (version 9.04), the network is detected without a problem, and it prompts me for the password. I enter the correct password, and it tries to connect, but fails, and prompts a retype. In the dialog box it shows me what I'd "previously" typed in, but instead of the actual password, it shows "37682c7ca28f784a6852ad2ae82fbab4ca9a66731b95649e9 82a45dd3ae83bee
". I'm not entirely sure why, I know I have the correct password, but why isn't it storing and connecting properly? It has nothing to do with settings; I went into the Live CD and it did the same thing.

Any thoughts would be appreciated!

---

### Post by Bachstelze on 2009-08-15
It was probably converted from ASCII to hexadecimal. And sorry, I can't help you further, I know nothing about graphical networking tools.

---

### Post by revengeofthecow on 2009-08-15
I doubt it. The password is only 11 characters long, and hex would be shorter than that, right? Anyway it shouldn't be 40+ characters...

---

### Post by Old_Grey_Wolf on 2009-08-15
Not HEX. I took the one from my computer connection and converted the code to ACSII. It was not the password. Must be encrypted or something else.

---

### Post by Old_Grey_Wolf on 2009-08-15
> **revengeofthecow said:**
> Any thoughts would be appreciated!

Does the network have MAC filtering turned on?

I've tried to let someone connect to my Wireless, pulled my hair out, then when DUH, I have MAC filtering turned on.

---

### Post by revengeofthecow on 2009-08-15
I'll check.

---

### Post by revengeofthecow on 2009-08-15
No, there's no MAC filtering going on. That shouldn't be the problem, as I have no problems connecting to the wireless network under Windows.

---

### Post by jflaker on 2009-08-15
The code you see is an encrypted password.  So it isn't what you typed for a WPA password.

As for not being what you typed, you probably typed it wrong when you originally entered it or when you tried to connect---either way, there is a mismatch.

My suggestion is to re-enter you password at your accesspoint then edit your connection (right click the network icon and edit connection) and remove the current wireless  and then connect to the network again by entering your confirmed password.

I've fat fingered it on occasion...I just start over and all is well.

---

### Post by Old_Grey_Wolf on 2009-08-15
OP,

If you provide information on the wireless router/switch and network adapter in your computer, brand and model, then maybe someone could help.

---

### Post by billconan on 2009-10-14
i have exactly the same problem here.

after i clicked the wireless network icon, i saw the dialog ask for password:

authentication required by wireless network

passwords or encryption keys are required to access the wireless network "xxxx"

wireless security wpa & wpa2 personal


i'm pretty sure i entered the correct password, but it doesn't work. after awhile, the dialog pops up again and ask for password as if i have entered the wrong password. and if i check the box "show password", i can see what i have entered to the password text box has been changed to something else - i long encrypted string.

how to solve the problem?

---

### Post by lavinog on 2009-10-14
Is the router configured for wpa or wep?

---

### Post by coastertal on 2009-10-18
I'm having the same problem.  I even copy and pasted my password straight from my routers info page and it's still doing the same thing.

I'm at a total loss but I'm also a super squeeky clean newbie.  I've only had ubuntu installed for 2 days.  Couldn't even get it to install on my clunker desktop, using it on my laptop only right now.

---

### Post by anewguy on 2009-10-18
I'll be the first to admit I haven't set up wireless in quite a while, and haven't had wireless now for about 4 months (I'm stuck on dialup now, when I used to have cable broadband!).  However......

Not sure how much applies now, but you used to have to be sure you specified whether it was wep, wpa/txxx (I don't remember for sure - tkp?? - I think they use terms more like personal and enterprise now) or wpa/aes, wpa or wpa2, using a passphrase or a password, and whether what you were using was in hex or in ascii.  You used to be able to define all this at the time network manager asked for the password/passphrase.  You need to be sure it all matches or you'll get screwy results like you are seeing.  You may be copying/pasting the password/passphrase, but you have to be sure to match all of the type - including whether 40 bit or 128 bit.  If need be, sometimes you have to revert to iwconfig (I *think* that was it) to manually set some of the things up.

Don't know if that can help you in your quest or not - just remember it's not just the "password" that has to match.

Dave :)

---

