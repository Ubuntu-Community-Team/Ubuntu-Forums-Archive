---
title: "eth1 save settings"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by gigaferz on 2006-11-18
Hello!

I just want to acomplish something that sounds very simple.

Let me explain myself.

Ever since I satrted used ubuntu , ive managed to help myself out of the most common problems.

Now my headache.

I need to have these settings in order to have Internet.

10mbps @ Full Duplex

I type in the terminal " sudo mii-tool -F 10baseT-FD eth1 " 

After this I need to do a "ctrl+alt +Backspace", Only doing it this way I will get access to the Internet.

Everyday I reboot or startup the computer, I need to do this.

So I am just asking how to keep these settings for everytime I Reboot or whenever I turn on the computer.

What is the name of that file?

Or should I download some kind of network manager I heard somebody talked about?

---

### Post by pdub on 2006-11-18
I used this method a while ago to solve a similar problem.

[http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html](http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html)

---

### Post by gigaferz on 2006-11-19
Thanks a lot...now... My concern is ethtool has never worked for me... Well it works to see the settings.. but if I wan to change the settings ethtool does not work, that is why I use mii-tool.

Anyway thank you for your reply, I'll give it a try .

---

### Post by dmizer on 2006-11-20
there's probably a far more elegant way of doing this but, this should be functional for ya.

edit /etc/rc.local as root with your favorite text editor and add the line:
```
mii-tool -F 10baseT-FD eth1
/etc/init.d/networking restart
```
before the line that says "exit 0"

save ... reboot ... should be all better.  if not, let me know and i'll come up with an alternative.

---

### Post by gigaferz on 2006-11-20
I did it, 
I rebooted a couple of times and The internet its available right away!

Thank you.

Now I also detected another minor problem.

On system-admin-Networking, There is a box below that says "Default gateway device" sometimes is blank and only by selecting eth1 I'll get the internet working, but well That happens 2 out of 10 times, so I guess is not that bad, but for some people might be too much trouble..

I think Its good to have all kinds of questions and answers for all the incoming ubuntu users.

Thank again!

---

### Post by gigaferz on 2007-03-14
Hello, I just installed Ubuntu Gameres edition wich is based on edgy.

So I just want to do the same thing mentioned above to make the settings permanent to 10mbps Fullduplex.

I tried already but there is no line "exit 0"

Thank you1

---

