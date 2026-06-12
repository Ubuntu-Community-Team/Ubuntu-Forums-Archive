---
title: "I Cant Connect To Internet"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by isaacnoona on 2008-03-26
hi 
imm new to linux and i just installed the 8.04 beta ...

i tried several times to connect to the internet but i cant...
i put in the wireless connection i want to connect to along with the password, then i takes forever to connect in other words ... its not connecting 

i need help ... ionno if theres something wrong with my card, or somethign with the driver in ubuntu ....
imm currently switching on and off with windows vista and hardy heron to connect to the internet thus posting this.

i have a compaq presario f500 
i have no idea waht kind of card i have but its average an intergrated card. 
i have a little switch when ever i want to connect to the internet, so when i turn the switch on the light turns blue on vista. whenever on ubuntu i turn the swtich on it stays yellow (in other words its staying off)
i have nno idea how to fix this ...
i need helpp 


thanks

---

### Post by wormser on 2008-03-27
Try turning the encryption off and connecting.  The following command will show your hardware details.

```
lspci
```

---

### Post by isaacnoona on 2008-03-27
how do i turn the encryption off?

---

### Post by wormser on 2008-03-27
You have to log into your router and go to wireless settings.  Post the output of the command in my other post.

---

### Post by isaacnoona on 2008-03-27
sorry i didnt know if you wantted all them or just the one about the network...

Network controller: Broadcom Corporation BCM94311MCG slan mini - PCI

sorry imm such a newb at this 
how do i reply on your post?! LOL

---

### Post by isaacnoona on 2008-03-27
> **wormser said:**
> Try turning the encryption off and connecting.  The following command will show your hardware details.

```
lspci
```
umm i have the network controller 
tell me if you need otherss or the entire thing
lol

Network Controller: Broadcom Corporation BCM9411MCG wlan mini - PCI

---

### Post by wormser on 2008-03-27
That is all the information needed.  Did you install it with System> Administration> Restricted Drivers?  Here are some trouble shooting things to try.  Have you tried connecting with out encryption yet?  Unplug the router for 10 seconds.  Search the forum for the model number.

---

### Post by uberlube on 2008-03-27
I have the exact same laptop and I have created the hoeto in my sig to help out with this :)

---

### Post by isaacnoona on 2008-03-27
> **wormser said:**
> That is all the information needed.  Did you install it with System> Administration> Restricted Drivers?  Here are some trouble shooting things to try.  Have you tried connecting with out encryption yet?  Unplug the router for 10 seconds.  Search the forum for the model number.

i haven't tried the encryption thingy yet ... lol i forgot the password for my router ... so ima re-install and get new info later when i have time
the weird thing is that i havent installed anything from restricted drivers ... 
ill most likly get my do anything related to my router tomm.
thanks for the help ill give heads up tomm!

---

### Post by isaacnoona on 2008-03-27
> **uberlube said:**
> I have the exact same laptop and I have created the hoeto in my sig to help out with this :)

hey uberlube
i took a look at your thread and it looks really effective ...
i havent really put tried it yet but i have one question
do you need gusty for this or could this also work in 8.04?!

---

