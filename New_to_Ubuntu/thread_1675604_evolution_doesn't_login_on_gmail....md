---
title: "evolution doesn't login on gmail..."
date: 2011-01-25
forum: New to Ubuntu
---

### Post by werty2010 on 2011-01-25
i have 2 gmail accounts which i manage them through evolution
one is working just fine

the other one, although i have the same settings, it just wont login
evolution gives me the following message:
"Error sending password:-ERR[AUTH] Username and password not accepted."

i tried to change the password on my account 2 times and retry on evolution but the same thing happens again

some help anyone?

---

### Post by werty2010 on 2011-01-26
bump

---

### Post by cipherboy_loc on 2011-01-26
Can you log into the one from the gMail/Google log in page?


Cipherboy

---

### Post by mr_luksom on 2011-01-26
I had the same problem with my gmail, I could not get around it. I switched to thunderbird, no issues.

---

### Post by werty2010 on 2011-01-26
> **cipherboy_loc said:**
> Can you log into the one from the gMail/Google log in page?


Cipherboy


yes i can
but besides that evolution behaves very strangely....
is there a way to reset evolution(restore it to the default settings with no accounts) and set it up from the the start?

---

### Post by cipherboy_loc on 2011-01-26
To reset Evolution:
```

rm ~/.evolution -rf

```

I wonder if it is the fact that you are using two of the same type of accounts (gmail) and it is having issues sending/receiving the mail from the right place...



Cipherboy

---

