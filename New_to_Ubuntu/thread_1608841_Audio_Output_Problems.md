---
title: "Audio Output Problems"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by sadpanda1990 on 2010-10-29
Well I'm sorry to bother you all but I'm having some trouble with my audio in meerkat. 
It's nothing to do with the OS but recently, the headphone jack has had an impact so it "thinks" that there is headphones in the jack.
I've been trying to figure out how to handle it but I haven't had any luck. 
Is there anyway to disable the headphone output in so the speakers can work?
I miss my music :guitar:

---

### Post by sadpanda1990 on 2010-10-29
Forgot to add, the laptop is a Sony Vaio vgn-ns20e.

---

### Post by ipey on 2010-10-29
In Lucid Remix, I just go to system --> sound --> output and change connector to analog speakers. I think you will find it in system --> preferences --> sound.

---

### Post by sadpanda1990 on 2010-10-29
Thanks and I tried that but it didn't seem to work.
It seems it's not going to be that simple? 
Anyone know how much it costs to replace a headphone jack?

---

### Post by ipey on 2010-10-30
does "aplay -l" shows sound card driver installed?
I had a similar problem with my asus eee pc 1015P. in my case, the internal speaker works fine but headphones produce no sound. It was resolved by installing alsa.

---

