---
title: "Ubuntu 8.10 runs very slowly, MacBook"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Gyroscope352 on 2009-04-06
Alright, guys, I'm sure you get noob stuff like this all the time, but I haven't found anything helpful in my searches.

I am running Ubuntu 8.10 on a MacBook 1,1. When I first got it, it was unbearable (windows often stopped responding for ~30 seconds, greying out), but after the updates it has improved a bit (though it is still painfully slow at points). When normal, it's pretty fast, but every so often (okay, it's pretty often, like once every minute or so) the system will just pause for, like, 10 seconds and have to catch up to whatever I am doing. Typing, scrolling, even moving my mouse over items in the drop-down menu bar. It will just stop responding for a second, and then eventually will catch up and highlight the item, or finish typing the text, or scroll down. What is wrong and how can I fix it?

---

### Post by linux_lover69 on 2009-04-06
Have you tried using another desktop environment like xfce?

---

### Post by Temposs on 2009-04-06
To try out xfce, open a terminal(Applications->Accessories->Terminal), then type:

```
sudo apt-get install xfce4
```

After it installs, log out and at the login screen, click the "Options" button at the bottom left, and click "Choose Session", then you should see XFCE as one of the options. Choose it and then login. You should load into the XFCE environment.

---

### Post by Gyroscope352 on 2009-04-06
> **linux_lover69 said:**
> Have you tried using another desktop environment like xfce?

I have not. How would I go about that, and would it ruin any themes I have installed?

---

### Post by Gyroscope352 on 2009-04-06
> **Temposs said:**
> To try out xfce, open a terminal(Applications->Accessories->Terminal), then type:

```
sudo apt-get install xfce4
```

After it installs, log out and at the login screen, click the "Options" button at the bottom left, and click "Choose Session", then you should see XFCE as one of the options. Choose it and then login. You should load into the XFCE environment.

Aaaaaand there we go. Would it mess up my installed themes though?

---

### Post by LowSky on 2009-04-06
XFCE is is different desktop altogether, it wont use you Gnome Themes.

Also try turning off compiz or desktop effects to get more speed out of the machine. If ita a Macbook you shouldn't really have such issues. The processor on those released even in 2006 is quite fast. hell my old Dell with only a P3 at 1 Ghz is not that bad. It works just fine

---

### Post by Gyroscope352 on 2009-04-06
Alright, XFCE did not solve the problem. I'm still having the exact same issues as before.

Any other possible solutions? I forgot to mention that I am running on 2 GB of RAM, making this even more curious.

---

