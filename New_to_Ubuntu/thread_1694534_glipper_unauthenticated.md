---
title: "glipper unauthenticated?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by s1wood on 2011-02-24
I saw glipper mentioned in another post and thought I would try it. 
The software centre has it but refused to install it as unauthenticated. 
Synaptic also said it was unauthenticated but I installed it anyway.
Now I can't find it - it said it was  a panel applet - I have done a restart but it still isn't showing anywhere. the software centre now has it ticked as installed.

So two questions here: 
a) why is is in the software centre if not authenticated?
b) how do I find it to use it?

Susan

---

### Post by cariboo on 2011-02-24
I haven't used glipper, but if is a panel applet, you should be able to add it by right-clicking on the panel.

---

### Post by ajgreeny on 2011-02-24
I never found glipper to be stable so very quickly started using **parcellite**.  It is very similar but does not seem to suffer from the same instability.

---

### Post by s1wood on 2011-02-24
Thanks for prompt replies

I tried installing parcellite - which was again down as unauthenticated.
That turns up in my Accessories and can be launched but nothing happens when I single click the applet. 

However I have now found a link which explains how to get glipper working - I had to ask 'add to panel' for 'clipboard manager' not 'glipper' so I am happy as far as that goes. 

I would still like to know why these packages are coming up as unauthenticated.

Susan

---

### Post by oldos2er on 2011-02-24
If you run ```
sudo apt-get update
``` in a terminal, it should tell you which repository is missing its gpg key.

---

