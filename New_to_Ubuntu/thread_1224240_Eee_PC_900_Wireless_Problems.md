---
title: "Eee PC 900 Wireless Problems"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by gjoellee on 2009-07-27
Hi, my sister bought an Eee PC 900 as she is traveling a lot, and need a computer to share images and surf on the internet. My sister does not know anything about computers, but she did not like the over simplified Xandros Linux which came with here Eee PC.

She asked me if I could make here computer better, and I installed Ubuntu Netbook Remix. Everything runs fine except for the wireless. Because of one reason I can't even connect to the internet at home.
This happens:

1. I select my home wireless network.

2. The authentication window appears and I enter the password for my home network.

3.I press connect, and the window disappears. The try icon shows the connecting to internet animation. (everything normal this far)

4. The authentication window appears again. The password is still there so I press connect one more time. After I while the authenication window shows again....and it loop like that.

Oh by the way, sometimes the password gains a lot of random letters and numbers.

---

### Post by bailbath on 2009-07-27
Sounds like a encryption problem what encryption are you using?
Ian

---

### Post by LookTJ on 2009-07-27
As I understand it, some wireless cards aren't able to use WPA1/2. Though most cards(if not all) can handle WEP.

Did you double check the password?

:)

---

### Post by bailbath on 2009-07-27
He should have no problems with the wireless card in a eeepc!?
Sometimes routers can be a pain with encryption so make sure you are using the correct setting in the router as well.

---

### Post by gjoellee on 2009-07-27
> **bailbath said:**
> Sounds like a encryption problem what encryption are you using?
Ian

WEP 40/128-bit Key

> **LookTJ said:**
> As I understand it, some wireless cards aren't able to use WPA1/2. Though most cards(if not all) can handle WEP.

Did you double check the password?

:)

Yes, my password is correct :)

---

### Post by LookTJ on 2009-07-27
> **bailbath said:**
> He should have no problems with the wireless card in a eeepc!?
Sometimes routers can be a pain with encryption so make sure you are using the correct setting in the router as well.
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access) 

Finished reading that.  You're right, he/she should have no problem with the wireless in the eeepc. Might be something in the router.

Or Ubuntu having driver trouble with the card, perhaps a bug.

---

### Post by bailbath on 2009-07-27
> **gjoellee said:**
> WEP 40/128-bit Key



Yes, my password is correct :)

Use WPA as it is more secure and is the default I believe of network manager.
Ian

---

### Post by bailbath on 2009-07-27
> **LookTJ said:**
> [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access) 

Finished reading that.  You're right, he/she should have no problem with the wireless in the eeepc. Might be something in the router.

Or Ubuntu having driver trouble with the card, perhaps a bug.


Not a bug for sure. That is a good link though worth the OP reading.
Thanks

---

### Post by rustutzman on 2009-07-27
I've had similar problems. Make sure connect automatically is checked in the connection manager for your wireless. Reboot and see if it connects.

Russ

edit: those random numbers are your encrypted password

---

### Post by LookTJ on 2009-07-27
> **gjoellee said:**
> WEP 40/128-bit Key
I recommend using the WPA2 protocol.

---

### Post by gjoellee on 2009-07-27
I somehow fixed it. I am writing from the EeePC now.

What I did was to enter the network connections window and made the computer connect to it on startup. For some reason it works now.

---

### Post by gjoellee on 2009-07-27
Ok, now there is a new problem :(

It does connect to the internet, it runs fine for a few minutes and then suddenly the internet gets really slow. It takes about 1min to folly load Google.com and loading a page on Facebook usually gets times out.

---

### Post by gjoellee on 2009-07-28
14 hour BUMP

---

### Post by gjoellee on 2009-07-28
I solved the problem by installing SliTaz.
For some reason the wireless works there and for some reason it does not in Ubuntu.

---

### Post by starcannon on 2009-07-28
Grats on getting it to work; may I also suggest the Array.org kernel?
 
You can get it [here]("http://array.org/ubuntu/"); be sure to read through the installation instructions fully, then just go for it; it looks tough, but its really just a copy paste walk through, and at the end you reboot into a fully functional Asus Eee running Ubuntu.
 
[http://array.org/ubuntu/](http://array.org/ubuntu/)
 
Enjoy.

---

