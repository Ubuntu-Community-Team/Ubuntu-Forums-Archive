---
title: "how to convert oog to mp3 files"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-12-27
my daughter has some music she has legally dowmloaded. i need to covert the files to mp3 and then burn them to a cd so she can play on a cd player.  how do i do this. happy holidays

---

### Post by pbrane on 2009-12-27
try **soundconverter**, it's in the repos. It can convert .ogg to .mp3.

---

### Post by rburkartjo on 2009-12-27
hey ya'll if anyone comes up with an answer  use the kiss principal i am 60 tks

---

### Post by ad_267 on 2009-12-27
I'm sorry, I've got no idea what you were trying to say there. "need*", "tks"? What was wrong with the previous answer?

If you're using Ubuntu 9.10, open up the Software Centre and search for soundconverter. If you're using a previous version of Ubuntu, open up Add/Remove and do the same. Then open it from the menu and drag and drop your files onto it. Set your preferences to mp3 then convert.

Edit: Actually, after reading your post, why do you need to convert them to mp3? Audio CDs don't use mp3, and you can burn OGG files to CD. Just use Brasero CD burner that comes with Ubuntu.

---

### Post by rburkartjo on 2009-12-27
bpr tks for the info will try

---

### Post by SuperSonic4 on 2009-12-27
You can burn directly as ogg using your favourite cd burner

If you insist on converting on them

```
pacpl -R -v -o ogg  -p -t mp3 . --outdir .
```

You will need pacpl though. Frankly soundconverter would be better

---

### Post by rburkartjo on 2009-12-27
ad corrected post sorry for typo

---

### Post by rburkartjo on 2009-12-27
super tks for your reply

---

### Post by Chronon on 2009-12-27
1) Don't transcode from one lossy format to another unless it is absolutely necessary as this reduces sound quality (significantly in some cases).

2) In this situation where you're trying to create an audio CD, you just want to decode the lossy format to PCM audio and burn this to disk.  A disk burning program like Brasero or K3b should do the job without any loss of quality.

(No idea what "tks" or "bpr" mean but I assume they are not crucial to the discussion here.)

---

### Post by Captain_tux on 2009-12-28
tks = Short for thanks.

pbr = Short for pbrane (first person to answer the question)

Dude said he's 60, but has a fine handle on the use of teen's language ;)

---

### Post by rburkartjo on 2009-12-30
tks ya'll

---

