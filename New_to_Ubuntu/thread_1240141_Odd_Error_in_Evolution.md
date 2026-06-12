---
title: "Odd Error in Evolution"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Riffster on 2009-08-14
Guys I'm getting the follwing error in Evolution email:

> 
Error while performing operation.

Host lookup failed: smtp.aliaslegion.com: Name or service not known

Host lookup failed: smtp.aliaslegion.com: Name or service not known

Host lookup failed: smtp.aliaslegion.com: Name or service not known

I know the site is valid because it's my own site and I can access the cPanel. 

I have had problems with the encryption key but that seems to have been solved so any clues?

I'm using Jaunty

---

### Post by LowSky on 2009-08-14
make sure you set up the port numbers correctly.

---

### Post by Riffster on 2009-08-14
> **LowSky said:**
> make sure you set up the port numbers correctly.


I'm not sure how I should be doing that. There's no obvious "port" number in the config panel that I've seen (I could be blind and/or stupid though ;) )

---

### Post by LewRockwell on 2009-08-14
repeat after me...

thun...der...bird...

.

---

### Post by Garyhans on 2009-08-14
I second - Thunderbird - Definitely

---

### Post by Riffster on 2009-08-14
> **LewRockwell said:**
> repeat after me...

thun...der...bird...

.


Ok whilst I love everything by Gerry Anderson that doesn't really help.

If I did migrate to Thunderbird - which I'm open to doing if feasable - I would need to transfer my existing mails across. I used Evo successfully on my Heron build with no problem. I'd also want to junk Evo if I move to a different mail system.

So - can I fix my initial problem or do I go to Thunderbird? Can I move my mails across? If not it's a non-starter?

---

### Post by Riffster on 2009-08-16
bump

---

### Post by fballem on 2009-08-16
> **Riffster said:**
> I'm not sure how I should be doing that. There's no obvious "port" number in the config panel that I've seen (I could be blind and/or stupid though ;) )

When you specify the server, you can specify the port number using :Port. For example, on a gmail account

pop.gmail.com:995
smtp.gmail.com:465

Hope this helps,

---

### Post by Riffster on 2009-08-18
> **fballem said:**
> When you specify the server, you can specify the port number using :Port. For example, on a gmail account

pop.gmail.com:995
smtp.gmail.com:465

Hope this helps,


Problem solved. Thankyou :)

---

