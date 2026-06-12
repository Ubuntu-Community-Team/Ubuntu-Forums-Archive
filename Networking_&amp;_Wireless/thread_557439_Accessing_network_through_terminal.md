---
title: "Accessing network through terminal?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by garyed on 2007-09-22
I'm trying to copy & paste some files from my Feisty computer to my windows computer both hooked up on the same router.  I can copy & paste form windows to Feisty just cliking on Places>Connect to Server> browse network & getting to the file manager but it work work backwards. I get access denied when I try to copy anything into Windows. I assume if I could get  into windows from terminal I could use chmod & maybe that would work.
Anyone have any ideas?

---

### Post by dcstar on 2007-09-22
> **garyed said:**
> I'm trying to copy & paste some files from my Feisty computer to my windows computer both hooked up on the same router.  I can copy & paste form windows to Feisty just cliking on Places>Connect to Server> browse network & getting to the file manager but it work work backwards. I get access denied when I try to copy anything into Windows. I assume if I could get  into windows from terminal I could use chmod & maybe that would work.
Anyone have any ideas?

You may be accessing Windows via its "Guest" account, which may only let you read and not write.

I would say you will have to set up - or log into - a Windows account that has write privileges.

---

### Post by garyed on 2007-09-22
You were right I guess.
When I went back to my windows computer I shared the hard drive without a password & allowed read & write priviliges & it works. 
I assume that makes it pretty insecure though.
I don't know how to access it once I give it a password.
As you might guess I've just started networking my computers so I know virtually nothing. 
I have another Edgy computer on my network that I haven't figured out  how to share with the Feisty one yet.

---

