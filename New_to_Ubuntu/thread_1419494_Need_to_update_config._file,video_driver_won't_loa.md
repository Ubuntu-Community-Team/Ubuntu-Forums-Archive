---
title: "Need to update config. file,video driver won't load"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-03-01
I'm on Ubuntu 9.10,a new user for about a week, and I did the Hardware search for driver for this older GeForce card(MX 400);it downloaded;I restated,but error comes up "problem parsing the config.file.Please update config file."So it is running on low graphics mode.Can someone help me to edit what I need to edit,so the driver will be enabled?and........step by step,I know nothing about editing,especially on Ubuntu

---

### Post by sandyd on 2010-03-01
> **Ben_222 said:**
> I'm on Ubuntu 9.10,a new user for about a week, and I did the Hardware search for driver for this older GeForce card(MX 400);it downloaded;I restated,but error comes up "problem parsing the config.file.Please update config file."So it is running on low graphics mode.Can someone help me to edit what I need to edit,so the driver will be enabled?and........step by step,I know nothing about editing,especially on Ubuntu

choose "exit to console login"
login using your username and password.
then at the prompt, type in
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo shutdown 0 -r
```

---

### Post by Ben_222 on 2010-03-02
Thanks,carlee,I had to go back to Hardware and reinstall,but now it is working great.Thank you so much,you are awesome!

---

