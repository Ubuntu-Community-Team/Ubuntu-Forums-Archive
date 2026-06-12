---
title: "google earth"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by rohan1 on 2009-02-06
Hi

Just downloaded google earth via synaptic manager...installation complete msg received..however I cannot find the application to launch....using hardy heron 8.04..thanks

---

### Post by TAFKARS on 2009-02-06
> **rohan1 said:**
> Hi

Just downloaded google earth via synaptic manager...installation complete msg received..however I cannot find the application to launch....using hardy heron 8.04..thanks

Applications > Internet > Google Earth  Should get you going, or type googleearth from a terminal and it should launch automatically,

---

### Post by rohan1 on 2009-02-06
Tried in terminal..says location of file not found...neither is it available in applications>internet

---

### Post by hyper_ch on 2009-02-06
please copy'n'paste the output of

```

googleearth

```
when typing it into the terminal.

---

### Post by rohan1 on 2009-02-06
bash: googleearth: command not found

---

### Post by hyper_ch on 2009-02-06
and what's the result of:
```

sudo apt-get install googleearth

``` ?

---

### Post by rohan1 on 2009-02-06
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth

---

### Post by hyper_ch on 2009-02-06
there we go, you obviously didn't download and install googleearth through synaptic.

My advice is to add the medibuntu repos and then download and install googleearth through synaptic.

---

### Post by rohan1 on 2009-02-06
hmmm...strange that!..will do as suggested..thanks

---

### Post by grs on 2009-02-06
I used this guide 

[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/) 

to install Googleearth. It installed fine but when I try to run a window spops up saying it can not create the cache directory, then a second saying that is has place the cache directory at /home/grs/.googleearth/cache  The program tries to load then quits straight away. Any ideas?

---

### Post by hyper_ch on 2009-02-06
grs: I'd say remove that one and use medibuntu to install googleearth

---

### Post by stchman on 2009-02-06
> **rohan1 said:**
> Hi

Just downloaded google earth via synaptic manager...installation complete msg received..however I cannot find the application to launch....using hardy heron 8.04..thanks

Googleearth is not available via the regular repos.  You have to go to Medibuntu to get it.  I am assuming you added the Medibuntu repos.

---

### Post by grs on 2009-02-07
I don't think I installed Mdeibuntu, Whats the command to uninstall googleearth, is there a guide for installing by Medibuntu?

---

