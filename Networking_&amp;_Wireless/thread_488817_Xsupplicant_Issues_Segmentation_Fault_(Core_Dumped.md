---
title: "Xsupplicant Issues: Segmentation Fault (Core Dumped)"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by makaira on 2007-06-30
I'm using Feisty Fawn on a Macbook Pro Core Duo (15"). I need to install Xsupplicant because my university uses PEAP. Here is what I've done:

(1) I apt-get'ed Xsupplicant and installed it. 

(2) I've downloaded both the "xsupplicant.conf" and "entrust.pem" from my university's website. I've edited the conf file with the correct information and moved both files to the /etc directory.

(3) I did an "iwconfig" to get the list of connections and have lo, eth0, wifi0, and ath0. ath0 is the wireless connection.

(4) I followed my university's directions and did:

```

xsupplicant -i ath0 &

```

What follows is the line:

```

Starting XSupplicant v. 1.2.4

```

the line below it has a blinking black box, but nothing actually happens. It seems as if it stalls. As soon as I hit any key, however, it gives me the line:

```

[1]+  Done                    xsupplicant -i ath0

```

So, I assume that it's done what I wanted it to do, and I move onto the next step.

(5) The uni directions say to give it this command:

```

xsup_set_pwd -i ath0

```

I do it, and it then asks me:

```

Please enter your password : 

```

which I do. Then it says:

```

Sending :

Segmentation fault (core dumped)

```

Now I'm not sure what to do.

---

### Post by makaira on 2007-06-30
If nobody has any idea on this (I was asking on irc as well), are there any other options for me to get PEAP working?

---

### Post by makaira on 2007-06-30
Disregard the thread. I got to frustrated with xsupplicant so I tried wpa_supplicant and it's working just fine. 

Now, if ubuntu could only make the uni's wireless signal stronger :)

---

