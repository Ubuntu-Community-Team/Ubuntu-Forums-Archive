---
title: "Sound douse not work. at all"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by thelostubunt on 2010-01-25
Hi
I have ubuntu 9.10. the sound douse not work at all. nothing zilch nota. i have it unmuted. it works in windows. i think it is something with pulse audio. I fixed it before but i reinstalled ubuntu. so it douse not work know. and i can not find how to fix the problem.

---

### Post by ubudog on 2010-01-25
What type of computer do you have?

---

### Post by thelostubunt on 2010-01-25
i have a gateway m465-e 
1.6ghz dual core 80gb hardrive 1.5 gb of ram. the sound worked the first time i loged on.

---

### Post by ubudog on 2010-01-25
> **thelostubunt said:**
> i have a gateway m465-e 
1.6ghz dual core 80gb hardrive 1.5 gb of ram. the sound worked the first time i loged on.

Open a terminal and post the output of dmesg ```
dmesg
```

---

### Post by thelostubunt on 2010-01-25
ok i will

---

### Post by llamabr on 2010-01-25
When you say zilch and nada, do you mean it doesn't work in firefox?  do you get startup sounds?  Can you play an mp3 from the terminal?  Some people with 9.10 are having trouble with pulse, and are solving it with:

```
sudo apt-get remove pulseaudio
```

report back if this solves it.

---

### Post by Psyco430404 on 2010-01-25
this is going to sound stupid, but check your mixer settings

---

### Post by ubudog on 2010-01-25
> **llamabr said:**
> When you say zilch and nada, do you mean it doesn't work in firefox?  do you get startup sounds?  Can you play an mp3 from the terminal?  Some people with 9.10 are having trouble with pulse, and are solving it with:

```
sudo apt-get remove pulseaudio
```

report back if this solves it.

+1 for this

---

### Post by thelostubunt on 2010-01-26
Hi
No sound none. anywhere. i removed pulse audio. it mest up ubuntu and then i had to reinstall it. ahahahah

---

### Post by thelostubunt on 2010-01-27
Hi
I reinstall ubuntu. It got so messed up. Now the sound works. ayayayayay

---

