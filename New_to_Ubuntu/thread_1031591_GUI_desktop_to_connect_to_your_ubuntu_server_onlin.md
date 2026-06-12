---
title: "GUI desktop to connect to your ubuntu server online"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by hosdes on 2009-01-05
Instead of using a terminal or ssh software, is there a way to use a gui that connects to your ubuntu 8.04 LTS server edition.  We have a minimual system installed on our dedicated server.  I see with ubuntu desktop edition it comes with a GUI that you can search or find packages through synatic package manager.

---

### Post by albinootje on 2009-01-05
> **hosdes said:**
> Instead of using a terminal or ssh software, is there a way to use a gui that connects to your ubuntu 8.04 LTS server edition.  We have a minimual system installed on our dedicated server.  I see with ubuntu desktop edition it comes with a GUI that you can search or find packages through synatic package manager.

With ssh you can use the "X11 forwarding" with :
```

ssh -X 

```
and after that you can start your graphical application.
The X11 forwarding should work also with putty as ssh-client.

Other options are VNC :
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
and FreeNX :
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by LowSky on 2009-01-05
i guess you could remote desktop into the server, just install a  light weight gui on the server like fluxbox or xfce, both are in the repos and can be easily added to the server edition

---

### Post by masque7 on 2009-01-05
> **hosdes said:**
> Instead of using a terminal or ssh software, is there a way to use a gui that connects to your ubuntu 8.04 LTS server edition.  We have a minimual system installed on our dedicated server.  I see with ubuntu desktop edition it comes with a GUI that you can search or find packages through synatic package manager.
You may found [this](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6) tutorial/guide useful

---

### Post by hosdes on 2009-01-05
thank you all for quick responses.

after I do "ssh -X" and install fluxbox from repos, how do I view it.  Connect my desktop to fluxbox to our server?  I could not get xfce or vnc from repos.

---

### Post by LowSky on 2009-01-05
VNC is a type of program one of the most popular is
vinagre

[https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

for xfce
```

sudo aptitude install xfce4
```

---

### Post by albinootje on 2009-01-05
> **hosdes said:**
> thank you all for quick responses.

after I do "ssh -X" and install fluxbox from repos, how do I view it.  Connect my desktop to fluxbox to our server?  I could not get xfce or vnc from repos.

After you've logged in with "ssh -X" you can start the application you want, for example :
```

sudo apt-get install synaptic
gksu synaptic

```

---

### Post by hosdes on 2009-01-05
when I did 
```
sudo aptitude install xfce4
```

it is installing all kinds of stuff.  lots.  it look like it was installing stuff all over again. normal?

then with step 2 I did this
```
sudo apt-get install synaptic
sudo apt-get install gksu
gksu synaptic
```

when I did gksu synaptic, it says "(gksu:9578): Gtk-WARNING **: cannot open display: "

---

