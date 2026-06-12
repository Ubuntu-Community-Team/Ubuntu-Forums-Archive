---
title: "Problems getting wireless in 8.10"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by marshall1001 on 2009-02-25
I've just got a new laptop and decided to put Ibex on it to play around.

I've just booted into live mode to try and see if there was any driver issues, and the system says it detects my wireless card but it does not say there are any wireless networks, any help? Will this problem fix itself after installation?

I already use Hardy Heron on my desktop machine but that's with an ethernet connection so I'm unfamiliar with the problem.

Help please?

---

### Post by llamabr on 2009-02-25
What kind of laptop?

Ubuntu is pretty good about finding and configuring your wireless device.  And even if it doesn't, we are.

Install away, is my advice.

---

### Post by marshall1001 on 2009-02-25
The laptop is an Acer TravelMate 3270, however I had to replace the Wireless that came with it to get it to work with my hackintosh partition. I think the Wireless card is Broadcom but it was my friend who did the legwork for it (I'm scared to open a laptop up) so I'm not sure on the model however.

I shall install and see if the problem's fixed.

---

### Post by missbliss on 2009-02-27
Hi, all.  I have had my wireless configured correctly before on my HPG60 laptop but neglected to save the page from which I followed instructions.  I had to do a re-install and need to configure it again.


Any help?  Anything I should post?

Ubuntu 8.10
HP G60

---

### Post by llamabr on 2009-02-27
> **missbliss said:**
> Hi, all.  I have had my wireless configured correctly before on my HPG60 laptop but neglected to save the page from which I followed instructions.  I had to do a re-install and need to configure it again.


Any help?  Anything I should post?

Ubuntu 8.10
HP G60

What trouble are you having now?

---

### Post by missbliss on 2009-02-27
> **llamabr said:**
> What trouble are you having now?

Need set up my wireless.

---

### Post by nothingspecial on 2009-02-27
What wireless card do you have?

---

### Post by missbliss on 2009-02-28
> **nothingspecial said:**
> What wireless card do you have?

Atheros AR24x 802.11abg PCI

---

### Post by cptrohn on 2009-02-28
> **missbliss said:**
> Atheros AR24x 802.11abg PCI

I have the same card, the linux backports is the way to go for the atheros card.

I would do a search for the thread on this because it is the easiest workaround that I found for it and the thread is very, very good and does a step by step that worked the 1rst time I tried it.

---

### Post by missbliss on 2009-02-28
> **cptrohn said:**
> I have the same card, the linux backports is the way to go for the atheros card.

I would do a search for the thread on this because it is the easiest workaround that I found for it and the thread is very, very good and does a step by step that worked the 1rst time I tried it.

Hey thanks for the head's up about searching for an Atheros thread.  I did and came up with: [http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24](http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24)

And it worked right off the bat!  :P  

It's getting saved to delicious!

---

### Post by cptrohn on 2009-02-28
> **missbliss said:**
> Hey thanks for the head's up about searching for an Atheros thread.  I did and came up with: [http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24](http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24)

And it worked right off the bat!  :P  

It's getting saved to delicious!

Glad that it worked for you!

---

### Post by Shady2175 on 2009-02-28
Hi I have Compaq Presario SR1124BX destop with a Linksys WMP300BN wireless card. I run XP on it, I have installed Ubuntu successfully but it won't recognize any kind of wireless card. How do I get it to recognize?  On the same note I have an HP Pavilion dv6000 laptop with the same issue.  How do I get my computers to have Ubuntu recognize my wireless cards so I can get on the internet?

---

### Post by missbliss on 2009-02-28
> **Shady2175 said:**
> Hi I have Compaq Presario SR1124BX destop with a Linksys WMP300BN wireless card. I run XP on it, I have installed Ubuntu successfully but it won't recognize any kind of wireless card. How do I get it to recognize?  On the same note I have an HP Pavilion dv6000 laptop with the same issue.  How do I get my computers to have Ubuntu recognize my wireless cards so I can get on the internet?

Anything Linksys is an Atheros chipset, *I think.*  Did you try the link I posted?  Give that a go and see what happens.

---

