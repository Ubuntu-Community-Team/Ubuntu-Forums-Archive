---
title: "Login pop up error?"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by rom3lol on 2011-02-07
I just recently installed guarddog firewall and messed around with the settings and then I uninstalled it.
Right now I rebooted my laptop and logged in an a error comes up

```
Could not update ICEauthority file/home/username/.ICEauthority
```

Thanks for all the help :)

---

### Post by rom3lol on 2011-02-07
Well I managed to fix it 
```
sudo rm .ICEauthority
```

But I still cant access the internet?

---

### Post by rom3lol on 2011-02-08
Can anyone help me? 
The problem occured when I installed guarddog then I removed it and rebooted ubuntu then I can't connect to the internet although it says im connected.

```
ping www.google.com
unknown host www.google.com

```

Is their a way to reset my iptables to the original file?

---

