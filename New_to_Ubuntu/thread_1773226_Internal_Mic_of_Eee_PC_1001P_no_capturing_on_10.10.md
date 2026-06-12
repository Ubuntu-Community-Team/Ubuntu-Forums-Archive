---
title: "Internal Mic of Eee PC 1001P no capturing on 10.10"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by iamchichi on 2011-06-01
I've been trying to fiddle with my alsa and pulse audio settings but I can't get the built-in mic of my eee pc 1001P to capture any sound. 

The only way I can use  a mic on it is to plug in an external microphone. 

@_@ 

Please help. :confused:

---

### Post by johngreth on 2011-06-02
In Preferences -> Sound -> Input, is the connector set to internal? Also, what is the Profile set to under hardware?

---

### Post by iamchichi on 2011-06-02
> **johngreth said:**
> In Preferences -> Sound -> Input, is the connector set to internal? Also, what is the Profile set to under hardware?

Hi Thanks for the reply. 
I'm using the internal audio input and output as indicated in the hardware setting tab as well as in the individual input and output settings tabs. 

I'm using an external mic and ear phone. 

Speaker works fine without the headphone
internal Mic doesn't capture a thing when external mic's unplugged.

 screenshots attached.

---

### Post by iamchichi on 2011-06-21
Problem solved
I went to Applications> Sound and Video > Pulse Audio Volume > Input Devises > Click on the unlock icon > slide the front left to 50 or whichever has the less background static sound or suits your ears well > front right slider down to silence. 

This works fine for skype calls 

settings for google talk and sound recorder may vary, just play with the sliders to achieve the desired sound quality.   

hope it helps other newbies like me

---

### Post by NoPoChris on 2011-07-08
Hey, I tried your solution and it worked for Skype (I also disabled the "Allow Skype to automatically adjust my mixer levels" option) but when I open up my browser and try to chat (Google+ Hangout) the settings are changed back to default and the mic stops working again. Is there a way to block my web browser from changing the mixer levels? I'm using Chrome on Asus EEE PC1001PXB running 11.04.

---

### Post by iamchichi on 2011-07-09
> **NoPoChris said:**
> Hey, I tried your solution and it worked for Skype (I also disabled the "Allow Skype to automatically adjust my mixer levels" option) but when I open up my browser and try to chat (Google+ Hangout) the settings are changed back to default and the mic stops working again. Is there a way to block my web browser from changing the mixer levels? I'm using Chrome on Asus EEE PC1001PXB running 11.04.

Haven't used 11.04. I'm still using the 10.10 Netbook version. And that doesn't happen in my netbook running on 10.10. 

Let's wait for pros to reply. 

^^ Cheers! From another beginner.

---

