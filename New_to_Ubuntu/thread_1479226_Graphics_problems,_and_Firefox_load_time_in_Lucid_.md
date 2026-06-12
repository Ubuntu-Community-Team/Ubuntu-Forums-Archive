---
title: "Graphics problems, and Firefox load time in Lucid (HELP)"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by applet3typod on 2010-05-10
Alright, I love Ubuntu, but I am having a few issues and would like some insight from the pros(or at least someone who knows more than me...ok anyone would do)

First: Firefox is running horribly slow. I have 2 computers that had Lucid (10.04) installed on it at the same time, and they are both having this issue. I disabled the IPv6 on both machines, and it helped with a lot of OS loading issues, but the speed of Mozilla went back to a crawl the next day. (other issues stayed resolved) What could be causing two machines to have the same laggy connection?

Second: I've noticed the graphics are a little poor compared to what I was getting with Windows on the same machine. I won't go to windows for anything, and I would really like to have the quality I've come to expect from my system. (I didn't know the OS could make a difference, seeing as how it's the same GPU) 

Any advice would be helpful!

---

### Post by -humanaut- on 2010-05-10
What is your internet connection? Are you connecting wirelessly or hardwired? Same performs on 2 machines screams Connection problem to me.

---

### Post by Midnighter on 2010-05-10
You say you disabled IPV6. Did you do it in firefox, or alter a setting machine-wide?

---

### Post by applet3typod on 2010-05-10
Honestly, thats what I assumed... they are both hardwired to the same router (sounds like network) but I work with networks daily and have reset everything, even taking the network down and going directly from the modem to one of the machines, still lags.... Also, I had a friend connect his laptop to the wireless network(same router that my two are hardwired to) and his connects without a hitch. (running Windows Vista unfortunately)

Other ideas? things I can try?

---

### Post by applet3typod on 2010-05-10
> **Midnighter said:**
> You say you disabled IPV6. Did you do it in firefox, or alter a setting machine-wide?
I believe I did it in Firefox because I had to type something in the address bar to bring up the dialog box to do the changing. How could I change it for the system, and is that what I should do?

---

### Post by applet3typod on 2010-05-10
[IMG]file:///home/tyler/Desktop/Screenshot-System%20Monitor.png[/IMG][IMG]http://file:///home/tyler/Desktop/Screenshot-System%20Monitor.png[/IMG] This is a current look at my resources.

---

### Post by emoguitarist06 on 2010-05-10
What kind of graphics card do you have? Nvidia? ATI? Intel?
and what kind of problems are you having?

---

### Post by applet3typod on 2010-05-10
> **emoguitarist06 said:**
> What kind of graphics card do you have? Nvidia? ATI? Intel?
and what kind of problems are you having?
Nvidia. No major problems... just poor quality. images look blurry or pixelated. Nothing that would make using the computer unbearable, but I'm used to this thing rendering much better quality.

---

### Post by emoguitarist06 on 2010-05-10
Did you install the Nvidia drivers that came with Ubuntu 10.04?
Via System > Administration > Hardware Drivers??
I have an Asus EeePC 1201N with Nvidia Ion and I activated the driver that came with Ubuntu and my graphics work flawless with compiz and worldofwarcraft via wine

---

### Post by applet3typod on 2010-05-10
> **emoguitarist06 said:**
> Did you install the Nvidia drivers that came with Ubuntu 10.04?
Via System > Administration > Hardware Drivers??
I have an Asus EeePC 1201N with Nvidia Ion and I activated the driver that came with Ubuntu and my graphics work flawless with compiz and worldofwarcraft via wine
yes I did, and to be honest, the only thing I noticed was the ability to use compiz... nothing looks any different. lol

(BTW, thanks for reminding me of the need to get Wine. I'm on a WoW withdraw. lol)

---

### Post by emoguitarist06 on 2010-05-10
> **applet3typod said:**
> yes I did, and to be honest, the only thing I noticed was the ability to use compiz... nothing looks any different. lol

(BTW, thanks for reminding me of the need to get Wine. I'm on a WoW withdraw. lol)

Yup WoW is perfect with wine

well honestly... IDK... I haven't used Windows in years and besides WoW I'm not a gamer so I really have no other basis to compare my graphics to anything else..

good luck!
Happy *Bunting!

---

### Post by applet3typod on 2010-05-10
still no more ideas on the Firefox issue?

---

### Post by lovinglinux on 2010-05-10
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by fuzZzball on 2010-05-11
Yea, setting these options did it for me though, already posted it somewhere else..

type in the url about:config, press the button 'I'll be carefull, I promise!'.

Now set the following to true by just double clicking it (changes states from true to false, and the other way around).

network.dns.disableIPv6 = true
network.http.pipelining = true
network.http.proxy.pipelining = true

and set network.http.pipelining.maxrequest to 8 (tnx lovinglinux :D).

ICEcat has the same problems (duh ;)), fixed both of them.

cheers

---

### Post by lovinglinux on 2010-05-12
> **fuzZzball said:**
> ...and set network.http.pipelining.maxrequest to 10 or 12.

[network.http.pipelining.maxrequest](http://kb.mozillazine.org/Network.http.pipelining.maxrequests) only accepts values from 1 to 8.

---

