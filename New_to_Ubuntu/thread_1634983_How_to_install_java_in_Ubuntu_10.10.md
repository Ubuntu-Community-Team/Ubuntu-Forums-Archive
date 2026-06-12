---
title: "How to install java in Ubuntu 10.10?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by BCMerlin on 2010-12-01
I want to install Java on Ubuntu, so I put this code in terminal:
```
[COLOR=Black]sudo apt-get install sun-java6-jre sun-java6-plugin equivs[/COLOR]
```

And this is what i got:

```

barbara@barbara-Aspire-5715Z:~$ sudo apt-get install sun-java6-jre sun-java6-plugin equivs
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Pakket sun-java6-jre is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron

Pakket sun-java6-plugin is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate

```
Any one who can tell me what's up?

I am running Ubuntu 10.10 on Acer Aspire 5715Z

---

### Post by philinux on 2010-12-01
Open synaptic, goto software sources/ repositories and enable the Partner repo. Then try installing.

---

### Post by BCMerlin on 2010-12-01
> **philinux said:**
> Open synaptic, goto software sources/ repositories and enable the Partner repo. Then try installing.
Ok, I want to do this, but I can't find the partner repo to enable. Can you be more specific?

---

### Post by philinux on 2010-12-01
> **BCMerlin said:**
> Ok, I want to do this, but I can't find the partner repo to enable. Can you be more specific?

In Synaptic. Settings>repositories>Other software Tab. Then click the reload button in synaptic

---

### Post by BCMerlin on 2010-12-01
> **philinux said:**
> In Synaptic. Settings>repositories>Other software Tab. Then click the reload button in synaptic
Now I am installing thanx. Still questions, cause the terminal looks like this more then two hour yet, does it take that long to install? Or is something wrong again?

---

### Post by ell02 on 2010-12-01
The thumbnail wont open here but i believe you have to hit the tab button. The sun agreement needs to be highlighted for you to accept it.

---

### Post by BCMerlin on 2010-12-01
> **ell02 said:**
> The thumbnail wont open here but i believe you have to hit the tab button. The sun agreement needs to be highlighted for you to accept it.
Thanx! You were right.

---

### Post by BCMerlin on 2010-12-01
I believe now it's done. I could close the terminal. Do I have to do something else yet?

---

### Post by eriktheblu on 2010-12-01
If the installer has finished running, it is safe to close.

If you hit the close button, it should pop up a warning if the application is still running. If there is no warning, you're probably safe.

---

### Post by BCMerlin on 2010-12-01
> **eriktheblu said:**
> If the installer has finished running, it is safe to close.

If you hit the close button, it should pop up a warning if the application is still running. If there is no warning, you're probably safe.
Yes, exactly. I am probably safe. :grin:

---

### Post by NCLI on 2010-12-01
> **BCMerlin said:**
> Yes, exactly. I am probably safe. :grin:
In the future, you can just install the package "ubuntu-restricted-extras" from the software center. That should give you flash, java, and a bunch of other nice stuff :p

---

