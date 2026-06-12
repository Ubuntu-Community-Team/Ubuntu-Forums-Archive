---
title: "Swap Space Increase: how to?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-02-28
Hey guys! So when doing the default install of 9.10, I am now noticing that it only set up 1.6GB SWAP. 

My system: Dell 1545 160GB HD, 2.16GHz, 3GB RAM. 

If I want to increase SWAP without deleting Ubuntu, or without loosing files, how would I do this? 

Complete Linux Newbie here, so go slow! Thanks!

---

### Post by asmoore82 on 2010-02-28
Why do you need more swap??

IMHO, Hibernation is not worth the trouble.

I've got 2 GB of RAM and only 0.5 GB of swap.

But your answer could be found here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by UbuNoob001 on 2010-02-28
> **asmoore82 said:**
> Why do you need more swap??
IMHO, Hibernation is not worth the trouble.
I've got 2 GB of RAM and only 0.5 GB of swap.
But your answer could be found here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


asmoore82 Thanks!: I am looking at using SAGEMATH to do some math computation work, and, eventually, taking a Python class. Figured i might need it (?). Maybe I don't. 

Here might be a typical computing session for me in the future: 1.Firefox open (6tabs)2. Pidgin open/chatting, 3. SAGEMATH open doing a computation or two, 4. terminal open. 5. Downloading a file through Firefox.  

Do you think my current 1.6GB SWAP with 3GB RAM might be enough? if not, do you think I should resize swap partion, or just create swap file as in that link you sent? I just am not familiar with partition editing so nervous about that

---

### Post by r-senior on 2010-02-28
I should imagine 3GB RAM would mean you hardly touching the swap. As I write, I have Firefox open with 6 tabs, Empathy, Evolution, Netbeans (which is a memory monster), a terminal and Dropbox and MySQL running in the background.

Ubuntu 9.10 with 2GB RAM, 18MB swap used. A token amount from the 1.5GB available.

---

### Post by louieb on 2010-02-28
If your not going to hibernate - you have more that enough swap now. With 3GB ram my guess it will never get used.  Good thing too - once you start having to use swap - it will just slow things down. You can always check the system monitor every now and then.

---

### Post by lyall on 2010-02-28
have you checked what the System Monitor says on the Resources tab?

try loading the apps you had open and see what the Memory and swap History says

it would be a place to start before changing your system

good luck and have fun learning

---

