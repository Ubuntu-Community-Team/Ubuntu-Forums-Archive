---
title: "Can't connect to SBC Yahoo ISP!"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by TheThinker on 2007-10-25
Okay everyone, I'm stumped. I have internet access, but I can only connect to my college (they give internet access to students, and so my college acts as its own ISP). I'm using GnomePPP, and the terminal command "connect to the ISP configured as provider" works as well in this regard. But Why, oh WHY can't I connect to SBC Yahoo?!

I did the following to try to get this ISP to accept me:
1) Used PPPconfig and entered the exact number, DNS server (as well as secondary DNS server), password and username, set authentication to PAP- This didn't work for SBC Yahoo. Even changing the authentication to CHAT and others gets nothing.

2) Used Wvdial and set it to Stupid mode = on, Carrier Check = off, entered correct number, password and username. In the end, it gives me bupkiss, and an error that says that my username, number and password are invalid (even when I get rid of the brackets). Strangely, GnomePPP, which uses Wvdial as its backend, works like a charm but only on my college ISP, not SBC Yahoo.

Has anyone succeeded in logging into SBC Yahoo through either GnomePPP, wvdial, or regular PPP in the terminal? If so, HELP ME PLEASE! I am so frustrated with this dumb ISP, and their customer service sucks! Mind you, this is dial-up.

---

### Post by TheThinker on 2007-10-27
Okay, it turns out that SBC Yahoo is really AT&T Yahoo now (the monster is growing it seems) and I chatted with their tech support using my University as my ISP. From what little I gathered, they have no clue what I'm talking about; all they knew was that Yahoo didn't support Linux and thus assumed that it was impossible to get me connected. Thanks for nothing, Yahoo. They couldn't even tell me about TCP/IP settings for windows and authentication methods! I take it that they know NOTHING about how their windows software works. 

Well, at least I got wvdial working now. It turns out that the password, username and phone number entries had this ---> ; preceding them. I deleted that character, added a few other lines to the configuration, such as Login Prompt, saved and exited. Typing "wvdial" in the terminal worked! However, it quit pretty much the same way GnomePPP did as mentioned in my previous post, saying "Disconnected. A modem hung up."

I'm getting really frustrated with this. Is it that the SBC Yahoo software CD for Windows has some sort of funny authentication program that my Ubuntu Gutsy lacks? That would explain why I'm able to login into my University instead of Yahoo. What I can't understand is why the modem would simply hang up; shouldn't I be able to hang up my modem myself, instead of someone from outside doing it?

Furthermore, is it really such a pain for these ISPs to provide technical support for Linux users? I'm no programmer, but I'd venture to say that connecting to the internet through Linux is actually quite easy in my experience. But with Yahoo, what gives?!

---

### Post by TheThinker on 2007-10-29
I had a big "Aaaaha!" moment today when I finally got a tech-helper from AT&T Yahoo who knew what I wanted. It turns out that Yahoo uses a protocol called PPPoE, which is licenced by AT&T it turns out. However, the Ubuntu repositories have this protocol on hand so I'm going to give it a test-drive on my modem to see what happens. 

Here's hoping that this thread will be marked "Solved"!:)

---

