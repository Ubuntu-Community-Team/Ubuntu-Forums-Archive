---
title: "Wireless Problem with Ubuntu 8.04 LTS"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by groogruxking40 on 2009-12-29
Hey everyone,
 
 I have been tearing my hair out trying to get my wireless to work.

Specs:

Asus 701 eeePC netbook
running Ubuntu  8.04 LTS 

This is what I've done:

My netbook was giving me major problems under 9.04, it was using waaaaaay too much hard drive space and memory, so I decided to downgrade to 8.04 LTS. Well there was a problem with the downgrade because the WIRELESS DRIVERS did not download.

When I go to Admin--Hardware Drivers I get this list:

Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards

Now, I did my research by downloading the madwifi as well as the Atheros driver and ran them in the terminal. 

When I go to Admin--Wireless Network Drivers, this is what's listed:

net5211 hardware present: yes

so then I go to Configure Network and it shows my network :

2WIRE121
WPA Personal
I put in my Network Password

Connection Settings:

Automatic configuration (DHCP)

so all that is fine.

So at the top I have the double monitors.. and it gives me only one option.. Manual Network Configuration. It does not show any wireless networks

ANYONE PLEASE HELP ME!!!

P.S. I know this was a long post, I was just trying to cover all my bases

:)

---

### Post by snowpine on 2009-12-29
8.04 has terrible support for netbook hardware; I would really recommend the latest (9.10).

If you really want to stick with 8.04 for whatever reason, I recommend visiting these sites:

[http://array.org/ubuntu/](http://array.org/ubuntu/)
[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

I have a different eee model (900ha) but for me, the 8.04 array.org kernel worked like a charm. Good luck!

---

### Post by groogruxking40 on 2009-12-29
> **snowpine said:**
> 8.04 has terrible support for netbook hardware; I would really recommend the latest (9.10).

If you really want to stick with 8.04 for whatever reason, I recommend visiting these sites:

[http://array.org/ubuntu/](http://array.org/ubuntu/)
[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

I have a different eee model (900ha) but for me, the 8.04 array.org kernel worked like a charm. Good luck!

I went to array.org/ubuntu and clicked this
[http://array.org/ubuntu/faq.html?id=8](http://array.org/ubuntu/faq.html?id=8)

but I didn't even have this navigation...  /etc/lsb-release file  
how do I access it so I know which kernel to install?

thanks a lot so far

---

### Post by snowpine on 2009-12-29
> **groogruxking40 said:**
> I went to array.org/ubuntu and clicked this
[http://array.org/ubuntu/faq.html?id=8](http://array.org/ubuntu/faq.html?id=8)

but I didn't even have this navigation...  /etc/lsb-release file  
how do I access it so I know which kernel to install?

thanks a lot so far

Since you say you're using Ubuntu 8.04, I would recommend the hardy kernel from array.org (hardy-proposed might be less stable).

FYI, it is the same kernel used by Ubuntu-eee, EEEbuntu, Easy Peasy, Cruncheee etc. so it is fairly widespread and trustworthy in my opinion.

---

### Post by groogruxking40 on 2009-12-29
> **snowpine said:**
> Since you say you're using Ubuntu 8.04, I would recommend the hardy kernel from array.org (hardy-proposed might be less stable).

FYI, it is the same kernel used by Ubuntu-eee, EEEbuntu, Easy Peasy, Cruncheee etc. so it is fairly widespread and trustworthy in my opinion.

doing it now... wish me luck :)

p.s. this is my dad's netbook.. I run a sony vaio pcg-k13 with 9.04.. do you reccommend a 9.10 upgrade for mine?? is it stable yet on vaios??

---

### Post by snowpine on 2009-12-29
> **groogruxking40 said:**
> doing it now... wish me luck :)

p.s. this is my dad's netbook.. I run a sony vaio pcg-k13 with 9.04.. do you reccommend a 9.10 upgrade for mine?? is it stable yet on vaios??

Good luck! :)

I have no experience with the Sony Vaio, sorry.

---

### Post by groogruxking40 on 2009-12-29
> **snowpine said:**
> Good luck! :)

I have no experience with the Sony Vaio, sorry.

update:

followed step by step.. still nothing

do I need remove the madwifi driver?  

this is getting on my nerves!

---

### Post by snowpine on 2009-12-29
> **groogruxking40 said:**
> update:

followed step by step.. still nothing

do I need remove the madwifi driver?  

this is getting on my nerves!

You need to reboot and choose the new kernel from the GRUB menu.

No idea about your madwifi question; I've never used those particular drivers.

---

### Post by groogruxking40 on 2009-12-29
> **snowpine said:**
> You need to reboot and choose the new kernel from the GRUB menu.

No idea about your madwifi question; I've never used those particular drivers.

I did that.. rebooted.. the new kernel was the 3rd one down..

what I did notice is that it removed this:



Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards

Now it says No proprietary drivers 

still scratching my head here

---

### Post by snowpine on 2009-12-29
Assuming you've carefully followed these instructions step by step:

[http://array.org/ubuntu/setup-hardy.html](http://array.org/ubuntu/setup-hardy.html)

Then rebooted and selected the eeepc kernel from the GRUB menu...

You should have working wireless (no need to install proprietary drivers).

The only "X factor" is that I don't know what steps you've already taken prior to your first post... it is possible that something you did has disabled wireless. At this point I would refer you to the eeeuser forums (link in my first post). There are some real experts over there (including the creator of the array.org kernel).

---

### Post by groogruxking40 on 2009-12-29
> **snowpine said:**
> Assuming you've carefully followed these instructions step by step:

[http://array.org/ubuntu/setup-hardy.html](http://array.org/ubuntu/setup-hardy.html)

Then rebooted and selected the eeepc kernel from the GRUB menu...

You should have working wireless (no need to install proprietary drivers).

The only "X factor" is that I don't know what steps you've already taken prior to your first post... it is possible that something you did has disabled wireless. At this point I would refer you to the eeeuser forums (link in my first post). There are some real experts over there (including the creator of the array.org kernel).

Yup, did that.

the only X factor I can see is that I installed the Atheros driver.. and the Madwifi so maybe that screwed something up.. I'm not sure

I did post over in eeeuser just now, hopefully some kind soul will help me out

---

### Post by groogruxking40 on 2009-12-29
> **groogruxking40 said:**
> Yup, did that.

the only X factor I can see is that I installed the Atheros driver.. and the Madwifi so maybe that screwed something up.. I'm not sure

I did post over in eeeuser just now, hopefully some kind soul will help me out

UPDATE:

Installed WICD and now it's seeing my network..

only problem is that when I click the connection it just says

None: Authenticating... over and over and over

any help would be appreciated.

---

### Post by groogruxking40 on 2009-12-30
BUMP!

still need help people

---

### Post by LuisGMarine on 2009-12-30
I was having a similar problem.  What you need to do is assign your wireless device a static IP.

I don't have wicd installed, but the window where it lists your wireless device there should be an option to configure it and set the settings or IP to manual. I think it's called Advanced Settings.

This is assuming your routers IP address is 192.168.1.1

Once the window comes up click on "use static IP's"
```
IP: 192.168.1.[COLOR="Red"]15[/COLOR]
Netmask: 255.255.255.0
Gateway: 192.168.1.1
```
*note* the red number you can change to whatever you like, I usually try to stay in the .10-.25 range.  I'm not 100% sure what the actual range is for the last set up numbers.
Then click the checkbox next to Static DNS.
```
DNS 1: 192.168.1.1
```

Of course from here, click on encryption key and stuff if you are trying to connect to a secured network.

---

### Post by groogruxking40 on 2009-12-30
> **LuisGMarine said:**
> I was having a similar problem.  What you need to do is assign your wireless device a static IP.

I don't have wicd installed, but the window where it lists your wireless device there should be an option to configure it and set the settings or IP to manual. I think it's called Advanced Settings.

This is assuming your routers IP address is 192.168.1.1

Once the window comes up click on "use static IP's"
```
IP: 192.168.1.[COLOR=Red]15[/COLOR]
Netmask: 255.255.255.0
Gateway: 192.168.1.1
```*note* the red number you can change to whatever you like, I usually try to stay in the .10-.25 range.  I'm not 100% sure what the actual range is for the last set up numbers.
Then click the checkbox next to Static DNS.
```
DNS 1: 192.168.1.1
```Of course from here, click on encryption key and stuff if you are trying to connect to a secured network.

did exactly as you told me.. still nothing.. it just says

NONE: authenticating... over and over

---

