---
title: "How do I remove the password I have setup at login?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by tegnoto89 on 2009-05-19
I want to use a bios password instead, and just have ubuntu boot straight to my desktop.

---

### Post by freak42 on 2009-05-19
system->administration->login window-> security -> tick enable automatic login

hth

---

### Post by lisati on 2009-05-19
If you're the only person to be using your computer, then there'll probably be no objections raised to this: have a look at System->Administration->Login Window, and click on the "Security" tab. There should be an option "Enable automatic login"

EDIT: Beaten to it by freak42 :):)

---

### Post by mcduck on 2009-05-19
> **tegnoto89 said:**
> I want to use a bios password instead, and just have ubuntu boot straight to my desktop.

You can't remove the password, as it's needed for other things than just logging in (all your administration tasks require you to confirm your identity by typing the password, removing that would make your system highly insecure).

If you want, you can of course set the login to automatic so you won't need to give the password every time you log in. To do that go to System/Administration/Login Window, and on the Security-tab enable the "Enable Automatic Login"-option and select the user to log in automatically.

If you enable the automatic login, you should also set your keyring password to empty one, otherwise you will need to type the keyring password every time you log in (with normal it's automatically unlocked at the same tiem you type your login password). That can be done by going to Applications/Accessories/Passwords and Encryption Keys, on the Passwords-tab right-click the "Passwords:login"-entry and select "Change Password", type in your old password but leave the fields for new one empty.

By the way, I just have to mention that BIOS passwords are highly insecure and can usually be reset in about 10 seconds using jumpers on the motherboard. And even without those jumpers removing CMOS battery and cutting the power from the machine will clear the password in 15-20 minutes.. So if you need to protect your system from anybody else than computer-illiterate family members BIOS password isn't the way to go.

---

### Post by expcman on 2009-06-14
"Oh, what a relief!"  Ever since I installed my Ubuntu 8.04 (last fall) I have been wondering about being nagged to "sign in" by giving my "i.d." and "password," something I do not have to do when booting up into my Windows OS ... yes, I am into dual booting, hoping in time to transition over into Linux - on this, "so far so good"!  But to-night I decided to see if I could find a way to change this boot process, and happily discovered this thread, which told me exactly what I needed to know!  So "thank you, thank you, thank you," a pattern used by my son when he was trying to express the sincerity of his appreciation!  Happily, it was quick and simple and easy, which reminds me of what one of my language teachers used to say, "Men, it is easy ... when you know how!"  It is the "learning how" that is difficult! So thanks for making this one easy!  Whew!!!!  Most sincerely, C. F. Jacks

---

