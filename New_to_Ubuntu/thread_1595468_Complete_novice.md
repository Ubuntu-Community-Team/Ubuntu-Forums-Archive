---
title: "Complete novice"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Brian_new_to_linux on 2010-10-13
Hello all 

I am utterly linux illiterate, but 10.10 looked the perfect replacement for linpus lite on my Acer Aspire one netbook.   I have downloaded the OS & the USB .iso install file to test that all my hardware works and it all looked just dandy, when connected by wire to my router, 
However, although the netbook is showing nearby wireless  connections, my own home network wireless signal does not appear and I cannot connect.
Have I done something wrong or is the problem with the router? When I reboot to Linpus lite it all works fine and connects as it should. 

Help!

Brian

---

### Post by petronell on 2010-10-13
First the obvious question, is your wireless network set to be a hidden SSID?

If so click on the network manager and choose connect to hidden network?

---

### Post by msmx5s on 2010-10-13
I don't suppose you have a hidden network on your router do you?

---

### Post by nothingspecial on 2010-10-13
First thing, get that wired connection back, then in your menus go

System > Administration > Aditional Drivers

See if that brings anything up.

If not, post back your wireless info

Open a terminal Applications > accessories > Terminal and type

```
sudo lshw -C network
```

It will ask for  your password but you won`t see it when you type it.

Copy and paste the gobbldygook it soits out in a new post back here.

---

### Post by Brian_new_to_linux on 2010-10-13
No my wireless router/network is not set to be hidden- In fact I often use my work laptop at home (Win XP) and my stepdaughter has also connected to without issues on an Vista (gak) laptop. 
I will try with the wired connection again when I get home tonight
THANK YOU ALL for your incredibly quick replies.  This is another reason I am so keen to move all of my machines (desktop and very old laptop)  to Unbuntu, when I am confident I know how to use it!

Bri

---

### Post by msmx5s on 2010-10-13
I'm pretty new to Ubuntu too, but the help you can get on here is amazing. :-)

I've managed to get answers to my problems up till now without asking a question, as it has already been answered on here - somewhere. lol

I've wiped Windows completely now :-)

---

### Post by Brian_new_to_linux on 2010-10-14
I did have every intention of having another go at this BUT.... my ancient XP desktop blew the p/s last night and I had to deal with that first (along with a blocked toilet and a washer dryer that will do neither :confused:-never rains,  but it b****** pours!).  
I will see if I can get it sorted tonight.
Thanks again for your suggestions and support. 
Brian

---

### Post by Chris Edgell on 2010-10-14
I just wanted to say that it will serve you well if you are really specific in the title to your thread. 

You see along the bar toward the top of the forum:

User CP   Forum Help    Forum Council   New Posts    Search   etc

When you click "Search" you will see that you can click on the option of "See all your own threads".  After you have had 10 or 20 questions answered, you will like being able to look back and having the title tell you what THAT thread is about.

One more thing: Click that User CP: Look on the right side...your Profile...Edit your details...and find the place where you can put what OS release you have in your computer -- then we can know right away if we might be able to be helping you.

So Brian, best of luck in your "pouring rain"  God bless!

---

### Post by delatun on 2010-10-14
Hey Brian, glad you're moving over to Linux--smart move. I still have plenty to learn but I'd suggest learning as much shell commands as possible from the start so you won't be stuck when your mouse doesn't work,etc. I work with clients in a 100% Windoze environment and I'll tell ya, it's nice to use the power of shell in my free time. Easier to learn in tandem with the graphical than being an expert with your mouse and retracing your steps with the keyboard. 

I agree with the previous post. Try that suggested command and you may need to update the drivers. I had that issue with my Lucid (another Ubuntu version) and my laptop a while back. The update should be pretty simple since most cards are supported. 

Saludos

---

### Post by Brian_new_to_linux on 2010-10-15
Hello All and thanks for your suggestions: 
Reconnecting to the network (wired) and using the network/connection manager worked a treat & I have now gone for a full install.  I will take on board the advice about posting with a specific question in the subject line. 
Works & looks fantastic.

Thanks 
Brian

---

