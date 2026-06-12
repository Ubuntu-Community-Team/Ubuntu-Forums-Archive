---
title: "Logging into sites  with firefox"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Georgia boy on 2009-12-26
Hi. I'm having trouble logging into sites on FireFox now.Version is 3.0.16. I was able to log onto my bank site earlier today then all of a sudden wasn't able to. Had the bank trying to help me out and they had given me several passwords and still no luck. Went to the Windows side and got hold of the bank again and they gave me another password. It worked in the Windows FireFox. I came back here with the same password that worked in Windows and tried it and no go. I even tried other sites that I have to log into and it wouldn't let me do that with them either.I'm not able to log onto any of the sites here. I just tried logging onto my IP site also. Same results.
Any ideas as to what the heck is going on here? As I said, when I go to my Windows side I can log in with no problems.](*,)

Thanks

Tom

---

### Post by lovinglinux on 2009-12-26
Have you checked your cookies preferences?

Have you tried to log in using a clean profile?

To create a new profile, close Firefox and run this on a terminal:

```
firefox -P
```

It will open the Profile Manager from where you can create and start a new profile. If it works, then we can narrow the problem down to profile settings or extensions.

---

### Post by Georgia boy on 2009-12-26
> **lovinglinux said:**
> Have you checked your cookies preferences?

Have you tried to log in using a clean profile?

To create a new profile, close Firefox and run this on a terminal:

```
firefox -P
```

It will open the Profile Manager from where you can create and start a new profile. If it works, then we can narrow the problem down to profile settings or extensions.


I got it done!!!! Thanks. After trying all afternoon to get it I finally figured out what had happened. Some how the accept cookies especially for the third party got unchecked. Don't remember what I had done but now that I have them checked I was able to go and log into the my IP provider home, OOo, and the bank. What a mess I tell you. Someone thought that I had a trojan and kept telling me to do a virus scan. Told them that I was using Ubuntu not Windows while doing all of this. Also had one of them trying to tell me to add them to the trusted sites in FireFox, but couldn't figure out what she was talking about. Went through all sections of the bar and didn't see anything on adding a trusted site anywhere.

I had figured it out finally before coming back and checking for any replies. Really do appreciate the help though. If I hadn't figured it out I would have been looking for replies and using them. Believe you me.

You can't believe how I was getting ready to pull my hair out. Don't need to do that because it's already turning gray on me as it is.:)

Hope that everyone is having a wonderful Holiday! I'm going to wish everyone a very Happy New Year!! May you all have great health, joy and happiness and also a little prosperity wouldn't hurt either!

 You guys and gals here have helped me a lot this year and I want you all to know how much I greatly appreciate it. Without the help that all of you have given me I would have struggled and then maybe even given up. But as it is, I'm still forging forward and constantly learning. Yes, I know. Also asking dumb questions still. But have to admit some of them gives you a chuckle as you shake your head at the questions. Yes. I still have Windows, but today I was glad I did because I did see that there was something different going on with the two and just had to figure out where the problem laid. But, as I'm gaining more confidence I plan on pulling the plug when the next LTS comes out. Completely get rid of Windows. Just a pain in the buns at times though explaining to someone that I use a different OS from their Windows. :lolflag:

Again everyone, thanks for putting up with me and the help you offer. 

Happy New Year everyone!!!!


Tom

---

