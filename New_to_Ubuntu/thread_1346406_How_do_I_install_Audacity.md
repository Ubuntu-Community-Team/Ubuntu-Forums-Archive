---
title: "How do I install Audacity???"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by mrs89 on 2009-12-05
Hi, I am totally new to Ubuntu. I actually just installed this OS the other night and am now really experimenting with it. Oh yeah, and I am using 9.10.

What I really need to do is install Audacity, but I am not sure how. I went to Applications and found it, but it reads "Not available in current data". I'm not entirely sure what this means?

I found a thread on here for installing Audacity on Ubuntu and it was all extremely confusing to me. Could anyone explain in the most simplest terms on how I'd install Audacity? And after actually installing the program, do I have to do more for the software to pick up inputs from, say, a mixer? What about saving the work on Audacity as mp3? I suppose it's not going to be as simple as downloading Lame? If anyone could give me a step by step on how to do all this I'd be extremely grateful. Thanks.

---

### Post by Paqman on 2009-12-05
> **mrs89 said:**
> 
What I really need to do is install Audacity, but I am not sure how. I went to Applications and found it, but it reads "Not available in current data". I'm not entirely sure what this means?


Something's gone wonky there. You should just be able to click on it to install. Go to System > Admin > Synaptic (which is just a more feature-rich software installer), hit the reload button and see if you can install Audacity from there. Post any error messages you get here.

> **mrs89 said:**
> I suppose it's not going to be as simple as downloading Lame?

Actually it will be. Lame is even a "suggested" package for audacity. That means that it won't be installed by default, but you know it will work if you choose to install it.

---

### Post by cartisdm on 2009-12-05
try doing it in the terminal:

```
sudo apt-get install audacity
```

---

### Post by cartisdm on 2009-12-05
double post

---

### Post by mrs89 on 2009-12-05
> **Paqman said:**
> Something's gone wonky there. You should just be able to click on it to install. Go to System > Admin > Synaptic (which is just a more feature-rich software installer), hit the reload button and see if you can install Audacity from there. Post any error messages you get here.



Actually it will be. Lame is even a "suggested" package for audacity. That means that it won't be installed by default, but you know it will work if you choose to install it.

I was able to download Audacity following your guidelines, no errors! Thank you!

I also downloaded the Lame MP3 encoder as well, and since I was able to save in the MP3 format from Audacity, I'm assuming its working.

I do get an error when trying to play it though, stating I need an MP3 decoder. Would this be found in the same place as Audacity/Lame? Is there anything in particular I should look for to be able to play it in the Movie Player?

---

### Post by JBAlaska on 2009-12-05
```
sudo apt-get install ubuntu-restricted-extras
```

Will get you what you need

---

### Post by mrs89 on 2009-12-05
> **JBAlaska said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

Will get you what you need
Worked, excellent!

Big thanks to all, I'm set now. =)

---

