---
title: "Flash Player Help!!!"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-09-13
Ok, so I'm a brand new Ubuntu user, and I really want to install flash player. I went to their site and tried to run the .deb for Ubuntu 8.04 +. Once I ran the install by choosing Open with GDebi Package Installer, it looked like it was working, but then it said Error: wrong arcatecture i386. I really need help. Please keep in mind that I am a total noob and don't know all the terms yet. Thanks for any help!

---

### Post by sisco311 on 2009-09-13
Search for flashplugin-nonfree in Synaptic or Add/Remove... and install it.

or click [here]("apt://flashplugin-nonfree"). (apturl link)

---

### Post by Ratscallion on 2009-09-13
Yup, just try searching for Flash, Adobe, or things on those lines in add/remove.

---

### Post by snowpine on 2009-09-13
Or from the terminal:

```
sudo apt-get install flashplugin-nonfree
```

If you install applications from the Ubuntu repositories (apt-get, synaptic, add/remove programs), you'll always get the right version that's guaranteed to work. If you download random apps from the internet, you are rolling the dice...

---

### Post by NoaHall on 2009-09-13
Follow this to set it up - [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

You have 64 bit, so it's best to use the alpha version - it works much much better.

---

### Post by Ratscallion on 2009-09-13
> **NoaHall said:**
> 

You have 64 bit, .

I don't and i386 sometimes doesn't work.. I seem to be on i686... But that's for another thread.

---

### Post by ashwinhgtx on 2009-09-13
You don't need to go to Adobe's site and download Flash. It's available in the repositories. Methods to install using Add/Remove programs, Synaptic Package Manager and the Terminal(command line) have been described in other posts.

Unlike Windows or OSX, almost all the software you need will be available in the repositories which you can access using Add/Remove programs, Synaptic Package Manager or the Terminal(using apt). You will be downloading the files from Ubuntu's own servers so you can trust them.

Have fun with Ubuntu.

---

### Post by NoaHall on 2009-09-13
@Rat
What's your point? You're not the OP, who more than incredibly likely has 64 bit.

@ash

The one in the  repositories SUCKS for 64 bit. DO NOT install it. It's only the rubbish 32 bit version. Instead, grab the alpha which works much better.

---

### Post by Ratscallion on 2009-09-13
> **NoaHall said:**
> @Rat
What's your point? You're not the OP, who more than incredibly likely has 64 bit.



Just sayin'...

---

### Post by Captainflowers91 on 2009-09-13
Ok, so I tried to imput the code into my terminal, and at first it was working, but then when it asked for my password, it wouldn't let me type in the terminal at all

---

### Post by snowpine on 2009-09-13
> **Captainflowers91 said:**
> Ok, so I tried to imput the code into my terminal, and at first it was working, but then when it asked for my password, it wouldn't let me type in the terminal at all

Your password is invisible while you're typing it. :)

---

### Post by NoaHall on 2009-09-13
> **Ratscallion said:**
> Just sayin'...

Fair enough :) But I think he does have 64 bit instead, i686 is a bit strange.

---

### Post by Ratscallion on 2009-09-13
> **NoaHall said:**
> Fair enough :) But I think he does have 64 bit instead, i686 is a bit strange.
I'm a rare geek.. One in a million :P... I agree, chances are, 64bit, however, we could always ask: Do you have 64bit?

---

### Post by sisco311 on 2009-09-13
> **NoaHall said:**
> 
The one in the  repositories SUCKS for 64 bit. DO NOT install it. It's only the rubbish 32 bit version. Instead, grab the alpha which works much better.

[s]flash 10 alpha is in the repos since intrepid.[/s]

---

### Post by Captainflowers91 on 2009-09-13
Ok! Yea, I got it runnin! Thank you all for all your help!

---

### Post by sisco311 on 2009-09-13
> **Captainflowers91 said:**
> Ok! Yea, I got it runnin! Thank you all for all your help!

Cool!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [COLOR="Red"]Thread Tools[/COLOR].

---

### Post by Ratscallion on 2009-09-13
> **sisco311 said:**
> Cool!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [COLOR=Red]Thread Tools[/COLOR].
(Or just edit the thread title :P)

---

### Post by NoaHall on 2009-09-13
> **sisco311 said:**
> flash 10 alpha is in the repos since intrepid.

No it's not. That's a 32 bit version, that's wrapped. It's not as good as the alpha 64 bit version. They wouldn't add something that's alpha to the repos.

---

### Post by sisco311 on 2009-09-13
> **NoaHall said:**
> No it's not. That's a 32 bit version, that's wrapped. It's not as good as the alpha 64 bit version. They wouldn't add something that's alpha to the repos.

Yep, your right!

OP: Sorry for the confusion. 

> **NoaHall said:**
> Follow this to set it up - [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

You have 64 bit, so it's best to use the alpha version - it works much much better.

+1

> **NoaHall said:**
> 
The one in the  repositories SUCKS for 64 bit. DO NOT install it. It's only the rubbish 32 bit version. Instead, grab the alpha which works much better.

+2

:)

---

### Post by NoaHall on 2009-09-13
Haha. 

OP:

If you did install as the other were saying, and not following my guide, note you can get much better performance by following my guide to install 64 bit alpha version of it.

Happy video watching.

---

### Post by NoaHall on 2009-09-13
Hehe :)

---

### Post by Ratscallion on 2009-09-14
Yup, Happy YouTubing, Flash utilising etc! Can you do what sisco311 has asked and mark the thread as [SOLVED] by using the thread tools now you're done? Cheers!

---

