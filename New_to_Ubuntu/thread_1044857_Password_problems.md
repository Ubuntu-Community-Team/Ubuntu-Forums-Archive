---
title: "Password problems"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by scheibo on 2009-01-19
I've recently installed Ubuntu 8.10 on a new Sony VAIO CS190 laptop and I'm having a bit of trouble with my password. The first problem resulted from me choosing the wrong keyboard layout (Canadian vs. USA), and I ended up fixing it by reading [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html) and changing my 18 character password to the letter 'e'. Once I was able to get on, I realized my keyboard layout was off, changed my layout to USA, changed the password to a different 18 character password and was on my merry way.

However, a problem occurred when I was attempting to install the updates on the computer. When I attempted to install, it asked for my password as expected, and I typed in the exact same password that I used to log in - no use. It denies it and says it is the incorrect password. I tried doing the quick hack where I logged into a root shell account in order to change it, but it didn't register this change. I'm completely at a loss for what to do - the computer allows me to log on using the password I created, but refuses to let me install updates when I attempt to use the same password. Very frustrating!

Any help would be appreciated!

EDIT: Also, when I try to edit my password through the GUI, it appears to hang when I press the 'Authenticate' button, and when I try to edit through the terminal it continues to say I've entered the incorrect password (which I haven't).

**EDIT2: **This kind of seems like a monologue, but I thought I would update anyone who reads this. I appear to have solved the problem by following this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) and changing the password to something else. However, I would *love* to know *why* my password didn't work in the first place! Thanks.

---

### Post by cariboo on 2009-01-19
I would assume, because you used the Canadian keyboard, that there were some characters in your original password, that weren't available, using the US keybaord.

JIm

---

### Post by scheibo on 2009-01-19
Yes, and as I mentioned, I realized this, changed my keyboard back and solved my first problem (not being able to log in). 

The second problem (being able to log in, but once logged in, not being able to use the password I logged in with to do anything else!) seems unrelated to the keyboard, but instead to possibly password length or complexity. Is there any restraint on the characters you can use in a password on Ubuntu? I would assume not, but that seems to be the case?

---

