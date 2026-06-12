---
title: "cant connect to &quot;network wifi(?)&quot;"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by libihero on 2011-05-30
i dont know what its called exactly, but my family has set up wifi that originates from one of our laptops. i can connect to it here on windows (it is called a public network), and i can see it on ubuntu, but when i click on it nothing happens. instead of the "wave" image on wireless, the image looks like a wired network image. any idea how i can get it to connect? sry for such a noobie description lol

---

### Post by wildmanne39 on 2011-05-30
> **libihero said:**
> i dont know what its called exactly, but my family has set up wifi that originates from one of our laptops. i can connect to it here on windows (it is called a public network), and i can see it on ubuntu, but when i click on it nothing happens. instead of the "wave" image on wireless, the image looks like a wired network image. any idea how i can get it to connect? sry for such a noobie description lol
Hi, I am not an expert I can only suggest basic things, right click on the icon that looks like a wire internet it should show wireless network make sure it is enabled, then you should be able to enter your password so you can connect with your router.

---

### Post by webofunni on 2011-05-30
are you able to see it on

```

sudo iwlist wlan0 scan | grep -A 25 -B 5 -i public

```

change the "public" to the actual id of the network, as per you mentioned it is public.

---

### Post by jtarin on 2011-05-30
Is the transmitting device secured or open? You might need to allow your device to connect.

---

### Post by libihero on 2011-06-05
@webofunni it does show up when i put that in the terminal
i attached an image to make it more clear what i mean. when i click "malek", the menu disappears and absolutely nothing happens (no spinning icon that the internet is even trying to connect)

---

### Post by jtarin on 2011-06-05
Though I haven't used it there is a[ command-line]("http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html") tool for controlling NetworkManager.This link includes the page for downloading for Ubuntu.

---

### Post by webofunni on 2011-06-06
check the logs to see what happens 

```

tail -f /var/log/syslog

```

Usually the network manager log goes to that file

check

/etc/rsyslog.d/50-default.conf to see the actual log file, if there is nothing in the above log

---

