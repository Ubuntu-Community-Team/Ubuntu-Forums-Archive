---
title: "Firestarter question"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Foxfire on 2009-01-04
When you install firestarter can you choose a differnt password then the one you log in with

---

### Post by bodhi.zazen on 2009-01-04
yes but you must do some fancy configuration.

FYI : Firestarter is no longer maintained and may not be the best option for you.

By default Ubuntu uses ufw and if you want a graphical interface install gufw

---

### Post by kansasnoob on 2009-01-04
Or if you have a simple configuration, like one computer - no networking, just run the command from terminal:

```
sudo ufw enable
```

And I don't think gufw is available in the 8.04 repos yet.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

I wish Firestarter were still in dev. I liked the gui log!

---

### Post by Foxfire on 2009-01-04
whats the best firewall to use then?

---

### Post by adult swim on 2009-01-04
they are all using the same firewall, it is just a different means of configuring it

---

### Post by hammondb3 on 2009-01-04
> **kansasnoob said:**
> Or if you have a simple configuration, like one computer - no networking, just run the command from terminal:

```
sudo ufw enable
```

And I don't think gufw is available in the 8.04 repos yet.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

I wish Firestarter were still in dev. I liked the gui log!

Hey Is Firestarter still used, does anyone use it for Ubuntu?

---

### Post by hammondb3 on 2009-01-04
Does anyone use Firestarter for Ubuntu still

---

### Post by amauk on 2009-01-04
> **hammondb3 said:**
> Does anyone use Firestarter for Ubuntu still
I do

---

### Post by hammondb3 on 2009-01-04
I read somewhere that its not maintaned any longer 
what does that mean

---

### Post by HermanAB on 2009-01-04
Unmaintained means that no-one is fixing any new found bugs.  It works.  You can use it.

Cheers,

Herman

---

