---
title: "Default Keyboard Layout at Login"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by dmaxel on 2010-01-03
Hi everyone. I have a little problem concerning my keyboard layouts. I installed Ubuntu using Wubi while I was in Germany. Apparently the system installed in English (as I specified), but originally used the keyboard layout for Germany. I logged in, added my US keyboard layout, and deleted the German one. After applying that, I also clicked the button to apply system-wide. Thing is, it's gone everywhere except at the login screen, where the Germany layout is selected by default. Therefore I have to change it to the US layout every time I log in, otherwise it'll log in with the German layout and will add that layout again to my list of layouts. Is there any way to completely get rid of the German layout? Or at least make the US layout default at login? Thanks for your time.

---

### Post by fritsmartfu on 2010-01-03
Hi dmaxel!
As a Dutchman in Hungary I had abpout the same problem: Living in Hungary I use a notebook with an Hungarian keyboard lay-out with Ubuntu 9.10 in Dutch.
I got always the American keyboard lay-out, untill I found during startup a bottom line where I could choose for the keyboard lay-out. 
After setting the keyboard lay-out there my problem was solved!

I hope that this solves your problem too.

Greetings, Fritsmartfu

---

### Post by dmaxel on 2010-01-03
Thanks for your quick reply fritsmartfu.

The thing is, the problem lays right there. I click on my username so that I can type in my password, and at the bottom comes the bar with the settings such as Language and Keyboard Layout. Language is correct, and never had any problems. However, the keyboard layout is always set to "Germany", so I have to set it back to my US layout. I have to do this every time I try to login. And even though I delete the Germany layout in my account and click on "Apply system-wide", it always appears at the bottom whenever I try to login, and therefore have to change again.

EDIT: Apparently it helped now when I used "sudo dpkg-reconfigure console-setup". Germany still shows up at login, but only if I want to change it from my US layout. :D Solved.

---

