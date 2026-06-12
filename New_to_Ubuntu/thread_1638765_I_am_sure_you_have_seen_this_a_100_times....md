---
title: "I am sure you have seen this a 100 times..."
date: 2010-12-06
forum: New to Ubuntu
---

### Post by deversole88 on 2010-12-06
I forgot my username and password so like an idiot not knowing anything  about computer when into the BIOS setup utility and set a supervisor  password and a HDD password thinking it was the same password needed to  access my computer. Now when I restart my computer it asks for my HDD  password, once entered in take me to a command screen that says  "grub>" ... How can I fix this so that I can use my computer normally  or just get it to load to the username and password screen??? Sorry to have to ask...

---

### Post by sikander3786 on 2010-12-06
Welcome to the forums :-)

If you have set it from Bios, you'll need to reset Bios to get rid of that.

There might be a jumper on your motherboard for that. Refer to manufacturer's manual.

---

### Post by Tony Flury on 2010-12-06
I can't help you with your specific question - but one thing I do know is that you are far more likely to get an reply if you ask a specific question in the Title - maybe something like : 

"Forgotten Username and Password - how do i log on".

can you repost and actually give people a chance to help you ?

---

### Post by Born-Thirsty on 2010-12-06
I gave an answer in a previous post, but will give a summary here based on the first response.
To reset the BIOS, one can usually just remove the bios battery and wait a minute or two and then reinsert it.

---

### Post by coffeecat on 2010-12-06
> **deversole88 said:**
> Now when I restart my computer it asks for my HDD  password, once entered in take me to a command screen that says  "grub>"

If you are getting a prompt that says "grub>" it seems to me that you have three problems: needing to unset your BIOS password; your forgotten Ubuntu password and username; and some issue that is preventing grub from displaying your grub menu. There is probably a problem in your Ubuntu root partition.

Perhaps you could tell us more about your setup and whether you had any problems booting up before you forgot your username and password.

---

