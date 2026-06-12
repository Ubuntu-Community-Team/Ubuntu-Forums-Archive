---
title: "where is the downloaded file !   :)"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by mahmoodkamal on 2010-09-27
i like firefox, but just to try, i downloaded chrome and installed it. It showed up in Applications>Internet. Next time when i logged in it was no longer there.

---

### Post by amauk on 2010-09-27
did you install chrome through the package manager?

---

### Post by Chesamo on 2010-09-27
It might have gotten taken off the Main Menu (glitch?). Try running ```
chromium-browser
``` if you installed it from the repositories, or ```
chrome
``` if you installed it from Google. (These are both Terminal commands)

---

### Post by jtarin on 2010-09-27
Do you have more than one account to login to?

---

### Post by JohnHeikkila on 2010-09-27
This has happened to me, too. I think I found it from Applications-->Other
Search through the Applications.

---

### Post by mahmoodkamal on 2010-09-27
1) I have more than one account on my system
2) I tried to run both the commands as mentioned by Chesamo but chrome was not found
3) Application > Others is not in my menu.

I tried to use Places > Search for Files to find chrome but could not find it. I installed it from the website. It asked me to 'Open with Gdebi Package Installer' which I agreed and installed.

---

### Post by da burger on 2010-09-27
Did you install it from the repos or from the google website?

Also I believe the command for chrome if you get it from google is google-chrome (I can't be sure because I use chromium).

---

### Post by mahmoodkamal on 2010-09-30
I have reinstalled chrome from the repository through Ubuntu Software Center. After installation it appeared in Applications>Internet. On my next login, it was no longer in the menu, although if I check through the package manager, it is installed.
 
How can make the Chrome appear on my Applications>Internet menu?

---

### Post by jtarin on 2010-09-30
System>Preferences>Main Menu....Left column select "Internet". Right side select "+ Add New Item".

---

### Post by mahmoodkamal on 2010-10-01
Thanks jtarin. I managed to solve the problem.

---

### Post by jtarin on 2010-10-01
Excellent...mark the thread as solved when you can. :)

---

