---
title: "Realtek 8172 wireless card driver"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-08-10
Okay, so I'm on Ubuntu 9.10 - I would update to 10.04 but I cannot connect to the internet with my Ubuntu machine. Naturally, being able to update to 10.04 would resolve this issue.

Now then, this page: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

Now, to give you an idea why this next part wasn't resolved in a few seconds, refer to the initial sentence: I can't connect to the internet with the ubuntu machine.

Gives me a driver originally for 8192SE which works as well with 8172. In order to use that, I need the linux headers, which I have, and build-essential, which I don't.

To install build-essential, I need g++ at 4:4.3.1
To install g++ 4:4.3.1 (in this case 4:4.4.1)ubuntu9 I need gcc-4.4-base-ubuntu9
I cannot install gcc-4.4-base because it breaks the existing package libgcc1 which depends on gcc-4.4-base-ubuntu8 (these names are slightly simplified for clarity)
I cannot install libgcc1-ubuntu9 because I do not have gcc-4.4-base-ubuntu9

Let me repeat that - I need gcc-4.4-base-ubuntu9 to install libgcc1-ubuntu9, whilst I cannot install gcc-4.4-base-ubuntu9 because it breaks libcc1-ubuntu8.

I am officially out of ideas.

---

### Post by Peter09 on 2010-08-10
Just double checking here - presumably this is a laptop because of your wireless requirements. You do not have access to a hard wired connection anywhere?
 
It is most probably the case that if you can update the system then your wireless problems will be resolved as well.
 
Perhaps the first question is - how do I a get a wired connection ...... even an old modem.
 
Sorry if this does not really answer your question - but its worth re-examining your options.

---

### Post by Elsoreth on 2010-08-10
> **Zeppelin! said:**
> Okay, so I'm on Ubuntu 9.10 - I would update to 10.04 but I cannot connect to the internet with my Ubuntu machine. Naturally, being able to update to 10.04 would resolve this issue.

Someone can correct me if I'm wrong, but if you can get the 10.04 iso to the ubuntu machine I believe there is a way to update from that.

For more information, [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) shows how after it shows how to do it when connected.

---

### Post by Zeppelin! on 2010-08-10
This is in fact a laptop, and in a few days I may be able to get ahold of a 10.04 disc for that, but until then my laptop is a brick, a state of affairs I do not hold with, which is why I'm putting so much effort into getting it running.

Though, to be clear, a clean 9.10 install /can/ mount .ISO yes?

As stated though, that's a few days away. Is there anything I can do to get to the bottom of this dependency tree I'm in (If you want to compare what I have, this is, again, a clean install of 9.10) before then? Would a slightly older version of build-essential work without upgrading all of those, and if so how would I find it?

Thanks for your assistance, by the by. Should have said that in the opening but I was tired and frustrated.

---

### Post by Zeppelin! on 2010-08-14
So, I updated to 10.04, and maybe my wireless card works.

Maybe.

I don't have wi-fi personally available yet, so I'm testing it out with public wi-fi.

I tried an internet cafe sort of dealie, and they had this 'portal' system, where your laptop connects to the wireless network and then is directed automatically to a page discussing the terms and conditions, which you accept, and once you've accepted can use the wireless freely. After getting the name of the network -the cafe's name- the wi-fi said it was connected at 0%. But the page never showed. I discussed it with their help line, but we were unable to get a workaround up.

So, I tried a public free wi-fi node, but this one also had a portal system, and the same problem. However, it showed me as connected 84% when outside the building the node was situated in.

I have yet to find a way to determine if the portals are my main issue.

That said, know anything about this?

---

