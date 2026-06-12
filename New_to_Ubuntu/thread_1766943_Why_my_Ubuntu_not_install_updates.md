---
title: "Why my Ubuntu not install updates?"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by H A NAZIR on 2011-05-25
Few days ago i start installing updates but during installation of updates light goes off (because i live in Pakistan and here is an electricity problem).After some time i start my computer again and go to Update Manager but when i click on updates it prompts about Partial Updates and Cancel.Then i click on Partial Updates after some processing with in a minute the updates finishes.And now whenever i log onto my computer it shows the message of Partial Update and Cancel.So please guide me about this problem
And from that day my ubuntu also giving me Software Installation failed problem(When i start installing software it gives me error "Software Installation or removal fails)and i cannot install any software
Please solve my problem

---

### Post by NightwishFan on 2011-05-25
I would open the terminal and run the command:
```
sudo apt-get -f install
```

Make sure it does not ask to 'remove' a lot of packages you know you need. It shouldn't but under severe circumstances it might.

---

### Post by H A NAZIR on 2011-05-25
> **NightwishFan said:**
> I would open the terminal and run the command:
```
sudo apt-get -f install
```

Make sure it does not ask to 'remove' a lot of packages you know you need. It shouldn't but under severe circumstances it might.

What is debian6 and what are its advantages?

---

### Post by NightwishFan on 2011-05-25
I suppose this is a bit off topic... Ubuntu is based on another Linux system called Debian. I find it to be more reliable and clearer defined about what is free or not. I suppose the Debian site itself can explain it best:

[http://www.debian.org/intro/why_debian](http://www.debian.org/intro/why_debian)
[http://www.debian.org/social_contract](http://www.debian.org/social_contract)
[https://secure.wikimedia.org/wikipedia/en/wiki/Debian](https://secure.wikimedia.org/wikipedia/en/wiki/Debian)

Did my command work for you?

---

