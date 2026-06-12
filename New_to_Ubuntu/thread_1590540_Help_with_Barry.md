---
title: "Help with Barry"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by DrGonzoRIP on 2010-10-08
I need help with Barry. I've installed all sorts of Barry packages. but am at a loss as to how to use it or get it to work. I looking to tether my Verizon Blackberry Storm 2. I'm running Ubuntu 10.04. I do have the tethering feature on my account.

---

### Post by LinksPatrocinados on 2010-10-08
Have you tried to uninstall and install all over again beginning the zero?

---

### Post by DrGonzoRIP on 2010-10-08
I haven't tried that. I guess what I'm looking for is what the next step after installing Barry is. Everything I've found thus far has been kinda vague.

---

### Post by richwillal on 2010-10-24
I'm using the current version of barry, and Ubuntu 10.10 and also trying to tether my Storm 2.  In the past once installing barry, I needed to edit the /etc/ppp/peers/barry-verizon script to include the password, and then start tethering in a terminal window using the following command:

```
sudo pppd call barry-verizon
```

A <ctrl>-C stopped it when I was ready to disconnect.  Now the same change fails to connect.  I get the following error:

```
exception caught in main(): Logic error: No password provided in SendPassword.
```

Any progress or hints are appreciated.

---

### Post by pgoffa01 on 2010-10-26
I'm using a Curve 3G 8530 w/ Sprint and I cannot figure out barry or opensync either.  I installed them in CLI and I got nothing.  I cannot believe that RIM did not make desktop software for Linux when they are both huge in the business market.  Unbelievable...any help would be appreciated.  I just want to access my media card via buntu and sync contacts and calendar to evolution.

---

### Post by simguru on 2011-01-10
> **richwillal said:**
> I'm using the current version of barry, and Ubuntu 10.10 and also trying to tether my Storm 2.  In the past once installing barry, I needed to edit the /etc/ppp/peers/barry-verizon script to include the password, and then start tethering in a terminal window using the following command:

```
sudo pppd call barry-verizon
```

A <ctrl>-C stopped it when I was ready to disconnect.  Now the same change fails to connect.  I get the following error:

```
exception caught in main(): Logic error: No password provided in SendPassword.
```

Any progress or hints are appreciated.

I received this error while dialing barry-att_cingular. Do you have a device password enabled? The device password, even while the device is unlocked, seems to preclude the Blackberry from sending the login information to the barry library. Disabling the device password fixed the problem.

---

### Post by Leonardo Helman on 2012-04-23
You can also pass -P password parameter to pppob (called on /etc/ppp/peers/yourconnection"

---

### Post by oldos2er on 2012-04-24
Old thread closed.

---

