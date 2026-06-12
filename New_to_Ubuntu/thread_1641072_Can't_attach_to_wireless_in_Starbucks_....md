---
title: "Can't attach to wireless in Starbucks ..."
date: 2010-12-08
forum: New to Ubuntu
---

### Post by hamstermoon on 2010-12-08
Has anyone had this problem before? 

I have Ubuntu on an MSI Wind U230 and when I go to Starbucks I can't get it to attach to their free wireless. Apparently I am supposed to be able to point the browser to the correct signal and then Firefox etc. should jump to their welcome page so I can log in. 

There were plenty of people in there using Macs and Windows without any problems but I couldn't do anything with it.

I manage quite easily at home with my wifi router and have used it out and about in several places (including a motorway service station on the M4 and Bristol Museum!) but no luck in Starbucks in Maida Vale in London!

---

### Post by sandyd on 2010-12-08
> **hamstermoon said:**
> Has anyone had this problem before? 

I have Ubuntu on an MSI Wind U230 and when I go to Starbucks I can't get it to attach to their free wireless. Apparently I am supposed to be able to point the browser to the correct signal and then Firefox etc. should jump to their welcome page so I can log in. 

There were plenty of people in there using Macs and Windows without any problems but I couldn't do anything with it.

I manage quite easily at home with my wifi router and have used it out and about in several places (including a motorway service station on the M4 and Bristol Museum!) but no luck in Starbucks in Maida Vale in London!
I *had* the same problem here.

It mainly is because the address for the welcome page cannot be resolved correctly, because in order for DNS lookups to work, you have to have access to a DNS server.

Which you don't, since you have to enter the welcome page first.

From a windows computer, ping the domain of the welcome page when it shows up.

i.e.
if the address is [http://google.com/fjfjfjfkjl](http://google.com/fjfjfjfkjl), you would run
```

ping google.com
```
in a command prompt.

Pinging the domain should show the ip address.
Write it down.

back in linux, run
```

sudo nano /etc/hosts

```
add this to the bottom of the file

```

ip-address-you-wrote-down domain
```
replace 'ip-address-you-wrote-down' and 'domain' with the correct stuff.

---

### Post by hamstermoon on 2010-12-08
Just had a thought  here ...

Presuming you are in the UK, do you know if Costa causes the same problem? They do cheaper coffee and also supply the internet free rather than you having to have a Starbucks card with money on it :p.

---

### Post by sandyd on 2010-12-08
> **hamstermoon said:**
> Just had a thought  here ...

Presuming you are in the UK, do you know if Costa causes the same problem? They do cheaper coffee and also supply the internet free rather than you having to have a Starbucks card with money on it :p.
[IMG]http://img716.imageshack.us/img716/9281/snapshot2b0.png[/IMG]
I have no idea. :P

---

### Post by ExileSith on 2010-12-08
Something similar but pretty different happened to me:

I was well within range of a wifi connection, but Ubuntu wouldn't acknowledge it at all, so I turned the wireless in my blackberry on, which connected at once, and then, noting the name of the signal, clicked on "Connect to hidden something(signal?)", entered it, and voila! It connected at once.

---

### Post by leclerc65 on 2010-12-08
My case is also different:
Clicking on the free website (DistrictMontreal.com, and one hotel in Ottawa) I will be lead to a website named Eyeinwireless.com before getting the welcome page. Then as long as use Windows they will leave me alone, otherwise I will get kicked out and cannot re-connect.
I cannot get get rid of Windows because of this. I travel with my eeePC for its feather weight, but I am really pissed because it run very slow with Win.

---

### Post by ExileSith on 2010-12-08
> **leclerc65 said:**
> My case is also different:
Clicking on the free website (DistrictMontreal.com, and one hotel in Ottawa) I will be lead to a website named Eyeinwireless.com before getting the welcome page. Then as long as use Windows they will leave me alone, otherwise I will get kicked out and cannot re-connect.
I cannot get get rid of Windows because of this. I travel with my eeePC for its feather weight, but I am really pissed because it run very slow with Win.

Dont really know if it would help, but what about installing wine, then installing a browner inside wine, and accessing the page from there?

---

### Post by beew on 2010-12-08
It is ridiculous that you would need to keep windows or use WINE just for that. Is there no Linux work around? It needs to be addressed, if Linux fails at a basic task like connecting to free wifi how can it be taken seriously?

---

### Post by hamstermoon on 2010-12-09
@ SD (oops ...) 

Looks like I am going to have to take the notebook out and try it in Costa and then report back. I have to go off to meet someone in a coffee shop next week so I will do that as preference.

---

### Post by leclerc65 on 2010-12-09
> **beew said:**
> It is ridiculous that you would need to keep windows or use WINE just for that. Is there no Linux work around? It needs to be addressed, if Linux fails at a basic task like connecting to free wifi how can it be taken seriously?
It doesn't fail to connect. It looks like the intermediate web site (Eyeinwireless) discriminates against Linux. I wonder how they treat iPods, iPads etc...
I tried Ubuntu, Fedora, Puppy all fail after a while. Puppy is the longest lasting (3 days or so).
I have no problem with Windows, I have XP dual boot on my other laptop. 
But why the hell they have grudge with Linux ?

---

