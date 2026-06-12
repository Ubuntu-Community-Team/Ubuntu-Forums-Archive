---
title: "Popcorn Hour A-100"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by peakshysteria on 2008-06-09
Can anybody share how to setup a Popcorn Hour A-100 Media Center so that it finds your Ubuntu Hardy Heron?

I'm thinking about buying a Popcorn Hour A-100 Media Center and I'm a newbie with little or close to no experience in networking (Samba or NFS).

---

### Post by TopiOkone on 2008-06-11
> **peakshysteria said:**
> Can anybody share how to setup a Popcorn Hour A-100 Media Center so that it finds your Ubuntu Hardy Heron?

I'm thinking about buying a Popcorn Hour A-100 Media Center and I'm a newbie with little or close to no experience in networking (Samba or NFS).

Im at work now without my Ubuntu. Trying to remember everything...

1. Turn on your PCH
2. Switch the Samba server on
3. Ubuntu -> Network -> Windows shares(?) and you should see your PCH

Actually this is easier than with XP. And I am VERY noob with Linux.

Let me know if you need more detailed instructions and I will check this as soon as I get home.

---

### Post by peakshysteria on 2008-06-11
I haven't set up samba yet. I just installed it via synaptic. But I'm kinda on thin ice here. Not sure how to configure samba yet. Any tips & tricks?

---

### Post by TopiOkone on 2008-06-12
Pfffffff... My mistake. I thought that you would like to see PCH with you Ubuntu. Not Ubuntu from your PCH. Sorry. :(

In your case I think the NFS is your solution. Don´t actually know how to set up it but NFS is for Linux and Samba is for Windows. NFS is also faster.

Do you have internal HDD in your PCH? I do have it and the way I use PCH with Ubuntu is that I just "push" everything from Ubuntu to PCH. I don´t play anything "over the network".

I know this might be a bit silly way to do it but at least it works .. :D

---

### Post by peakshysteria on 2008-06-12
It sounds great. But no, *when* I buy a PCH it's not going to have a HDD. At least not an internal. I prefer supersilent :) I might get an external drive. As I'm sure you know it comes default without any HDD. I was thinking of running it like that in the beginning. Meaning I'm gonna have to stream media from Ubuntu to the PCH right? Then NFS is all I need? Or am I wrong?

---

### Post by TopiOkone on 2008-06-12
Yep. NFS or MyIhome are the tools for you. [http://www.networkedmediatank.com/download/myihome.html](http://www.networkedmediatank.com/download/myihome.html)

Happy :popcorn:corn hours!

---

### Post by peakshysteria on 2008-06-13
Thanks man. Came across a PCH today. Got a good price for it as well :) So I bought it. Haven't tested NFS yet. It found my desktop at once :) But I'm not to well known with how it all works with passwords and creating shared folder etc. Kinda greek to me this....I guess I'll have to read up on it.

And it seems that the eject device button works when it want to and not every time. Which is kinda frustrating. But besides that it all seems very nice actually. I'll give it some work tonight to test it properly. Then I'll read up on NFS and see how I manage.

____

Edit:

I can find the shared folder in Popcorn. But I can't access it. It says:
```
wrong username or password. Click return to return to the previous screen.
```
Any tips and tricks? I have installed NFS and Samba via synaptic. And other local machines can find the main machine easy. I still haven't installed a HDD to Popcorn. It looks like this is the problem. Can anyone verify that NFS or Samba doesn't work on Popcorn without an HDD? Or is there a way to make NFS work without an HDD?

---

