---
title: "MySQL"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by am65 on 2010-02-12
Hello,

I want to install MySQL in my Ubuntu and use it to store personal data.

In Windows I used SQL Server Express and blocked it from internet using a firewall (the old Symantec Personal Firewall).

But in Ubuntu I haven't found any firewall that allows you to set the security by application. For example, I put MSQLSERVER.exe as "blocked" and that was all I needed.

In Ubuntu I have installed Gufw 9.10.4 but I'm not sure what it does because I have set it to disallow by default and anyway I can browse with Mozilla.

Is it safe just installing MySQL? Is it not possible to connect to it from the Internet?

Thanks

---

### Post by steve-shinn on 2010-02-12
Test your ports vunerability here :-

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

I think you will be pleasantly suprised at just how secure you are.

---

### Post by The Cog on 2010-02-13
I think that by default, MySQL only listens on the loopback address 127.0.0.1 which is not accessible from outside the machine it's installed on.

---

### Post by Shark_AtK12 on 2010-02-13
> **steve-shinn said:**
> Test your ports vunerability here :-
 
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
 
I think you will be pleasantly suprised at just how secure you are.
 
What a great site

---

