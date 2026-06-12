---
title: "[SOLVED] Unwanted applications run at every login"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by perce on 2008-12-22
I've just installed Xubuntu on a very old computer, and everytime I log in it runs a terminal and update-notifier, despite the fact that I always close the terminal before logging out, and that I unchecked update-notifier from the list of applications to be run at every login. How can I fix this?

Thank you

---

### Post by jimmy the saint on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=854557&highlight=lighter+side+xubuntu](http://ubuntuforums.org/showthread.php?t=854557&highlight=lighter+side+xubuntu)

the answer is in that thread

---

### Post by perce on 2008-12-22
I've already tried the configuration suggested in that thread, but it doesn't worm

Thank you

---

### Post by RomanIvanov on 2008-12-22
May be you saved session in Quit window and now you always have this applications to run. this behavior is set by default after installation.

how I fixed this: 
1.Close all applications
2. Applications -> Quit
3. In Quit dialog check "Save session for future logins"
4. Restart

5. Applications -> Quit
6. In Quit dialog UNcheck "Save session for future logins"
7. Restart

Enjoy Xubuntu!

---

### Post by perce on 2008-12-22
No, that box is unchecked, and moreover I always close update-notifier before logout

---

### Post by nandemonai on 2008-12-22
> **perce said:**
> No, that box is unchecked, and moreover I always close update-notifier before logout

They're saying that initially your session was indeed saved as that is the default behavior.

Follow those steps and you should be good to go.

alternatively you could manually delete the old session files from ~/.cache/sessions where they are stored.

---

### Post by perce on 2008-12-22
Thank you very much to you all! I didn't understand RomanIvanov's post correctly the first time, and many thanks to nandemonai for pointing me out that I was missing something.

---

### Post by RomanIvanov on 2008-12-23
Please support idea to uncheck it by default to avoid misunderstanding(problems): [http://brainstorm.ubuntu.com/idea/16756/](http://brainstorm.ubuntu.com/idea/16756/)

---

