---
title: "How do I specify the pop and smtp port numbers for Evolution?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-11-04
Hi Ubuntu Community:

How do I specify the pop and smtp port numbers for Evolution?

Thanks):P!
Phil Smith
Duluth, GA

---

### Post by dndrich on 2009-11-04
The simplest way is to append it to the server information. For example, I configured GMail IMAP in Evolution. Now, for the incoming IMAP server it requires ssl, so when checking that I suspect Evolution sets the correct port number, and it works. But for out going mail using SMTP GMail requires port 587. Yet there appears to be no place in Evolution to put that number. But, under the server information, if you put it in like this for example:

smtp.gmail.com:587

See the :587 at the end of the server? That works.

---

### Post by LewRockwell on 2009-11-04
thunderbird

.

---

### Post by dndrich on 2009-11-04
Does your post mean "use Thunderbird"? It was quite terse. This fellow wants to use Evolution, and the method I supplied will work.

---

### Post by LewRockwell on 2009-11-04
> **dndrich said:**
> Does your post mean "use Thunderbird"? It was quite terse. This fellow wants to use Evolution, and the method I supplied will work.

OP and OT seems fairly neutral...

If Thunderbird was shipped with Ubuntu(instead of Evolution) then the likelihood of the question pertaining to Thunderbird would be significant

> **Phil Smith said:**
> How do I specify the pop and smtp port numbers for Evolution?

some prefer Thunderbird

and are inclined to share

your response to our generosity is noted> Adjective
**terse**
   1. (of speech or style) **Brief, concise, to the point.**

**Brief, concise, to the point.**

as intended and delivered indeed

.

---

### Post by Wolowitz on 2009-11-04
> **Phil Smith said:**
> Hi Ubuntu Community:

How do I specify the pop and smtp port numbers for Evolution?

Thanks):P!
Phil Smith
Duluth, GA

In Evolution, click on Edit, then Preferences. 
If you already have an account, highlight it and push Edit. 
Under the Receiving Email tab, you can enter your pop server address and username. Enter smtp in the Sending Email tab. 

Is that what you needed?

---

### Post by Old Jimma on 2009-11-05
Thanks go to dndrich for an accurate and precise reply!!

From Evolution, edit > preferences then highlight email account and choose edit.

Then, choose the receiving email tab, put a colon after your pop server name and the port number your ISP wants you to use.

Then, choose the sending email tab, put a colon after your smtp server name and the port number your ISP wants you to use.

Evolution is so great! And the Ubuntu Community is so great!!

All the best,
Phil Smith

---

### Post by sliketymo on 2009-11-05
> **Phil Smith said:**
> Hi Ubuntu Community:

How do I specify the pop and smtp port numbers for Evolution?

Thanks):P!
Phil Smith
Duluth, GA


):PIt may be statistically impossible.

---

### Post by philinux on 2009-11-05
> **Phil Smith said:**
> Thanks go to dndrich for an accurate and precise reply!!

From Evolution, edit > preferences then highlight email account and choose edit.

Then, choose the receiving email tab, put a colon after your pop server name and the port number your ISP wants you to use.

Then, choose the sending email tab, put a colon after your smtp server name and the port number your ISP wants you to use.

Evolution is so great! And the Ubuntu Community is so great!!

All the best,
Phil Smith

+1. I switched to EVO last month. Three reasons.

1. Integrated to gnome desktop for notifications etc.
2. Integrated PIM.
3  Display Previous and Next message buttons actually work as intended.

---

### Post by Old Jimma on 2009-11-05
Just to add a little more to the Evo vs T-bird debate:

My confession: I was a T-bird user for years. In my opinion T-Bird is so-so. :-\"

However, I've seen the light: :idea:

 Evo has ALOT more features, works faster and is native gnome. 

I sure wish Epiphany had a search bar and speed dial like FF. I'd be a 100% gnome boy.

\\:D/

All the best,
Phil Smith
Duluth, GA

---

### Post by philinux on 2009-11-05
> **Phil Smith said:**
> Just to add a little more to the Evo vs T-bird debate:

My confession: I was a T-bird user for years. In my opinion T-Bird is so-so. :-\"

However, I've seen the light: :idea:

 Evo has ALOT more features, works faster and is native gnome. 

I sure wish Epiphany had a search bar and speed dial like FF. I'd be a 100% gnome boy.

\\:D/

All the best,
Phil Smith
Duluth, GA

There is, as far as I can see one real PITA with evo, and thats this.
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/438841](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/438841)

---

