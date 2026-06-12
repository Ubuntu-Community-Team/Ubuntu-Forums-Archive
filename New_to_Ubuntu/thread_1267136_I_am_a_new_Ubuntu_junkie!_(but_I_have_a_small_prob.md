---
title: "I am a new Ubuntu junkie! (but I have a small problem)"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by roasterx on 2009-09-15
Friends, Geeks, Lovers!

After many years of a secret crush on Linux, I have finally installed Ubuntu and It is so exciting. 

But I have a problem.

I'm a science teacher on a secret mission of using Ubuntu on all of my lab machines. After installing Ubuntu, I am unable to connect to our network. This is where I need your help. 

Treat me like a Linux newborn, let's start from the beginning and you'll have the satisfaction of knowing that you've helped to bring Linux into a public setting. 

Tell me what I need to do and I will do it. 

Yours in nerdery.

---

### Post by mike555 on 2009-09-15
a little more info would help, when you say "lab machines" does that mean they are independent desktops running sharing or what?

---

### Post by drinkpepsi on 2009-09-15
Which version of Ubuntu are you using? When you say join the network, is this a new network between the lab machines, or you are trying to join an existing windows network with these machines?

---

### Post by roasterx on 2009-09-15
> **mike555 said:**
> a little more info would help, when you say "lab machines" does that mean they are independent desktops running sharing or what?

Yes they are independent desktops that will be sharing (and old, which is how I am able to procure them). 

Thanks so much for asking

---

### Post by roasterx on 2009-09-15
> **drinkpepsi said:**
> Which version of Ubuntu are you using? When you say join the network, is this a new network between the lab machines, or you are trying to join an existing windows network with these machines?

I am using Ubuntu 9.04 and I am trying to join the existing school network.

Thanks so much for helping. If you guys keep asking, I will learn the answers and someday this puppy will work.

---

### Post by Barrucadu on 2009-09-15
Does the network use DHCP, or does each computer have a static IP?

---

### Post by halitech on 2009-09-15
Also, does Windows require logging into a Domain Controller in order to access the network? If it does, Ubuntu will require this as well.

---

### Post by roasterx on 2009-09-15
> **Barrucadu said:**
> Does the network use DHCP, or does each computer have a static IP?


The school network uses DHCP. 

Thank you for asking.

---

### Post by bacardiandwatermelon on 2009-09-15
> **halitech said:**
> Also, does Windows require logging into a Domain Controller in order to access the network? If it does, Ubuntu will require this as well.

**I was going to say this... You may need to install likewise-open to authenticate with the ad**

---

### Post by stderr on 2009-09-15
Yes, check the above first. 

Should that not be the case, I wonder what steps you've taken to try and make a connection, if any? 

I'll just give a brief, very basic, introduction:

By default, Ubuntu uses NetworkManager to handle wired and wireless connections. You can configure the connections with the NetworkManager utility under System->Administration->Network. Assuming you're connecting the PCs with ethernet cables, click Unlock, then select Wired connection, and click Properties. I would expect 'Enable roaming mode' to be selected: this essentially means use DHCP, which is what you want.

If you didn't see a Wired connection selection in the window, then open a terminal (Application->Accessories->Terminal) and run this command:

```
ifconfig
```

That lists your network devices; if we're talking about a wired connection, I'd expect to see an entry for "eth0" (= the 0th ethernet connection) in the list, and some information beside it. You will also see an entry called "lo" (= loopback). Don't worry about that.

( 
If you happen to be trying to make wireless connections, additionally running the following command (which lists all wireless devices) will provide us with even more useful information:

```
iwconfig
```
)

Another place to look is in the file "/etc/network/interfaces". This is owned by the "root" user, so if you want to make changes to the file, you have to have root permissions. However, at the moment, we just want to read it, so we don't need root permissions. It contains instructions for loading network devices on startup; but there's a little getcha, for any network devices listed in here will be handled by Linux's basic networking scripts, and not by NetworkManager. Any other devices not listed in here will be handled by NetworkManager. 

You can read the file by executing

```
gedit /etc/network/interfaces
```

You could expect to see something like this (which is fine):

```
auto lo
iface lo inet loopback

```

I'm not really proposing any solutions yet, just trying to familiarise you a little more with how some basic network configuration can be carried out. I would ask you to post the output of ifconfig (and iwconfig if applicable) and your /etc/network/interfaces, but since you haven't got a network connection on those computers, it may be easier to just give us the gist - what were the settings in the NetworkManager configuration utility, what network devices showed up on ifconfig/iwconfig, and what network devices showed up in /etc/network/interfaces?

Oh, and if you could clarify as to what type of connection you're trying to forge - wired or wireless :) In the eventuality that you're creating wireless connections, is there any wireless security set up on the network?

---

### Post by roasterx on 2009-09-15
> **roasterx said:**
> The school network uses DHCP. 

Thank you for asking.

OK, I am an idiot.. I know. The school network does not use DHCP. It uses static IP, and I have been given an address. 

Isn't a Domain Controller a part of NT? We don't use NT, but we do use Novell. 


Thank you so much for all of your help.

---

### Post by gordintoronto on 2009-09-15
> **roasterx said:**
> 
Tell me what I need to do and I will do it. 



Were the same computers previously connected to the network?  How did they connect?  Or how do other computers connect?

Oh, and you will get better/faster help next time if your message subject attracts people who might have the answer, such as "Need to connect to Windows NT Server" or whatever.

---

### Post by roasterx on 2009-09-15
> **gordintoronto said:**
> Were the same computers previously connected to the network?  How did they connect?  Or how do other computers connect?

Oh, and you will get better/faster help next time if your message subject attracts people who might have the answer, such as "Need to connect to Windows NT Server" or whatever.


The same computer was connected to my network, but that was when it had XP as its OS. 

Thanks for the tip, I'll remember that next time.

---

### Post by roasterx on 2009-09-15
OK, we are making some genuine progress. 


I have entered the DNS, gateway, subnet, etc. I can tell that I am connected to the network, because I can see the network.

I cannot, however, access the internet via Firefox now.

---

### Post by roasterx on 2009-09-16
Anyone?

---

### Post by madnessjack on 2009-09-16
You may need to get a proxy address from your IT department, they should be able to help with gateway stuff. Hope this helps.

---

### Post by roasterx on 2009-09-16
> **madnessjack said:**
> You may need to get a proxy address from your IT department, they should be able to help with gateway stuff. Hope this helps.

Where do I enter the proxy address into Ubuntu?


Thanks for replying

---

### Post by del_diablo on 2009-09-16
For firefox just to browse the web:
Edit ---> Preferences ---> Advanced ---> Network, then there is a button marked Settings. A Window will now pop up, set it the the 2nd one form the top(it reads: "Auto-detect proxy settings for this network".
Se if your school got any guide for connecting with an outsider computer, it usually says what the proxy is. I think there is a way to set it for the entire system, i would however not know. I do set each application to use proxy myself, but that is another matter.

---

### Post by pirate paul on 2009-09-16
> **bacardiandwatermelon said:**
> **I was going to say this... You may need to install likewise-open to authenticate with the ad**

Bacardi is an offencive brand name..... Drink Scotch or white rum. bacardi test on animals and do not participate in fair trade. B00000000000000000000000000

BOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO

---

### Post by roasterx on 2009-09-16
> **del_diablo said:**
> For firefox just to browse the web:
Edit ---> Preferences ---> Advanced ---> Network, then there is a button marked Settings. A Window will now pop up, set it the the 2nd one form the top(it reads: "Auto-detect proxy settings for this network".
Se if your school got any guide for connecting with an outsider computer, it usually says what the proxy is. I think there is a way to set it for the entire system, i would however not know. I do set each application to use proxy myself, but that is another matter.


That did it!!!

Thank you all for your help!

Long live open source.

---

### Post by roasterx on 2009-09-16
I am writing this post from the very machine that I was having problems with.


Thank you all again.

---

### Post by del_diablo on 2009-09-17
Just nice to help :P

---

### Post by wobin77 on 2009-09-17
> **del_diablo said:**
> Just nice to help :P

It's sometimes the most simple solution which gives an answer to the most difficult questions!  ;-)

---

