---
title: "Karmic graphic problem"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by folabiklan on 2009-12-10
Hi pls i recently installed 9.10 on my pc and it wasnt ok in my opinion. Anyway installed some debs manually thru gdebi. When i wanted 2 reboot i found that all d button 4 power did not respond. As it is a desktop i did a hard stop n switched off d power. Wen i booted d pc i found that it bootf, showed the splash ubuntu page and went into a terminal page on 1 side. It did not boot d graphical display.

Av tried 2 run startx, stop gdm n ran dpkg reconfigure but still nothing works. Wen i typd exit it goes back 2 d login page.
Help me. Or is d system gone permanently?

---

### Post by 5nak3 on 2009-12-10
I have a very hard time understanding what you are saying as the language used is not proper English. 

In any case, I will try and assist you. If what I understand is correct the system if throwing you to a terminal login, to get the graphical login you need to press ctrl+alt+f7.

If you rewrite your problem properly I'm sure that more people could help you.

---

### Post by folabiklan on 2009-12-10
Oops sorry. I meant that i run karmic and i put off my computer without shutting down properly. I just switched off at the mains. When i boot the pc now i get thrown into a terminal window as you said. I have tried ctrl alt f7 but it did not work. It gives a error message but i cant post it obviously. I need help my install cd is damaged so i can't even reinstall

---

### Post by 5nak3 on 2009-12-10
I'm not an expert on this matter, and ideally an error message would help.

While I do not recommend making any changes until someone who is more qualified has a look at the topic. I would say that if there was a way to burn a new live cd as you say your current one is damaged you could try and log into the computer and mount the hard drive via the live cd to save any important files you may have.

In doing so, backing up the data would mean should you need to do a clean install you have the important files already backed up.

---

### Post by realzippy on 2009-12-10
...is it a root terminal you are dropped to?
Run 
**fsck**

...press"Y" if asked..

---

### Post by folabiklan on 2009-12-10
None of d suggestions worked. Back 2 windows i guess. When u pple figure out hw 2 take care of dis then i will order a cd n use

---

### Post by sandyd on 2009-12-10
> **folabiklan said:**
> Oops sorry. I meant that i run karmic and i put off my computer without shutting down properly. I just switched off at the mains. When i boot the pc now i get thrown into a terminal window as you said. I have tried ctrl alt f7 but it did not work. It gives a error message but i cant post it obviously. I need help my install cd is damaged so i can't even reinstall
if it says something along the lines of "filesystem unmountable"
follow the instructions onscreen to login.
then type in
```

fsck -y

```

---

