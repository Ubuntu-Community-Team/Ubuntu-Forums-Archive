---
title: "What is the use of Passwords and Encryption Keys?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-27
There is an option named  **Passwords and Encryption Keys **in Applications>Accessories..And i have never used it before..What is the use of this?

---

### Post by Gixxy on 2010-03-27
> **getyourkarthick said:**
> There is an option named  **Passwords and Encryption Keys **in Applications>Accessories..And i have never used it before..What is the use of this?

It stores passwords and encryption keys... duh  :D

It is sort of like a password wallet... stores wifi keys, browser keys stuff like that...

---

### Post by jmr423 on 2010-03-27
I would recommend not storing your passwords like this. Writing them all down on a peice of paper is your best bet.

---

### Post by Didius Falco on 2010-03-27
This should answer all your questions: [http://library.gnome.org/users/seahorse/stable/index-info.html.en](http://library.gnome.org/users/seahorse/stable/index-info.html.en)

I hope it helps...

Regards,

Didius

---

### Post by Gixxy on 2010-03-27
> **jmr423 said:**
> I would recommend not storing your passwords like this. Writing them all down on a peice of paper is your best bet.

Ya, post-it notes on the monitor or under the keyboard are your best bet to keep your passwords secure.... [-X

---

### Post by QIII on 2010-03-27
> **Gixxy said:**
> Ya, post-it notes on the monitor or under the keyboard are your best bet to keep your passwords secure.... [-X

I don't think the poster was suggesting that, exactly.

I wouldn't use an application on a computer to store passwords for that computer.  Everyone knows where the files are stored (you could use an application that stores a ghost, I suppose).  But it's still not a good idea.

But writing them down is a good idea.  Since you should not be using one password for everything from soup to nuts (and I'm sure you are not doing that, right?), a piece of paper in your wallet, for instance, would be good.  Two dozen usernames and passwords are hard to keep track of in your head.  Especially when you are changing them periodically (which you are doing, right?)

If you have a "junk drawer" near by (everyone has one, right?), you could toss an inconspicuous little notebook from your local office supply store there.

Some security folks say you can even keep it in a messy drawer in your computer desk.  You could put an 8 1/2 x 11 piece of notebook paper in a messy folder where it would be overlooked by a nervous ne'er-do-well.  Just don't use a big black marker and label it "Passwords" on the front.

---

### Post by Paqman on 2010-03-27
You can use it to create an encyption key. If you want to encrypt a folder, for example, you can create a key, and if you install the package seahorse-plugins, you'll be able to encrypt a folder from a right click. No need for 3rd party software like Truecrypt, Ubuntu has this stuff built in.

---

### Post by Paqman on 2010-03-27
> **Gixxy said:**
> Ya, post-it notes on the monitor or under the keyboard are your best bet to keep your passwords secure.... [-X

Writing your passwords down next to your machine is perfectly acceptable for prevent an external attack, although it obviously won't be any use against casual prying. If a determined adversary has physical access to your machine, the fact that they don't have the passwords won't stop them.

---

### Post by Gixxy on 2010-03-27
chances are that the average person standing in front of your computer 
(if they had the chance) would have no idea how to get the passwords out of your linux wallet but they would know how to look for your passwords in your draws or under your keyboard. I never save browser passwords but in general it is not a security issue. Physical access for someone that knows what they are doing = death.... but this isn't that type of a question....

---

### Post by 3rdalbum on 2010-03-27
The passwords and encryption keys are not stored in cleartext, they are stored in encrypted format. The master password is usually the same as your password, and the keyring is unlocked when you log in.

It's not always practical to use "a piece of paper" for all the contents of your keyring. Your wifi encryption key is usually so long and so random-looking that it's a pain to type in every time you want to connect. Also, services like Ubuntu One store their passwords in there when you 'authorise' the computer. You wouldn't want to be authorising and deauthorising your machine all the time, it requires a trip to Firefox to authorise.

---

