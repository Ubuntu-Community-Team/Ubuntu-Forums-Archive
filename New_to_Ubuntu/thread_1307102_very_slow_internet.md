---
title: "very slow internet"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by natman on 2009-10-30
Hi,
I just did a fresh install of kubuntu 9.10 things seems to be fine but the internet is just very slow - it works but is just slow ( both wifi and ethernet connections ) When i load up firefox it takes about 2-3 min before a homepage loads. Can anyone help me out?

Thanks:
Patrick

---

### Post by coolbrook on 2009-10-30
Have you tried shutting down your router for a few minutes and restarting?

---

### Post by natman on 2009-10-30
ya did that, no help i am also using the internet on another computer and its fine.

---

### Post by lovinglinux on 2009-10-30
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by natman on 2009-10-30
wow setting network dns from false to true seems to have solved it, thank you very much!!!

---

### Post by Fife3951 on 2009-10-31
I thought I was having the same problem with Karmic... but that fix didn't work for me... Synaptic is running at 20 kB/s...  Hmmm...

---

### Post by lovinglinux on 2009-10-31
> **Fife3951 said:**
> I thought I was having the same problem with Karmic... but that fix didn't work for me... Synaptic is running at 20 kB/s...  Hmmm...

What about Firefox?

To solve Synaptic issues, go to Software Sources and select another server. The default server is probably being hammered by too many downloads.

---

### Post by Fife3951 on 2009-10-31
> **lovinglinux said:**
> What about Firefox?

To solve Synaptic issues, go to Software Sources and select another server. The default server is probably being hammered by too many downloads.

Hey loving,

Firefox is slow, but manageable.

It's seems to be just on my install of Karmic.  Just as a test I tried DLing the .img of Karmic i386 from Ubuntu.com on both my Karmic install and on my other HP laptop running Vista.  Karmic was at 250 kbps and Vista was at 1.2 mbps.

Very frustrating, especially because I hate Vista.:confused:

---

### Post by k3lt01 on 2009-10-31
> **Fife3951 said:**
> I thought I was having the same problem with Karmic... but that fix didn't work for me... Synaptic is running at 20 kB/s...  Hmmm...That is probably because everyone is downloading the new version and updating putting a huge load on the server.

---

### Post by Jennifer82 on 2009-10-31
> **lovinglinux said:**
> What about Firefox?

To solve Synaptic issues, go to Software Sources and select another server. The default server is probably being hammered by too many downloads.

This.

---

### Post by Fife3951 on 2009-10-31
> **k3lt01 said:**
> That is probably because everyone is downloading the new version and updating putting a huge load on the server.

As I said before, it's not just when in synaptic.  It's doing anything in Karmic  

"It's seems to be just on my install of Karmic. Just as a test I tried DLing the .img of Karmic i386 from Ubuntu.com on both my Karmic install and on my other HP laptop running Vista. Karmic was at 250 kbps and Vista was at 1.2 mbps."

Two laptops on two different OS's downloading the same thing at the same time on the same network should not have that large of a difference in speed.

---

### Post by soupowl on 2009-11-05
I don't understand why this says "resolved". It is certainly not resolved.  I have tried every fix suggested, and none had any effect.  Out of interest, I just went through the process of wiping 9.10, re-installing 8.04 (Hardy Heron) - everything worked perfectly, good speeds etc, then upgrading to  8.10 (Intrepid Ibex), again everything perfect.  Then I upgraded to the Karmic Koala (better named the Sleepy Sloth), and bingo!  Once again the internet slowed, some sites were unusable, and my network connected showed 32% instead of its usual 100%.
This is hardly encouraging people to migrate from Microsoft.

---

### Post by sliketymo on 2009-11-05
Some people seem to be having good luck by disabling ipv6 in their kernel boot configuration.

---

### Post by k3lt01 on 2009-11-05
> **soupowl said:**
> I don't understand why this says "resolved". It is certainly not resolved.It is solved for the Original Poster, He/She is the only person who can mark the thread as such so for them their internet is working properly now.

May I suggest you start your own thread and post the specs of your PC and your problem as completely as possible. That way people will see you have a problem that needs to be [SOLVED].

---

### Post by lidex on 2009-11-11
> **soupowl said:**
>   Out of interest, I just went through the process of wiping 9.10, re-installing 8.04 (Hardy Heron) - everything worked perfectly, good speeds etc, then upgrading to  8.10 (Intrepid Ibex), again everything perfect.  Then I upgraded to the Karmic Koala (better named the Sleepy Sloth), and bingo!  Once again the internet slowed, some sites were unusable, and my network connected showed 32% instead of its usual 100%.
This is hardly encouraging people to migrate from Microsoft.
I thought one could only upgrade to the next release (other than between LTS). You should try a clean install.

---

### Post by t0mc4t on 2009-11-11
Hello,

May I know how to disable it?
Thanks...

> **sliketymo said:**
> Some people seem to be having good luck by disabling ipv6 in their kernel boot configuration.

---

