---
title: "Thunderbird Mail"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by daniell59 on 2009-06-24
Thunderbird mail is no longer available. When I click on Thunderbird mail, the little marker turns, but then the mail does not come up.
Previous to this is worked perfect until I turned the computer off, then on.

Thanks

---

### Post by cariboo on 2009-06-24
Could you open an Applications-->Accessories-->Terminal and type:

```
thunderbird
```

Paste the output in your next post.

---

### Post by daniell59 on 2009-06-24
> **cariboo907 said:**
> Could you open an Applications-->Accessories-->Terminal and type:

```
thunderbird
```

Paste the output in your next post.

Thanks, but I am not sure what you want me to type.

---

### Post by jimv on 2009-06-24
Type the word "thunderbird" into the terminal.  This will launch Thunderbird.  Then watch the terminal to see if anything that looks like an error pops up.  Often programs will give output in the terminal that you wouldn't see normally.

---

### Post by daniell59 on 2009-06-24
> **jimv said:**
> Type the word "thunderbird" into the terminal.  This will launch Thunderbird.  Then watch the terminal to see if anything that looks like an error pops up.  Often programs will give output in the terminal that you wouldn't see normally.

I got this  Segmentation fault

---

### Post by halitech on 2009-06-24
> **daniell59 said:**
> I got this  Segmentation fault

can you post the entire message here so we can see the entire message

---

### Post by daniell59 on 2009-06-24
> **halitech said:**
> can you post the entire message here so we can see the entire message

This is everything

daniel@daniel-desktop:~$ thunderbird
Segmentation fault
daniel@daniel-desktop:~$

---

### Post by halitech on 2009-06-24
wow, not much help there at all... 

what about
```
dmesg | tail
```

---

### Post by daniell59 on 2009-06-24
> **halitech said:**
> wow, not much help there at all... 

what about```
dmesg | tail
```


Could you post exactly what I should type so that I can copy/paste

Thanks

---

### Post by daniell59 on 2009-06-24
> **daniell59 said:**
> Could you post exactly what I should type so that I can copy/paste

Thanks

Also, is it possible for me to reinstall the program. I do not have a clue what I am doing.

---

### Post by daniell59 on 2009-06-24
How, I do not have a clue.

---

### Post by halitech on 2009-06-24
> **daniell59 said:**
> Could you post exactly what I should type so that I can copy/paste

Thanks

post what is in the code box

depending on what is wrong a reinstall may not do any good

---

### Post by Sir Jasper on 2009-06-24
Hi halitech,

I wonder if the cryptic change of header two posts back means the problem is fixed? 

You may not have noticed the header change since it looks as if you were both posting at the same time.

My regards

---

### Post by daniell59 on 2009-06-24
> **Sir Jasper said:**
> Hi halitech,

I wonder if the cryptic change of header two posts back means the problem is fixed? 

You may not have noticed the header change since it looks as if you were both posting at the same time.

My regards

I shut off the computer for a short time. I rebooted, and it was back.

---

### Post by halitech on 2009-06-24
> **Sir Jasper said:**
> Hi halitech,

I wonder if the cryptic change of header two posts back means the problem is fixed? 

You may not have noticed the header change since it looks as if you were both posting at the same time.

My regards

> **daniell59 said:**
> I shut off the computer for a short time. I rebooted, and it was back.

ok, no I missed the header change but glad to hear it's now working for you.

---

