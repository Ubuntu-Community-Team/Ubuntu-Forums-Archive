---
title: "Internet died on one comp on network"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by akatsuki on 2008-11-15
I've been using ubuntu for 6 months now, but I'm pretty much still a noob.

Yesterday, my ubuntu desktop completely loses internet while my sister was surfing the net. It's only a network w/ a ubuntu laptop and windows xp laptop. The two laptops still have internet and are functioning completely fine. The desktop can still do everything but go online. 

When I reboot it, it goes through the load-up screen w/ the completion bar and then goes to the text-load part. This is like the terminal screen, it says what's being loaded and what's [OK]. It goes through this part real fast, but I catch a red [FAIL] for the first/second load process. Can't quite make out what failed to load since it's scrolling through too fast. Then I see another one at the bottom, about the network manager having some issue. Can't quite make out what the rest of the message says.

After it finishes booting up, I check the network manager, nothing seems wrong, so I have no clue what's going on. 
I also have firestarter installed. When I tried to turn it off to see if it's causing any problems, it refuses to load up. 

I've checked all the cables, even tried a new one that I've checked using my laptop, and made sure everything's connected correctly.

Now, I'm just confused about what's going on and what's wrong w/ my comp. 
Please help this n00b. thanks!

---

### Post by cariboo on 2008-11-15
There are a couple of things we need to know, in a terminal type:

```
sudo lshw -C network > network.txt
```

This will print out what type of network card and which driver it uses. The above command pipes the output to a text file, so you can copy it to your windows partition and let us see the outoput of the above command.

BTW if things are scrolling by to fast in a console just press the pause/break key to stop the scolling.

Jim

---

### Post by akatsuki on 2008-11-15
here's the output of the network stuff

btw, thanks for the pause/break tip

---

