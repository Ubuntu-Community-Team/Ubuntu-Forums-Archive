---
title: "chfn Full name"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by cowboy.bebop on 2011-06-18
I did a man on chfn and I read it, and it seems you have to specify which user name you are changing the finger name for. I guess it wont work if you dont include the username, but after doing a 'sudo chfn' it shows 'Full name:' but how do you input your full name if it will only take one word?

I tried 'sudo chfn -f <first name><last name> <username>'
but then it tells me <last name> doesnt exist, wtf?

Of course im not actually putting the corner brackets with those words but im sure you understand, what am I doing wrong here?

---

### Post by cowboy.bebop on 2011-06-18
I must be a complete and utter retard I used that double quotes prior to the username:

sudo chfn -f "First Last" <username>

---

